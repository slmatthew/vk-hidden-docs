# audio
Методы для работы с аудиозаписями

## Список методов
* [audio.add](#audioadd) — добавить аудиозапись к себе
* [audio.addToFavorites](#audioaddtofavorites)
* [audio.addToPlaylist](#audioaddtoplaylist) — добавить аудиозапись в плейлист
* [audio.createPlaylist](#audiocreateplaylist) — создать плейлист
* [audio.delete](#audiodelete) — удалить аудиозапись из добавленных
* [audio.deletePlaylist](#audiodeleteplaylist) — удалить плейлист
* [audio.edit](#audioedit) — отредактировать данные аудиозаписи
* [audio.editPlaylist](#audioeditplaylist) — отредактировать данные плейлиста
* [audio.followArtist](#audiofollowartist) — подписаться на артиста
* [audio.followPlaylist](#audiofollowplaylist)
* [audio.get](#audioget) — получить аудиозаписи
* [audio.getAlbumsByArtist](#audiogetalbumsbyartist) — получить альбомы исполнителя
* [audio.getArtists](#audiogetartists)
* [audio.getAudiosByArtist](#audiogetaudiosbyartist) — получить треки артиста
* [audio.getBroadcast](#audiogetbroadcast) — включена ли трансляция треков в статус
* [audio.getButtonTracks](#audiogetbuttontracks) — получить список аудиозаписей в плейлисте
* [audio.getById](#audiogetbyid) — получить аудизаписи по их идентификаторам
* [audio.getCatalog](#audiogetcatalog) — получить чарт
* [audio.getCatalogBlockById](#audiogetcatalogblockbyid) — получить секцию чарта
* [audio.getCount](#audiogetcount) — получить количество аудиозаписей
* [audio.getHints](#audiogethints)
* [audio.getLyrics](#audiogetlyrics) — получить слова песни
* [audio.getOnboardingOffer](#audiogetonboardingoffer)
* [audio.getPlaylistById](#audiogetplaylistbyid) — получить плейлист по его идентификатору
* [audio.getPlaylists](#audiogetplaylists) — получить плейлисты
* [audio.getPopular](#audiogetpopular) — получить популярные треки
* [audio.getRecentAudios](#audiogetrecentaudios) — получить недавно прослушанные треки
* [audio.getRecommendations](#audiogetrecommendations) — получить музыкальные рекомендации
* [audio.getRestrictionPopup](#audiogetrestrictionpopup) — получить информацию об ограничении доступа к аудиозаписи
* [audio.getSearchTrends](#audiogetsearchtrends) — получить популярные поисковые запросы
* [audio.getStoryCatalog](#audiogetstorycatalog) — получить аудиозаписи которые можно использовать в историях
* [audio.getStorySearchCatalog](#audiogetstorysearchcatalog)
* [audio.getUploadServer](#audiogetuploadserver) — получить адрес для загрузки аудиозаписи
* [audio.reorder](#audioreorder) — Изменить положение аудиозаписи
* [audio.reorderPlaylists](#audioreorderplaylists) — изменить положение плейлиста
* [audio.restore](#audiorestore) — восстановить удаленную аудиозапись
* [audio.save](#audiosave) — сохранить аудиозапись после загрузки
* [audio.search](#audiosearch) — поиск по аудиозаписям
* [audio.searchAlbums](#audiosearchalbums) — поиск альбомов
* [audio.searchArtists](#audiosearchartists) — поиск исполнителей
* [audio.searchMain](#audiosearchmain) — общий поиск
* [audio.searchPlaylists](#audiosearchplaylists) — найти плейлист
* [audio.sendStartEvent](#audiosendstartevent)
* [audio.sendTrackReaction](#audiosendtrackreaction)
* [audio.setBroadcast](#audiosetbroadcast) — установить аудиозапись в статус
* [audio.setForDownload](#audiosetfordownload)
* [audio.setPlaylistForDownload](#audiosetplaylistfordownload)
* [audio.subscribeToQueue](#audiosubscribetoqueue) — возвращает адрес какого-то специального лонгпула
* [audio.unfollowArtist](#audiounfollowartist) — отписаться от артиста

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

## audio.addToFavorites
### Параметры

| Параметр | Тип | Описание                 |
|----------|-----|--------------------------|
| owner_id | int | ID владельца аудиозаписи |
| audio_id | int | ID аудиозаписи           |

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

## audio.followArtist
Подписаться на артиста

### Параметры

| Параметр  | Тип    | Описание                                                        |
|-----------|--------|-----------------------------------------------------------------|
| artist_id | string | ID артиста                                                      |
| ref       | string | Этот параметр используется для статистики. Я использовал `home` |

## audio.followPlaylist
### Параметры

| Параметр    | Тип    | Описание               |
|-------------|--------|------------------------|
| owner_id    | int    | ID владельца плейлиста |
| playlist_id | int    | ID плейлиста           |
| access_key  | string | Ключ доступа           |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "playlist_id": 82750000,
      "owner_id": 305360617
    }
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

## audio.getArtists
Не удалось вызвать этот метод.

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

## audio.getButtonTracks
Получить список аудиозаписей в плейлисте

### Параметры

| Параметр     | Тип    | Описание                                         |
|--------------|--------|--------------------------------------------------|
| id           | string | ID плейлиста в формате {owner_id}\_{playlist_id} |
| count        | int    | Количество аудиозаписей                          |
| shuffle_seed | int    | Рандомное число для случайной сортировки         |

### Пример ответа

<details>
  <summary>Открыть</summary>

  `next_from` приходит только если `count` меньше, чем количество аудиозаписей в плейлисте

  ```json
  {
    "response": {
      "next_from": "",
      "audios": [
        {
          "artist": "Boulevard Depo",
          "id": 67604118,
          "owner_id": -2001604118,
          "title": "Введение",
          "duration": 34,
          "access_key": "",
          "ads": {
            "content_id": "-2001604118_67604118",
            "duration": "34",
            "account_age_type": "3",
            "puid1": "554",
            "puid22": "14"
          },
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
          ]
        }
      ]
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
Получить слова песни

### Параметры

| Параметр  | Тип | Описание |
|-----------|-----|----------|
| lyrics_id | int | ID слов  |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "lyrics_id": 447900000,
      "text": ""
    }
  }
  ```
</details>

## audio.getOnboardingOffer
Просто метод. Мне выдало ошибку 104 Not found

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
Получить недавно прослушанные треки

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
Получить музыкальные рекомендации

### Параметры

| Параметр     | Тип    | Описание                                                                                 |
|--------------|--------|------------------------------------------------------------------------------------------|
| count        | int    | Количество аудиозаписей                                                                  |
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
Получить популярные поисковые запросы

### Параметры
Эти параметры ни на что не влияют

| Параметр     | Тип    | Описание            |
|--------------|--------|---------------------|
| count        | int    | Количество запросов |
| offset       | int    | Оффсет              |
| need_queries | string | Неизвестно          |

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
Получить аудиозаписи которые можно использовать в историях

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
### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "sections": [
        {
          "id": "PUldVA8HR0RzSVNUagdTRGpJUFQPBRY",
          "name": "",
          "blocks": [],
          "url": "https:\/\/vk.com\/",
          "is_selected": 1,
          "total_count": 1
        }
      ]
    }
  }
  ```
</details>

## audio.getUploadServer
Получить адрес для загрузки аудиозаписи

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "upload_url": ""
    }
  }
  ```
</details>

## audio.reorder
Изменить положение аудиозаписи

### Параметры

| Параметр | Тип | Описание                                                          |
|----------|-----|-------------------------------------------------------------------|
| audio_id | int | ID аудиозаписи, позицию которой меняем                            |
| after    | int | ID аудиозаписи, после которой будет поставлена первая аудиозапись |
| before   | int | ID аудиозаписи, перед которой будет поставлена первая аудиозапись |

Вы должны выбрать либо `before`, либо `after`. Параметры нельзя использовать одновременно

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": 1
  }
  ```
</details>

## audio.reorderPlaylists
Изменить положение плейлиста

### Параметры

| Параметр    | Тип | Описание                                                     |
|-------------|-----|--------------------------------------------------------------|
| owner_id    | int | ID владельца плейлиста                                       |
| playlist_id | int | ID плейлиста                                                 |
| after       | int | ID плейлиста, после которого будет поставлен первый плейлист |
| before      | int | ID плейлиста, перед которым будет поставлен первый плейлист  |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": 1
  }
  ```
</details>

## audio.restore
Восстановить удаленную аудиозапись

### Параметры

| Параметр | Тип | Описание       |
|----------|-----|----------------|
| owner_id | int | ID владельца   |
| audio_id | int | ID аудиозаписи |

## audio.save
Сохранить аудиозапись после загрузки

### Параметры

| Параметр | Тип    | Описание                                                                   |
|----------|--------|----------------------------------------------------------------------------|
| audio    | string | Параметр, возвращаемый после [загрузки](https://vk.com/dev/upload_files_2) |
| server   | string | Параметр, возвращаемый после [загрузки](https://vk.com/dev/upload_files_2) |
| hash     | string | Параметр, возвращаемый после [загрузки](https://vk.com/dev/upload_files_2) |
| artist   | string | Автор композиции                                                           |
| title    | string | Название композиции                                                        |

## audio.search
Поиск по аудиозаписям

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
Поиск альбомов

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
Поиск исполнителей

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
Общий поиск

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
Найти плейлист

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

## audio.sendStartEvent
### Параметры

| Параметр | Тип    | Описание                                     |
|----------|--------|----------------------------------------------|
| uuid     | string | Неизвестно                                   |
| audio_id | string | Аудиозапись в формате {owner_id}\_{audio_id} |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": 1
  }
  ```
</details>

## audio.sendTrackReaction
### Параметры

| Параметр | Тип    | Описание        |
|----------|--------|-----------------|
| user_id  | int    | ID пользователя |
| audio_id | string | Аудиозапись     |
| reaction | string | Неизвестно      |
| position | float  | Неизвестно      |

## audio.setBroadcast
Установить аудиозапись в статус

### Параметры

| Параметр   | Тип    | Описание                                                                                         |
|------------|--------|--------------------------------------------------------------------------------------------------|
| audio      | string | Аудиозапись в формате {owner_id}\_{audio_id}. Если не передать этот параметр, то статус пропадет |
| target_ids | string | ID страниц, куда будет установлен статус                                                         |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": []
  }
  ```
</details>

## audio.setForDownload
### Параметры

| Параметр | Тип | Описание                 |
|----------|-----|--------------------------|
| owner_id | int | ID владельца аудиозаписи |
| audio_id | int | ID аудиозаписи           |

### Пример ответа

<details>
  <summary>Открыть</summary>

 ```json
  {
    "response": 1
  }
  ```
</details>

## audio.setPlaylistForDownload
### Параметры

| Параметр    | Тип    | Описание               |
|-------------|--------|------------------------|
| owner_id    | int    | ID владельца плейлиста |
| playlist_id | int    | ID плейлиста           |
| access_key  | string | Ключ доступа           |

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": 1
  }
  ```
</details>

## audio.subscribeToQueue
Возвращает адрес какого-то специального лонгпула

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": {
      "url": ""
    }
  }
  ```
</details>

## audio.unfollowArtist
Отписаться от артиста

### Параметры

| Параметр  | Тип    | Описание                |
|-----------|--------|-------------------------|
| artist_id | string | ID артиста              |
| user_id   | int    | ID пользователя         |
| ref       | string | Параметр для статистики |