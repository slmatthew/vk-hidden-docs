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

# settings.getActivityHistory
Получить историю активности

## Параметры

| Параметр | Тип    | Описание                                                         |
|----------|--------|------------------------------------------------------------------|
| hash     | string | `history_hash` из [settings.getSecurityInfo](getSecurityInfo.md) |

## Пример ответа
```json
{
  "response": {
    "code": 241,
    "history": [
      {
        "device": "laptop",
        "platform": "Windows",
        "browser": "Браузер Firefox",
        "country": "Россия",
        "city": "Москва",
        "date": "сегодня в 23:40",
        "ip": "192.168.0.1",
        "remix_seed": "123456789",
        "photo": "https://vk.com/images/activity_history/icon_78.png"
      },
      {
        "device": "android",
        "platform": "HMD Global Nokia 5.1 Plus",
        "browser": "Приложение ВКонтакте",
        "country": "Россия",
        "city": "Москва",
        "date": "сегодня в 22:25",
        "ip": "192.168.0.1",
        "remix_seed": "12345678",
        "photo": "https://vk.com/images/activity_history/icon_78.png"
      },
      {
        "device": "unrecognized",
        "platform": "Неизвестный тип устройства",
        "browser": "Приложение slmatthew apps",
        "country": "Франция",
        "city": "",
        "date": "сегодня в 22:00",
        "ip": "192.168.0.1",
        "remix_seed": "123456789",
        "photo": "https://vk.com/images/dquestion_d.png"
      }
    ]
  }
}
```

# settings.getReserveCodes
Получить список резервных кодов 2FA

## Параметры

| Параметр | Тип    | Описание                                                       |
|----------|--------|----------------------------------------------------------------|
| hash     | string | `codes_hash` из [settings.getSecurityInfo](getSecurityInfo.md) |

## Пример ответа
Если в начале кода стоит знак `-` — код уже был использован

```json
{
  "response": {
    "code": 155,
    "email": "me***@slmatthew.dev",
    "list": [
      {
        "code": "-12341234"
      },
      {
        "code": "12341234"
      },
      {
        "code": "12341234"
      },
      {
        "code": "12341234"
      },
      {
        "code": "12341234"
      },
      {
        "code": "12341234"
      },
      {
        "code": "12341234"
      },
      {
        "code": "12341234"
      },
      {
        "code": "12341234"
      },
      {
        "code": "12341234"
      }
    ]
  }
}
```

# settings.getSecurityInfo
Возвращает данные для раздела «Безопасность»

## Пример ответа
```json
{
  "response": {
    "code": 251,
    "can_enable_otp": true,
    "reset_hash": "jfugibofksltphjgufbldkfjbugjffjb",
    "has_otp_by_sms": true,
    "has_otp_by_app": true,
    "otp_hash": "ajchgyeoflbpdyfjbs",
    "logout_hash": "1234567890_ajchgyeoflbpdyfjbs",
    "codes_hash": "ajchgyeoflbpdyfjbs",
    "history_hash": "ajchgyeoflbpdyfjbs",
    "phone_masked": "+7 *** *** ** 11",
    "email_masked": "me***@slmatthew.dev",
    "password_change_date": "обновлён год назад",
    "change_email_hash": "1234567890_ajchgyeoflbpdyfjbs",
    "otp_reset_hash": "jfugibofksltphjgufbldkfjbugjffjb",
    "trusted_hash": "ajchgyeoflbpdyfjbs",
    "trusted_date": 1582562000,
    "validate_devices_count": 2,
    "validate_devices_hash": "ajchgyeoflbpdyfjbs",
    "last_activity": [
      {
        "remix_seed": "123456789",
        "time_str": "сегодня в 23:23",
        "country": "Россия",
        "browser": "Браузер Firefox",
        "ip": "192.168.0.1",
        "photo": "https://vk.com/images/activity_history/icon_78.png"
      },
      {
        "remix_seed": "123456789",
        "time_str": "сегодня в 22:25",
        "country": "Россия",
        "browser": "Приложение ВКонтакте",
        "ip": "192.168.0.1",
        "photo": "https://vk.com/images/activity_history/icon_78.png"
      },
      {
        "remix_seed": "12345678",
        "time_str": "сегодня в 22:25",
        "country": "Россия",
        "browser": "Приложение ВКонтакте",
        "ip": "192.168.0.1",
        "photo": "https://vk.com/images/activity_history/icon_78.png"
      }
    ]
  }
}
```

# settings.getValidateDevices
Получить список привязанных устройств

## Параметры

| Параметр | Тип    | Описание                                                                  |
|----------|--------|---------------------------------------------------------------------------|
| hash     | string | `validate_devices_hash` из [settings.getSecurityInfo](getSecurityInfo.md) |

## Пример ответа
```json
{
  "response": {
    "code": 302,
    "devices": [
      {
        "device_hash": "32characters",
        "name": "Device 1",
        "date": "8 мая",
        "delete_hash": "18characters"
      },
      {
        "device_hash": "32characters",
        "name": "Device 2",
        "date": "12 апреля",
        "delete_hash": "18characters"
      }
    ]
  }
}
```

# settings.sendReserveCodes
Отправить резервные коды 2FA

## Параметры

| Параметр | Тип    | Описание                                                       |
|----------|--------|----------------------------------------------------------------|
| hash     | string | `codes_hash` из [settings.getSecurityInfo](getSecurityInfo.md) |

## Пример ответа
```json
{
  "response": {
    "code": 281
  }
}
```