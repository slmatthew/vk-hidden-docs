# audio
Методы для работы с аудиозаписями

## Список методов
* [audio.add](#audioadd) — добавить аудиозапись к себе
* [audio.addToPlaylist](#audioaddtoplaylist) — добавить аудиозаписи в плейлист
* [audio.createPlaylist](#audiocreateplaylist) — создать плейлист
* [audio.delete](#audiodelete) — удалить свою аудиозапись
* [audio.deletePlaylist](#audiodeleteplaylist) — удалить плейлист
* [audio.edit](#audioedit) — отредактировать данные аудиозаписи
* [audio.editPlaylist](#audioeditplaylist) — отредактировать данные плейлиста
* [audio.get](#audioget) — получить список аудиозаписей (своих, у других людей или в плейлисте)
* [audio.getAlbumsByArtist](#audiogetalbumsbyartist) — получить альбомы исполнителя
* [audio.getAudiosByArtist](#audiogetaudiosbyartist) — получить треки исполнителя
* [audio.getBroadcast](#audiogetbroadcast) — включена ли трансляция треков в статус
* [audio.getById](#audiogetbyid) — получить аудиозаписи по ID
* [audio.getCatalog](#audiogetcatalog) — получить список секций с аудиозаписями или плейлистами
* [audio.getCatalogBlockById](#audiogetcatalogblockbyid) — получить секцию
* [audio.getCount](#audiogetcount) — получить количество аудиозаписей
* [audio.getHints](#audiogethints) — получить подсказки при поиске
* [audio.getLyrics](#audiogetlyrics) — получить слова песни
* [audio.getPlaylistById](#audiogetplaylistbyid) — получить плейлист по ID
* [audio.getPlaylists](#audiogetplaylists) — получить список плейлистов
* [audio.getPopular](#audiogetpopular) — получить популярные треки
* [audio.getRecentAudios](#audiogetrecentaudios) — получить недавно прослушанные треки
* [audio.getRecommendations](#audiogetrecommendations) — получить музыкальные рекомендации или похожие на аудиозапись треки
* [audio.getRestrictionPopup](#audiogetrestrictionpopup) — получить информацию об ограничении доступа к аудиозаписи
* [audio.getSearchTrends](#audiogetsearchtrends) — получить популярные поисковые запросы
* [audio.getStoryCatalog](#audiogetstorycatalog) — получить аудиозаписи, которые можно использовать в историях
* [audio.getStorySearchCatalog](#audiogetstorysearchcatalog) — поиск аудиозаписей, которые можно использовать в историях
* [audio.getUploadServer](#audiogetuploadserver) — получить адрес для загрузки аудиозаписи
* [audio.reorder](#audioreorder) — изменить положение аудиозаписи
* [audio.reorderPlaylists](#audioreorderplaylists) — изменить положение плейлиста
* [audio.restore](#audiorestore) — восстановить удаленную аудиозапись
* [audio.save](#audiosave) — сохранить аудиозапись после загрузки
* [audio.search](#audiosearch) — поиск по аудиозаписям
* [audio.searchAlbums](#audiosearchalbums) — поиск альбомов
* [audio.searchArtists](#audiosearchartists) — поиск исполнителей
* [audio.searchMain](#audiosearchmain) — поиск всех объектов, связанных с разделом музыки
* [audio.searchPlaylists](#audiosearchplaylists) — поиск плейлистов
* [audio.setBroadcast](#audiosetbroadcast) — установить аудиозапись в статус профиля или сообществ



## audio.add

Добавляет чужую аудиозапись к себе.

### Параметры

| Параметр     | Тип    | Описание                |
|--------------|--------|-------------------------|
| **owner_id** | int    | ID владельца            |
| **audio_id** | int    | ID аудио                |
| access_key   | string | Ключ доступа            |
| track_code   | string | Трек-код для статистики |

### Тип возвращаемого значения

```ts
type AudioAdd = number;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```js
  456239735
  ```
</details>



## audio.addToPlaylist

Добавляет аудиозаписи в плейлист.

### Параметры

| Параметр        | Тип    | Описание                                                        |
|-----------------|--------|-----------------------------------------------------------------|
| **owner_id**    | int    | ID владельца плейлиста                                          |
| **playlist_id** | int    | ID плейлиста                                                    |
| **audio_ids**   | string | ID аудиозаписей в формате `{owner_id}_{audio_id}` через запятую |

### Тип возвращаемого значения

```ts
type AudioAddToPlaylist = { audio_id: number }[];
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  [
    { "audio_id": 456239736 }
  ]
  ```
</details>



## audio.createPlaylist

Создаёт плейлист.

В качестве `owner_id` можно указать либо свой ID, либо ID группы, в которую можно добавлять аудиозаписи.

### Параметры

| Параметр     | Тип    | Описание                                              |
|--------------|--------|-------------------------------------------------------|
| **owner_id** | int    | ID пользователя или группы                            |
| **title**    | string | Название плейлиста                                    |
| description  | string | Описание плейлиста                                    |
| audio_ids    | string | Список аудиозаписей в формате `{owner_id}_{audio_id}` |

### Тип возвращаемого значения

```ts
type AudioCreatePlaylist = VKPlaylist;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "id": 8,
    "owner_id": 88262293,
    "type": 0,
    "title": "Тайтл",
    "description": "Описание",
    "count": 0,
    "followers": 0,
    "plays": 0,
    "create_time": 1595147240,
    "update_time": 1595147240,
    "genres": [],
    "is_following": false,
    "permissions": {
      "play": true,
      "share": true,
      "edit": true,
      "follow": true
    },
    "subtitle_badge": false,
    "play_button": false,
    "access_key": "...",
    "album_type": "playlist",
    "meta": {
      "view": "compact"
    }
  }
  ```
</details>



## audio.delete

Удаляет аудиозапись из добавленных.

### Параметры

| Параметр     | Тип | Описание     |
|--------------|-----|--------------|
| **owner_id** | int | ID владельца |
| **audio_id** | int | ID аудио     |

### Тип возвращаемого значения

```ts
type AudioDelete = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```js
  1
  ```
</details>



## audio.deletePlaylist

Удаляет плейлист.

### Параметры

| Параметр        | Тип | Описание     |
|-----------------|-----|--------------|
| **owner_id**    | int | ID владельца |
| **playlist_id** | int | ID плейлиста |

### Тип возвращаемого значения

```ts
type AudioDeletePlaylist = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```js
  1
  ```
</details>



## audio.edit

Редактирует данные аудиозаписи.

**Обратите внимание:** для некоторых треков может прийти 15 ошибка API (Access Denied).
Отличить разрешенные и запрещенные для редактирования треки невозможно, поэтому нужно проверять каждый вызов.

Однако, по моим наблюдениям, наличие поля `main_artists` всегда означает запрет на редактирование.

### Параметры

| Параметр      | Тип    | Описание                                            |
|---------------|--------|-----------------------------------------------------|
| **owner_id**  | int    | ID владельца аудиозаписи                            |
| **audio_id**  | int    | ID аудиозаписи                                      |
| artist        | string | Новое название исполнителя                          |
| title         | string | Новое название аудиозаписи                          |
| text          | string | Новый текст аудиозаписи                             |
| genre_id      | int    | [ID жанра](https://vk.com/dev/objects/audio_genres) |
| no_search     | flag   | Исключить аудиозапись из поиска                     |

Для редактирования одного или нескольких полей необязательно передавать все остальные.

### Тип возвращаемого значения

```ts
// Возвращает lyrics_id (если есть текст песни) или 0
type AudioEdit = number;
```

### Пример ответа

<details>
  <summary>Открыть</summary>
  ```js
  314927765
  ```
</details>



## audio.editPlaylist

Редактирует данные плейлиста.

### Параметры

| Параметр        | Тип    | Описание               |
|-----------------|--------|------------------------|
| **owner_id**    | int    | ID владельца плейлиста |
| **playlist_id** | int    | ID плейлиста           |
| title           | string | Название плейлиста     |
| description     | string | Описание плейлиста     |

Для редактирования одного поля необязательно передавать все остальные.

### Тип возвращаемого значения

```ts
type AudioEditPlaylist = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```js
  1
  ```
</details>



## audio.get
Получить аудиозаписи

### Параметры

| Параметр     | Тип    | Описание                                                            |
|--------------|--------|---------------------------------------------------------------------|
| owner_id     | int    | ID владельца аудиозаписей. По умолчанию ваш ID                      |
| count        | int    | Количество аудиозаписей                                             |
| offset       | int    | Смещение                                                            |
| playlist_id  | int    | ID плейлиста                                                        |
| extended     | flag   | Возвращать в ответе поля `profiles` и `groups`                      |
| fields       | string | Дополнительные поля для `profiles` и `groups`                       |
| shuffle_seed | int    | Рандомное число. Используется для случайной сортировки аудиозаписей |

### Тип возвращаемого значения

```ts
interface AudioGet {
  count: number
  items: VKAudio[]
  // profiles и groups возвращаются всегда:
  // если нет объектов, то возвращается пустой массив
  profiles?: VKUser[]
  groups?: VKGroup[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "count": 16,
    "items": [
      {
        "artist": "Anne-Marie",
        "id": 456239728,
        "owner_id": 88262293,
        "title": "Alarm",
        "duration": 219,
        "access_key": "...",
        "ads": {
          "content_id": "88262293_456239728",
          "duration": "219",
          "account_age_type": "3",
          "puid1": "554",
          "puid22": "14"
        },
        "is_explicit": true,
        "is_focus_track": false,
        "is_licensed": true,
        "track_code": "...",
        "url": "https://cs7-1v4.vkuseraudio.net/p4/b1ee...qQpDOAworV6aHmdmGB&long_chunk=1",
        "date": 1593884324,
        "album": {
          "id": 128721,
          "title": "Alarm (Remixes)",
          "owner_id": -2000128721,
          "access_key": "...",
          "thumb": {
            "width": 300,
            "height": 300,
            "photo_34": "https://sun9-55.userapi.com/c846217/v846217368/1c155b/TwDPBBlui4Y.jpg",
            "photo_68": "https://sun9-57.userapi.com/c846217/v846217368/1c1559/_vM0aBzNKvE.jpg",
            "photo_135": "https://sun7-7.userapi.com/c846217/v846217368/1c1557/ACYLOgJu90o.jpg",
            "photo_270": "https://sun9-46.userapi.com/c846217/v846217368/1c1554/SGvkSBuOTwk.jpg",
            "photo_300": "https://sun9-72.userapi.com/c846217/v846217368/1c1552/Rvbbz6sKMdw.jpg",
            "photo_600": "https://sun9-1.userapi.com/c846217/v846217368/1c1551/BzOIUxmIzXQ.jpg",
            "photo_1200": "https://sun9-10.userapi.com/c846217/v846217368/1c1550/amcpWlIUkro.jpg"
          }
        },
        "main_artists": [
          {
            "name": "Anne-Marie",
            "domain": "313759640627391837",
            "id": "313759640627391837"
          }
        ],
        "subtitle": "Marshmello Remix",
        "short_videos_allowed": false,
        "stories_allowed": false
      }
    ]
  }
  ```
</details>



## audio.getAlbumsByArtist

Возвращает альбомы исполнителя.

### Параметры

| Параметр      | Тип    | Описание            |
|---------------|--------|---------------------|
| **artist_id** | string | ID артиста          |
| count         | int    | Количество альбомов |
| offset        | int    | Смещение            |

### Тип возвращаемого значения

```ts
interface AudioGetAlbumsByArtist {
  count: number
  items: VKAlbum[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "count": 2,
    "items": [{
      "id": 7983755,
      "owner_id": -2000983755,
      "type": 1,
      "title": "Да!",
      "description": "",
      "count": 7,
      "followers": 1176,
      "plays": 10883,
      "create_time": 1593721219,
      "update_time": 1593721219,
      "genres": [{
        "id": 2,
        "name": "Рок"
      }],
      "is_following": false,
      "year": 2020,
      "photo": {
        "width": 300,
        "height": 300,
        "photo_34": "https://sun9-55.userapi.com/c857632/v857632021/21c1e4/3KVzchpR3NI.jpg",
        "photo_68": "https://sun9-18.userapi.com/c857632/v857632021/21c1e2/KNEQcE8bvts.jpg",
        "photo_135": "https://sun9-25.userapi.com/c857632/v857632021/21c1e0/XQ2aGUwSo_k.jpg",
        "photo_270": "https://sun9-13.userapi.com/c857632/v857632021/21c1dd/H6ZYJYt2VdQ.jpg",
        "photo_300": "https://sun9-37.userapi.com/c857632/v857632021/21c1db/cf1grLthEzQ.jpg",
        "photo_600": "https://sun9-69.userapi.com/c857632/v857632021/21c1da/SN4JxhJGtuk.jpg",
        "photo_1200": "https://sun9-4.userapi.com/c857632/v857632021/21c1d9/qmxOjFMaVmY.jpg"
      },
      "permissions": {
        "play": true,
        "share": true,
        "edit": false,
        "follow": true
      },
      "subtitle_badge": false,
      "play_button": false,
      "access_key": "...",
      "is_explicit": false,
      "main_artists": [{
        "name": "Семинар",
        "domain": "8438335135630426544",
        "id": "8438335135630426544"
      }],
      "album_type": "main_only"
    }]
  }
  ```
</details>



## audio.getAudiosByArtist

Возвращает треки артиста.

### Параметры

| Параметр      | Тип    | Описание                                |
|---------------|--------|-----------------------------------------|
| **artist_id** | string | ID артиста                              |
| type          | string | `main`, `featured`, `top` или `snippet` |
| count         | int    | Количество аудиозаписей                 |
| offset        | int    | Смещение                                |

### Тип возвращаемого значения

```ts
interface AudioGetAudiosByArtist {
  count: number
  items: VKAudio[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "count": 7,
    "items": [{
      "artist": "Семинар",
      "id": 69529061,
      "owner_id": -2001529061,
      "title": "Одиночный пикет",
      "duration": 253,
      "access_key": "...",
      "ads": {
        "content_id": "-2001529061_69529061",
        "duration": "253",
        "account_age_type": "3",
        "puid1": "554",
        "puid22": "4"
      },
      "is_explicit": false,
      "is_focus_track": false,
      "is_licensed": true,
      "track_code": "...",
      "url": "...",
      "date": 1593790914,
      "album": {
        "id": 7993968,
        "title": "Одиночный пикет",
        "owner_id": -2000993968,
        "access_key": "...",
        "thumb": {
          "width": 300,
          "height": 300,
          "photo_34": "https://sun7-8.userapi.com/c858036/v858036676/20ab29/ELGtS2DlIkk.jpg",
          "photo_68": "https://sun7-6.userapi.com/c858036/v858036676/20ab27/kJyh2G3RgzY.jpg",
          "photo_135": "https://sun7-7.userapi.com/c858036/v858036676/20ab25/ATgyBM6QdbQ.jpg",
          "photo_270": "https://sun7-7.userapi.com/c858036/v858036676/20ab22/16UD39J-j1Q.jpg",
          "photo_300": "https://sun7-8.userapi.com/c858036/v858036676/20ab20/tWYzl0s8zMw.jpg",
          "photo_600": "https://sun7-8.userapi.com/c858036/v858036676/20ab1f/8OKex01bMDs.jpg",
          "photo_1200": "https://sun7-8.userapi.com/c858036/v858036676/20ab1e/sEbwJg11Au8.jpg"
        }
      },
      "main_artists": [{
        "name": "Семинар",
        "domain": "8438335135630426544",
        "id": "8438335135630426544"
      }],
      "short_videos_allowed": false,
      "stories_allowed": false
    }]
  }
  ```
</details>



## audio.getBroadcast

Показывает, включена ли трансляция играющих аудиозаписей в статус (1 - включена, 0 - выключена).

### Тип возвращаемого значения

```ts
interface AudioGetBroadcast {
  enabled: 0 | 1
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "enabled": 0
  }
  ```
</details>



## audio.getById

Возвращает аудиозаписи по ID.

### Параметры

| Параметр   | Тип    | Описание                                              |
|------------|--------|-------------------------------------------------------|
| **audios** | string | Список аудиозаписей в формате `{owner_id}_{audio_id}` |

### Тип возвращаемого значения

```ts
type AudioGetById = VKAudio[];
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  [{
    "artist": "Galantis",
    "id": 456239726,
    "owner_id": 88262293,
    "title": "Holy Water",
    "duration": 176,
    "access_key": "...",
    "ads": {
      "content_id": "88262293_456239726",
      "duration": "176",
      "account_age_type": "3",
      "puid1": "554",
      "puid22": "14"
    },
    "is_explicit": false,
    "is_focus_track": false,
    "is_licensed": true,
    "track_code": "...",
    "url": "...",
    "date": 1591658249,
    "album": {
      "id": 5574897,
      "title": "Holy Water",
      "owner_id": -2000574897,
      "access_key": "...",
      "thumb": {
        "width": 300,
        "height": 300,
        "photo_34": "https://sun9-66.userapi.com/c850336/v850336422/1ee4b5/vAax1ooeAOM.jpg",
        "photo_68": "https://sun9-16.userapi.com/c850336/v850336422/1ee4b3/gVP8updyQ3Y.jpg",
        "photo_135": "https://sun9-19.userapi.com/c850336/v850336422/1ee4b1/JiWJLXa5XCA.jpg",
        "photo_270": "https://sun9-6.userapi.com/c850336/v850336422/1ee4ae/xeatEmSj_kU.jpg",
        "photo_300": "https://sun9-46.userapi.com/c850336/v850336422/1ee4ac/Zy7j36CjT5A.jpg",
        "photo_600": "https://sun9-60.userapi.com/c850336/v850336422/1ee4ab/f9SBDJrh86s.jpg",
        "photo_1200": "https://sun9-75.userapi.com/c850336/v850336422/1ee4aa/3_-o1FWuCGc.jpg"
      }
    },
    "main_artists": [{
      "name": "Galantis",
      "domain": "2964507775719132986",
      "id": "2964507775719132986"
    }],
    "short_videos_allowed": false,
    "stories_allowed": false
  }]
  ```
</details>



## audio.getCatalog

Возвращает список разделов с аудиозаписями, альбомами, плейлистами, артистами и так далее
(при использовании параметров, описанных ниже, могут вернуться и многие другие разделы, включая свои
и чужие аудиозаписи).

При использовании параметра `artist_id` возвращаются только те разделы, в которых упоминается этот автор:
его "профиль" (информация об артисте), популярные треки, альбомы и так далее.

При использовании параметра `query` возвращаются данные из всех разделов, в которых имеется информация
об этом запросе.

### Параметры

| Параметр   | Тип    | Описание                                      |
|------------|--------|-----------------------------------------------|
| artist_id  | string | ID артиста                                    |
| count      | int    | Количество разделов                           |
| fields     | string | Дополнительные поля для `profiles` и `groups` |
| start_from | string | Смещение (поле `next_from`)                   |
| query      | string | Строка поиска                                 |

### Тип возвращаемого значения

```ts
interface AudioGetCatalog {
  items: VKAudioCatalog[]
  profiles: VKUser[]
  groups: VKGroup[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "items": [{
      "title": "Специально для Вас",
      "subtitle": "best drop ever feat. Skrillex, Skrillex Gta, Luude, Example feat. Georgi Kay, BRUER и другие",
      "type": "audios_special",
      "count": 285,
      "source": "recoms_recoms",
      "id": "PUlYRhcOWkpkWl5UDxYIBzIKBRlSFhY",
      "next_from": "PUlYVA8GWhs",
      "audios": [{
        "artist": "best drop ever feat. Skrillex, Skrillex Gta",
        "id": 63282854,
        "owner_id": -2001282854,
        "title": "Red Lips",
        "duration": 259,
        "access_key": "...",
        "ads": {
          "content_id": "-2001282854_63282854",
          "duration": "259",
          "account_age_type": "3",
          "puid1": "554",
          "puid22": "14"
        },
        "is_explicit": false,
        "is_focus_track": false,
        "is_licensed": true,
        "track_code": "...",
        "url": "...",
        "date": 1583527213,
        "album": {
          "id": 6879768,
          "title": "DJ Suvelo",
          "owner_id": -2000879768,
          "access_key": "...",
          "thumb": {
            "width": 300,
            "height": 300,
            "photo_34": "https://sun9-16.userapi.com/c854216/v854216380/2037d6/ohNCfyUfq08.jpg",
            "photo_68": "https://sun9-10.userapi.com/c854216/v854216380/2037d4/-ufDbUrUDfM.jpg",
            "photo_135": "https://sun9-51.userapi.com/c854216/v854216380/2037d2/M9w5voEoQSQ.jpg",
            "photo_270": "https://sun7-8.userapi.com/c854216/v854216380/2037cf/xroY_Qom6T0.jpg",
            "photo_300": "https://sun7-7.userapi.com/c854216/v854216380/2037cd/SgPArBeO_JU.jpg",
            "photo_600": "https://sun9-21.userapi.com/c854216/v854216380/2037cc/w3DkcEf47iI.jpg",
            "photo_1200": "https://sun9-67.userapi.com/c854216/v854216380/2037cb/wf0VlliuPRA.jpg"
          }
        },
        "main_artists": [{
          "name": "best drop ever",
          "domain": "2176746528624184220",
          "id": "2176746528624184220"
        }],
        "featured_artists": [
          {
            "name": "Skrillex",
            "domain": "901642645687974686",
            "id": "901642645687974686"
          },
          {
            "name": "Skrillex Gta",
            "domain": "2909821709422804596",
            "id": "2909821709422804596"
          }
        ],
        "short_videos_allowed": false,
        "stories_allowed": false
      }],
      "thumbs": [{
        "width": 300,
        "height": 300,
        "photo_34": "https://sun9-16.userapi.com/c854216/v854216380/2037d6/ohNCfyUfq08.jpg",
        "photo_68": "https://sun9-10.userapi.com/c854216/v854216380/2037d4/-ufDbUrUDfM.jpg",
        "photo_135": "https://sun9-51.userapi.com/c854216/v854216380/2037d2/M9w5voEoQSQ.jpg",
        "photo_270": "https://sun7-8.userapi.com/c854216/v854216380/2037cf/xroY_Qom6T0.jpg",
        "photo_300": "https://sun7-7.userapi.com/c854216/v854216380/2037cd/SgPArBeO_JU.jpg",
        "photo_600": "https://sun9-21.userapi.com/c854216/v854216380/2037cc/w3DkcEf47iI.jpg",
        "photo_1200": "https://sun9-67.userapi.com/c854216/v854216380/2037cb/wf0VlliuPRA.jpg"
      }]
    }],
    "next_from": "PUlYVA8FFg",
    "profiles": [],
    "groups": []
  }
  ```
</details>



## audio.getCatalogBlockById

Возвращает отдельный раздел с аудиозаписями, плейлистами, альбомами, артистами или пользователями.

### Параметры

| Параметр     | Тип    | Описание                                       |
|--------------|--------|------------------------------------------------|
| **block_id** | string | ID секции                                      |
| count        | int    | Количество возвращаемых объектов               |
| extended     | flag   | Возвращать в ответе поля `profiles` и `groups` |
| fields       | string | Дополнительные поля для `profiles` и `groups`  |
| start_from   | string | Смещение (поле `next_from`)                    |
| shuffle      | flag   | Перемешать треки                               |

### Тип возвращаемого значения

```ts
interface AudioGetCatalogBlockById {
  block: VKAudioCatalog
  profiles?: VKUser[]
  groups?: VKGroup[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "block": {
      "title": "Новинки",
      "subtitle": "",
      "type": "audios",
      "count": 404,
      "source": "recoms_new_audios",
      "id": "PUlYRhcOWlJqSVhBFw5JBScfCBpaU0kb",
      "next_from": "PUlYVA8FFg",
      "audios": [{
        "artist": "Cream Soda",
        "id": 456242704,
        "owner_id": -192611626,
        "title": "Сердце Лёд",
        "duration": 212,
        "access_key": "...",
        "ads": {
          "content_id": "-192611626_456242704",
          "duration": "212",
          "account_age_type": "3",
          "puid1": "554",
          "puid22": "14"
        },
        "is_explicit": false,
        "is_focus_track": false,
        "is_licensed": true,
        "track_code": "...",
        "url": "...",
        "date": 1594943388,
        "album": {
          "id": 8081184,
          "title": "Сердце Лёд",
          "owner_id": -2000081184,
          "access_key": "...",
          "thumb": {
            "width": 300,
            "height": 300,
            "photo_34": "https://sun9-71.userapi.com/c857320/v857320680/1d802d/pvd-lCBYbIQ.jpg",
            "photo_68": "https://sun9-18.userapi.com/c857320/v857320680/1d802b/izKYymN-Qvo.jpg",
            "photo_135": "https://sun7-7.userapi.com/c857320/v857320680/1d8029/NLbEyTzQzJM.jpg",
            "photo_270": "https://sun9-61.userapi.com/c857320/v857320680/1d8026/Wp7c4g7SC_s.jpg",
            "photo_300": "https://sun7-8.userapi.com/c857320/v857320680/1d8024/pIuK25e3bkE.jpg",
            "photo_600": "https://sun9-17.userapi.com/c857320/v857320680/1d8023/CtRj3c904vQ.jpg",
            "photo_1200": "https://sun9-41.userapi.com/c857320/v857320680/1d8022/BtCQGoh6Mak.jpg"
          }
        },
        "main_artists": [{
          "name": "Cream Soda",
          "domain": "7209762816919878348",
          "id": "7209762816919878348"
        }],
        "short_videos_allowed": false,
        "stories_allowed": true
      }]
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

### Тип возвращаемого значения

```ts

```

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

### Тип возвращаемого значения

```ts

```

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

### Тип возвращаемого значения

```ts

```

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

### Тип возвращаемого значения

```ts

```

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

| Параметр   | Тип    | Описание                                      |
|------------|--------|-----------------------------------------------|
| owner_id   | int    | Чьи плейлисты нужно получить                  |
| fields     | string | Дополнительные поля для `profiles` и `groups` |
| start_from | string | Оффсет                                        |
| offset     | int    | Оффсет                                        |
| count      | int    | Количество плейлистов                         |
| filters    | string | -                                             |
| extended   | int    | Флаг                                          |

### Тип возвращаемого значения

```ts

```

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

### Тип возвращаемого значения

```ts

```

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

### Тип возвращаемого значения

```ts

```

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

### Тип возвращаемого значения

```ts

```

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

### Тип возвращаемого значения

```ts

```

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

### Тип возвращаемого значения

```ts

```

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

### Тип возвращаемого значения

```ts

```

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

### Тип возвращаемого значения

```ts

```

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

### Тип возвращаемого значения

```ts

```

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

### Тип возвращаемого значения

```ts

```

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

### Тип возвращаемого значения

```ts

```

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

Сохраняет аудиозапись в своем списке аудиозаписей после [загрузки](https://vk.com/dev/upload_files_2).

### Параметры

| Параметр     | Тип    | Описание                                                                   |
|--------------|--------|----------------------------------------------------------------------------|
| **audio**    | string | Параметр, возвращаемый после [загрузки](https://vk.com/dev/upload_files_2) |
| **server**   | string | Параметр, возвращаемый после [загрузки](https://vk.com/dev/upload_files_2) |
| **hash**     | string | Параметр, возвращаемый после [загрузки](https://vk.com/dev/upload_files_2) |
| artist       | string | Автор композиции (по умолчанию `Unknown artist`)                           |
| title        | string | Название композиции (по умолчанию `Untitled`)                              |

### Тип возвращаемого значения

```ts

```

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

### Тип возвращаемого значения

```ts

```

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

### Тип возвращаемого значения

```ts

```

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

### Тип возвращаемого значения

```ts

```

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

### Тип возвращаемого значения

```ts

```

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

### Тип возвращаемого значения

```ts

```

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

### Тип возвращаемого значения

```ts

```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "response": []
  }
  ```
</details>
