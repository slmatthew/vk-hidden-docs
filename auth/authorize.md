# Переполучение токена со сменой приложения
Перед реализацией нижеописанных действий не забудьте [получить токен, используя прямую авторизацию](password.md).

## Что необходимо для такой авторизации
1. Откройте страницу `https://vk.com/editapp?id={APP_ID}&section=options`
2. Заполните поля «Название пакета для Android» и «Отпечаток сертификата для Android» (подойдут любые значения)
3. [Получите](password.md) токен от приложения Android (проверялось с ним)

## Реализация
Подготовьте запрос к `https://oauth.vk.com/authorize` со следующими параметрами:

| Параметр        | Тип    | Описание                                          |
|-----------------|--------|---------------------------------------------------|
| redirect_uri    | string | `https://oauth.vk.com/blank.html`                 |
| display         | string | `page`                                            |
| response_type   | string | `token`                                           |
| access_token    | string | [Полученный токен](password.md)                   |
| revoke          | int    | `1`                                               |
| lang            | string | `ru`                                              |
| scope           | int    | `136297695` *(для всех прав доступа)*             |
| client_id       | int    | ID вашего приложения                              |
| v               | string | Версия API. Рекомендуется использовать `5.130`    |
| sdk_package     | string | Значение поля «Название пакета для Android»       |
| sdk_fingerprint | string | Значение поля «Отпечаток сертификата для Android» |

На данном этапе вы можете выбрать между двумя способами: самостоятельно получить токен в браузере или реализовать это через код.

### Самостоятельное получение токена

1. Откройте [url](#реализация)
2. Нажмите кнопку «Разрешить»
3. Скопируйте токен из url, на который произошел редирект

### Эмуляция действий пользователя

1. Получите содержимое [страницы](#реализация)
2. Получите часть ссылки из содержимого страницы с помощью регулярки `/(\/auth_by_token.+?)"/`
3. Составьте ссылку вида `https://oauth.vk.com${полученная часть ссылки}`. Отправьте запрос
4. В поле `Location` в хедерах будет ссылка. Получите оттуда `access_token` с помощью регулярки `/#access_token=([a-z0-9]{85})/`

Немного измененный пример из [кода VK Desktop](https://github.com/danyadev/vk-desktop/blob/master/src/components/auth/index.js):

```js
const querystring = require('querystring');
const request = require('./my-awesome-request');

function getAppToken(androidToken) {
  const query = querystring({
    redirect_uri: 'https://oauth.vk.com/blank.html',
    display: 'page',
    response_type: 'token',
    access_token: androidToken,
    revoke: 1,
    lang: 'ru',
    scope: 136297695, // все возможные права
    client_id: 6717234, // ID приложения VK Desktop
    v: '5.130',
    sdk_package: 'ru.danyadev.vkdesktop',
    sdk_fingerprint: '9E76F3AF885CD6A1E2378197D4E7DF1B2C17E46C'
  });

  // data = строка, в которой находится верстка сайта
  const { data } = await request(`https://oauth.vk.com/authorize?${query}`);

  const link = 'https://oauth.vk.com' + data.match(/(\/auth_by_token.+?)"/)[1];
  const { headers } = await request(link);

  return headers.location.match(/#access_token=([a-z0-9]{85})/)[1];
}
```
