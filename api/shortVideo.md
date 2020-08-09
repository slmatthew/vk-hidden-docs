# shortVideo
Секция методов `shortVideo` используется в клипах.

## Список методов
* [shortVideo.create](create.md)
* [shortVideo.getAudioMeta](getAudioMeta.md)
* [shortVideo.getOwnerVideos](getOwnerVideos.md)
* [shortVideo.getTopVideos](getTopVideos.md)
* [shortVideo.markClipsBadgeViewed](markClipsBadgeViewed.md)
* [shortVideo.notInterested](notInterested.md)

## Доступ
Для доступа к этой секции нужен токен от VK для Android.

## Кое-что ещё
Технически, клипы — это обычные видео, но у них отличается поле `type`. У обычных видео `type = video`, у клипов `type = short_video`.

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

# shortVideo.getAudioMeta
Получить данные об аудиозаписи, которую можно использовать в клипе.

## Параметры

| Параметр | Тип    | Описание                                                      |
|----------|--------|---------------------------------------------------------------|
| audio    | string | Аудиозапись в формате `{owner_id}_{audio_id}`, например `1_1` |

## Пример ответа
```json
{
  "response": {
    "url": "https://vk.link/to/audio.mp3",
    "waveform": [0, 0, 1, 0, 0],
    "start_position": 53
  }
}
```

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

# shortVideo.markClipsBadgeViewed
Пометить вкладку «Клипы» как просмотренную

## Пример ответа
```json
{
  "response": 1
}
```

# shortVideo.notInterested
Пометить клип как неинтересный

## Параметры

| Параметр | Тип | Описание           |
|----------|-----|--------------------|
| owner_id | int | ID владельца клипа |
| video_id | int | ID видео           |

## Пример ответа
```json
{
  "response": 1
}
```