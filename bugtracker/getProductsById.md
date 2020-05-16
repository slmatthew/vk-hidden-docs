# bugtracker.getProductsById
Получить продукты по ID.

## Параметры

| Параметр    | Тип    | Описание                                     |
|-------------|--------|----------------------------------------------|
| product_ids | string | ID продуктов через запятую                   |
| extended    | int    | Флаг. Вернуть расширенную информацию или нет |

## Пример ответа
extended = 0

```json
{
  "response": {
    "items": [
      {
        "id": 1,
        "title": "Product",
        "description": "Description",
        "photo": "",
        "is_available": true,
        "reports_count": 5000,
        "wishes_reports_count": 1000
      }
    ]
  }
}
```

extended = 1

```json
{
  "response": {
    "items": [
      {
        "id": 1,
        "title": "Product",
        "description": "Description",
        "photo": "",
        "is_available": true,
        "counters": [
          {
            "type": "reporters_count",
            "count": 1000,
            "url": ""
          },
          {
            "type": "reports_count",
            "count": 5000,
            "url": "bugs?product=1&status=100"
          },
          {
            "type": "open_reports_count",
            "count": 500,
            "url": "bugs?product=1&status=0"
          },
          {
            "type": "in_progress_reports_count",
            "count": 3500,
            "url": "bugs?product=1&status=4,1"
          },
          {
            "type": "closed_reports_count",
            "count": 1500,
            "url": "bugs?product=1&status=2,5"
          }
        ],
        "reports_count": 5000,
        "wishes_reports_count": 1000,
        "open_reports_count": 50,
        "in_progress_reports_count": 3500,
        "closed_reports_count": 1500,
        "members_count": 1000,
        "can_add_report": true,
        "can_view_versions": true,
        "leave_hash": "",
        "leave_button": "Выйти из тестирования",
        "note": "Версия 1.0 (1111)",
        "status_note": "",
        "licence_status": 3,
        "is_licence_ok": true,
        "is_notify_enabled": true,
        "set_notify_hash": "",
        "can_view_branches": true
      }
    ]
  }
}
```

Проект, к которому можно присоединиться
```json
{
  "response": {
    "id": 2,
    "title": "Product",
    "description": "Description",
    "photo": "",
    "join_hash": "",
    "join_button": "Присоединиться",
    "note": "",
    "status_note": "Вы отказались от участия в тестировании",
    "licence_status": 5
  }
}
```