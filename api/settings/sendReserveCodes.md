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