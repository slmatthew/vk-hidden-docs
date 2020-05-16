# shortVideo.create
Возвращает адрес для загрузки клипа.

## Параметры

| Параметр           | Тип    | Описание                                               |
|--------------------|--------|--------------------------------------------------------|
| clickable_stickers | string | Кликабельные стикеры неизвестно в каком формате        |
| file_size          | float  | Размер файла: от 16 384 до 2 147 483 647. Обязательный |
| title              | string | Название клипа (или видео). Обязательный               |
| description        | string | Описание клипа. Обязательный                           |
| group_id           | int    | ID группы                                              |
| latitude           | string | Широта                                                 |
| longitude          | string | Долгота                                                |
| audio_id           | string | Аудиозапись неизвестно в каком формате                 |
| analytics          | string | Неизвестно                                             |
| mask_ids           | string | ID масок                                               |
| wallpost           | int    | Флаг. Опубликовать клип на стене или нет               |

К сожалению, я так и не разобрался, как правильно загружать клипы.

## Пример ответа
```json
{
  "response": {
    "owner_id": 305360617,
    "video_id": 456230000,
    "upload_url": "https://vu.mycdn.me/upload.do?sig=123qwerty&expires=1589466332158&clientType=15&appId=vkintegration&id=2013406630000&userId=0"
  }
}
```