# shortVideo.getOwnerVideos
Получить клипы пользователя или сообщества

## Параметры

| Параметры | Тип | Описание          |
|-----------|-----|-------------------|
| owner_id  | int | ID владельца      |
| count     | int | Количество клипов |

## Пример ответа
При использовании кликабельных стикеров или музыки появляется поле `short_video_info`. Нужно подробнее изучить то, что может в нём содержаться.

```json
{
  "response": {
    "count": 5,
    "items": [
      {
        "can_comment": 1,
        "can_edit": 1,
        "can_like": 1,
        "can_repost": 1,
        "can_subscribe": 1,
        "can_add_to_faves": 0,
        "can_add": 0,
        "can_attach_link": 1,
        "comments": 0,
        "date": 1589286817,
        "description": "тестттттт #лучшедома [club22822305|@team]",
        "duration": 14,
        "image": [
          {
            "height": 96,
            "url": "https://i.mycdn.me/getVideoPreview?id=755834161897&idx=0&type=39&tkn=someString&fn=vid_s&c_uniq_tag=someTag",
            "width": 130,
            "with_padding": 1
          },
          {
            "height": 120,
            "url": "https://i.mycdn.me/getVideoPreview?id=755834161897&idx=0&type=39&tkn=someString&fn=vid_m&c_uniq_tag=someTag",
            "width": 160,
            "with_padding": 1
          },
          {
            "height": 240,
            "url": "https://i.mycdn.me/getVideoPreview?id=755834161897&idx=0&type=39&tkn=someString&fn=vid_l&c_uniq_tag=someTag",
            "width": 320,
            "with_padding": 1
          },
          {
            "height": 450,
            "url": "https://i.mycdn.me/getVideoPreview?id=755834161897&idx=0&type=39&tkn=someString&fn=vid_x&c_uniq_tag=someTag",
            "width": 800,
            "with_padding": 1
          },
          {
            "height": 720,
            "url": "https://i.mycdn.me/getVideoPreview?id=755834161897&idx=0&type=39&tkn=someString&fn=vid_w&c_uniq_tag=someTag",
            "width": 405
          },
          {
            "height": 569,
            "url": "https://i.mycdn.me/getVideoPreview?id=755834161897&idx=0&type=39&tkn=someString&fn=vid_t&c_uniq_tag=someTag",
            "width": 320
          },
          {
            "height": 1280,
            "url": "https://i.mycdn.me/getVideoPreview?id=755834161897&idx=0&type=39&tkn=someString&fn=vid_u&c_uniq_tag=someTag",
            "width": 720
          }
        ],
        "first_frame": [
          {
            "height": 720,
            "url": "https://i.mycdn.me/getVideoPreview?id=755834161897&idx=0&type=32&tkn=someString&c_uniq_tag=someTag",
            "width": 405
          },
          {
            "height": 480,
            "url": "https://i.mycdn.me/getVideoPreview?id=755834161897&idx=0&type=33&tkn=someString&c_uniq_tag=someTag",
            "width": 270
          },
          {
            "height": 240,
            "url": "https://i.mycdn.me/getVideoPreview?id=755834161897&idx=0&type=34&tkn=someString&c_uniq_tag=someTag",
            "width": 135
          },
          {
            "height": 128,
            "url": "https://i.mycdn.me/getVideoPreview?id=755834161897&idx=0&type=35&tkn=someString&c_uniq_tag=someTag",
            "width": 72
          },
          {
            "height": 960,
            "url": "https://i.mycdn.me/getVideoPreview?id=755834161897&idx=0&type=38&tkn=someString&c_uniq_tag=someTag",
            "width": 540
          },
          {
            "height": 1280,
            "url": "https://i.mycdn.me/getVideoPreview?id=755834161897&idx=0&type=39&tkn=someString&c_uniq_tag=someTag",
            "width": 720
          }
        ],
        "width": 1080,
        "height": 1920,
        "id": 456230000,
        "owner_id": 305360617,
        "title": "Клип @slmatthew",
        "player": "https://vk.com/video_ext.php",
        "added": 1,
        "track_code": "someTrackCode",
        "repeat": 1,
        "type": "short_video",
        "views": 97,
        "likes": {
          "count": 1,
          "user_likes": 0
        },
        "reposts": {
          "count": 0,
          "user_reposted": 0
        },
        "short_video_info": {
          "audio": {

          }
        }
      }
    ],
    "next_from": "PUkGEFNHDhIZAg1UDwBeUHRYUE8GBhY",
    "profiles": [
      {
        "id": 305360617,
        "first_name": "Матвей",
        "last_name": "Вишневский",
        "is_closed": false,
        "can_access_closed": true
      }
    ],
    "groups": []
  }
}
```