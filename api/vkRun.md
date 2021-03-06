# vkRun

Шаги ВКонтакте (изначально VK Run) — трекер активности с рейтингом, связанных с платформой «Здоровье ВКонтакте».

## Доступ

Для доступа к секции `vkRun` необходимо использовать токен от VK для Android.

## Список методов

* [vkRun.getLeaderboard](#vkrungetleaderboard) — получить топ по шагам
* [vkRun.setSteps](#vkrunsetsteps) — установить количество пройденных шагов
* [vkRun.setTarget](#vkrunsettarget) — установить цель по шагам



## vkRun.getLeaderboard

Возвращает топ-25 друзей по шагам.

### Параметры

| Параметр   | Тип    | Описание                                     |
|------------|--------|----------------------------------------------|
| **date**   | string | Текущая дата в формате `yyyy-mm-dd`          |
| **type**   | string | `day`, `week` или `month`                    |
| local_time | string | Текущая дата в формате `yyyy-mm-ddThh:mm:ss` |

### Тип возвращаемого значения

```ts
interface VkRunGetLeaderboard {
  position: number
  // 25 пользователей
  leaderboard: VkRunUser[]
}

interface VkRunUser {
  steps: number
  // Дистанция в метрах
  distance: number
  user: {
    id: number
    // Полное имя
    name: string
    first_name: string
    last_name: string
    photo_50: string
    photo_100: string
    photo_200: string
    // Интересный факт: всегда 0
    sex: number
  }
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "position": 19,
    "leaderboard": [
      {
        "steps": 0,
        "distance": 0,
        "user": {
          "id": 305360617,
          "name": "Матвей Вишневский",
          "first_name": "Матвей",
          "last_name": "Вишневский",
          "photo_50": "...",
          "photo_100": "...",
          "photo_200": "...",
          "sex": 0
        }
      }
    ]
  }
  ```
</details>



## vkRun.setSteps

Устанавливает количество пройденных шагов.

### Параметры

| Параметр     | Тип    | Описание                           |
|--------------|--------|------------------------------------|
| **steps**    | int    | Количество шагов                   |
| **distance** | int    | Дистанция ходьбы                   |
| **date**     | string | Дата, в которую были пройдены шаги |

Дистанция ходьбы (`distance`) указывается в метрах.

Дата (`date`) должна быть в формате `год-месяц-день`.

### Тип возвращаемого значения

```ts
interface VkRunSetSteps {
  steps: number
  distance: number
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "steps": 8000,
    "distance": 8000
  }
  ```
</details>



## vkRun.setTarget

Устанавливает цель по шагам на определенную дату.

### Параметры

| Параметр  | Тип    | Описание         |
|-----------|--------|------------------|
| **steps** | int    | Количество шагов |
| **date**  | string | Дата             |

Дата (`date`) должна быть в формате `год-месяц-день`.

### Тип возвращаемого значения

```ts
interface VkRunSetTarget {
  steps: number
  // Если вы достигли указанного количества шагов на момент date, то будет равно 1
  strike: 1 | 0
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "steps": 8000,
    "strike": 1
  }
  ```
</details>
