# audio
Методы для работы с аудиозаписями

## Список методов
* [audio.add](#audioadd)
* [audio.createPlaylist](#audiocreateplaylist)
* [audio.delete](#audiodelete)
* [audio.deletePlaylist](#audiodeleteplaylist)
* [audio.followArtist](#audiofollowartist)
* [audio.followPlaylist](#audiofollowplaylist)
* [audio.get](#audioget)
* [audio.getAudiosByArtist](#audiogetaudiosbyartist)
* [audio.getById](#audiogetbyid)
* [audio.restore](#audiorestore)
* [audio.save](#audiosave)
* [audio.search](#audiosearch)
* [audio.searchPlaylists](#audiosearchplaylists)
* [audio.sendStartEvent](#audiosendstartevent)
* [audio.sendTrackReaction](#audiosendtrackreaction)
* [audio.setBroadcast](#audiosetbroadcast)
* [audio.setForDownload](#audiosetfordownload)
* [audio.setPlaylistForDownload](#audiosetplaylistfordownload)

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
```json
{
  "response": 456200000
}
```

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

## audio.delete
Удалить аудиозапись из добавленных

### Параметры

| Параметр | Тип | Описание     |
|----------|-----|--------------|
| owner_id | int | ID владельца |
| audio_id | int | ID аудио     |

### Пример ответа
```json
{
  "response": 1
}
```

## audio.deletePlaylist
Удалить плейлист

### Параметры

| Параметр    | Тип | Описание     |
|-------------|-----|--------------|
| playlist_id | int | ID плейлиста |
| owner_id    | int | ID владельца |

### Пример ответа
```json
{
  "response": 1
}
```

## audio.followArtist
Подписаться на артиста

### Параметры

| Параметр  | Тип    | Описание                                                        |
|-----------|--------|-----------------------------------------------------------------|
| artist_id | string | ID артиста                                                      |
| ref       | string | Этот параметр используется для статистики. Я использовал `home` |

## audio.followPlaylist
### Параметры

| Параметр    | Тип    | Описание                 |
|-------------|--------|--------------------------|
| playlist_id | int    | ID плейлиста             |
| owner_id    | int    | ID владельца плейлиста   |
| access_key  | string | Ключ доступа к плейлисту |

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

## audio.getById
Получить аудизаписи по их идентификаторам

### Параметры

| Параметр | Тип    | Описание                    |
|----------|--------|-----------------------------|
| audios   | string | Идентификаторы аудиозаписей |

### Пример ответа
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

## audio.sendStartEvent
### Параметры

| Параметр | Тип    | Описание                                     |
|----------|--------|----------------------------------------------|
| uuid     | string | Неизвестно                                   |
| audio_id | string | Аудиозапись в формате {owner_id}\_{audio_id} |

### Пример ответа
```json
{
  "response": 1
}
```

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
```json
{
  "response": []
}
```

## audio.setForDownload
### Параметры

| Параметр | Тип | Описание                 |
|----------|-----|--------------------------|
| owner_id | int | ID владельца аудиозаписи |
| audio_id | int | ID аудиозаписи           |

### Пример ответа
```json
{
  "response": 1
}
```

## audio.setPlaylistForDownload
### Параметры

| Параметр    | Тип    | Описание               |
|-------------|--------|------------------------|
| owner_id    | int    | ID владельца плейлиста |
| playlist_id | int    | ID плейлиста           |
| access_key  | string | Ключ доступа           |

### Пример ответа
```json
{
  "response": 1
}
```