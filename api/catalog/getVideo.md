# catalog.getVideo
Получение каталогов видеозаписей.

## Параметры

| Параметр | Тип | Описание    |
|----------|-----|-------------|
| `owner_id` | `int` | Идентификатор пользователя или сообщества |
| `need_blocks` | `boolean` | Возвращать ли информацию о каталогах сразу |

## Особенности
* `fields` не поддерживается, но падеж имени можно менять через `name_case`.
* С `need_blocks=1` всегда возвращается 100 видеозаписей. Чтобы получить следующие, нужно вызывать [catalog.getSection](getSection.md) с указанием `section_id`.
* В профилях всегда зачем то возаращается статус, город, страна, информация о карьере и образовании.

## Пример ответа


```json5
{
    "catalog": {
        "default_section": "PUldVA8AR0RzSVaaaaaaaLTAcHW1J-Ul1ESA",
        "sections": [
            {
                "id": "PUldVA8AR0RzSVNUaaaaaaaW1J-Ul1ESA",
                "title": "Видео",
                "blocks": [
                    {
                        "id": "PUlQVA8GR0R3aaaaaaaaaaaacHW1J-Ul1ESA",
                        "data_type": "action",
                        "layout": {
                            "name": "horizontal_buttons"
                        },
                        "buttons": [
                            {
                                "action": {
                                    "type": "follow"
                                },
                                "owner_id": 23048942,
                                "ref_layout_name": "horizontal_buttons",
                                "ref_data_type": "action"
                            }
                        ]
                    },
                    {
                        "id": "PUlQVA8GR0R3W0tMF1saaaaaaaaaaaKEikZS1oXAElcckdLRwAWUVc7",
                        "data_type": "none",
                        "layout": {
                            "name": "separator"
                        }
                    },
                    {
                        "id": "PUlQVA8GR0R3W0taaaaaaaaaaaaaQDhRkR0tCFw5fSmRaXFQPBRY",
                        "data_type": "none",
                        "layout": {
                            "name": "header",
                            "title": "Альбомы"
                        },
                        "buttons": [
                            {
                                "action": {
                                    "type": "open_section"
                                },
                                "section_id": "PUlQVA8GR0R3aaaaaaaa5SXURI",
                                "title": "Показать все",
                                "ref_items_count": 5,
                                "ref_layout_name": "double_stacked_slider",
                                "ref_data_type": "albums"
                            }
                        ]
                    },
                    {
                        "id": "PUlQVA8GR0R3W0tMF2tYaaaaaaaaaaaIXDl9KZFpcVA8FR0R0XUtMBwdbUn5SXURI",
                        "data_type": "albums",
                        "layout": {
                            "name": "double_stacked_slider",
                            "owner_id": 23048942
                        },
                        "albums_ids": [
                            "23048942_54480037",
                            "23048942_54480036",
                            "23048942_54480035",
                            "23048942_53448107",
                            "23048942_48249941"
                        ]
                    },
                    {
                        "id": "PUlQVA8GR0R3W0tMF1scaaaaaaaaaBtUGRZfRHxfRVQEAUlcdxY",
                        "data_type": "none",
                        "layout": {
                            "name": "separator"
                        }
                    },
                    {
                        "id": "PUlQVA8GR0aaaaaaaDhRkR0tCFw5fSmRaXFQPBRY",
                        "data_type": "none",
                        "layout": {
                            "name": "header",
                            "title": "Видео"
                        }
                    },
                    {
                        "id": "PUlQVA8GR0R3W0tMFaaaaaaaaaaflJdREg",
                        "data_type": "videos",
                        "layout": {
                            "name": "list",
                            "owner_id": 23048942
                        },
                        "next_from": "PUlYVA8GW0pkWEtMBUk",
                        "videos_ids": [
                            "23048942_456239067",
                            "3869934_456239118",
                            "-67429811_456242185",
                            // ...
                        ]
                    }
                ],
                "next_from": "PUlYVA8GaaaaaaaaaaaaaaUZEdLQhcOX0pkWlxUDwVHRHRdS0wHB1tSflJdREg",
                "buttons": []
            }
        ]
    },
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
        },
        // ...
    ],
    "groups": [
        {
            "id": 67429811,
            "name": "Волшебный мир Blu-ray | DVD и не только",
            "screen_name": "bdanddvd",
            "is_closed": 0,
            "type": "group",
            "is_admin": 0,
            "is_member": 0,
            "is_advertiser": 0,
            "members_count": 3455,
            "member_status": 0,
            "city": {
                "id": 1,
                "title": "Москва"
            },
            "country": {
                "id": 1,
                "title": "Россия"
            },
            "activity": "Открытая группа",
            "verified": 0,
            "trending": 0,
            "photo_50": "https://sun9-55.userapi.com/impg/c853628/v853628461/2348b2/ntYoH-T9jKw.jpg?size=50x0&quality=90&crop=10,633,690,690&sign=0c5b214a3b40f2874366eb244990e375&c_uniq_tag=ICDjega3C5LgiKLeMpLLafFCP07Nn1DaxBl1G6xCi1E&ava=1",
            "photo_100": "https://sun9-55.userapi.com/impg/c853628/v853628461/2348b2/ntYoH-T9jKw.jpg?size=100x0&quality=90&crop=10,633,690,690&sign=417877e9ae4cef2a54e2cc8407729e67&c_uniq_tag=duYKNd2Th2guJcL4yGRg6-C-FuCoIW2auUJkg5nwRd8&ava=1"
        }
    ],
    "videos": [
        {
            "can_comment": 1,
            "can_like": 1,
            "can_repost": 0,
            "can_subscribe": 1,
            "can_add_to_faves": 1,
            "can_add": 1,
            "comments": 1,
            "date": 1490813515,
            "description": "",
            "duration": 14,
            "image": [
                {
                    "height": 96,
                    "url": "https://sun9-13.userapi.com/c837426/v837426942/33f50/HX2ZwdbvEXw.jpg",
                    "width": 130,
                    "with_padding": 1
                },
                {
                    "height": 120,
                    "url": "https://sun9-64.userapi.com/c837426/v837426942/33f4f/tPyutLxXwk4.jpg",
                    "width": 160,
                    "with_padding": 1
                },
                {
                    "height": 240,
                    "url": "https://sun9-70.userapi.com/c837426/v837426942/33f4e/C001h6rlknw.jpg",
                    "width": 320,
                    "with_padding": 1
                },
                {
                    "height": 450,
                    "url": "https://sun9-55.userapi.com/c837426/v837426942/33f4d/xo8BsdyW2OM.jpg",
                    "width": 800,
                    "with_padding": 1
                }
            ],
            "first_frame": [
                {
                    "height": 180,
                    "url": "https://sun9-29.userapi.com/c836134/v836134942/2db72/THQ0IjTQN1Q.jpg",
                    "width": 320
                },
                {
                    "height": 90,
                    "url": "https://sun9-32.userapi.com/c836134/v836134942/2db73/CAGayU7heO0.jpg",
                    "width": 160
                },
                {
                    "height": 74,
                    "url": "https://sun9-23.userapi.com/c836134/v836134942/2db74/ZBZSTSVmdP8.jpg",
                    "width": 130
                },
                {
                    "height": 450,
                    "url": "https://sun9-39.userapi.com/c836134/v836134942/2db71/2Pg39kVGjqo.jpg",
                    "width": 800
                }
            ],
            "width": 1280,
            "height": 720,
            "id": 456239067,
            "owner_id": 23048942,
            "title": "Зверопой - Денег нет, но ты держись",
            "is_favorite": false,
            "player": "https://vk.com/video_ext.php?oid=23048942&id=456239067&hash=0fbd1018533c5d13&__ref=vk.android&api_hash=1595767904c0c673eb09d02b8765_GIYDGMZYGQ4TAOA",
            "added": 0,
            "track_code": "video_c356983fSt1L0Wul-Ch_ULDCG8lcqCgtSIw0YsiFj6Kihd7PMwlIz3niW5HAEQ",
            "type": "video",
            "views": 731,
            "likes": {
                "count": 10,
                "user_likes": 0
            }
        },
        // ...
    ],
    "albums": [
        {
            "count": 4,
            "owner_id": 23048942,
            "title": "Live Event 2014 (#LE14)",
            "updated_time": 1407960995,
            "id": 54480035,
            "image": [
                {
                    "height": 96,
                    "url": "https://sun9-62.userapi.com/c543303/u23048942/video/s_09a49def.jpg",
                    "width": 130,
                    "with_padding": 1
                },
                {
                    "height": 120,
                    "url": "https://sun9-5.userapi.com/c543303/u23048942/video/m_80958945.jpg",
                    "width": 160,
                    "with_padding": 1
                },
                {
                    "height": 240,
                    "url": "https://sun9-20.userapi.com/c543303/u23048942/video/l_398a7c65.jpg",
                    "width": 320,
                    "with_padding": 1
                }
            ]
        },
        // ...
    ]
}
```
