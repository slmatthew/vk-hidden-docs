# bugtracker.updateBugreportVersion
Добавить отметку об актуальности отчета в новой версии продукта

## Параметры

| Параметр     | Тип    | Описание                               |
|--------------|--------|----------------------------------------|
| bugreport_id | int    | ID репорта                             |
| hash         | string | `bugreport.close_on_update.close_hash` |
| actual       | int    | Флаг. `1` - актуально                  |

## Пример ответа
```json
{
  "response": 1
}
```