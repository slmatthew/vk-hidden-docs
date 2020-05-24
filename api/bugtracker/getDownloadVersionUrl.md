# bugtracker.getDownloadVersionUrl
Получить адрес для загрузки версии.

## Параметр

| Параметр   | Тип    | Описание                          |
|------------|--------|-----------------------------------|
| product_id | int    | ID продукта                       |
| version_id | int    | ID версии                         |
| hash       | string | `download_hash` из объекта версии |

## Пример ответа
```json
{
  "response": {
    "url": "https://vk.link/to/version.apk",
    "app_title": "VK для Android",
    "bundle_name": "com.vkontakte.android",
    "build_id": 1234,
    "build_title": "1.0"
  }
}
```