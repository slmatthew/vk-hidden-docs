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