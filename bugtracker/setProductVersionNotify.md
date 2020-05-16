# bugtracker.setProductVersionNotify
Настроить уведомления о новых версиях

## Параметры

| Параметры  | Тип    | Описание                                              |
|------------|--------|-------------------------------------------------------|
| product_id | int    | ID продукта                                           |
| hash       | string | `set_notify_hash` из `getProductsById` с `extended=1` |

## Пример ответа
```json
{
  "response": {
    "is_notify_enabled": false
  }
}
```