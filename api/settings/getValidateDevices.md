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