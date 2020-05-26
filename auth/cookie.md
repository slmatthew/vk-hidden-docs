# Авторизация с получением cookies
Авторизация с получением cookies необходима далеко не во всех случаях, потому что почти все действия можно выполнить через API.

## vk.com
Для начала сделайте запрос к `https://vk.com`, сохраните куки.

В полученном HTML найдите два хеша. Можно использовать эти регулярки:
* `/name=\"ip_h\" value=\"(.*?)\"/s`
* `/name=\"lg_h\" value=\"(.*?)\"/s`

Сделайте POST-запрос к `https://login.vk.com/?act=login` с этими параметрами:
* `act = login`
* `role = al_frame`
* `_origin = https://vk.com`
* `utf8 = 1`
* `email` - логин
* `pass` - пароль
* `lg_h` - полученный `lg_h`
* `ip_h` - полученный `ip_h`

Сохраните полученные куки, после чего сделайте запрос к значению поля `Location` из хедеров. Сохраните куки.

Вот пример кода на PHP:

```php
// requests.php
function request(string $url, array &$cookie, array $postfields = [], string $agent = 'Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/46.0.2490.86 Safari/537.36'): array {
  $ch = curl_init($url);
  $headers = [];

  curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
  curl_setopt($ch, CURLOPT_USERAGENT, $agent);
  curl_setopt($ch, CURLOPT_SSL_VERIFYPEER, false);

  if($cookie) {
    $to_send = [];
    foreach($cookie as $name => $val) {
      $to_send[] = "{$name}={$val}";
    }

    curl_setopt($ch, CURLOPT_COOKIE, implode('; ', $to_send));
  }

  curl_setopt($ch, CURLOPT_HEADERFUNCTION,
    function($curl, $header) use(&$headers) {
      $len = strlen($header);
      $header = explode(':', $header, 2);
      if(count($header) < 2) {
        return $len;
      }

      $headers[strtolower(trim($header[0]))][] = trim($header[1]);

      return $len;
    }
  );

  if(!empty($postfields)) {
    curl_setopt($ch, CURLOPT_POST, true);
    curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($postfields));
  }

  $exec = curl_exec($ch);
  curl_close($ch);

  $data = [
    'data' => $exec,
    'headers' => $headers
  ];

  if(isset($headers['set-cookie'])) {
    foreach($headers['set-cookie'] as $c) {
      preg_match("!(.*?)=(.*?);(.*)!s", $c, $res);

      if($res[2] == 'DELETED') {
        if(isset($cookie[$res[1]])) unset($cookie[$res[1]]);
      } else {
        $cookie[$res[1]] = $res[2].';'.$res[3];
      }
    }
  }

  return $data;
}

// main.php
const VK_USERNAME = '';
const VK_PASSWORD = '';

$cookie = [];

$main = request('https://vk.com', $cookie);

preg_match('/name=\"ip_h\" value=\"(.*?)\"/s', $main['data'], $ip_h);
preg_match('/name=\"lg_h\" value=\"(.*?)\"/s', $main['data'], $lg_h);

$ip_h = $ip_h[1];
$lg_h = $lg_h[1];

$post = [
  'act' => 'login',
  'role' => 'al_frame',
  '_origin' => 'https://vk.com',
  'utf8' => 1,
  'email' => VK_USERNAME,
  'pass' => VK_PASSWORD,
  'lg_h' => $lg_h,
  'ip_h' => $ip_h
];

$login = request('https://login.vk.com/?act=login', $cookie, $post);
if(!isset($login['headers']['location'])) {
  die('Login failed');
}

$final = request($login['headers']['location'][0], $cookie);
if(!isset($final['headers']['set-cookie'])) {
  die('Login (2) failed');
}
```