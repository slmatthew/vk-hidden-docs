# catalog.getSection
Получение содержимого секции.

## Параметры

| Параметр | Тип | Описание    |
|----------|-----|-------------|
| `section_id` | `string` | Идентификатор секции из [catalog.getAudio](getAudio.md) или [catalog.getVideo](getVideo.md) |
| `start_from` | `string` | Сдвиг выборки |

## Особенности
* `fields` не поддерживается, но падеж имени можно менять через `name_case`.
* При первом запросе всегда возвращается 100 аудиозаписей.
* При указании `start_from` возвращается каждый раз рандомное число элементов, `count` не работает.
* При наличии `start_from` в запросе многие поля не возвращаются - `profiles`, `groups` и `playlists`.

## Пример ответа
```json5
{
    "section": {
        "id": "PUldVA8FR0RzSVNaaaaaaaaaaaaaaaaW1J-Ul1ESA",
        "title": "Музыка",
        "blocks": [
            {
                "id": "PUlQVaaaaaaaaaaaaaaaaaJdREg",
                "data_type": "music_audios",
                "layout": {
                    "name": "list",
                    "owner_id": 23048942
                },
                "next_from": "PUlYaaaaaDwQW",
                "audios_ids": [
                    "23048942_415536025",
                    "23048942_414401713",
                    "23048942_411946390",
                    // ...
                ]
            }
        ],
        "next_from": "PUlYVAaUDwQW PUlQVA8GR0R3W0tMFaaaaaaaaaaaaVHRHRdS0wHB1tSflJdREg",
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
            "access_key": "2038ecb22483231cef",
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
            "track_code": "915c1395vwOa854tHQmu8Zq2c9VfpEEfeog8yUk8Wr3CccxvncCKQsvIwTo7EP3Vt5Zl6wi4YSRMuQKZeDZKtd9z5TSVxexGysfACCYXnMqmhVf0cq4ROF-zJPx7Nkq133blNJXF0WCTyJ02IxK6xqaFV-hcqBAdVqNivH0KY5v3dcgw2gVP5QCa8Q",
            "url": "https://psv4.vkuseraudio.net/c6183/u3869934/75805db2232/audios/73d3172e5ad4/index.m3u8?extra=woS8HnpgaxR3xlg_E5-Jremf1nhGl9_uLrGlK72QI4F2fXZe0UPQ2YgIZMvWfm6owUUnY4TbvKtxRY8kzqHYWElHKX7a_OOzCQUnvH2IcdlUjwFHSuIGR9GaArCcKHv_9_QW2wcJZ_SQfZXImj4tDw&long_chunk=1",
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
                    "photo_34": "https://sun9-3.userapi.com/c849524/v849524055/1364e3/zbAlF0ap-GQ.jpg",
                    "photo_68": "https://sun9-32.userapi.com/c849524/v849524055/1364e1/arJDYM2SAew.jpg",
                    "photo_135": "https://sun9-22.userapi.com/c849524/v849524055/1364df/IhFkFhphQ0I.jpg",
                    "photo_270": "https://sun9-51.userapi.com/c849524/v849524055/1364dc/5TIiltmss4w.jpg",
                    "photo_300": "https://sun9-7.userapi.com/c849524/v849524055/1364da/hjb2V3Jkk3E.jpg",
                    "photo_600": "https://sun9-43.userapi.com/c849524/v849524055/1364d9/8lerjcJJqaI.jpg",
                    "photo_1200": "https://sun9-36.userapi.com/c849524/v849524055/1364d8/Xe6T_tuh-_0.jpg"
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
            "photo_50": "https://sun9-4.userapi.com/c848532/v848532955/1925e1/5zjStkw1qmI.jpg?ava=1",
            "photo_100": "https://sun9-64.userapi.com/c848532/v848532955/1925e0/NFZUqS5lX38.jpg?ava=1",
            "friend_status": 3,
            "activity": "Страница не используется, оставлена в целях архива. Писать в Telegram: vladislav805",
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
                {
                    "group_id": 104924272,
                    "country_id": 1,
                    "city_id": 1,
                    "from": 2015,
                    "position": "Разработчик"
                },
                {
                    "group_id": 11283947,
                    "country_id": 1,
                    "city_id": 2,
                    "from": 2019,
                    "until": 2019,
                    "position": "Стажёр-разработчик интерфейсов"
                }
            ],
            "university": 60,
            "university_name": "ГУАП",
            "faculty": 259,
            "faculty_name": "Институт вычислительных систем и программирования (Институт №4)",
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
                    "photo_34": "https://sun9-6.userapi.com/c857736/v857736060/18d424/tWGsRerkuDs.jpg",
                    "photo_68": "https://sun9-18.userapi.com/c857736/v857736060/18d422/wMhvWEXTmf4.jpg",
                    "photo_135": "https://sun9-59.userapi.com/c857736/v857736060/18d420/TerEdNpwWvo.jpg",
                    "photo_270": "https://sun9-43.userapi.com/c857736/v857736060/18d41d/6r7gsRV9SyE.jpg",
                    "photo_300": "https://sun9-13.userapi.com/c857736/v857736060/18d41b/5qcWy84HizM.jpg",
                    "photo_600": "https://sun9-59.userapi.com/c857736/v857736060/18d41a/gK_zRGos26g.jpg",
                    "photo_1200": "https://sun9-38.userapi.com/c857736/v857736060/18d419/RPFqBPeIG54.jpg"
                },
                {
                    "width": 300,
                    "height": 300,
                    "photo_34": "https://sun9-17.userapi.com/c858028/v858028086/130195/o9gtz6WDaj8.jpg",
                    "photo_68": "https://sun9-52.userapi.com/c858028/v858028086/130193/3eJbsCMcGEw.jpg",
                    "photo_135": "https://sun9-71.userapi.com/c858028/v858028086/130191/fseNAR9G21o.jpg",
                    "photo_270": "https://sun9-58.userapi.com/c858028/v858028086/13018e/GIz6wLEoPKU.jpg",
                    "photo_300": "https://sun9-17.userapi.com/c858028/v858028086/13018c/eFEZ1bgL6Xo.jpg",
                    "photo_600": "https://sun9-15.userapi.com/c858028/v858028086/13018b/kVNLRehDADg.jpg",
                    "photo_1200": "https://sun9-62.userapi.com/c858028/v858028086/13018a/nKCnQ82zeqQ.jpg"
                },
                {
                    "width": 300,
                    "height": 300,
                    "photo_34": "https://sun9-21.userapi.com/c851428/v851428394/82cd8/eTb0t2ISBAU.jpg",
                    "photo_68": "https://sun9-48.userapi.com/c851428/v851428394/82cd6/XcwA0MZxaMc.jpg",
                    "photo_135": "https://sun9-66.userapi.com/c851428/v851428394/82cd4/65AJmr-ce50.jpg",
                    "photo_270": "https://sun9-58.userapi.com/c851428/v851428394/82cd1/RL4jmTGd18M.jpg",
                    "photo_300": "https://sun9-4.userapi.com/c851428/v851428394/82ccf/XxGfh8ArGfo.jpg",
                    "photo_600": "https://sun9-44.userapi.com/c851428/v851428394/82cce/MSrwHNwd1iY.jpg",
                    "photo_1200": "https://sun9-52.userapi.com/c851428/v851428394/82ccd/gkkMFYRgur8.jpg"
                }
            ],
            "access_key": "2e05feb0c01e73e994",
            "album_type": "playlist"
        },
    ]
}
```
