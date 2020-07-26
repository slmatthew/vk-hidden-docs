# catalog

Методы для работы с каталогами.

## Список методов

* [catalog.getAudio](#cataloggetaudio)
* [catalog.getVideo](#cataloggetvideo)
* [catalog.getSection](#cataloggetsection)

## Доступ
Для доступа к этой секции нужен токен от официальных приложений VK и User-Agent от официального приложения, например, `VKAndroidApp/5.56.1-4841`.

Например, при авторизации через iPhone без User-Agent списки возращаются, но без ссылок на аудио.

## catalog.getAudio

Получение каталогов аудиозаписей.

### Параметры

| Параметр | Тип | Описание    |
|----------|-----|-------------|
| `owner_id` | `int` | Идентификатор пользователя или сообщества |
| `need_blocks` | `boolean` | Возвращать ли информацию о каталогах сразу |

### Особенности
* `fields` не поддерживается, но падеж имени можно менять через `name_case`.
* С `need_blocks=1` всегда возвращается 100 аудиозаписей. Чтобы получить следующие, нужно вызывать [catalog.getSection](#cataloggetsection) с указанием `section_id`.
* В профилях всегда зачем то возаращается статус, информация о карьере и образовании.

### Тип возвращаемого значения
#### Без `need_blocks`
```ts
interface CatalogGetAudio {
  catalog: {
    default_section: string;
    sections: {
      id: string;
      title: string;
    }[];
  };
}
```

#### `need_blocks=1`
```ts
interface CatalogGetAudio {
  catalog: {
    default_section: string;
    sections: {
      id: string;
      title: string;
      blocks: {
        id: string;
        data_type: 'none' | 'music_playlists' | 'music_audios';
        layout: {
          name: 'header';
          title: string;
        } | {
          name: 'large_slider' | 'list';
          owner_id: number;
        };
        buttons?: {
          action: {
            type: 'open_section';
          }[];
          section_id: string;
          title: string;
          ref_items_count: number;
          ref_layout_name: 'large_slider' | 'list';
          ref_data_type: 'music_playlists' | 'music_audios';
        }[];
        player_ids?: string[]; // ${owner_id}_${playlist_id}
        audio_ids?: string[]; // ${owner_id}_${audio_id}
        next_from?: string;
      };
      next_from: string;
      buttons: {
          action: {
              type: 'owner_button';
          };
          owner_id: number;
          ref_items_count: number;
          ref_layout_name: 'list';
          ref_data_type: 'music_audios';
      }[]
    }[];
  };
  profiles?: VKUser[];
  groups?: VKGroup[];
  audios?: VKAudio[];
  playlists?: VKAudioPlaylist[];
}
```

### Пример ответа

<details>
  <summary>Открыть (без need_blocks)</summary>
  ```json5
  {
    "catalog": {
      "default_section": "...",
      "sections": [
        {
            "id": "...",
            "title": "Музыка"
          }
      ]
    }
  }
  ```
</details>

<details>
  <summary>Открыть (с need_blocks=1)</summary>
  ```json5
    {
      "catalog": {
          "default_section": "...",
          "sections": [
              {
                  "id": "...",
                  "title": "Музыка",
                  "blocks": [
                      {
                          "id": "...",
                          "data_type": "none",
                          "layout": {
                              "name": "header",
                              "title": "Плейлисты"
                          },
                          "buttons": [
                              {
                                  "action": {
                                      "type": "open_section"
                                  },
                                  "section_id": "...",
                                  "title": "Показать все",
                                  "ref_items_count": 14,
                                  "ref_layout_name": "large_slider",
                                  "ref_data_type": "music_playlists"
                              }
                          ]
                      },
                      {
                          "id": "...",
                          "data_type": "music_playlists",
                          "layout": {
                              "name": "large_slider",
                              "owner_id": 23048942
                          },
                          "playlists_ids": [
                              "23048942_55179332",
                              "23048942_54808613",
                              "23048942_54548648",
                              // ...
                          ]
                      },
                      {
                          "id": "...",
                          "data_type": "none",
                          "layout": {
                              "name": "button",
                              "owner_id": 23048942
                          },
                          "buttons": [
                              {
                                  "action": {
                                      "type": "play_audios_from_block"
                                  },
                                  "block_id": "...",
                                  "ref_items_count": 917,
                                  "ref_layout_name": "list",
                                  "ref_data_type": "music_audios"
                              },
                              {
                                  "action": {
                                      "type": "play_shuffled_audios_from_block"
                                  },
                                  "block_id": "...-Ul1ESA",
                                  "ref_items_count": 917,
                                  "ref_layout_name": "list",
                                  "ref_data_type": "music_audios"
                              }
                          ]
                      },
                      {
                          "id": "...",
                          "data_type": "music_audios",
                          "layout": {
                              "name": "list",
                              "owner_id": 23048942
                          },
                          "next_from": "...",
                          "audios_ids": [
                              "23048942_456239137",
                              "23048942_456239135",
                              "23048942_456239134",
                              // ...
                          ]
                      }
                  ],
                  "next_from": "...",
                  "buttons": [
                      {
                          "action": {
                              "type": "owner_button"
                          },
                          "owner_id": 23048942,
                          "ref_items_count": 917,
                          "ref_layout_name": "list",
                          "ref_data_type": "music_audios"
                      }
                  ]
              }
          ]
      },
      "profiles": [
          {
              "id": 23048942,
              "first_name": "Владислав",
              "last_name": "Велюга",
              "city": {
                  "id": 2,
                  "title": "Санкт-Петербург"
              },
              "country": {
                  "id": 1,
                  "title": "Россия"
              },
              "photo_50": "...",
              "photo_100": "...",
              "friend_status": 3,
              "activity": "...",
              "verified": 0,
              "career": [
                  {
                      "group_id": 51843784,
                      "country_id": 1,
                      "city_id": 2,
                      "from": 2012,
                      "until": 2015,
                      "position": "Разработчик"
                  },
                  // ...
              ],
              "university": 60,
              "university_name": "ГУАП",
              "faculty": 259,
              "faculty_name": "...",
              "graduation": 2019,
              "education_form": "Очное отделение",
              "education_status": "Студент (бакалавр)"
          }
      ],
      "audios": [
          {
              "artist": "Научно-технический рэп",
              "id": 456239134,
              "owner_id": 23048942,
              "title": "Коммутатор",
              "duration": 186,
              "url": "...",
              "date": 1500634522,
              "genre_id": 18,
              "short_videos_allowed": false,
              "stories_allowed": false
          },
          // ...
      ],
      "playlists": [
          {
              "id": 55179332,
              "owner_id": 23048942,
              "type": 0,
              "title": "Savage",
              "description": "",
              "count": 8,
              "followers": 0,
              "plays": 0,
              "create_time": 1491714970,
              "update_time": 1491714970,
              "genres": [],
              "is_following": false,
              "thumbs": [
                  {
                      "width": 300,
                      "height": 300,
                      "photo_34": "...",
                      "photo_68": "...",
                      "photo_135": "...",
                      "photo_270": "...",
                      "photo_300": "...",
                      "photo_600": "...",
                      "photo_1200": "..."
                  },
                  // ...
              ],
              "access_key": "..."
          },
          // ...
      ]
  }
  ```
</details>



## catalog.getSection

Получение содержимого секции.

### Параметры

| Параметр | Тип | Описание    |
|----------|-----|-------------|
| `section_id` | `string` | Идентификатор секции из [catalog.getAudio](#cataloggetaudio) или [catalog.getVideo](#cataloggetvideo) |
| `start_from` | `string` | Сдвиг выборки |

### Особенности

* `fields` не поддерживается, но падеж имени можно менять через `name_case`.
* При первом запросе всегда возвращается 100 аудиозаписей.
* При указании `start_from` возвращается каждый раз рандомное число элементов, `count` не работает.
* При наличии `start_from` в запросе многие поля не возвращаются - `profiles`, `groups` и `playlists`.

## Пример ответа

<details>
  <summary>Открыть</summary>
  ```json5
  {
      "section": {
          "id": "...",
          "title": "Музыка",
          "blocks": [
              {
                  "id": "...",
                  "data_type": "music_audios",
                  "layout": {
                      "name": "list",
                      "owner_id": 23048942
                  },
                  "next_from": "...",
                  "audios_ids": [
                      "23048942_415536025",
                      "23048942_414401713",
                      "23048942_411946390",
                      // ...
                  ]
              }
          ],
          "next_from": "...",
          "buttons": [
              // только без start_from
              {
                  "action": {
                      "type": "owner_button"
                  },
                  "owner_id": 23048942,
                  "ref_items_count": 917,
                  "ref_layout_name": "list",
                  "ref_data_type": "music_audios"
              }
          ]
      },
      "audios": [
          {
              "artist": "Avril Lavigne",
              "id": 415536025,
              "owner_id": 23048942,
              "title": "I Will Be",
              "duration": 240,
              "access_key": "...",
              "ads": {
                  "content_id": "23048942_415536025",
                  "duration": "240",
                  "account_age_type": "3",
                  "puid1": "554",
                  "puid22": "11"
              },
              "is_explicit": false,
              "is_focus_track": false,
              "is_licensed": true,
              "track_code": "...",
              "url": "...",
              "date": 1448209337,
              "genre_id": 21,
              "album": {
                  "id": 31617,
                  "title": "The Best Damn Thing (Expanded Edition)",
                  "owner_id": -2000031617,
                  "access_key": "4e21dd8eb2d35d19b6",
                  "thumb": {
                      "width": 300,
                      "height": 300,
                      "photo_34": "...",
                      "photo_68": "...",
                      "photo_135": "...",
                      "photo_270": "...",
                      "photo_300": "...",
                      "photo_600": "...",
                      "photo_1200": "..."
                  }
              },
              "short_videos_allowed": false,
              "stories_allowed": false
          },
          // ...
      ],
      // Только без start_from
      "profiles": [
          {
              "id": 23048942,
              "first_name": "Владислав",
              "last_name": "Велюга",
              "is_closed": true,
              "can_access_closed": true,
              "city": {
                  "id": 2,
                  "title": "Санкт-Петербург"
              },
              "country": {
                  "id": 1,
                  "title": "Россия"
              },
              "photo_50": "...",
              "photo_100": "...",
              "friend_status": 3,
              "activity": "...",
              "verified": 0,
              "trending": 0,
              "career": [
                  {
                      "group_id": 51843784,
                      "country_id": 1,
                      "city_id": 2,
                      "from": 2012,
                      "until": 2015,
                      "position": "Разработчик"
                  },
                  // ...
              ],
              "university": 60,
              "university_name": "ГУАП",
              "faculty": 259,
              "faculty_name": "...",
              "graduation": 2019,
              "education_form": "Очное отделение",
              "education_status": "Студент (бакалавр)"
          }
      ],

      // Только без start_from
      "playlists": [
          {
              "id": 55179332,
              "owner_id": 23048942,
              "type": 0,
              "title": "Savage",
              "description": "",
              "count": 8,
              "followers": 0,
              "plays": 0,
              "create_time": 1491714970,
              "update_time": 1491714970,
              "genres": [],
              "is_following": false,
              "thumbs": [
                  {
                      "width": 300,
                      "height": 300,
                      "photo_34": "...",
                      "photo_68": "...",
                      "photo_135": "...",
                      "photo_270": "...",
                      "photo_300": "...",
                      "photo_600": "...",
                      "photo_1200": "..."
                  },
                  // ...
              ],
              "access_key": "...",
              "album_type": "playlist"
          },
      ]
  }
  ```
</details>
