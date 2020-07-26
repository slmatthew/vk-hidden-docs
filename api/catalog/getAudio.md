# catalog.getAudio
Получение каталогов аудиозаписей.

## Параметры

| Параметр | Тип | Описание    |
|----------|-----|-------------|
| `owner_id` | `int` | Идентификатор пользователя или сообщества |
| `need_blocks` | `boolean` | Возвращать ли информацию о каталогах сразу |

## Особенности
* `fields` не поддерживается, но падеж имени можно менять через `name_case`.
* С `need_blocks=1` всегда возвращается 100 аудиозаписей. Чтобы получить следующие, нужно вызывать [catalog.getSection](getSection.md) с указанием `section_id`.
* В профилях всегда зачем то возаращается статус, информация о карьере и образовании.

## Пример ответа
### Без `need_blocks`
```json5
{
    "catalog": {
        "default_section": "PUldVA8FR0RzSaaaaaUl1ESA",
        "sections": [
            {
                "id": "PUldVA8FR0RzSVaaaacHW1J-Ul1ESA",
                "title": "Музыка"
            }
        ]
    }
}
```

### `need_blocks=1`
```json5
{
    "catalog": {
        "default_section": "PUldVA8FR0RzSaaaaaaaaAcHW1J-Ul1ESA",
        "sections": [
            {
                "id": "PUldVA8FRaaaaaZFaa1J-Ul1ESA",
                "title": "Музыка",
                "blocks": [
                    {
                        "id": "PUlQVA8GR0R3W0tMaaaaaaJXHdHS0cAFlFXOw",
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
                                "section_id": "PUlQVA8GR0R3W0tMFaaaaaaatdTgwAWRs",
                                "title": "Показать все",
                                "ref_items_count": 14,
                                "ref_layout_name": "large_slider",
                                "ref_data_type": "music_playlists"
                            }
                        ]
                    },
                    {
                        "id": "PUlQVA8GR0R3W0aaaaaaTgwAWRs",
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
                        "id": "PUlQVA8GR0R3aaaaaaaaXOw",
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
                                "block_id": "PUlQVA8GR0R3W0tMF0aaaaaaHJJU0cZFlpTZFFYCw",
                                "ref_items_count": 917,
                                "ref_layout_name": "list",
                                "ref_data_type": "music_audios"
                            },
                            {
                                "action": {
                                    "type": "play_shuffled_audios_from_block"
                                },
                                "block_id": "PUlQVA8GR0R3aaaaaa1J-Ul1ESA",
                                "ref_items_count": 917,
                                "ref_layout_name": "list",
                                "ref_data_type": "music_audios"
                            }
                        ]
                    },
                    {
                        "id": "PUlQVA8GR0R3aaaaaaaaSflJdREg",
                        "data_type": "music_audios",
                        "layout": {
                            "name": "list",
                            "owner_id": 23048942
                        },
                        "next_from": "PUlYVA8FW1ZqSVpUDwQW",
                        "audios_ids": [
                            "23048942_456239137",
                            "23048942_456239135",
                            "23048942_456239134",
                            // ...
                        ]
                    }
                ],
                "next_from": "PUlYVA8FW1ZqSVpUDwQW PUlQVA8GRaaaaaaaaaaRaaaaaaaaHRdS0wHB1tSflJdREg",
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
            "photo_50": "https://sun9-4.userapi.com/c848532/v848532955/1925e1/5zjStkw1qmI.jpg?ava=1",
            "photo_100": "https://sun9-64.userapi.com/c848532/v848532955/1925e0/NFZUqS5lX38.jpg?ava=1",
            "friend_status": 3,
            "activity": "Страница не используется, оставлена в целях архива. Писать в Telegram: vladislav805",
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
    "audios": [
        {
            "artist": "Научно-технический рэп",
            "id": 456239134,
            "owner_id": 23048942,
            "title": "Коммутатор",
            "duration": 186,
            "url": "https://cs9-15v4.vkuseraudio.net/p5/5c8b9d18d42960.mp3?extra=YO4h58p5HiETeaD3soq80qlMdwx3RtFoR8ZPsoZC4pcAFk13QI54iHoRdv_nDblWzWqtY5tLaiLv3GrUmjceuMo4DTVmz-g9l61AOl7StoagsheXrSSRPPNetXQHoMtUODZ5rq5qxZfsjMGVtLymFA&long_chunk=1",
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
                    "photo_34": "https://sun9-6.userapi.com/c857736/v857736060/18d424/tWGsRerkuDs.jpg",
                    "photo_68": "https://sun9-18.userapi.com/c857736/v857736060/18d422/wMhvWEXTmf4.jpg",
                    "photo_135": "https://sun9-59.userapi.com/c857736/v857736060/18d420/TerEdNpwWvo.jpg",
                    "photo_270": "https://sun9-43.userapi.com/c857736/v857736060/18d41d/6r7gsRV9SyE.jpg",
                    "photo_300": "https://sun9-13.userapi.com/c857736/v857736060/18d41b/5qcWy84HizM.jpg",
                    "photo_600": "https://sun9-59.userapi.com/c857736/v857736060/18d41a/gK_zRGos26g.jpg",
                    "photo_1200": "https://sun9-38.userapi.com/c857736/v857736060/18d419/RPFqBPeIG54.jpg"
                },
                // ...
            ],
            "access_key": "2e05feb0c01e73e994"
        },
        // ...
    ]
}
```
