# store

Методы для работы со стикерами

## Список методов

* [store.activateProduct](#storeactivateproduct) — Добавляет набор стикеров в список стикеров
* [store.addStickersToFavorite](#storeaddstickerstofavorite) — Добавляет стикеры в избранные
* [store.deactivateProduct](#storedeactivateproduct) — Удаляет набор стикеров из списка стикеров
* [store.getCatalog](#storegetcatalog) — Возвращает баннеры и названия разделов
* [store.getFavoriteStickers](#storegetfavoritestickers) — Возвращает избранные стикеры
* [store.getProducts](#storegetproducts) — Возвращает наборы стикеров по различным фильтрам
* [store.getPurchases](#storegetpurchases) —
* [store.getSpecialEvents](#storegetspecialevents) —
* [store.getStickers](#storegetstickers) — Возвращает массив стикеров по ID
* [store.getStickersKeywords](#storegetstickerskeywords) —
* [store.getStockItemByName](#storegetstockitembyname) —
* [store.getStockItemByProductId](#storegetstockitembyproductid) —
* [store.getStockItemByStickerId](#storegetstockitembystickerid) —
* [store.getStockItems](#storegetstockitems) —
* [store.getSubscription](#storegetsubscription) —
* [store.hasNewItems](#storehasnewitems) —
* [store.hasStickersUpdates](#storehasstickersupdates) —
* [store.markAsViewed](#storemarkasviewed) —
* [store.removeStickersFromFavorite](#storeremovestickersfromfavorite) —
* [store.reorderProducts](#storereorderproducts) —
* [store.updateSubscription](#storeupdatesubscription) —



## store.activateProduct

Возвращает набор стикеров в список стикеров.

Для удаления набора из списка нужно вызвать метод [store.deactivateProduct](#storedeactivateproduct).

### Параметры

| Параметр       | Тип    | Описание           |
|----------------|--------|--------------------|
| **type**       | string | `stickers`         |
| **product_id** | int    | ID набора стикеров |

### Тип возвращаемого значения

```ts
type StoreActivateProduct = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>



## store.addStickersToFavorite

Добавляет стикеры в избранные.

Для получения избранных стикеров воспользуйтесь методом [store.getFavoriteStickers](#storegetfavoritestickers).

### Параметры

| Параметр        | Тип    | Описание                  |
|-----------------|--------|---------------------------|
| **sticker_ids** | string | ID стикеров через запятую |

### Тип возвращаемого значения

```ts
type StoreAddStickersToFavorite = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>



## store.deactivateProduct

Удаляет набор стикеров из списка стикеров.

Для добавления набора обратно нужно вызвать метод [store.deactivateProduct](#storedeactivateproduct).

### Параметры

| Параметр       | Тип    | Описание           |
|----------------|--------|--------------------|
| **type**       | string | `stickers`         |
| **product_id** | int    | ID набора стикеров |

### Тип возвращаемого значения

```ts
type StoreDeactivateProduct = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>



## store.getCatalog

Возвращает баннеры и названия разделов.

### Параметры

| Параметр | Тип    | Описание   |
|----------|--------|------------|
| **type** | string | `stickers` |

### Тип возвращаемого значения

```ts
interface StoreGetCatalog {
  banners: Banner[]
  sections: { name: string, title: string }[]
}

interface Banner {
  type: 'stock_item'
  photo_480: string
  photo_640: string
  photo_960: string
  photo_1280: string
  stock_item: StockItem
}

interface StockItem {
  product: VKStickerPack
  description: string
  author: string
  can_purchase: 0 | 1
  can_gift: 0 | 1
  free: 0 | 1
  payment_type: 'balance'
  price: number
  price_str: string
  price_buy: number
  price_buy_str: string
  price_gift: number
  price_gift_str: string
  photo_35: string
  photo_70: string
  photo_140: string
  photo_296: string
  photo_592: string
  background: string
  demo_photos_560: string[]
  // Все поля old_price_* возвращаются только при наличии поля price_gift_discount
  old_price?: number
  old_price_str?: string
  old_price_buy?: number
  old_price_buy_str?: string
  old_price_gift?: number
  old_price_gift_str?: string
  price_gift_discount?: string
  version_hash: string
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "banners": [{
      "type": "stock_item",
      "stock_item": {
        "product": {
          "id": 533,
          "type": "stickers",
          "purchased": 0,
          "active": 0,
          "title": "Бисквит",
          "stickers": [{
            "sticker_id": 19558,
            "is_allowed": true,
            "images": [
              { "url": "https://vk.com/sticker/1-19558-64", "width": 64, "height": 64 },
              { "url": "https://vk.com/sticker/1-19558-128", "width": 128, "height": 128 },
              { "url": "https://vk.com/sticker/1-19558-256", "width": 256, "height": 256 },
              { "url": "https://vk.com/sticker/1-19558-352", "width": 352, "height": 352 }
            ],
            "images_with_background": [
              { "url": "https://vk.com/sticker/1-19558-64b", "width": 64, "height": 64 },
              { "url": "https://vk.com/sticker/1-19558-128b", "width": 128, "height": 128 },
              { "url": "https://vk.com/sticker/1-19558-256b", "width": 256, "height": 256 },
              { "url": "https://vk.com/sticker/1-19558-352b", "width": 352, "height": 352 }
            ]
          }],
          "icon": [
            { "url": "https://vk.com/sticker/1-19558-512", "width": 512, "height": 512 },
            { "url": "https://vk.com/sticker/1-19558-352", "width": 352, "height": 352 },
            { "url": "https://vk.com/sticker/1-19558-256", "width": 256, "height": 256 },
            { "url": "https://vk.com/sticker/1-19558-128", "width": 128, "height": 128 },
            { "url": "https://vk.com/sticker/1-19558-64", "width": 64, "height": 64 }
          ],
          "previews": [
            { "url": "https://vk.com/sticker/2-533-thumb-22-", "width": 22, "height": 22 },
            { "url": "https://vk.com/sticker/2-533-thumb-34-", "width": 34, "height": 34 },
            { "url": "https://vk.com/sticker/2-533-thumb-44-", "width": 44, "height": 44 },
            { "url": "https://vk.com/sticker/2-533-thumb-68-", "width": 68, "height": 68 },
            { "url": "https://vk.com/sticker/2-533-thumb-102-", "width": 102, "height": 102 }
          ],
          "url": "https://vk.com/stickers/biscuit"
        },
        "description": "Хвост торчком, большие ушки —\nБерегитесь, печенюшки!",
        "author": "Ирина Брэдкэт",
        "can_purchase": 1,
        "can_gift": 1,
        "free": 0,
        "payment_type": "balance",
        "price": 0,
        "price_str": "Бесплатно",
        "price_buy": 0,
        "price_buy_str": "Бесплатно",
        "price_gift": 5,
        "price_gift_str": "5 голосов",
        "photo_35": "https://vk.com/sticker/2-533-cover-35b-",
        "photo_70": "https://vk.com/sticker/2-533-cover-70b-",
        "photo_140": "https://vk.com/sticker/2-533-cover-140b-",
        "photo_296": "https://vk.com/sticker/2-533-preview-296-1",
        "photo_592": "https://vk.com/sticker/2-533-preview-592-1",
        "background": "https://vk.com/sticker/2-533-background--",
        "demo_photos_560": [
          "https://vk.com/sticker/2-533-demo-560-1",
          "https://vk.com/sticker/2-533-demo-560-2",
          "https://vk.com/sticker/2-533-demo-560-3"
        ],
        "old_price": 10,
        "old_price_str": "10 голосов",
        "old_price_buy": 10,
        "old_price_buy_str": "10 голосов",
        "old_price_gift": 10,
        "old_price_gift_str": "10 голосов",
        "price_gift_discount": "50%",
        "version_hash": "..."
      },
      "photo_480": "https://sun9-54.userapi.com/hfw0TFpGgHU68o2kMwc4F0lO-5aNYBaeVJM2aQ/ndnB4NFXOL8.png",
      "photo_960": "https://sun9-10.userapi.com/VofWBUh_F9l_mX9Uqg-1SgrBh2HKt1hKKbQxtw/SzH0B82D45E.png",
      "photo_640": "https://sun9-4.userapi.com/krZXPdmrkZgSJPfOPwQxTZFC6vpmyp3dVvftLg/qb6t0jYWpk8.png",
      "photo_1280": "https://sun9-45.userapi.com/AYg2r24EwwVmTa86AjWTxCVw6rw2w-5e3oOuMg/2Uk_cL3qp7M.png"
    }],
    "sections": [
      { "name": "summer", "title": "Лето" },
      { "name": "new", "title": "Новые" },
      { "name": "popular", "title": "Популярные" },
      { "name": "free", "title": "Бесплатные" }
    ]
  }
  ```
</details>



## store.getFavoriteStickers

Возвращает избранные стикеры.

Для добавления избранных стикеров воспользуйтесь методом [store.addStickersToFavorite](#storeaddstickerstofavorite).

### Параметры

Нет.

### Тип возвращаемого значения

```ts
interface StoreGetFavoriteStickers {
  count: number
  items: VKSticker[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "count": 1,
    "items": [{
      "sticker_id": 1,
      "is_allowed": true,
      "images": [
        { "url": "https://vk.com/sticker/1-1-64", "width": 64, "height": 64 },
        { "url": "https://vk.com/sticker/1-1-128", "width": 128, "height": 128 },
        { "url": "https://vk.com/sticker/1-1-256", "width": 256, "height": 256 },
        { "url": "https://vk.com/sticker/1-1-352", "width": 352, "height": 352 }
      ],
      "images_with_background": [
        { "url": "https://vk.com/sticker/1-1-64b", "width": 64, "height": 64 },
        { "url": "https://vk.com/sticker/1-1-128b", "width": 128, "height": 128 },
        { "url": "https://vk.com/sticker/1-1-256b", "width": 256, "height": 256 },
        { "url": "https://vk.com/sticker/1-1-352b", "width": 352, "height": 352 }
      ]
    }]
  }
  ```
</details>



## store.getProducts

Возвращает наборы стикеров по различным фильтрам.

### Параметры

| Параметр    | Тип    | Описание                                         |
|-------------|--------|--------------------------------------------------|
| **type**    | string | `stickers`                                       |
| **filters** | string | Список из `purchased`, `active` и `promoted`     |
| extended    | flag   | Включить в объект стикерпака дополнительные поля |

Поле `filters` должно включать как минимум одно из предложенных значений,
но может включать два или три значения сразу, перечисляя их через запятую.

Возможные значения поля `filters`:
  * `purchased` — все купленные стикеры
  * `active` — стикеры, отображаемые в списке используемых стикеров. Эти стикеры можно [менять местами](#storereorderproducts),
[удалять](#storedeactivateproduct) и [восстанавливать](#storeactivateproduct)
  * `promoted` — неизвестно

Если не указать поле `extended`, то вам придет сильно обрезанная версия описания стикерпака, которая
не содержит ни названия, ни иконки, ни самих стикеров.

### Тип возвращаемого значения

```ts
interface StoreGetProducts {
  count: number
  items: SimpleStikerPack[] | VKStikerPack[]
}

// Приходит, если не указать поле extended
interface SimpleStikerPack {
  id: number
  type: 'stickers'
  purchased: 0 | 1
  active: 0 | 1
  purchase_date?: number
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "count": 142,
    "items": [{
      "id": 561,
      "type": "stickers",
      "purchased": 1,
      "active": 1,
      "purchase_date": 1589896548
    }]
  }
  ```
</details>



## store.getPurchases



## store.getSpecialEvents



## store.getStickers

Возвращает массив стикеров по ID.

### Параметры

| Параметр        | Тип    | Описание                  |
|-----------------|--------|---------------------------|
| **sticker_ids** | string | ID стикеров через запятую |

### Тип возвращаемого значения

```ts
type StoreGetStickers = VKSticker[];
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  [{
    "sticker_id": 1,
    "is_allowed": true,
    "images": [
      { "url": "https://vk.com/sticker/1-1-64", "width": 64, "height": 64 },
      { "url": "https://vk.com/sticker/1-1-128", "width": 128, "height": 128 },
      { "url": "https://vk.com/sticker/1-1-256", "width": 256, "height": 256 },
      { "url": "https://vk.com/sticker/1-1-352", "width": 352, "height": 352 }
    ],
    "images_with_background": [
      { "url": "https://vk.com/sticker/1-1-64b", "width": 64, "height": 64 },
      { "url": "https://vk.com/sticker/1-1-128b", "width": 128, "height": 128 },
      { "url": "https://vk.com/sticker/1-1-256b", "width": 256, "height": 256 },
      { "url": "https://vk.com/sticker/1-1-352b", "width": 352, "height": 352 }
    ]
  }]
  ```
</details>



## store.getStickersKeywords



## store.getStockItemByName



## store.getStockItemByProductId



## store.getStockItemByStickerId



## store.getStockItems



## store.getSubscription



## store.hasNewItems



## store.hasStickersUpdates



## store.markAsViewed



## store.removeStickersFromFavorite



## store.reorderProducts



## store.updateSubscription
