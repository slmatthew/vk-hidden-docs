# vkRun
VK Run — это шагомер от ВКонтакте, релиз которого, судя по всему, отложили из-за пандемии коронавируса.

## Список методов
* [vkRun.getLeaderboard](getLeaderboard.md)
* [vkRun.getSteps](getSteps.md)
* [vkRun.setSteps](setSteps.md)
* [vkRun.setTarget](setTarget.md)

## Доступ
Для доступа к этой секции нужен токен от VK для Android.

# vkRun.getLeaderboard
Получение топа по шагам.

## Параметры
Оба параметра не являются обязательными.

| Параметр   | Тип    | Описание                                     |
|------------|--------|----------------------------------------------|
| local_time | string | Текущая дата в формате `yyyy-mm-ddThh:mm:ss` |
| date       | string | Текущая дата в формате `yyyy-mm-dd`          |

## Возможный ответ
`km_count` может иметь тип `int`, если равен нулю.

```json
{
  "response": {
    "daily": {
      "steps": 2,
      "distance": 7,
      "target_steps": 8000,
      "km_count": 0.007,
      "position": 1,
      "leaderboard": [
        {
          "steps": 2,
          "distance": 7,
          "user": {
            "id": 305360617,
            "name": "Матвей Вишневский",
            "photo_50": "https://sun1-95.userapi.com/bswxPp5CLI_p2a-rZZd1xjiudXVekZ1ak4flaQ/tSDUGjqZaTU.jpg?ava=1",
            "photo_100": "https://sun1-18.userapi.com/277tRs6qmz_zng9pXKUWu18p0Dd2xZfze2G4bg/0OgGfXyvJ7A.jpg?ava=1",
            "photo_200": "https://sun1-94.userapi.com/GB6tjihUNfMctO9GJP4eydzbJB12iKT9VgdLqg/ijSF_DqqF1o.jpg?ava=1"
          }
        }
      ]
    },
    "monthly": {
      "steps": 2,
      "distance": 7,
      "km_count": 0.007,
      "position": 1,
      "leaderboard": [
        {
          "steps": 2,
          "distance": 7,
          "user": {
            "id": 305360617,
            "name": "Матвей Вишневский",
            "photo_50": "https://sun1-95.userapi.com/bswxPp5CLI_p2a-rZZd1xjiudXVekZ1ak4flaQ/tSDUGjqZaTU.jpg?ava=1",
            "photo_100": "https://sun1-18.userapi.com/277tRs6qmz_zng9pXKUWu18p0Dd2xZfze2G4bg/0OgGfXyvJ7A.jpg?ava=1",
            "photo_200": "https://sun1-94.userapi.com/GB6tjihUNfMctO9GJP4eydzbJB12iKT9VgdLqg/ijSF_DqqF1o.jpg?ava=1"
          }
        }
      ]
    }
  }
}
```

# vkRun.getSteps
Должен возвращать количество шагов, но не делает этого

## Пример ответа
```json
{
  "response": 1
}
```

# vkRun.setSteps
Шагомер

## Параметры
| Параметр | Тип    | Описание                        |
|----------|--------|---------------------------------|
| steps    | int    | Количество шагов                |
| distance | int    | Дистанция ходьбы (в метрах)     |
| date     | string | Дата в формате `год-месяц-день` |

## Пример ответа
```json
{
  "response": {
    "steps": 2,
    "distance": 7
  }
}
```

# vkRun.setTarget
Установить цель по шагам

## Параметры

| Параметр | Тип | Описание         |
|----------|-----|------------------|
| steps    | int | Количество шагов |

## Пример ответа
```json
{
  "response": {
    "steps": 8000
  }
}
```