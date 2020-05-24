# bugtracker.addUserDevice
Добавить устройства

## Параметры

| Параметр  | Тип    | Описание      |
|-----------|--------|---------------|
| device_id | int    | ID устройства |
| hash      | string | `add_hash`    |

## Пример ответа
```json
{
  "response": {
    "can_add_device": true,
    "device": {
      "id": 1,
      "status": 0,
      "title": "Device",
      "platform": {
        "id": 4,
        "name": "Android"
      },
      "model": "Model",
      "platform_version": {
        "id": 10007,
        "name": "6.0 Marshmallow"
      },
      "user_device_id": 483300000,
      "edit_hash": "",
      "remove_hash": ""
    }
  }
}
```