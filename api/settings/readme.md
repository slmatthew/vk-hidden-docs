# settings
Секция для работы с настройками безопасности. Обязательно прочитайте пункт [Подтверждение паролем](#подтверждение-паролем).

## Список методов
* [settings.getActivityHistory](getActivityHistory.md)
* [settings.getReserveCodes](getReserveCodes.md)
* [settings.getSecurityInfo](getSecurityInfo.md)
* [settings.getValidateDevices](getValidateDevices.md)
* [settings.sendReserveCodes](sendReserveCodes.md)

## Доступ
1. [Авторизоваться](../../auth/password.md) на `vk.com` и сохранить куки
2. Сделать POST-запрос на `https://login.vk.com/?app_id=7344294&act=web_token&vkui=1` со следующими заголовками:
  * User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:77.0) Gecko/20100101 Firefox/77.0 *или от любого другого браузера*
  * Передайте cookies, полученные на первом этапе
3. Получить токен из запроса

```json
{
  "access_token": ""
}
```

## Подтверждение паролем
При вызове некоторых методов, например [settings.getValidateDevices](getValidateDevices.md), может потребоваться подтверждение аккаунта. Обычная ошибка выглядит так:

```json
{
  "error": {
    "error_code": 15,
    "error_msg": "Access denied: you must validate your account for this action"
  }
}
```

С первого взлгяда непонятно, как нужно подтвердить аккаунт.

**Всё меняется**, если добавить в запрос параметр `vkui = 1`. Ошибка теперь выглядит так:

```json
{
  "error": {
    "error_code": 3302,
    "error_msg": "Password validation needed",
    "session": "qwerty12345"
  }
}
```

> Вы можете к каждому запросу добавлять `vkui = 1`

Теперь вы можете подтвердить действие с помощью пароля. Для этого нужно вызвать метод `auth.validationPassword` с этими параметрами:
* `password` (string) — пароль
* `session` (string) — значение поля `session` из объекта ошибки

При успешном подтверждении ответ будет таким:

```json
{
  "response": {
    "code": 23,
    "message": ""
  }
}
```

После этого вы можете вызвать метод, для которого требовалось подтверждение.