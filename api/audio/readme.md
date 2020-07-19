# audio
Методы для работы с аудиозаписями

## Список методов
* [audio.add](#audioadd) — Добавить аудиозапись к себе
* [audio.addToPlaylist](#audioaddtoplaylist) — Добавить аудиозапись в плейлист
* [audio.createPlaylist](#audiocreateplaylist) — Создать плейлист
* [audio.delete](#audiodelete) — Удалить свою аудиозапись
* [audio.deletePlaylist](#audiodeleteplaylist) — Удалить плейлист
* [audio.edit](#audioedit) — Отредактировать данные аудиозаписи
* [audio.editPlaylist](#audioeditplaylist) — Отредактировать данные плейлиста
* [audio.get](#audioget) — Получить список аудиозаписей
* [audio.getAlbumsByArtist](#audiogetalbumsbyartist) — Получить альбомы исполнителя
* [audio.getAudiosByArtist](#audiogetaudiosbyartist) — Получить треки исполнителя
* [audio.getBroadcast](#audiogetbroadcast) — Включена ли трансляция треков в статус
* [audio.getById](#audiogetbyid) — Получить аудиозаписи по ID
* [audio.getCatalog](#audiogetcatalog) — Получить список секций с аудиозаписями или плейлистами
* [audio.getCatalogBlockById](#audiogetcatalogblockbyid) — Получить секцию
* [audio.getCount](#audiogetcount) — Получить количество аудиозаписей
* [audio.getHints](#audiogethints) — Получить подсказки при поиске
* [audio.getLyrics](#audiogetlyrics) — Получить слова песни
* [audio.getPlaylistById](#audiogetplaylistbyid) — Получить плейлист по ID
* [audio.getPlaylists](#audiogetplaylists) — Получить список плейлистов
* [audio.getPopular](#audiogetpopular) — Получить популярные треки
* [audio.getRecentAudios](#audiogetrecentaudios) — Получить недавно прослушанные треки
* [audio.getRecommendations](#audiogetrecommendations) — Получить музыкальные рекомендации или похожие на аудиозапись треки
* [audio.getRestrictionPopup](#audiogetrestrictionpopup) — Получить информацию об ограничении доступа к аудиозаписи
* [audio.getSearchTrends](#audiogetsearchtrends) — Получить популярные поисковые запросы
* [audio.getStoryCatalog](#audiogetstorycatalog) — Получить аудиозаписи, которые можно использовать в историях
* [audio.getStorySearchCatalog](#audiogetstorysearchcatalog) — Поиск аудиозаписей, которые можно использовать в историях
* [audio.getUploadServer](#audiogetuploadserver) — Получить адрес для загрузки аудиозаписи
* [audio.reorder](#audioreorder) — Изменить положение аудиозаписи
* [audio.reorderPlaylists](#audioreorderplaylists) — Изменить положение плейлиста
* [audio.restore](#audiorestore) — Восстановить удаленную аудиозапись
* [audio.save](#audiosave) — Сохранить аудиозапись после загрузки
* [audio.search](#audiosearch) — Поиск по аудиозаписям
* [audio.searchAlbums](#audiosearchalbums) — Поиск альбомов
* [audio.searchArtists](#audiosearchartists) — Поиск исполнителей
* [audio.searchMain](#audiosearchmain) — общий поиск
* [audio.searchPlaylists](#audiosearchplaylists) — найти плейлист
* [audio.setBroadcast](#audiosetbroadcast) — установить аудиозапись в статус

## audio.add
Добавить аудиозапись к себе

### Параметры

| Параметр   | Тип    | Описание                |
|------------|--------|-------------------------|
| owner_id   | int    | ID владельца            |
| audio_id   | int    | ID аудио                |
| access_key | string | Ключ доступа            |
| track_code | string | Трек-код для статистики |
| ref        | string | Неизвестно              |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": 456200000
  }
  ```
</details>

## audio.addToPlaylist
Добавить аудиозапись в плейлист

### Параметры

| Параметр    | Тип    | Описание                                                       |
|-------------|--------|----------------------------------------------------------------|
| owner_id    | int    | ID владельца плейлиста                                         |
| playlist_id | int    | ID плейлиста                                                   |
| audio_ids   | string | ID аудиозаписей в формате {owner_id}\_{audio_id} через запятую |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": [
      {
        "audio_id": 456240000
      }
    ]
  }
  ```
</details>

## audio.createPlaylist
Создать плейлист

### Параметры

| Параметр    | Тип    | Описание                                       |
|-------------|--------|------------------------------------------------|
| owner_id    | int    | ID владельца плейлиста                         |
| title       | string | Название плейлиста                             |
| description | string | Описание плейлиста                             |
| audio_ids   | string | Аудиозаписи, которые нужно добавить в плейлист |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "id": 82750000,
      "owner_id": 305360617,
      "type": 0,
      "title": "test playlist",
      "description": "",
      "count": 0,
      "followers": 0,
      "plays": 0,
      "create_time": 1591962784,
      "update_time": 1591962784,
      "genres": [],
      "album_type": "playlist",
      "meta": {
        "view": "compact"
      }
    }
  }
  ```
</details>

## audio.delete
Удалить аудиозапись из добавленных

### Параметры

| Параметр | Тип | Описание     |
|----------|-----|--------------|
| owner_id | int | ID владельца |
| audio_id | int | ID аудио     |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": 1
  }
  ```
</details>

## audio.deletePlaylist
Удалить плейлист

### Параметры

| Параметр    | Тип | Описание     |
|-------------|-----|--------------|
| playlist_id | int | ID плейлиста |
| owner_id    | int | ID владельца |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": 1
  }
  ```
</details>

## audio.edit
Отредактировать данные аудиозаписи

### Параметры

| Параметр  | Тип    | Описание                                                      |
|-----------|--------|---------------------------------------------------------------|
| owner_id  | int    | ID владельца аудиозаписи                                      |
| audio_id  | int    | ID аудиозаписи                                                |
| artist    | string | Новое название исполнителя                                    |
| title     | string | Новое название композиции                                     |
| text      | string | Новый текст аудиозаписи                                       |
| genre_id  | int    | ID жанра из [списка](https://vk.com/dev/objects/audio_genres) |
| no_search | int    | Флаг. Если 1 - аудиозапись не будет доступна в поиске         |

### Пример ответа

<details>
  <summary>Открыть</summary>

  Возвращает ID слов аудиозаписи, если они указаны

  ```json
  {
    "response": 447900000
  }
  ```
</details>

## audio.editPlaylist
Отредактировать данные плейлиста

### Параметры

| Параметр    | Тип    | Описание               |
|-------------|--------|------------------------|
| owner_id    | int    | ID владельца плейлиста |
| playlist_id | int    | ID плейлиста           |
| title       | string | Название плейлиста     |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": 1
  }
  ```
</details>

## audio.get
Получить аудиозаписи

### Параметры

| Параметр     | Тип | Описание                                                            |
|--------------|-----|---------------------------------------------------------------------|
| owner_id     | int | Чьи аудиозаписи нужно получить. По умолчанию — ID владельца токена  |
| count        | int | Количество аудиозаписей                                             |
| offset       | int | Оффсет                                                              |
| playlist_id  | int | ID плейлиста                                                        |
| extended     | int | Флаг. Если 1, то в ответе API будут поля `profiles` и `groups`      |
| shuffle      | int | Флаг. Вроде-бы ни на что не влияет                                  |
| shuffle_seed | int | Рандомное число. Используется для случайной сортировки аудиозаписей |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "count": 481,
      "items": [
        {
          "artist": "ФОНКЕР",
          "id": 456200000,
          "owner_id": 305360617,
          "title": "ЛЮТЫЙ",
          "duration": 142,
          "access_key": "",
          "ads": {
            "content_id": "305360617_456200000",
            "duration": "142",
            "account_age_type": "3",
            "puid1": "554",
            "puid22": "11"
          },
          "is_licensed": true,
          "track_code": "",
          "url": "",
          "date": 1592003498,
          "genre_id": 3,
          "no_search": 1
        }
      ]
    }
  }
  ```
</details>

## audio.getAlbumsByArtist
Получить альбомы исполнителя

### Параметры

| Параметр  | Тип    | Описание            |
|-----------|--------|---------------------|
| artist_id | string | ID артиста          |
| count     | int    | Количество альбомов |
| offset    | int    | Оффсет              |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "count": 15,
      "items": [
        {
          "id": 7646592,
          "owner_id": -2000646592,
          "type": 1,
          "title": "OLD BLOOD",
          "description": "",
          "count": 12,
          "followers": 642749,
          "plays": 17346937,
          "create_time": 1590673347,
          "update_time": 1590673347,
          "genres": [
            {
              "id": 10,
              "name": "Хип-хоп"
            }
          ],
          "is_following": true,
          "year": 2020,
          "followed": {
            "playlist_id": 82750000,
            "owner_id": 305360617
          },
          "photo": {
            "width": 300,
            "height": 300,
            "photo_34": "",
            "photo_68": "",
            "photo_135": "",
            "photo_270": "",
            "photo_300": "",
            "photo_600": "",
            "photo_1200": ""
          },
          "access_key": "",
          "is_explicit": true,
          "main_artists": [
            {
              "name": "Boulevard Depo",
              "domain": "4351355679024274167",
              "id": "4351355679024274167"
            }
          ],
          "album_type": "main_feat"
        }
      ]
    }
  }
  ```
</details>

## audio.getAudiosByArtist
Получить треки артиста

### Параметры

| Параметр  | Тип    | Описание                |
|-----------|--------|-------------------------|
| artist_id | string | ID артиста              |
| type      | string | Неизвестно              |
| count     | int    | Количество аудиозаписей |
| offset    | int    | Оффсет                  |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "count": 93,
      "items": [
        {
          "artist": "Boulevard Depo",
          "id": 67604025,
          "owner_id": -2001604025,
          "title": "Friendly Fire",
          "duration": 122,
          "access_key": "",
          "ads": {
            "content_id": "-2001604025_67604025",
            "duration": "122",
            "account_age_type": "3",
            "puid1": "554",
            "puid22": "14"
          },
          "is_focus_track": true,
          "is_licensed": true,
          "track_code": "",
          "url": "",
          "date": 1590673418,
          "album": {
            "id": 7646592,
            "title": "OLD BLOOD",
            "owner_id": -2000646592,
            "access_key": "",
            "thumb": {
              "width": 300,
              "height": 300,
              "photo_34": "",
              "photo_68": "",
              "photo_135": "",
              "photo_270": "",
              "photo_300": "",
              "photo_600": "",
              "photo_1200": ""
            }
          },
          "main_artists": [
            {
              "name": "Boulevard Depo",
              "domain": "4351355679024274167",
              "id": "4351355679024274167"
            }
          ],
          "subtitle": "Prod. Avepack",
          "stories_allowed": true
        }
      ]
    }
  }
  ```
</details>

## audio.getBroadcast
Узнать, транслируется ли аудиозапись в статус

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "enabled": 0
    }
  }
  ```
</details>

## audio.getById
Получить аудизаписи по их идентификаторам

### Параметры

| Параметр | Тип    | Описание                    |
|----------|--------|-----------------------------|
| audios   | string | Идентификаторы аудиозаписей |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": [
      {
        "artist": "ФОНКЕР",
        "id": 456200000,
        "owner_id": 305360617,
        "title": "ЛЮТЫЙ",
        "duration": 142,
        "access_key": "",
        "ads": {
          "content_id": "305360617_456200000",
          "duration": "142",
          "account_age_type": "3",
          "puid1": "554",
          "puid22": "11"
        },
        "is_licensed": true,
        "track_code": "",
        "url": "",
        "date": 1592003498,
        "genre_id": 3,
        "no_search": 1
      }
    ]
  }
  ```
</details>

## audio.getCatalog
Получить чарт

### Параметры

| Параметр   | Тип    | Описание                                                     |
|------------|--------|--------------------------------------------------------------|
| artist_id  | string | ID артиста                                                   |
| fields     | string | Дополнительные поля пользователя                             |
| context    | string | Неизвестно                                                   |
| count      | int    | Количество аудиозаписей                                      |
| extended   | int    | Флаг. Если `1`, то в ответе будут поля `profiles` и `groups` |
| start_from | string | Оффсет                                                       |

Значение `fields` из кода: `first_name_gen,photo_50,photo_100,photo_200`

> Есть еще один параметр, но мне лень его искать

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "items": [
        {
          "title": "Специально для Вас",
          "subtitle": "Oasis, Intelligency, Tolstoi, Andsan, The Boombox и другие",
          "type": "audios_special",
          "count": 293,
          "source": "recoms_recoms",
          "id": "",
          "next_from": "",
          "audios": [
            {
              "artist": "Oasis",
              "id": 59098396,
              "owner_id": -2001098396,
              "title": "D'You Know What I Mean?",
              "duration": 464,
              "access_key": "",
              "ads": {
                "content_id": "-2001098396_59098396",
                "duration": "464",
                "account_age_type": "3",
                "puid1": "554",
                "puid22": "14"
              },
              "is_licensed": true,
              "track_code": "",
              "url": "",
              "date": 1576137009,
              "album": {
                "id": 940078,
                "title": "Time Flies... 1994-2009",
                "owner_id": -2000940078,
                "access_key": "",
                "thumb": {
                  "width": 300,
                  "height": 300,
                  "photo_34": "",
                  "photo_68": "",
                  "photo_135": "",
                  "photo_270": "",
                  "photo_300": "",
                  "photo_600": "",
                  "photo_1200": ""
                }
              },
              "main_artists": [
                {
                  "name": "Oasis",
                  "domain": "7038390183186746",
                  "id": "7038390183186746"
                }
              ]
            }
          ],
          "thumbs": [
            {
              "width": 300,
              "height": 300,
              "photo_34": "",
              "photo_68": "",
              "photo_135": "",
              "photo_270": "",
              "photo_300": "",
              "photo_600": "",
              "photo_1200": ""
            },
            {
              "width": 0,
              "height": 0
            }
          ]
        }
      ],
      "next_from": "",
      "profiles": [],
      "groups": []
    }
  }
  ```
</details>

## audio.getCatalogBlockById
Получить секцию чарта

### Параметры

| Параметр   | Тип    | Описание                                                        |
|------------|--------|-----------------------------------------------------------------|
| block_id   | string | ID секции                                                       |
| start_from | string | Оффсет (поле `next_from`)                                       |
| shuffle    | string | `true` или `false`. Если `true`, то содержимое секции изменится |
| refresh    | string | `true` или `false`. Если `true`, то содержимое секции изменится |
| count      | int    | Количество аудиозаписей                                         |
| extended   | int    | Флаг                                                            |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "block": {
        "title": "Специально для Вас",
        "subtitle": "MC Анюта, Jagdhorngruppe des Zentralen Orchesters der Forstwirtschaft, ДЕТИ RAVE и другие",
        "type": "audios_special",
        "count": 288,
        "source": "recoms_recoms",
        "id": "",
        "next_from": "",
        "audios": [
          {
            "artist": "MC Анюта",
            "id": 37036507,
            "owner_id": -2001036507,
            "title": "Жигули",
            "duration": 218,
            "access_key": "",
            "ads": {
              "content_id": "-2001036507_37036507",
              "duration": "218",
              "account_age_type": "3",
              "puid1": "554",
              "puid22": "14"
            },
            "is_licensed": true,
            "track_code": "",
            "url": "",
            "date": 1545243738,
            "album": {
              "id": 2488067,
              "title": "Заблуждение",
              "owner_id": -2000488067,
              "access_key": "",
              "thumb": {
                "width": 300,
                "height": 300,
                "photo_34": "",
                "photo_68": "",
                "photo_135": "",
                "photo_270": "",
                "photo_300": "",
                "photo_600": "",
                "photo_1200": ""
              }
            },
            "main_artists": [
              {
                "name": "MC Анюта",
                "domain": "1741845004227911003",
                "id": "1741845004227911003"
              }
            ]
          }
        ],
        "thumbs": [
          {
            "width": 300,
            "height": 300,
            "photo_34": "",
            "photo_68": "",
            "photo_135": "",
            "photo_270": "",
            "photo_300": "",
            "photo_600": "",
            "photo_1200": ""
          }
        ]
      }
    }
  }
  ```
</details>

## audio.getCount
Получить количество аудиозаписей

### Параметры

| Параметр | Тип | Описание     |
|----------|-----|--------------|
| owner_id | int | ID владельца |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": 100
  }
  ```
</details>

## audio.getHints

Возвращает список возможных вариантов запроса. Если не передать `q`, то выведет топ-5 запросов.

### Параметры

| Параметр | Тип    | Описание      |
|----------|--------|---------------|
| q        | string | Строка поиска |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "count": 5,
      "items": [
        {
          "name": "сектор газа"
        },
        {
          "name": "король и шут"
        },
        {
          "name": "rammstein"
        },
        {
          "name": "кино"
        },
        {
          "name": "ария"
        }
      ]
    }
  }
  ```
</details>

## audio.getLyrics

Возвращает текст песни. Поле `lyrics_id` можно получить из объекта аудиозаписи у поля с таким же названием.
Часто можно встретить песни, у которых не возвращается `lyrics_id`, поэтому нужно проверять их наличие перед использованием.

### Параметры

| Параметр  | Тип | Описание         |
|-----------|-----|------------------|
| lyrics_id | int | ID текста песни  |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "lyrics_id": 314927765,
      "text": "Я знаю, где живет любовь. <продолжение текста ...>"
    }
  }
  ```
</details>

## audio.getPlaylistById
Получить плейлист по его идентификатору

### Параметры

| Параметр    | Тип | Описание               |
|-------------|-----|------------------------|
| owner_id    | int | ID владельца плейлиста |
| playlist_id | int | ID плейлиста           |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "id": 82750000,
      "owner_id": 305360617,
      "type": 0,
      "title": "test",
      "description": "",
      "count": 1,
      "followers": 0,
      "plays": 0,
      "create_time": 1591962698,
      "update_time": 1594637580,
      "genres": [],
      "is_following": false,
      "access_key": "",
      "album_type": "playlist",
      "meta": {
        "view": "compact"
      }
    }
  }
  ```
</details>

## audio.getPlaylists
Получить плейлисты

### Параметры

| Параметр   | Тип    | Описание                         |
|------------|--------|----------------------------------|
| owner_id   | int    | Чьи плейлисты нужно получить     |
| fields     | string | Дополнительные поля пользователя |
| start_from | string | Оффсет                           |
| offset     | int    | Оффсет                           |
| count      | int    | Количество плейлистов            |
| filters    | string | -                                |
| extended   | int    | Флаг                             |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "count": 61,
      "items": [
        {
          "id": 82700000,
          "owner_id": 305360617,
          "type": 0,
          "title": "test playlist",
          "description": "",
          "count": 0,
          "followers": 0,
          "plays": 0,
          "create_time": 1591962698,
          "update_time": 1591962698,
          "genres": [],
          "access_key": "",
          "album_type": "playlist",
          "meta": {
            "view": "compact"
          }
        }
      ],
      "next_from": ""
    }
  }
  ```
</details>

## audio.getPopular
Получить популярные треки

### Параметры

| Параметр | Тип | Описание                |
|----------|-----|-------------------------|
| count    | int | Количество аудиозаписей |
| offset   | int | Оффсет                  |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": [
      {
        "artist": "Dua Lipa",
        "id": 456240861,
        "owner_id": -30462549,
        "title": "Lost In Your Light (feat. Miguel)",
        "duration": 203,
        "access_key": "",
        "is_explicit": false,
        "is_focus_track": false,
        "is_licensed": true,
        "track_code": "",
        "url": "",
        "date": 1492759440,
        "album": {
          "id": 1076509,
          "title": "Dua Lipa (Deluxe)",
          "owner_id": -2000076509,
          "access_key": "",
          "thumb": {
            "width": 300,
            "height": 300,
            "photo_34": "",
            "photo_68": "",
            "photo_135": "",
            "photo_270": "",
            "photo_300": "",
            "photo_600": "",
            "photo_1200": ""
          }
        },
        "short_videos_allowed": false,
        "stories_allowed": false
      }
    ]
  }
  ```
</details>

## audio.getRecentAudios

Возвращает недавно прослушанные треки.

### Параметры

| Параметр    | Тип | Описание                              |
|-------------|-----|---------------------------------------|
| **user_id** | int | ID юзера, чьи аудиозаписи мы получаем |
| count       | int | Количество аудиозаписей               |
| offset      | int | Оффсет                                |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "count": 100,
      "items": [
        {
          "artist": "GONE.Fludd",
          "id": 456452940,
          "owner_id": 474499274,
          "title": "ВТОРНИК",
          "duration": 112,
          "is_explicit": false,
          "is_focus_track": false,
          "is_licensed": true,
          "track_code": "",
          "url": "",
          "date": 1594070316,
          "album": {
            "id": 8020519,
            "title": "ВТОРНИК",
            "owner_id": -2000020519,
            "access_key": ""
          },
          "main_artists": [
            {
              "name": "GONE.Fludd",
              "domain": "5201359060516373864",
              "id": "5201359060516373864"
            }
          ],
          "short_videos_allowed": false,
          "stories_allowed": false
        }
      ]
    }
  }
  ```
</details>

## audio.getRecommendations

Возвращает музыкальные рекомендации или похожие на определенную аудиозапись треки.

### Параметры

| Параметр     | Тип    | Описание                                                                                 |
|--------------|--------|------------------------------------------------------------------------------------------|
| count        | int    | Количество аудиозаписей (по умолчанию 100)                                               |
| target_audio | string | Аудиозапись в формате {owner_id}\_{audio_id}, на которой будут основываться рекомендации |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "count": 975,
      "items": [
        {
          "artist": "PLATO",
          "id": 65824357,
          "owner_id": -2001824357,
          "title": "3 БЕЛОРУССКИ",
          "duration": 125,
          "access_key": "",
          "ads": {
            "content_id": "-2001824357_65824357",
            "duration": "125",
            "account_age_type": "3",
            "puid1": "554",
            "puid22": "14"
          },
          "is_explicit": true,
          "is_licensed": true,
          "track_code": "",
          "url": "",
          "date": 1587880392,
          "album": {
            "id": 7331311,
            "title": "ЛЕГЕНДАРНАЯ ПЫЛЬ 2.0 ",
            "owner_id": -2000331311,
            "access_key": "",
            "thumb": {
              "width": 300,
              "height": 300,
              "photo_34": "",
              "photo_68": "",
              "photo_135": "",
              "photo_270": "",
              "photo_300": "",
              "photo_600": "",
              "photo_1200": ""
            }
          },
          "main_artists": [
            {
              "name": "PLATO",
              "domain": "2082190515421126875",
              "id": "2082190515421126875"
            }
          ]
        }
      ]
    }
  }
  ```
</details>

## audio.getRestrictionPopup
Получить информацию об ограничении доступа к аудиозаписи

### Параметры

| Параметр   | Тип    | Описание                                     |
|------------|--------|----------------------------------------------|
| audio_id   | string | Аудиозапись в формате {owner_id}\_{audio_id} |
| track_code | string | Параметр для сбора статистики                |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "title": "Аудиозапись недоступна",
      "icons": [
        {
          "height": 72,
          "url": "https:\/\/vk.com\/images\/media\/pensive_face_72x72.png",
          "width": 72
        },
        {
          "height": 144,
          "url": "https:\/\/vk.com\/images\/media\/pensive_face_144x144.png",
          "width": 144
        },
        {
          "height": 216,
          "url": "https:\/\/vk.com\/images\/media\/pensive_face_216x216.png",
          "width": 216
        },
        {
          "height": 288,
          "url": "https:\/\/vk.com\/images\/media\/pensive_face_288x288.png",
          "width": 288
        }
      ],
      "text": "Так решил музыкант или его представитель"
    }
  }
  ```
</details>

## audio.getSearchTrends

Возвращает популярные поисковые запросы.

### Параметры

| Параметр | Тип | Описание             |
|----------|-----|----------------------|
| count    | int | Количество элементов |
| offset   | int | Оффсет               |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "count": 6,
      "items": [
        {
          "name": "morgenshtern"
        },
        {
          "name": "мы открываем бизнес"
        },
        {
          "name": "макс корж"
        },
        {
          "name": "дочка прокурора"
        },
        {
          "name": "сектор газа"
        },
        {
          "name": "хавчик"
        }
      ]
    }
  }
  ```
</details>

## audio.getStoryCatalog

Возвращает аудиозаписи, которые можно использовать в историях.

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "sections": [
        {
          "id": "",
          "name": "",
          "blocks": [
            {
              "id": "",
              "block_view_type": "triple_stacked_slider_picker",
              "url": "https:\/\/vk.com\/",
              "music_audios": [
                {
                  "artist": "HARU",
                  "id": 456241346,
                  "owner_id": -183773637,
                  "title": "Утопаю",
                  "duration": 185,
                  "access_key": "",
                  "is_explicit": false,
                  "is_focus_track": false,
                  "is_licensed": true,
                  "track_code": "",
                  "url": "",
                  "date": 1594331849,
                  "album": {
                    "id": 8016169,
                    "title": "Утопаю",
                    "owner_id": -2000016169,
                    "access_key": "",
                    "thumb": {
                      "width": 300,
                      "height": 300,
                      "photo_34": "",
                      "photo_68": "",
                      "photo_135": "",
                      "photo_270": "",
                      "photo_300": "",
                      "photo_600": "",
                      "photo_1200": ""
                    }
                  },
                  "main_artists": [
                    {
                      "name": "HARU",
                      "domain": "4958089606319368585",
                      "id": "4958089606319368585"
                    }
                  ],
                  "short_videos_allowed": true,
                  "stories_allowed": true
                }
              ],
              "owner_id": -183773637,
              "fullscreen_view_type": "list_picker",
              "title": "Новинки",
              "data_type": "music_audios"
            }
          ],
          "url": "https:\/\/vk.com\/",
          "is_selected": 1,
          "next_from": "PUlYVA8FFg",
          "total_count": 3
        }
      ]
    }
  }
  ```
</details>

## audio.getStorySearchCatalog

Возвращает список найденных песен для прикрепления к истории.

### Параметры

| Параметр | Тип    | Описание      |
|----------|--------|---------------|
| query    | string | Строка поиска |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "sections": [
      {
        "id": "PUldVA8HR0RzSVNUagdTRGpJUFQPBRY",
        "name": "",
        "blocks": [{
          "id": "PUlQVA8GR0R3W0tMF2tZUmRHS0EXDkk6M1tdRVNoHlZyX1kqQARfVX5JRVQAFlFEGVhRVBkWX0R8WEVUBAFJXHcW",
          "block_view_type": "list_picker",
          "url": "https://vk.com/",
          "no_header": 1,
          "music_audios": [{
            "artist": "VERBEE",
            "id": 68784845,
            "owner_id": -2001784845,
            "title": "Принцесса",
            "duration": 117,
            "access_key": "...",
            "ads": {
              "content_id": "-2001784845_68784845",
              "duration": "117",
              "account_age_type": "3",
              "puid1": "554",
              "puid22": "14"
            },
            "is_explicit": false,
            "is_focus_track": false,
            "is_licensed": true,
            "track_code": "...",
            "url": "...",
            "date": 1592583398,
            "no_search": 1,
            "album": {
              "id": 7861792,
              "title": "Принцесса",
              "owner_id": -2000861792,
              "access_key": "60a6d61af956c4c187",
              "thumb": {
                "width": 300,
                "height": 300,
                "photo_34": "https://sun7-8.userapi.com/c857220/v857220302/1bd044/lufhjf4fggw.jpg",
                "photo_68": "https://sun7-6.userapi.com/c857220/v857220302/1bd042/tZGN11-2fu0.jpg",
                "photo_135": "https://sun7-7.userapi.com/c857220/v857220302/1bd040/5FJisGHMJfc.jpg",
                "photo_270": "https://sun7-7.userapi.com/c857220/v857220302/1bd03d/tMmi291b-tA.jpg",
                "photo_300": "https://sun7-7.userapi.com/c857220/v857220302/1bd03b/DJHz6iWmrFo.jpg",
                "photo_600": "https://sun7-9.userapi.com/c857220/v857220302/1bd03a/eLCKbhDa1oU.jpg",
                "photo_1200": "https://sun7-7.userapi.com/c857220/v857220302/1bd039/SMq8E76aysg.jpg"
              }
            },
            "main_artists": [{
              "name": "VERBEE",
              "domain": "2451624268979701525",
              "id": "2451624268979701525"
            }],
            "short_videos_allowed": true,
            "stories_allowed": true
          }],
          "fullscreen_view_type": "list_picker",
          "title": "Все аудиозаписи",
          "data_type": "music_audios"
        }],
        "url": "https://vk.com/",
        "is_selected": 1,
        "total_count": 1
      }
    ]
  }
  ```
</details>

## audio.getUploadServer

Возвращает адрес для загрузки аудиозаписи.

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "upload_url": "..."
  }
  ```
</details>

## audio.reorder

Изменяет положение аудиозаписи.

### Параметры

| Параметр | Тип | Описание                                                          |
|----------|-----|-------------------------------------------------------------------|
| audio_id | int | ID аудиозаписи, у которой меняем позицию                          |
| after    | int | ID аудиозаписи, после которой будет поставлена первая аудиозапись |
| before   | int | ID аудиозаписи, перед которой будет поставлена первая аудиозапись |

Вы должны использовать либо `before`, либо `after`. Нельзя использовать оба параметра сразу.

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```js
  1
  ```
</details>

## audio.reorderPlaylists

Изменяет положение плейлиста.

### Параметры

| Параметр    | Тип | Описание                                                     |
|-------------|-----|--------------------------------------------------------------|
| owner_id    | int | ID владельца плейлиста                                       |
| playlist_id | int | ID плейлиста                                                 |
| after       | int | ID плейлиста, после которого будет поставлен первый плейлист |
| before      | int | ID плейлиста, перед которым будет поставлен первый плейлист  |

Вы должны использовать либо `before`, либо `after`. Нельзя использовать оба параметра сразу.

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```js
  1
  ```
</details>

## audio.restore

Восстанавливает удаленную аудиозапись.

### Параметры

| Параметр | Тип | Описание       |
|----------|-----|----------------|
| owner_id | int | ID владельца   |
| audio_id | int | ID аудиозаписи |

## audio.save

Сохраняет аудиозапись после [загрузки](https://vk.com/dev/upload_files_2).

### Параметры

| Параметр     | Тип    | Описание                                                                   |
|--------------|--------|----------------------------------------------------------------------------|
| **audio**    | string | Параметр, возвращаемый после [загрузки](https://vk.com/dev/upload_files_2) |
| **server**   | string | Параметр, возвращаемый после [загрузки](https://vk.com/dev/upload_files_2) |
| **hash**     | string | Параметр, возвращаемый после [загрузки](https://vk.com/dev/upload_files_2) |
| artist       | string | Автор композиции (по умолчанию `Unknown artist`)                           |
| title        | string | Название композиции (по умолчанию `Untitled`)                              |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "artist": "артист",
    "id": 456239733,
    "owner_id": 88262293,
    "title": "тайтл",
    "duration": 219,
    "is_explicit": false,
    "is_focus_track": false,
    "track_code": "...",
    "url": "https://cs7-1v4.v...TU&long_chunk=1",
    "date": 1595144321,
    "short_videos_allowed": false,
    "stories_allowed": false
  }
  ```
</details>

## audio.search

Возвращает найденные аудиозаписи.

### Параметры

| Параметр       | Тип    | Описание                                                             |
|----------------|--------|----------------------------------------------------------------------|
| q              | string | Строка поиска                                                        |
| search_own     | int    | Флаг. Если 1, то в результатах поиска будут и аудио владельца токена |
| performer_only | int    | Флаг. Отвечает за поиск по артистам                                  |
| owner_id       | int    | ID владельца                                                         |
| offset         | int    | Оффсет                                                               |
| count          | int    | Количество аудиозаписей                                              |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "count": 1,
      "items": [
        {
          "id": 456200000,
          "owner_id": 305360617,
          "artist": "ФОНКЕР",
          "title": "ЛЮТЫЙ",
          "duration": 142,
          "date": 1592003498,
          "url": ""
        }
      ]
    }
  }
  ```
</details>

## audio.searchAlbums

Возвращает найденные альбомы.
Отличается от плейлистов тем, что альбомы могут быть выпущены только исполнителями.


### Параметры

| Параметр | Тип    | Описание                         |
|----------|--------|----------------------------------|
| q        | string | Строка поиска                    |
| count    | int    | Количество альбомов (плейлистов) |
| offset   | int    | Оффсет                           |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "count": 285,
      "items": [
        {
          "id": 6176862,
          "owner_id": -2000176862,
          "type": 1,
          "title": "Test & Recognise",
          "description": "",
          "count": 4,
          "followers": 478,
          "plays": 14519,
          "create_time": 1574649097,
          "update_time": 1574649097,
          "genres": [
            {
              "id": 53,
              "name": "Электронная"
            }
          ],
          "is_following": false,
          "year": 2014,
          "photo": {
            "width": 300,
            "height": 300,
            "photo_34": "",
            "photo_68": "",
            "photo_135": "",
            "photo_270": "",
            "photo_300": "",
            "photo_600": "",
            "photo_1200": ""
          },
          "access_key": "",
          "subtitle": "Remixes",
          "is_explicit": false,
          "main_artists": [
            {
              "name": "Seekae",
              "domain": "7081472811774942189",
              "id": "7081472811774942189"
            }
          ],
          "album_type": "main_only"
        }
      ]
    }
  }
  ```
</details>

## audio.searchArtists

Возвращает найденных исполнителей.

### Параметры

| Параметр | Тип    | Описание                               |
|----------|--------|----------------------------------------|
| q        | string | Строка поиска                          |
| count    | int    | Количество исполнителей. Максимум 1000 |
| offset   | int    | Оффсет                                 |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "count": 103,
      "items": [
        {
          "name": "Boulevard Depo",
          "domain": "boulevarddepo",
          "id": "4351355679024274167",
          "photo": [
            {
              "height": 100,
              "url": "",
              "width": 100
            },
            {
              "height": 135,
              "url": "",
              "width": 135
            },
            {
              "height": 50,
              "url": "",
              "width": 50
            },
            {
              "height": 270,
              "url": "",
              "width": 270
            },
            {
              "height": 198,
              "url": "",
              "width": 198
            }
          ]
        },
        {
          "name": "Boulevard des airs",
          "domain": "boulevarddesairs",
          "id": "1914845056630918822"
        }
      ]
    }
  }
  ```
</details>

## audio.searchMain

Возвращает все найденные объекты, связанные с разделом музыки.

### Параметры

| Параметр | Тип    | Описание      |
|----------|--------|---------------|
| q        | string | Строка поиска |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "albums": {
        "count": 0,
        "items": []
      },
      "audios": {
        "count": 0,
        "items": []
      },
      "artists": {
        "count": 0,
        "items": []
      },
      "playlists": {
        "count": 0,
        "items": []
      },
      "own_audios": {
        "count": 0,
        "items": []
      },
      "own_playlists": {
        "count": 0,
        "items": []
      },
      "own_albums": {
        "count": 0,
        "items": []
      }
    }
  }
  ```
</details>

## audio.searchPlaylists

Возвращает найденные плейлисты.
Отличается от альбомов тем, что плейлисты могут составляться и обычными пользователями (`owner_id` > 0).

### Параметры

| Параметр | Тип    | Описание      |
|----------|--------|---------------|
| q        | string | Строка поиска |
| owner_id | int    | ID владельца  |
| offset   | int    | Оффсет        |
| filters  | string | Фильтры       |
| count    | int    | Количество    |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "count": 15921,
      "items": [
        {
          "id": 82753370,
          "owner_id": 305360617,
          "type": 1,
          "title": "OLD BLOOD",
          "description": "",
          "count": 12,
          "followers": 598848,
          "plays": 12717640,
          "create_time": 1590673347,
          "update_time": 1590673347,
          "genres": [
            {
              "id": 10,
              "name": "Хип-хоп"
            }
          ],
          "year": 2020,
          "original": {
            "playlist_id": 7646592,
            "owner_id": -2000646592,
            "access_key": ""
          },
          "photo": {
            "width": 300,
            "height": 300,
            "photo_34": "",
            "photo_68": "",
            "photo_135": "",
            "photo_270": "",
            "photo_300": "",
            "photo_600": "",
            "photo_1200": ""
          },
          "access_key": "",
          "is_explicit": true,
          "main_artists": [
            {
              "name": "Boulevard Depo",
              "domain": "4351355679024274167",
              "id": "4351355679024274167"
            }
          ],
          "album_type": "main_feat"
        },
        {
          "id": 85412888,
          "owner_id": -28905875,
          "type": 0,
          "title": "BOULEVARD DEPO – «OLD BLOOD»",
          "description": "",
          "count": 12,
          "followers": 64811,
          "plays": 1367311,
          "create_time": 1590699505,
          "update_time": 1590699739,
          "genres": [],
          "photo": {
            "width": 300,
            "height": 300,
            "photo_34": "",
            "photo_68": "",
            "photo_135": "",
            "photo_270": "",
            "photo_300": "",
            "photo_600": "",
            "photo_1200": ""
          },
          "access_key": "",
          "album_type": "playlist"
        }
      ]
    }
  }
  ```
</details>

## audio.setBroadcast
Установить аудиозапись в статус

### Параметры

| Параметр   | Тип    | Описание                                                                                         |
|------------|--------|--------------------------------------------------------------------------------------------------|
| audio      | string | Аудиозапись в формате {owner_id}\_{audio_id}. Если не передать этот параметр, то статус пропадет |
| target_ids | string | ID профилей или сообществ, куда будет установлен статус                                          |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": []
  }
  ```
</details>
