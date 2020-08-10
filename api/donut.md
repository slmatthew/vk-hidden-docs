# donut

Методы для работы с VK Donut

## Доступ

- Методы `donut.cancelSubscription`, `donut.getFriends` и `donut.getPaymentLink`
  работают только при использовании токена VK для Android;
- Метод `donut.getSubscriptions` возвращает поля `profiles`, `groups` и `count`
  только при использовании токена VK для Android;
- Остальные методы могут работать с любым токеном.

## Список методов

* [donut.cancelSubscription](#donutcancelsubscription) — отменить подписку на сообщество
* [donut.getFriends](#donutgetfriends) — получить список друзей-донов в сообществе
* [donut.getPaymentLink](#donutgetpaymentLink) — получить данные для оплаты подписки
* [donut.getSubscriptions](#donutgetsubscriptions) — получить список подписок
* [donut.isDon](#donutisdon) — проверить, является ли текущий пользователь доном сообщества
* [donut.revertUnsubscription](#donutrevertunsubscription) — возобновить подписку на сообщество



## donut.cancelSubscription

Отменяет подписку на сообщество.

### Параметры

| Параметр     | Тип | Описание                    |
|--------------|-----|-----------------------------|
| **owner_id** | int | Отрицательный ID сообщества |

### Тип возвращаемого значения

```ts
type DonutCancelSubscription = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>

### Связанные методы

* execute.cancelDonutSubscription — отменить подписку на сообщество
* [donut.getSubscriptions](#donutgetsubscriptions) — получить список подписок
* [donut.revertUnsubscription](#donutrevertunsubscription) — возобновить подписку на сообщество



## donut.getFriends

Возвращает список друзей-донов в сообществе.

### Параметры

| Параметр     | Тип    | Описание                          |
|--------------|--------|-----------------------------------|
| **owner_id** | int    | Отрицательный ID сообщества       |
| **count**    | int    | Количество друзей                 |
| offset       | int    | Смещение                          |
| fields       | string | Дополнительные поля пользователей |

### Тип возвращаемого значения

```ts
interface DonutGetFriends {
  count: number
  items: VKUser[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "count": 4,
    "items": [{
      "id": 180544766,
      "first_name": "Михаил",
      "last_name": "Милестон",
      "is_closed": false,
      "can_access_closed": true
    }]
  }
  ```
</details>



## donut.getPaymentLink

Возвращает данные для оплаты подписки на сообщество.

Чтобы оплатить подписку, нужно открыть ссылку из поля `payment_link` в ответе.

### Параметры

| Параметр     | Тип    | Описание                                        |
|--------------|--------|-------------------------------------------------|
| **owner_id** | int    | Отрицательный ID сообщества                     |
| **amount**   | int    | Сумма платежа                                   |
| **source**   | string | Любая строка. Используется для сбора статистики |

Если `amount` будет меньше, чем минимальная сумма платежа, то сервер вернет ошибку `10 Internal server error`.

### Тип возвращаемого значения

```ts
interface DonutGetPaymentLink {
  payment_link: string
  merchant_id: number
  merchant_data: string
  merchant_sign: string
  success_waiting_time: number
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "payment_link": "https://vk.com/vkpay#action=recurrent&merchant_id=681000&data=%7B%22merchant_data%22%3A%22somerandomstring%3D%3D%22%2C%22merchant_sign%22%3A%22somerandomstring%22%7D",
    "merchant_id": 681000,
    "merchant_data": "...",
    "merchant_sign": "...",
    "success_waiting_time": 40
  }
  ```
</details>



## donut.getSubscriptions

Возвращает список подписок текущего пользователя.

### Параметры

| Параметр  | Тип | Описание            |
|-----------|-----|---------------------|
| **count** | int | Количество подписок |
| offset    | int | Смещение            |

### Тип возвращаемого значения

```ts
interface DonutGetSubscriptions {
  subscriptions: {
    owner_id: number
    next_payment_date: number
    // active - активная подписка, expiring - отмененная
    status: 'active' | 'expiring'
    // Только если status = expiring
    payment_link?: string
    text: string
  }[]
  count: number
  profiles: VKUser[]
  groups: VKGroup[]
}
```

### Пример ответа

<details>
  <summary>Активная подписка</summary>

  ```json
  {
    "subscriptions": [{
      "owner_id": -12345,
      "next_payment_date": 1598628648,
      "status": "active",
      "text": "50 ₽ в месяц"
    }],
    "count": 1,
    "profiles": [],
    "groups": [{
      "id": 12345,
      "name": "хардбасия",
      "screen_name": "...",
      "is_closed": 2,
      "type": "group",
      "is_admin": 0,
      "is_member": 1,
      "is_advertiser": 0,
      "photo_50": "https://vk.com/images/community_50.png?ava=1",
      "photo_100": "https://vk.com/images/community_100.png?ava=1",
      "photo_200": "https://vk.com/images/community_200.png?ava=1"
    }]
  }
  ```
</details>

<details>
  <summary>Отмененная подписка</summary>

  ```json
  {
    "subscriptions": [{
      "owner_id": -12345,
      "next_payment_date": 1598628648,
      "status": "expiring",
      "payment_link": "https://vk.com/club12345?w=donut_payment-12345&source=subscriptions_list",
      "text": "50 ₽ в месяц"
    }],
    "count": 1,
    "profiles": [],
    "groups": [{
      "id": 12345,
      "name": "хардбасия",
      "screen_name": "...",
      "is_closed": 2,
      "type": "group",
      "is_admin": 0,
      "is_member": 1,
      "is_advertiser": 0,
      "photo_50": "https://vk.com/images/community_50.png?ava=1",
      "photo_100": "https://vk.com/images/community_100.png?ava=1",
      "photo_200": "https://vk.com/images/community_200.png?ava=1"
    }]
  }
  ```
</details>

### Связанные методы

* [donut.cancelSubscription](#donutcancelsubscription) — отменить подписку на сообщество
* [donut.revertUnsubscription](#donutrevertunsubscription) — возобновить подписку на сообщество



## donut.isDon

Проверяет, является ли текущий пользователь доном сообщества.

### Параметры

| Параметр     | Тип | Описание                    |
|--------------|-----|-----------------------------|
| **owner_id** | int | Отрицательный ID сообщества |

### Тип возвращаемого значения

```ts
type DonutIsDon = 0 | 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>


## donut.revertUnsubscription

Возобновляет подписку.

### Параметры

| Параметр     | Тип | Описание                    |
|--------------|-----|-----------------------------|
| **owner_id** | int | Отрицательный ID сообщества |

### Тип возвращаемого значения

```ts
type DonutRevertUnsubscription = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>

### Связанные методы

* [donut.cancelSubscription](#donutcancelsubscription) — отменить подписку на сообщество
* [donut.getSubscriptions](#donutgetsubscriptions) — получить список подписок
