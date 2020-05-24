# bugtracker.getProductBranches
Получить ветки продукта.

## Параметры

| Параметр   | Тип | Описание    |
|------------|-----|-------------|
| product_id | int | ID продукта |

## Пример ответа
```json
{
  "response": {
    "count": 1,
    "items": [
      {
        "id": 1,
        "title": "Branch name",
        "description": "Branch description",
        "photo": "",
        "parent_product": {
          "id": 2,
          "title": "Parent product",
          "description": "Parent product description",
          "photo": ""
        },
        "reports_count": 1
      }
    ]
  }
}
```