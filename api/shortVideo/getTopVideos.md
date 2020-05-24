# shortVideo.getTopVideos
Получить видосы для ленты

## Параметры
> `?` в конце типа означает, что это не точно

| Параметр   | Тип     | Описание                                                       |
|------------|---------|----------------------------------------------------------------|
| tag        | string? | Возможно, хештег                                               |
| trackId    | string? | Возможно, ID аудиозаписи в формате `audio{owner_id}_{mark_id}` |
| maskId     | string? | ID маски. Наверное, в формате `mask{owner_id}_{mask_id}`       |
| from_video | string? | Оффсет. Наверное, в формате `video{owner_id}_{video_id}`       |
| track_code | string  | Используется для сбора статистики                              |
| filters    | string  | Неизвестно                                                     |
| count      | int     | Количество клипов                                              |

## Пример ответа
```json
{
  "response": {
    "count": 672,
    "items": [
      {
        "can_comment": 1,
        "can_like": 1,
        "can_repost": 0,
        "can_subscribe": 1,
        "can_add_to_faves": 0,
        "can_add": 0,
        "comments": 1,
        "date": 1589147157,
        "description": "Как думайте, почему до сих пор так? 😔",
        "duration": 34,
        "image": [
          {
            "height": 96,
            "url": "https://i.mycdn.me/getVideoPreview?id=703917263514&idx=0&type=39&tkn=someString&fn=vid_s&c_uniq_tag=someTag",
            "width": 130,
            "with_padding": 1
          },
          {
            "height": 120,
            "url": "https://i.mycdn.me/getVideoPreview?id=703917263514&idx=0&type=39&tkn=someString&fn=vid_m&c_uniq_tag=someTag",
            "width": 160,
            "with_padding": 1
          },
          {
            "height": 240,
            "url": "https://i.mycdn.me/getVideoPreview?id=703917263514&idx=0&type=39&tkn=someString&fn=vid_l&c_uniq_tag=someTag",
            "width": 320,
            "with_padding": 1
          },
          {
            "height": 450,
            "url": "https://i.mycdn.me/getVideoPreview?id=703917263514&idx=0&type=39&tkn=someString&fn=vid_x&c_uniq_tag=someTag",
            "width": 800,
            "with_padding": 1
          },
          {
            "height": 720,
            "url": "https://i.mycdn.me/getVideoPreview?id=703917263514&idx=0&type=39&tkn=someString&fn=vid_w&c_uniq_tag=someTag",
            "width": 405
          },
          {
            "height": 569,
            "url": "https://i.mycdn.me/getVideoPreview?id=703917263514&idx=0&type=39&tkn=someString&fn=vid_t&c_uniq_tag=someTag",
            "width": 320
          },
          {
            "height": 1280,
            "url": "https://i.mycdn.me/getVideoPreview?id=703917263514&idx=0&type=39&tkn=someString&fn=vid_u&c_uniq_tag=someTag",
            "width": 720
          }
        ],
        "first_frame": [
          {
            "height": 720,
            "url": "https://i.mycdn.me/getVideoPreview?id=703917263514&idx=0&type=32&tkn=someString&c_uniq_tag=someTag",
            "width": 405
          },
          {
            "height": 480,
            "url": "https://i.mycdn.me/getVideoPreview?id=703917263514&idx=0&type=33&tkn=someString&c_uniq_tag=someTag",
            "width": 270
          },
          {
            "height": 240,
            "url": "https://i.mycdn.me/getVideoPreview?id=703917263514&idx=0&type=34&tkn=someString&c_uniq_tag=someTag",
            "width": 135
          },
          {
            "height": 128,
            "url": "https://i.mycdn.me/getVideoPreview?id=703917263514&idx=0&type=35&tkn=someString&c_uniq_tag=someTag",
            "width": 72
          },
          {
            "height": 960,
            "url": "https://i.mycdn.me/getVideoPreview?id=703917263514&idx=0&type=38&tkn=someString&c_uniq_tag=someTag",
            "width": 540
          },
          {
            "height": 1280,
            "url": "https://i.mycdn.me/getVideoPreview?id=703917263514&idx=0&type=39&tkn=someString&c_uniq_tag=someTag",
            "width": 720
          }
        ],
        "width": 480,
        "height": 852,
        "id": 456230000,
        "owner_id": 537872794,
        "title": "Клип @ismayamusic",
        "player": "https://vk.com/video_ext.php",
        "added": 0,
        "track_code": "",
        "repeat": 1,
        "type": "short_video",
        "views": 108,
        "likes": {
          "count": 2,
          "user_likes": 0
        }
      }
    ],
    "next_from": "PUkIGFZcBBRkUUs6YXFfKRIiWztPV1soPDpfOmFxXykSIls7T1dbKDwmVFQZFg0UKQY2AFxQDglkUUtUSA",
    "profiles": [
      {
        "id": 537872794,
        "first_name": "Маис",
        "last_name": "Мамедов",
        "is_closed": false,
        "can_access_closed": true
      }
    ],
    "groups": []
  }
}
```