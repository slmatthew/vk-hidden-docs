# vkRun

VK Run — это шагомер от ВКонтакте, релиз которого, судя по всему, отложили из-за пандемии коронавируса

## Доступ

Для доступа к секции `vkRun` необходимо использовать токен от VK для Android.

## Список методов

* [vkRun.getLeaderboard](#vkrungetleaderboard) — получить топ по шагам
* [vkRun.getSteps](#vkrungetsteps) — получить количество шагов
* [vkRun.setSteps](#vkrunsetsteps) — установить количество пройденных шагов
* [vkRun.setTarget](#vkrunsettarget) — установить цель по шагам



## vkRun.getLeaderboard

Возвращает топ по шагам.

### Параметры

| Параметр   | Тип    | Описание                                     |
|------------|--------|----------------------------------------------|
| local_time | string | Текущая дата в формате `yyyy-mm-ddThh:mm:ss` |
| date       | string | Текущая дата в формате `yyyy-mm-dd`          |

### Тип возвращаемого значения

```ts
interface VkRunGetLeaderboard {
  daily: VkRunLeaderboard
  monthly: VkRunLeaderboard
}

interface VkRunLeaderboard {
  steps: number
  // Дистанция в метрах
  distance: number
  target_steps: number
  // Дистанция в километрах. Всегда дробное кроме 0
  km_count: number
  // Позиция в топе
  position: number
  leaderboard: {
    steps: number
    distance: number
    user: {
      id: number
      name: string
      photo_50: string
      photo_100: string
      photo_200: string
    }
  }[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "daily": {
      "steps": 0,
      "distance": 0,
      "target_steps": 8000,
      "km_count": 0,
      "position": 1,
      "leaderboard": [{
        "steps": 0,
        "distance": 0,
        "user": {
          "id": 305360617,
          "name": "Матвей Вишневский",
          "photo_50": "...",
          "photo_100": "...",
          "photo_200": "..."
        }
      }]
    },
    "monthly": {
      "steps": 0,
      "distance": 0,
      "km_count": 0,
      "position": 1,
      "leaderboard": [{
        "steps": 0,
        "distance": 0,
        "user": {
          "id": 305360617,
          "name": "Матвей Вишневский",
          "photo_50": "...",
          "photo_100": "...",
          "photo_200": "..."
        }
      }]
    }
  }
  ```
</details>



## vkRun.getSteps

Судя по названию, должен возвращать количество шагов, но в ответе всегда единица.

### Тип возвращаемого значения

```ts
type VkRunGetSteps = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
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

Устанавливает цель по шагам.

### Параметры

| Параметр  | Тип | Описание         |
|-----------|-----|------------------|
| **steps** | int | Количество шагов |

### Тип возвращаемого значения

```ts
interface VkRunSetTarget {
  steps: number
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "steps": 10000
  }
  ```
</details>