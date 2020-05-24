# bugtracker.saveBugreport
Сохранить репорт

## Параметры

| Параметр           | Тип     | Описание                                           |
|--------------------|---------|----------------------------------------------------|
| bugreport_id       | int     | ID репорта. Если 0, то будет создан новый репорт   |
| product_id         | int     | ID продукта                                        |
| title              | string  | Заголовок                                          |
| description        | string  | Шаги воспроизведения                               |
| state_supposed     | string  | Ожидаемый результат                                |
| state_actual       | string  | Фактический результат                              |
| severity           | int     | Приоритет                                          |
| issue_type         | int     | Тип проблемы                                       |
| confidential       | int     | Флаг. Отвечает за скрытие документов               |
| attachments        | string  | Скорее всего, вложения в стиле `photo1_1,photo1_2` |
| tags               | string  | ID тегов через запятую                             |
| platforms          | string  | ID платформ через запятую                          |
| platforms_versions | string  | Версии платформ через запятую                      |
| user_devices       | string  | ID устройств через запятую                         |
| phone              | unknown | ?                                                  |
| hash               | string  | `hash` из `bugtracker.editBugreport`               |
| comment            | unknown | ?                                                  |

## Пример ответа
```json
{
  "response": {
    "bugreport_id": 123
  }
}
```