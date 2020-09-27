# audio

Методы для работы с аудиозаписями

## Доступ

Для доступа ко всем методам, кроме `audio.add`, `audio.edit`, `audio.getUploadServer` и `audio.save`,
необходимо использовать токен VK для Android.

## Список методов

* [audio.add](#audioadd) — добавить аудиозапись к себе
* [audio.addToPlaylist](#audioaddtoplaylist) — добавить аудиозаписи в плейлист
* [audio.createPlaylist](#audiocreateplaylist) — создать плейлист
* [audio.delete](#audiodelete) — удалить свою аудиозапись
* [audio.deletePlaylist](#audiodeleteplaylist) — удалить плейлист
* [audio.edit](#audioedit) — отредактировать данные аудиозаписи
* [audio.editPlaylist](#audioeditplaylist) — отредактировать данные плейлиста
* [audio.get](#audioget) — получить список аудиозаписей в профиле или плейлисте
* [audio.getAlbumsByArtist](#audiogetalbumsbyartist) — получить альбомы исполнителя
* [audio.getAudiosByArtist](#audiogetaudiosbyartist) — получить треки исполнителя
* [audio.getBroadcast](#audiogetbroadcast) — включена ли трансляция треков в статус
* [audio.getById](#audiogetbyid) — получить аудиозаписи по ID
* [audio.getCatalog](#audiogetcatalog) — получить список разделов с аудиозаписями или плейлистами
* [audio.getCatalogBlockById](#audiogetcatalogblockbyid) — получить раздел по ID
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
* [audio.search](#audiosearch) — поиск аудиозаписей
* [audio.searchAlbums](#audiosearchalbums) — поиск альбомов
* [audio.searchArtists](#audiosearchartists) — поиск исполнителей
* [audio.searchMain](#audiosearchmain) — поиск всех объектов, связанных с разделом музыки
* [audio.searchPlaylists](#audiosearchplaylists) — поиск плейлистов
* [audio.setBroadcast](#audiosetbroadcast) — установить аудиозапись в статус профиля или сообществ



## audio.add

Добавляет чужую аудиозапись к себе.

Метод так же позволяет добавлять аудиозаписи из своего списка, даже если они были удалены **несколько лет назад**.

### Параметры

| Параметр     | Тип    | Описание                      |
|--------------|--------|-------------------------------|
| **owner_id** | int    | ID владельца аудиозаписи      |
| **audio_id** | int    | ID аудиозаписи                |
| access_key   | string | Ключ доступа                  |
| track_code   | string | Параметр для сбора статистики |

### Тип возвращаемого значения

Возвращает ID добавленной аудиозаписи.

```ts
type AudioAdd = number;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  456239735
  ```
</details>



## audio.addToPlaylist

Добавляет аудиозаписи в плейлист.

### Параметры

| Параметр        | Тип    | Описание                                              |
|-----------------|--------|-------------------------------------------------------|
| **owner_id**    | int    | ID владельца плейлиста                                |
| **playlist_id** | int    | ID плейлиста                                          |
| **audio_ids**   | string | Список аудиозаписей в формате `{owner_id}_{audio_id}` |

### Тип возвращаемого значения

Возвращает список с ID добавленных аудиозаписей.

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

### Связанные методы

* execute.addAudioToPlaylist — добавить аудиозаписи в плейлист



## audio.createPlaylist

Создает плейлист.

### Параметры

| Параметр     | Тип    | Описание                                              |
|--------------|--------|-------------------------------------------------------|
| **owner_id** | int    | ID пользователя или группы                            |
| **title**    | string | Название плейлиста                                    |
| description  | string | Описание плейлиста                                    |
| audio_ids    | string | Список аудиозаписей в формате `{owner_id}_{audio_id}` |

В качестве `owner_id` можно указать либо свой ID, либо ID группы, в которую можно добавлять аудиозаписи.

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

Удаляет аудиозапись из добавленных с [возможностью ее восстановления](#audiorestore).

### Параметры

| Параметр     | Тип | Описание                 |
|--------------|-----|--------------------------|
| **owner_id** | int | ID владельца аудиозаписи |
| **audio_id** | int | ID аудиозаписи           |

### Тип возвращаемого значения

```ts
type AudioDelete = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>



## audio.deletePlaylist

Удаляет плейлист **без возможности восстановления**.

### Параметры

| Параметр        | Тип | Описание               |
|-----------------|-----|------------------------|
| **owner_id**    | int | ID владельца плейлиста |
| **playlist_id** | int | ID плейлиста           |

### Тип возвращаемого значения

```ts
type AudioDeletePlaylist = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>



## audio.edit

Редактирует данные аудиозаписи.

**Обратите внимание:** для треков, которые нельзя редактировать приходит 15 ошибка API `Access Denied`.

Понять, что редактировать трек разрешено, можно только после вызова этого метода с передачей двух
обязательных параметров. Если редактировать нельзя, то придет ошибка, а если можно, то вернется число.

Понять, что редактировать трек запрещено, можно либо с помощью вызова этого метода, либо проверив
аудиозапись на наличие поля `main_artists`. Если этого поля не будет, то это не означает, что редактировать
трек разрешено.

### Параметры

| Параметр     | Тип    | Описание                                            |
|--------------|--------|-----------------------------------------------------|
| **owner_id** | int    | ID владельца аудиозаписи                            |
| **audio_id** | int    | ID аудиозаписи                                      |
| artist       | string | Новое название исполнителя                          |
| title        | string | Новое название аудиозаписи                          |
| text         | string | Новый текст аудиозаписи                             |
| genre_id     | int    | [ID жанра](https://vk.com/dev/objects/audio_genres) |
| no_search    | flag   | Исключить аудиозапись из поиска                     |

Для редактирования одного или нескольких полей необязательно передавать все остальные.

### Тип возвращаемого значения

```ts
// Возвращает lyrics_id (если есть текст песни) или 0
type AudioEdit = number;
```

### Пример ответа

<details>
  <summary>Открыть</summary>
  ```json
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

  ```json
  1
  ```
</details>



## audio.get

Возвращает аудиозаписи:
  * С вашей страницы (если не указывать или указать ваш `owner_id`)
  * Со страницы другого пользователя или группы (при указании `owner_id`)
  * Из плейлиста пользователя или группы (при указании `playlist_id`)

### Параметры

| Параметр     | Тип    | Описание                                                            |
|--------------|--------|---------------------------------------------------------------------|
| owner_id     | int    | ID владельца аудиозаписей. По умолчанию ваш ID                      |
| playlist_id  | int    | ID плейлиста                                                        |
| access_key   | string | Ключ доступа                                                        |
| shuffle_seed | int    | Рандомное число. Используется для случайной сортировки аудиозаписей |
| count        | int    | Количество аудиозаписей                                             |
| offset       | int    | Смещение                                                            |
| extended     | flag   | Возвращать в ответе поля `profiles` и `groups`                      |
| fields       | string | Дополнительные поля для `profiles` и `groups`                       |

При указании поля `shuffle_seed` включается сортировка аудиозаписей,
однако если указывать одно и то же число, список не будет меняться.

### Тип возвращаемого значения

```ts
interface AudioGet {
  count: number
  items: VKAudio[]
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
    "items": [{
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
      "url": "...",
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
      "main_artists": [{
        "name": "Anne-Marie",
        "domain": "313759640627391837",
        "id": "313759640627391837"
      }],
      "subtitle": "Marshmello Remix",
      "short_videos_allowed": false,
      "stories_allowed": false
    }]
  }
  ```
</details>

### Связанные методы

* execute.CommunityAudiosAndPlaylists — получить превью треков и плейлистов



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
(при использовании некоторых параметров, могут вернуться и многие другие разделы, включая свои
и чужие аудиозаписи).

### Параметры

| Параметр   | Тип    | Описание                                      |
|------------|--------|-----------------------------------------------|
| artist_id  | string | ID артиста                                    |
| query      | string | Строка поиска                                 |
| count      | int    | Количество разделов                           |
| start_from | string | Смещение (поле `next_from`)                   |
| fields     | string | Дополнительные поля для `profiles` и `groups` |

При использовании параметра `artist_id` возвращаются только те разделы, в которых упоминается этот автор:
его "профиль" (информация об артисте), популярные треки, альбомы и так далее.

При использовании параметра `query` возвращаются данные из всех разделов, в которых имеется информация
об этом запросе.

### Тип возвращаемого значения

```ts
interface AudioGetCatalog {
  items: VKAudioCatalog[]
  next_from?: string
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
| **block_id** | string | ID раздела                                     |
| shuffle      | flag   | Перемешать треки                               |
| count        | int    | Количество возвращаемых объектов               |
| start_from   | string | Смещение (поле `next_from`)                    |
| extended     | flag   | Возвращать в ответе поля `profiles` и `groups` |
| fields       | string | Дополнительные поля для `profiles` и `groups`  |

### Тип возвращаемого значения

```ts
interface AudioGetCatalogBlockById {
  block: VKAudioCatalog
  next_from?: string
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

Возвращает количество аудиозаписей.

### Параметры

| Параметр     | Тип | Описание                  |
|--------------|-----|---------------------------|
| **owner_id** | int | ID владельца аудиозаписей |

### Тип возвращаемого значения

```ts
type AudioGetCount = number;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  43
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
interface AudioGetHints {
  count: number
  items: { name: string }[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "count": 5,
    "items": [
      { "name": "сектор газа" },
      { "name": "король и шут" },
      { "name": "rammstein" },
      { "name": "ария" },
      { "name": "кино" }
    ]
  }
  ```
</details>



## audio.getLyrics

Возвращает текст песни.

### Параметры

| Параметр      | Тип | Описание        |
|---------------|-----|-----------------|
| **lyrics_id** | int | ID текста песни |

Поле `lyrics_id` можно получить из объекта аудиозаписи.
В некоторых аудиозаписях данное поле отсутствует.

### Тип возвращаемого значения

```ts
interface AudioGetLyrics {
  lyrics_id: number
  text: string
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "lyrics_id": 314927765,
    "text": "Я знаю, где живет любовь. <продолжение текста ...>"
  }
  ```
</details>



## audio.getPlaylistById

Возвращает плейлист по ID.

### Параметры

| Параметр        | Тип    | Описание               |
|-----------------|--------|------------------------|
| **owner_id**    | int    | ID владельца плейлиста |
| **playlist_id** | int    | ID плейлиста           |
| access_key      | string | Ключ доступа           |

### Тип возвращаемого значения

```ts
type AudioGetPlaylistById = VKPlaylist;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "id": 7,
    "owner_id": 88262293,
    "type": 0,
    "title": "Тайтл",
    "description": "",
    "count": 0,
    "followers": 0,
    "plays": 0,
    "create_time": 1595147212,
    "update_time": 1595147212,
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



## audio.getPlaylists

Возвращает список плейлистов.

### Параметры

| Параметр     | Тип    | Описание                                       |
|--------------|--------|------------------------------------------------|
| **owner_id** | int    | ID пользователя или группы                     |
| filters      | string | `all`, `owned` или `followed`                  |
| count        | int    | Количество плейлистов                          |
| start_from   | string | Смещение (поле `next_from`)                    |
| offset       | int    | Смещение                                       |
| extended     | flag   | Возвращать в ответе поля `profiles` и `groups` |
| fields       | string | Дополнительные поля для `profiles` и `groups`  |

Поля `start_from` и `offset` отвечают за смещение, но работают по разному:
  * Поле `start_from` не требует сохранения количества полученных плейлистов и не имеет никаких багов.
  * Поле `offset` же требует передавать в него количество уже загруженных плейлистов. Так же,
    если между двумя запросами пользователь добавит плейлист или удалит его, то в результате
    мы можем увидеть один уже полученный плейлист или пропустить еще не полученный.
    С полем `start_from` таких проблем нет.

### Тип возвращаемого значения

```ts
interface AudioGetPlaylists {
  count: number
  items: VKPlaylist[]
  next_from?: string
  profiles?: VKUser[]
  groups?: VKGroup[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "count": 3,
    "items": [{
      "id": 7,
      "owner_id": 88262293,
      "type": 0,
      "title": "Тайтл",
      "description": "",
      "count": 0,
      "followers": 0,
      "plays": 0,
      "create_time": 1595147212,
      "update_time": 1595147212,
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
    }],
    "next_from": "PUlYVA8FFg"
  }
  ```
</details>



## audio.getPopular

Возвращает популярные треки.

### Параметры

| Параметр | Тип | Описание                |
|----------|-----|-------------------------|
| count    | int | Количество аудиозаписей |
| offset   | int | Смещение                |

### Тип возвращаемого значения

```ts
type AudioGetPopular = VKAudio[];
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  [{
    "artist": "Dua Lipa",
    "id": 456240861,
    "owner_id": -30462549,
    "title": "Lost In Your Light (feat. Miguel)",
    "duration": 203,
    "access_key": "...",
    "ads": {
      "content_id": "-30462549_456240861",
      "duration": "203",
      "account_age_type": "3",
      "puid1": "554",
      "puid22": "11"
    },
    "is_explicit": false,
    "is_focus_track": false,
    "is_licensed": true,
    "track_code": "...",
    "url": "...",
    "date": 1492759440,
    "album": {
      "id": 1076509,
      "title": "Dua Lipa (Deluxe)",
      "owner_id": -2000076509,
      "access_key": "...",
      "thumb": {
        "width": 300,
        "height": 300,
        "photo_34": "https://sun9-31.userapi.com/c850624/v850624473/897e3/V1ZYebaC7Ek.jpg",
        "photo_68": "https://sun9-61.userapi.com/c850624/v850624473/897e1/8r12iNEvDNw.jpg",
        "photo_135": "https://sun9-65.userapi.com/c850624/v850624473/897df/fUb4rQZ7Upw.jpg",
        "photo_270": "https://sun9-63.userapi.com/c850624/v850624473/897dc/SIx4ElilzAQ.jpg",
        "photo_300": "https://sun9-21.userapi.com/c850624/v850624473/897da/f6GrbQ2iekk.jpg",
        "photo_600": "https://sun9-62.userapi.com/c850624/v850624473/897d9/W9TLz2sqldI.jpg",
        "photo_1200": "https://sun9-34.userapi.com/c850624/v850624473/897d8/KlfaLUvJogU.jpg"
      }
    },
    "short_videos_allowed": false,
    "stories_allowed": false
  }]
  ```
</details>



## audio.getRecentAudios

Возвращает недавно прослушанные треки.

### Параметры

| Параметр    | Тип | Описание                |
|-------------|-----|-------------------------|
| **user_id** | int | ID пользователя         |
| count       | int | Количество аудиозаписей |
| offset      | int | Смещение                |

### Тип возвращаемого значения

```ts
interface AudioGetRecentAudios {
  count: number
  items: VKAudio[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "count": 100,
    "items": [{
      "artist": "Galantis feat. Uffie",
      "id": 456239725,
      "owner_id": 88262293,
      "title": "Spaceship (feat. Uffie)",
      "duration": 167,
      "is_explicit": false,
      "is_focus_track": false,
      "is_licensed": true,
      "track_code": "...",
      "url": "...",
      "date": 1591653457,
      "album": {
        "id": 3001059,
        "title": "Spaceship (feat. Uffie)",
        "owner_id": -2000001059,
        "access_key": ""
      },
      "main_artists": [{
        "name": "Galantis",
        "domain": "2964507775719132986",
        "id": "2964507775719132986"
      }],
      "featured_artists": [{
        "name": "Uffie",
        "domain": "7292887933358092165",
        "id": "7292887933358092165"
      }],
      "short_videos_allowed": false,
      "stories_allowed": false
    }]
  }
  ```
</details>



## audio.getRecommendations

Возвращает музыкальные рекомендации или похожие на определенную аудиозапись треки,
если передать параметр `target_audio`.

### Параметры

| Параметр     | Тип    | Описание                                      |
|--------------|--------|-----------------------------------------------|
| target_audio | string | Аудиозапись в формате `{owner_id}_{audio_id}` |
| count        | int    | Количество аудиозаписей (по умолчанию 100)    |
| offset       | int    | Смещение                                      |

### Тип возвращаемого значения

```ts
interface AudioGetRecommendations {
  count: number
  items: VKAudio[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "count": 874,
    "items": [{
      "artist": "Tony Baffoni",
      "id": 46641266,
      "owner_id": -2001641266,
      "title": "Punk Stronger",
      "duration": 422,
      "access_key": "...",
      "ads": {
        "content_id": "-2001641266_46641266",
        "duration": "422",
        "account_age_type": "3",
        "puid1": "554",
        "puid22": "19"
      },
      "is_explicit": false,
      "is_focus_track": false,
      "is_licensed": true,
      "track_code": "...",
      "url": "...",
      "date": 1578658063,
      "album": {
        "id": 4045297,
        "title": "Punk Stronger",
        "owner_id": -2000045297,
        "access_key": "...",
        "thumb": {
          "width": 300,
          "height": 300,
          "photo_34": "https://sun9-65.userapi.com/c855428/v855428701/1f85c9/OPMskFnGp5M.jpg",
          "photo_68": "https://sun9-76.userapi.com/c855428/v855428701/1f85c7/LZ1BgDk_DVQ.jpg",
          "photo_135": "https://sun9-43.userapi.com/c855428/v855428701/1f85c5/3syD7JvniuU.jpg",
          "photo_270": "https://sun9-69.userapi.com/c855428/v855428701/1f85c2/VHVGovJnZyk.jpg",
          "photo_300": "https://sun9-43.userapi.com/c855428/v855428701/1f85c0/uj23uDgnmHg.jpg",
          "photo_600": "https://sun9-27.userapi.com/c855428/v855428701/1f85bf/qX24VYq0_HI.jpg",
          "photo_1200": "https://sun9-19.userapi.com/c855428/v855428701/1f85be/aZwghVU3Esg.jpg"
        }
      },
      "main_artists": [{
        "name": "Tony Baffoni",
        "domain": "8762839818532256366",
        "id": "8762839818532256366"
      }],
      "short_videos_allowed": false,
      "stories_allowed": false
    }]
  }
  ```
</details>



## audio.getRestrictionPopup

Возвращает информацию об ограничении доступа к аудиозаписи.

**Внимание:** данный метод не определяет, является ли аудиозапись заблокированной или нет.

Если передать в этот метод рабочую аудиозапись, то метод вернет стандартную заглушку:
```
         Аудиозапись недоступна
Так решил музыкант или его представитель
```

Такой же текст метод вернет и для некоторых других уже заблокированных аудиозаписей,
но иногда могут встретиться и другие варианты, например такой (из примера ответа):
```
         Аудиозапись доступна с подпиской
Так решил музыкант или его представитель. Оформите
   подписку и получите расширенные возможности.
```

### Параметры

| Параметр     | Тип    | Описание                                      |
|--------------|--------|-----------------------------------------------|
| **audio_id** | string | Аудиозапись в формате `{owner_id}_{audio_id}` |
| track_code   | string | Параметр для сбора статистики                 |

### Тип возвращаемого значения

```ts
interface AudioGetRestrictionPopup {
  title: string
  text: string
  icons: { width: number, height: number, url: string }[]
  music_subscription_event?: 'exclusive'
  button?: VKButton
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "title": "Аудиозапись доступна с подпиской",
    "button": {
      "action": {
        "target": "internal",
        "type": "open_url",
        "url": "https://vk.com/popup?act=buy_music_subscription&source=link"
      },
      "title": "Оформить подписку"
    },
    "icons": [
      {
        "height": 72,
        "url": "https://vk.com/images/media/pensive_face_72x72.png",
        "width": 72
      },
      {
        "height": 144,
        "url": "https://vk.com/images/media/pensive_face_144x144.png",
        "width": 144
      },
      {
        "height": 216,
        "url": "https://vk.com/images/media/pensive_face_216x216.png",
        "width": 216
      },
      {
        "height": 288,
        "url": "https://vk.com/images/media/pensive_face_288x288.png",
        "width": 288
      }
    ],
    "music_subscription_event": "exclusive",
    "text": "Так решил музыкант или его представитель. Оформите подписку и получите расширенные возможности."
  }
  ```
</details>



## audio.getSearchTrends

Возвращает популярные поисковые запросы.

### Параметры

| Параметр | Тип | Описание             |
|----------|-----|----------------------|
| count    | int | Количество элементов |
| offset   | int | Смещение             |

### Тип возвращаемого значения

```ts
interface AudioGetSearchTrends {
  count: number
  items: { name: string }[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "count": 20,
    "items": [
      { "name": "miyagi" },
      { "name": "fendi" },
      { "name": "the" },
      { "name": "morgenshtern" },
      { "name": "скриптонит" },
      { "name": "моргенштерн" },
      { "name": "сектор газа" },
      { "name": "lil" },
      { "name": "мияги" },
      { "name": "кадилак" }
    ]
  }
  ```
</details>



## audio.getStoryCatalog

Возвращает аудиозаписи, которые можно использовать в историях.

### Параметры

| Параметр   | Тип    | Описание                    |
|------------|--------|-----------------------------|
| count      | int    | Количество блоков           |
| start_from | string | Смещение (поле `next_from`) |

### Тип возвращаемого значения

```ts
interface AudioGetStoryCatalog {
  sections: VKAudioStorySection[]
}

interface VKAudioStorySection {
  id: string
  name: string
  blocks: VKAudioStoryBlock[]
  url: string
  is_selected: 1
  next_from?: string
  total_count: number
}

interface VKAudioStoryBlock {
  id: string
  block_view_type: 'triple_stacked_slider_picker'
  url: string
  music_audios: VKAudio[]
  owner_id: number
  fullscreen_view_type: 'list_picker'
  title: string
  data_type: 'music_audios'
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "sections": [{
      "id": "PUldVA8GR0RzSVNUagdTRGpJUFQPBRY",
      "name": "",
      "blocks": [{
        "id": "PUlQVA8GR0R3W0tMF2tZVGRHS04XDkZXflheQQYCWFFqSVxUDxY0VX5JRVQBFlFUaklYQxcOWhs",
        "block_view_type": "triple_stacked_slider_picker",
        "url": "https://vk.com/",
        "music_audios": [{
          "artist": "Cream Soda",
          "id": 456241448,
          "owner_id": -183773637,
          "title": "Сердце Лёд",
          "duration": 212,
          "access_key": "...",
          "ads": {
            "content_id": "-183773637_456241448",
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
          "date": 1594936401,
          "album": {
            "id": 8081184,
            "title": "Сердце Лёд",
            "owner_id": -2000081184,
            "access_key": "...",
            "thumb": {
              "width": 300,
              "height": 300,
              "photo_34": "https://sun7-7.userapi.com/c857320/v857320680/1d802d/pvd-lCBYbIQ.jpg",
              "photo_68": "https://sun7-9.userapi.com/c857320/v857320680/1d802b/izKYymN-Qvo.jpg",
              "photo_135": "https://sun7-7.userapi.com/c857320/v857320680/1d8029/NLbEyTzQzJM.jpg",
              "photo_270": "https://sun7-8.userapi.com/c857320/v857320680/1d8026/Wp7c4g7SC_s.jpg",
              "photo_300": "https://sun7-8.userapi.com/c857320/v857320680/1d8024/pIuK25e3bkE.jpg",
              "photo_600": "https://sun7-7.userapi.com/c857320/v857320680/1d8023/CtRj3c904vQ.jpg",
              "photo_1200": "https://sun7-8.userapi.com/c857320/v857320680/1d8022/BtCQGoh6Mak.jpg"
            }
          },
          "main_artists": [{
            "name": "Cream Soda",
            "domain": "7209762816919878348",
            "id": "7209762816919878348"
          }],
          "short_videos_allowed": false,
          "stories_allowed": true
        }],
        "owner_id": -183773637,
        "fullscreen_view_type": "list_picker",
        "title": "Новинки",
        "data_type": "music_audios"
      }],
      "url": "https://vk.com/",
      "is_selected": 1,
      "next_from": "PUlYVA8FFg",
      "total_count": 3
    }]
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
// Описан в методе выше
type AudioGetStorySearchCatalog = AudioGetStoryCatalog;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "sections": [{
      "id": "PUldVA8HR0RzSVNUagdTRGpJUFQPBRY",
      "name": "",
      "blocks": [{
        "id": "PUlQVA8GR0R3W0tMF2tZUmRHS0EXDkk6M1tdRVNoHlZyX1kqQARfVX43HEYBB1k6M1tdRQBoHlZyX1tUGRZeRHxJNkUNFkdEcklTRRkWWlNkUVgL",
        "block_view_type": "list_picker",
        "url": "https://vk.com/",
        "no_header": 1,
        "music_audios": [{
          "artist": "MATRANG, Баста",
          "id": 52301274,
          "owner_id": -2001301274,
          "title": "Привет",
          "duration": 195,
          "access_key": "...",
          "ads": {
            "content_id": "-2001301274_52301274",
            "duration": "195",
            "account_age_type": "3",
            "puid1": "554",
            "puid22": "14"
          },
          "is_explicit": false,
          "is_focus_track": false,
          "is_licensed": true,
          "track_code": "...",
          "url": "...",
          "date": 1559735459,
          "album": {
            "id": 4878866,
            "title": "Привет",
            "owner_id": -2000878866,
            "access_key": "...",
            "thumb": {
              "width": 300,
              "height": 300,
              "photo_34": "https://sun7-9.userapi.com/c852320/v852320164/146b17/fZiahTMz7co.jpg",
              "photo_68": "https://sun7-8.userapi.com/c852320/v852320164/146b15/GpA8CPkpuuE.jpg",
              "photo_135": "https://sun7-8.userapi.com/c852320/v852320164/146b13/tCavZykKSL0.jpg",
              "photo_270": "https://sun7-6.userapi.com/c852320/v852320164/146b10/SZXbfzX-Shg.jpg",
              "photo_300": "https://sun7-6.userapi.com/c852320/v852320164/146b0e/uSziIaxD450.jpg",
              "photo_600": "https://sun7-7.userapi.com/c852320/v852320164/146b0d/E6kDgHMCsqY.jpg",
              "photo_1200": "https://sun7-7.userapi.com/c852320/v852320164/146b0c/Ttd6hXc-aII.jpg"
            }
          },
          "main_artists": [
            {
              "name": "MATRANG",
              "domain": "4563136988003343146",
              "id": "4563136988003343146"
            },
            {
              "name": "Баста",
              "domain": "2860392754699853973",
              "id": "2860392754699853973"
            }
          ],
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
    }]
  }
  ```
</details>



## audio.getUploadServer

Возвращает адрес для загрузки аудиозаписи.

### Тип возвращаемого значения

```ts
interface AudioGetUploadServer {
  upload_url: string
}
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

| Параметр     | Тип | Описание                                                   |
|--------------|-----|------------------------------------------------------------|
| **audio_id** | int | ID аудиозаписи, у которой меняем позицию                   |
| before       | int | ID аудиозаписи, перед которой будет поставлена аудиозапись |
| after        | int | ID аудиозаписи, после которой будет поставлена аудиозапись |

Вы должны использовать либо `before`, либо `after`. Нельзя использовать оба параметра сразу.

### Тип возвращаемого значения

```ts
type AudioReorder = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>



## audio.reorderPlaylists

Изменяет положение плейлиста.

### Параметры

| Параметр        | Тип | Описание                                              |
|-----------------|-----|-------------------------------------------------------|
| **owner_id**    | int | ID владельца плейлиста                                |
| **playlist_id** | int | ID плейлиста                                          |
| before          | int | ID плейлиста, перед которым будет поставлен плейлист  |
| after           | int | ID плейлиста, после которого будет поставлен плейлист |

Вы должны использовать либо `before`, либо `after`. Нельзя использовать оба параметра сразу.

### Тип возвращаемого значения

```ts
type AudioReorderPlaylists = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>



## audio.restore

Восстанавливает удаленную аудиозапись.

**Внимание:** метод может не восстановить аудиозапись, а выдать 15 ошибку
`Access denied: can not restore too late`, даже если с момента удаления прошла всего секунда.

Если восстановить аудиозапись не удалось, вы можете использовать [audio.add](#audioadd) для
добавления аудиозаписи и [audio.reorder](#audioreorder) для перемещения на старое положение.

### Параметры

| Параметр     | Тип | Описание                 |
|--------------|-----|--------------------------|
| **owner_id** | int | ID владельца аудиозаписи |
| **audio_id** | int | ID аудиозаписи           |

### Тип возвращаемого значения

```ts
type AudioRestore = VKAudio;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "artist": "Galantis",
    "id": 456239739,
    "owner_id": 88262293,
    "title": "Holy Water",
    "duration": 176,
    "access_key": "...",
    "ads": {
      "content_id": "88262293_456239739",
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
    "date": 1595181602,
    "album": {
      "id": 6662324,
      "title": "Church",
      "owner_id": -2000662324,
      "access_key": "...",
      "thumb": {
        "width": 300,
        "height": 300,
        "photo_34": "https://sun9-72.userapi.com/c855328/v855328237/1eadf9/vnhIHV1Z6r4.jpg",
        "photo_68": "https://sun9-33.userapi.com/c855328/v855328237/1eadf7/Z24BeWRX5mA.jpg",
        "photo_135": "https://sun9-68.userapi.com/c855328/v855328237/1eadf5/k2NyMgcDJuc.jpg",
        "photo_270": "https://sun9-25.userapi.com/c855328/v855328237/1eadf2/Qb2VLx3DsN0.jpg",
        "photo_300": "https://sun9-5.userapi.com/c855328/v855328237/1eadf0/9tedhIMwRd4.jpg",
        "photo_600": "https://sun9-75.userapi.com/c855328/v855328237/1eadef/jAJ3KsEwhmc.jpg",
        "photo_1200": "https://sun9-38.userapi.com/c855328/v855328237/1eadee/p3LqYbLbYlE.jpg"
      }
    },
    "main_artists": [{
      "name": "Galantis",
      "domain": "2964507775719132986",
      "id": "2964507775719132986"
    }],
    "short_videos_allowed": false,
    "stories_allowed": false
  }
  ```
</details>



## audio.save

Сохраняет аудиозапись в своем списке аудиозаписей после [загрузки](https://vk.com/dev/upload_files_2).

### Параметры

| Параметр   | Тип    | Описание                                                                   |
|------------|--------|----------------------------------------------------------------------------|
| **audio**  | string | Параметр, возвращаемый после [загрузки](https://vk.com/dev/upload_files_2) |
| **server** | string | Параметр, возвращаемый после [загрузки](https://vk.com/dev/upload_files_2) |
| **hash**   | string | Параметр, возвращаемый после [загрузки](https://vk.com/dev/upload_files_2) |
| artist     | string | Автор композиции (по умолчанию `Unknown artist`)                           |
| title      | string | Название композиции (по умолчанию `Untitled`)                              |

### Тип возвращаемого значения

```ts
type AudioSave = VKAudio;
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
    "url": "...",
    "date": 1595144321,
    "short_videos_allowed": false,
    "stories_allowed": false
  }
  ```
</details>



## audio.search

Возвращает найденные аудиозаписи.

### Параметры

| Параметр       | Тип    | Описание                                |
|----------------|--------|-----------------------------------------|
| **q**          | string | Строка поиска                           |
| search_own     | flag   | Включить в поиск свои аудиозаписи       |
| performer_only | flag   | Учитывать при поиске только имя артиста |
| count          | int    | Количество аудиозаписей                 |
| offset         | int    | Смещение                                |

### Тип возвращаемого значения

```ts
interface AudioSearch {
  count: number
  items: VKAudio[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "count": 2,
    "items": [{
      "artist": "Blueface feat. NLE Choppa",
      "id": 456423991,
      "owner_id": 474499303,
      "title": "Holy Moly",
      "duration": 117,
      "access_key": "...",
      "ads": {
        "content_id": "474499303_456423991",
        "duration": "117",
        "account_age_type": "3",
        "puid1": "554",
        "puid22": "14"
      },
      "is_explicit": true,
      "is_focus_track": false,
      "is_licensed": true,
      "track_code": "...",
      "url": "...",
      "date": 1583120470,
      "album": {
        "id": 6910969,
        "title": "Find The Beat",
        "owner_id": -2000910969,
        "access_key": "...",
        "thumb": {
          "width": 300,
          "height": 300,
          "photo_34": "https://sun9-53.userapi.com/c857216/v857216158/114f1d/dgOwQQcgkj4.jpg",
          "photo_68": "https://sun9-10.userapi.com/c857216/v857216158/114f1b/wLme_yA0ZwU.jpg",
          "photo_135": "https://sun9-58.userapi.com/c857216/v857216158/114f19/pTtEDzBo5j0.jpg",
          "photo_270": "https://sun9-43.userapi.com/c857216/v857216158/114f16/HfPSBg_km_w.jpg",
          "photo_300": "https://sun9-41.userapi.com/c857216/v857216158/114f14/0IPQMMPOkF4.jpg",
          "photo_600": "https://sun9-8.userapi.com/c857216/v857216158/114f13/FPCG77xZCRc.jpg",
          "photo_1200": "https://sun9-75.userapi.com/c857216/v857216158/114f12/nM8GKx9ALC0.jpg"
        }
      },
      "main_artists": [{
        "name": "Blueface",
        "domain": "5567090177057503639",
        "id": "5567090177057503639"
      }],
      "featured_artists": [{
        "name": "NLE Choppa",
        "domain": "5044437380400510414",
        "id": "5044437380400510414"
      }],
      "short_videos_allowed": false,
      "stories_allowed": false
    }]
  }
  ```
</details>



## audio.searchAlbums

Возвращает найденные альбомы.

Отличается от плейлистов тем, что альбомы могут быть выпущены только исполнителями.

### Параметры

| Параметр | Тип    | Описание            |
|----------|--------|---------------------|
| **q**    | string | Строка поиска       |
| count    | int    | Количество альбомов |
| offset   | int    | Смещение            |

### Тип возвращаемого значения

```ts
interface AudioSearchAlbums {
  count: number
  items: VKAlbum[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "count": 295,
    "items": [{
      "id": 126839,
      "owner_id": -2000126839,
      "type": 1,
      "title": "Holy Diver",
      "description": "",
      "count": 18,
      "followers": 2865,
      "plays": 65811,
      "create_time": 1491423781,
      "update_time": 1561139745,
      "genres": [{
        "id": 12,
        "name": "Метал"
      }],
      "is_following": false,
      "year": 2012,
      "photo": {
        "width": 300,
        "height": 300,
        "photo_34": "https://sun9-23.userapi.com/c845218/v845218241/1477bc/mswuasNGv5Y.jpg",
        "photo_68": "https://sun9-22.userapi.com/c845218/v845218241/1477ba/X7_Ab4cSnl0.jpg",
        "photo_135": "https://sun9-38.userapi.com/c845218/v845218241/1477b8/W0ITCxzRhXQ.jpg",
        "photo_270": "https://sun9-23.userapi.com/c845218/v845218241/1477b5/O0d01O8MpTE.jpg",
        "photo_300": "https://sun9-75.userapi.com/c845218/v845218241/1477b3/a5w9fnnRyBM.jpg",
        "photo_600": "https://sun9-3.userapi.com/c845218/v845218241/1477b2/C1Lwb4KPB7A.jpg",
        "photo_1200": "https://sun9-51.userapi.com/c845218/v845218241/1477b1/PKHveyBj-G4.jpg"
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
      "subtitle": "Deluxe Edition",
      "is_explicit": false,
      "main_artists": [{
        "name": "Dio",
        "domain": "4158699898177050137",
        "id": "4158699898177050137"
      }],
      "album_type": "main_only"
    }]
  }
  ```
</details>



## audio.searchArtists

Возвращает найденных исполнителей.

### Параметры

| Параметр | Тип    | Описание                               |
|----------|--------|----------------------------------------|
| **q**    | string | Строка поиска                          |
| count    | int    | Количество исполнителей. Максимум 1000 |
| offset   | int    | Смещение                               |

### Тип возвращаемого значения

```ts
interface AudioSearchArtists {
  count: number
  items: VKArtist[]
}

interface VKArtist {
  id: string
  name: string
  domain: string
  photo?: { width: number, height: number, url: string }[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "count": 103,
    "items": [{
      "name": "Boulevard Depo",
      "domain": "boulevarddepo",
      "id": "4351355679024274167",
      "photo": [
        { "height": 100, "url": "...", "width": 100 },
        { "height": 135, "url": "...", "width": 135 },
        { "height": 50, "url": "...", "width": 50 },
        { "height": 270, "url": "...", "width": 270 },
        { "height": 198, "url": "...", "width": 198 }
      ]
    }]
  }
  ```
</details>



## audio.searchMain

Возвращает все найденные объекты, связанные с разделом музыки.

### Параметры

| Параметр | Тип    | Описание      |
|----------|--------|---------------|
| **q**    | string | Строка поиска |

### Тип возвращаемого значения

```ts
interface VKList<T> {
  count: number
  items: T[]
}

interface AudioSearchMain {
  albums: VKList<VKAlbum>
  audios: VKList<VKAudio>
  artists: VKList<VKArtist>
  playlists: VKList<VKPlaylist>
  own_audios: VKList<VKAudio>
  own_playlists: VKList<VKPlaylist>
  own_albums: VKList<VKAlbum>
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "albums": {
      "count": 30,
      "items": [{
        "id": 2909952,
        "owner_id": -2000909952,
        "type": 1,
        "title": "Морг",
        "description": "",
        "count": 1,
        "followers": 631,
        "plays": 18341,
        "create_time": 1524674167,
        "update_time": 1545240988,
        "genres": [{
          "id": 10,
          "name": "Хип-хоп"
        }],
        "is_following": false,
        "year": 2018,
        "photo": {
          "width": 300,
          "height": 300,
          "photo_34": "https://sun7-6.userapi.com/c846417/v846417632/33961/Ffp6Rgejous.jpg",
          "photo_68": "https://sun7-9.userapi.com/c846417/v846417632/3395f/i-3N78E04pg.jpg",
          "photo_135": "https://sun7-8.userapi.com/c846417/v846417632/3395d/5UsLXbHdpOc.jpg",
          "photo_270": "https://sun7-7.userapi.com/c846417/v846417632/3395a/2UPQ5KPEckk.jpg",
          "photo_300": "https://sun7-7.userapi.com/c846417/v846417632/33958/ccUv93JGzcE.jpg",
          "photo_600": "https://sun7-6.userapi.com/c846417/v846417632/33957/l8kK8qOAJo8.jpg",
          "photo_1200": "https://sun7-8.userapi.com/c846417/v846417632/33956/Dy4ydlxN9qk.jpg"
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
        "is_explicit": true,
        "main_artists": [{
          "name": "Jubilee",
          "domain": "4372543522501467211",
          "id": "4372543522501467211"
        }],
        "album_type": "main_only"
      }]
    },
    "audios": {
      "count": 3601,
      "items": [{
        "artist": "Jubilee",
        "id": 456590904,
        "owner_id": 371745470,
        "title": "Морг",
        "duration": 159,
        "access_key": "...",
        "ads": {
          "content_id": "371745470_456590904",
          "duration": "159",
          "account_age_type": "3",
          "puid1": "554",
          "puid22": "14"
        },
        "is_explicit": true,
        "is_focus_track": false,
        "is_licensed": true,
        "track_code": "...",
        "url": "...",
        "date": 1524733409,
        "album": {
          "id": 2909952,
          "title": "Морг",
          "owner_id": -2000909952,
          "access_key": "...",
          "thumb": {
            "width": 300,
            "height": 300,
            "photo_34": "https://sun7-6.userapi.com/c846417/v846417632/33961/Ffp6Rgejous.jpg",
            "photo_68": "https://sun7-9.userapi.com/c846417/v846417632/3395f/i-3N78E04pg.jpg",
            "photo_135": "https://sun7-8.userapi.com/c846417/v846417632/3395d/5UsLXbHdpOc.jpg",
            "photo_270": "https://sun7-7.userapi.com/c846417/v846417632/3395a/2UPQ5KPEckk.jpg",
            "photo_300": "https://sun7-7.userapi.com/c846417/v846417632/33958/ccUv93JGzcE.jpg",
            "photo_600": "https://sun7-6.userapi.com/c846417/v846417632/33957/l8kK8qOAJo8.jpg",
            "photo_1200": "https://sun7-8.userapi.com/c846417/v846417632/33956/Dy4ydlxN9qk.jpg"
          }
        },
        "main_artists": [{
          "name": "Jubilee",
          "domain": "4372543522501467211",
          "id": "4372543522501467211"
        }],
        "short_videos_allowed": false,
        "stories_allowed": false
      }]
    },
    "artists": {
      "count": 500,
      "items": [{
        "name": "MORGENSHTERN",
        "domain": "morgenshtern",
        "id": "424386446084080541",
        "photo": [
          { "height": 100, "url": "...", "width": 100 },
          { "height": 135, "url": "...", "width": 135 },
          { "height": 50, "url": "...", "width": 50 },
          { "height": 270, "url": "...", "width": 270 },
          { "height": 198, "url": "...", "width": 198 }
        ]
      }]
    },
    "playlists": {
      "count": 1255,
      "items": [{
        "id": 1,
        "owner_id": -14017140,
        "type": 0,
        "title": "Коррозия Металла - Богиня морга (2018)",
        "description": "",
        "count": 13,
        "followers": 166,
        "plays": 7662,
        "create_time": 1531424918,
        "update_time": 1531424918,
        "genres": [],
        "is_following": false,
        "photo": {
          "width": 300,
          "height": 300,
          "photo_34": "https://sun9-55.userapi.com/c844320/v844320503/9fed3/VqKT7t5ithc.jpg",
          "photo_68": "https://sun9-48.userapi.com/c844320/v844320503/9fed1/6fhozlv1dwk.jpg",
          "photo_135": "https://sun9-14.userapi.com/c844320/v844320503/9fecf/DGmBOepVLB8.jpg",
          "photo_270": "https://sun9-46.userapi.com/c844320/v844320503/9fecc/xsGpxjHeWnc.jpg",
          "photo_300": "https://sun9-64.userapi.com/c844320/v844320503/9feca/8zJTTJl4zjo.jpg",
          "photo_600": "https://sun9-72.userapi.com/c844320/v844320503/9fec9/SlxsPKA4Wy8.jpg",
          "photo_1200": "https://sun9-12.userapi.com/c844320/v844320503/9fec8/dZIsX5Yl5sw.jpg"
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
        "album_type": "playlist"
      }]
    },
    "own_audios": {
      "count": 1,
      "items": [{
        "artist": "MORGENSHTERN, Витя АК",
        "id": 456239715,
        "owner_id": 88262293,
        "title": "РАТАТАТАТА",
        "duration": 118,
        "access_key": "...",
        "ads": {
          "content_id": "88262293_456239715",
          "duration": "118",
          "account_age_type": "3",
          "puid1": "554",
          "puid22": "14"
        },
        "is_explicit": true,
        "is_focus_track": false,
        "is_licensed": true,
        "track_code": "...",
        "url": "...",
        "date": 1585566342,
        "album": {
          "id": 6511315,
          "title": "ЛЕГЕНДАРНАЯ ПЫЛЬ",
          "owner_id": -2000511315,
          "access_key": "...",
          "thumb": {
            "width": 300,
            "height": 300,
            "photo_34": "https://sun7-9.userapi.com/c854028/v854028325/1cbcdc/5w-est2b8M8.jpg",
            "photo_68": "https://sun7-9.userapi.com/c854028/v854028325/1cbcda/T_RaoVNWr6I.jpg",
            "photo_135": "https://sun7-8.userapi.com/c854028/v854028325/1cbcd8/MSPm0wNc6Yk.jpg",
            "photo_270": "https://sun7-8.userapi.com/c854028/v854028325/1cbcd5/Z3s7GNvAW3w.jpg",
            "photo_300": "https://sun7-9.userapi.com/c854028/v854028325/1cbcd3/BLDcJamT8UM.jpg",
            "photo_600": "https://sun7-7.userapi.com/c854028/v854028325/1cbcd2/-Foooa6O0Is.jpg",
            "photo_1200": "https://sun7-8.userapi.com/c854028/v854028325/1cbcd1/vpsju_dkqcc.jpg"
          }
        },
        "main_artists": [
          {
            "name": "MORGENSHTERN",
            "domain": "424386446084080541",
            "id": "424386446084080541"
          },
          {
            "name": "Витя АК",
            "domain": "8901459601699630854",
            "id": "8901459601699630854"
          }
        ],
        "short_videos_allowed": false,
        "stories_allowed": false
      }]
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
  ```
</details>



## audio.searchPlaylists

Возвращает найденные плейлисты.
Отличается от альбомов тем, что плейлисты могут составляться и обычными пользователями (`owner_id` > 0).

### Параметры

| Параметр | Тип    | Описание                      |
|----------|--------|-------------------------------|
| **q**    | string | Строка поиска                 |
| filters  | string | `all`, `owned` или `followed` |
| count    | int    | Количество плейлистов         |
| offset   | int    | Смещение                      |

### Тип возвращаемого значения

```ts
interface AudioSearchPlaylists {
  count: number
  items: VKPlaylist[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "count": 28974,
    "items": [{
      "id": 74797456,
      "owner_id": -6836787,
      "type": 0,
      "title": "Architects - Holy Hell [2018]",
      "description": "",
      "count": 11,
      "followers": 3945,
      "plays": 213567,
      "create_time": 1541077103,
      "update_time": 1541743095,
      "genres": [],
      "is_following": false,
      "photo": {
        "width": 300,
        "height": 300,
        "photo_34": "https://sun7-6.userapi.com/c850232/v850232890/5c432/J5xxDAAoqG8.jpg",
        "photo_68": "https://sun7-9.userapi.com/c850232/v850232890/5c430/RiZxuw2vZC8.jpg",
        "photo_135": "https://sun7-6.userapi.com/c850232/v850232890/5c42e/KOyag5CK44c.jpg",
        "photo_270": "https://sun7-7.userapi.com/c850232/v850232890/5c42b/1vxnF1-MPj0.jpg",
        "photo_300": "https://sun7-9.userapi.com/c850232/v850232890/5c429/sQrDqOEedGM.jpg",
        "photo_600": "https://sun7-9.userapi.com/c850232/v850232890/5c428/4WfjtpqZ6kY.jpg",
        "photo_1200": "https://sun7-8.userapi.com/c850232/v850232890/5c427/Q8eOUBobWPg.jpg"
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
      "album_type": "playlist"
    }]
  }
  ```
</details>



## audio.setBroadcast

Включает или выключает трансляцию аудиозаписи в статус.

Если не передать параметр `audio`, то трансляция будет выключена.

Если не указать параметр `target_ids`, то по умолчанию будет использован ID владельца токена.

### Параметры

| Параметр   | Тип    | Описание                                                |
|------------|--------|---------------------------------------------------------|
| target_ids | string | ID профилей или сообществ, куда будет установлен статус |
| audio      | string | Аудиозапись в формате `{owner_id}_{audio_id}`           |

### Тип возвращаемого значения

Возвращает ID профилей или сообществ, где были применены изменения

```ts
type AudioSetBroadcast = number[];
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  [88262293]
  ```
</details>
