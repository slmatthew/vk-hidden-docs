# Переполучение токена со сменой приложения
Получив токен с использованием [прямой авторизации](password.md), вы можете получить токен от своего приложения.

## Что необходимо для такой авторизации
1. Откройте страницу `https://vk.com/editapp?id={APP_ID}&section=options`
2. Заполните поля «Название пакета для Android» и «Отпечаток сертификата для Android»
3. [Получите](password.md) токен от приложения Android (проверялось с ним)

## Реализация
Отправьте запрос к `https://oauth.vk.com/authorize` со следующими параметрами:
* `redirect_uri = https://oauth.vk.com/blank.html`
* `display = page`
* `response_type = token`
* `access_token` — полученный токен
* `revoke = 1`
* `lang = ru`
* `scope = 136297695`
* `client_id` — ID вашего приложения
* `v = 5.130`
* `sdk_package` — значение поля «Название пакета для Android»
* `sdk_fingerprint` — значение поля «Отпечаток сертификата для Android»

На этом этапе вы можете либо открыть эту страницу, либо получить токен другим способом.

Из полученной HTML-разметки вы должны вытащить ссылку на страницу авторизации с помощью регулярки `/(\/auth_by_token.+?)"/`. Возьмем полученную строку за `link`

Далее отправьте запрос на `https://oauth.vk.com{link}` и из хедера `Location` достаньте токен с помощью регулярки `/#access_token=([a-z0-9]{85})/`.

Немного измененный пример из [кода VK Desktop](https://github.com/danyadev/vk-desktop/blob/master/src/components/auth/index.js):

```js
function getToken(token) {
  const query = qs({
    redirect_uri: 'https://oauth.vk.com/blank.html',
    display: 'page',
    response_type: 'token',
    access_token: token,
    revoke: 1,
    lang: 'ru',
    scope: 136297695,
    client_id: 6717234,
    v: '5.130',
    sdk_package: 'ru.danyadev.vkdesktop',
    sdk_fingerprint: '9E76F3AF885CD6A1E2378197D4E7DF1B2C17E46C'
  });

  const { data } = await request(`https://oauth.vk.com/authorize?${query}`);

  const link = 'https://oauth.vk.com' + data.match(/(\/auth_by_token.+?)"/)[1];
  const { headers } = await request(link);

  return headers.location.match(/#access_token=([a-z0-9]{85})/)[1];
}
```