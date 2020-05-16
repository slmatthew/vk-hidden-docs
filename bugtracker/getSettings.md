# bugtracker.getSettings
Получить список устройств

## Пример ответа
`login_ha` — логин HockeyApp
`login_tf` — логин TestFlight

```json
{
  "response": {
    "login_ha": "ha***@slmatthew.dev",
    "login_tf": "",
    "devices": [
      {
        "id": 1,
        "status": 0,
        "title": "Device",
        "platform": {
          "id": 1,
          "name": "Windows"
        },
        "model": "Model",
        "user_device_id": 483300000
      },
      {
        "id": 2,
        "status": 0,
        "title": "Device",
        "platform": {
          "id": 4,
          "name": "Android"
        },
        "model": "Model",
        "platform_version": {
          "id": 10012,
          "name": "9.0 P"
        },
        "user_device_id": 483300000
      }
    ],
    "can_add_device": true
  }
}
```