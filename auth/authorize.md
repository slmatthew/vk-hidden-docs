# Переполучение токена со сменой приложения
Получив токен с использованием [прямой авторизации](password.md), вы можете получить токен от своего приложения.

## Что необходимо для такой авторизации
1. Откройте страницу `https://vk.com/editapp?id={APP_ID}&section=options`
2. Заполните поля «Название пакета для Android» и «Отпечаток сертификата для Android» (подойдут любые значения)
3. [Получите](password.md) токен от приложения Android (проверялось с ним)

## Реализация
Подготовьте запрос к `https://oauth.vk.com/authorize` со следующими параметрами:
* `redirect_uri = https://oauth.vk.com/blank.html`
* `display = page`
* `response_type = token`
* `access_token` — полученный токен
* `revoke = 1`
* `lang = ru`
* `scope = 136297695`
* `client_id` — ID вашего приложения
* `v` — версия VK API (например, `5.130`)
* `sdk_package` — значение поля «Название пакета для Android»
* `sdk_fingerprint` — значение поля «Отпечаток сертификата для Android»

Здесь вы можете либо открыть эту страницу в браузере или вебвью, либо получить токен автоматически с помощью дополнительного запроса.

Если открыть страницу, то покажется страница с названием приложения, списком прав и кнопкой для получения токена. При её нажатии вас перебросит на `redirect_uri` (`https://oauth.vk.com/blank.html`), где в самой ссылке и будет находиться токен.

Если же вы хотите получить токен автоматически, то нужно получить содержимое этой страницы и с помощью регулярного выражения `/(\/auth_by_token.+?)"/` получить часть ссылки.

Затем нужно составить ссылку вида `https://oauth.vk.com${полученная часть ссылки}` и сделать туда запрос. Полученная ссылка перенаправит вас уже на `https://oauth.vk.com/blank.html` с токеном в ссылке, который можно получить с помощью регулярного выражения `/#access_token=([a-z0-9]{85})/`.

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
