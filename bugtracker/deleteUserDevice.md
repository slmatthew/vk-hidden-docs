# bugtracker.deleteUserDevice
Удалить устройство

## Параметры

| Параметр       | Тип    | Описание      |
|----------------|--------|---------------|
| user_device_id | int    | ID устройства |
| hash           | string | `remove_hash` |

## Пример ответа
```json
{
  "response": {
    "can_add_device": true,
    "platform_ids": [
      1
    ]
  }
}
```