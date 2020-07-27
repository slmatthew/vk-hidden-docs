# store

Методы для работы со стикерами

## Список методов

* [store.activateProduct](#storeactivateproduct) — добавляет набор стикеров в список стикерпаков
* [store.addStickersToFavorite](#storeaddstickerstofavorite) — добавляет стикеры в избранные
* [store.deactivateProduct](#storedeactivateproduct) — удаляет набор стикеров из списка стикерпаков
* [store.getCatalog](#storegetcatalog) — возвращает баннеры и названия разделов
* [store.getFavoriteStickers](#storegetfavoritestickers) — возвращает избранные стикеры
* [store.getProducts](#storegetproducts) — возвращает купленные или активные стикерпаки
* [store.getStickers](#storegetstickers) — возвращает массив стикеров по ID
* [store.getStickersKeywords](#storegetstickerskeywords) — возвращает подсказки для стикеров
* [store.getStockItemByName](#storegetstockitembyname) — возвращает стикерпак по его названию
* [store.getStockItemByProductId](#storegetstockitembyproductid) — возвращает стикерпак по его ID
* [store.getStockItemByStickerId](#storegetstockitembystickerid) — возвращает стикерпак по ID стикера в нем
* [store.getStockItems](#storegetstockitems) — возвращает список всех стикерпаков, по ID или из указанного раздела
* [store.removeStickersFromFavorite](#storeremovestickersfromfavorite) — удаляет стикеры из избранных
* [store.reorderProducts](#storereorderproducts) — перемещает набор стикеров в списке стикерпаков на другое место



## store.activateProduct

Добавляет набор стикеров в список стикерпаков.

Для удаления набора из списка нужно вызвать метод [store.deactivateProduct](#storedeactivateproduct).

### Параметры

| Параметр       | Тип    | Описание      |
|----------------|--------|---------------|
| **type**       | string | `stickers`    |
| **product_id** | int    | ID стикерпака |

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

Для удаления избранных стикеров воспользуйтесь методом [store.removeStickersFromFavorite](#storeremovestickersfromfavorite).

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

Удаляет набор стикеров из списка стикерпаков.

Для добавления набора обратно нужно вызвать метод [store.activateProduct](#storeactivateproduct).

### Параметры

| Параметр       | Тип    | Описание      |
|----------------|--------|---------------|
| **type**       | string | `stickers`    |
| **product_id** | int    | ID стикерпака |

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

interface VKStickerPackBanner {
  type: 'stock_item'
  photo_480: string
  photo_640: string
  photo_960: string
  photo_1280: string
  stock_item: VKStickerPackStockItem
}

interface VKStickerPackStockItem {
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
  price_gift?: number
  price_gift_str?: string
  photo_35: string
  photo_70: string
  photo_140: string
  photo_296: string
  photo_592: string
  background: string
  demo_photos_560: string[]
  new?: 1
  badge?: {
    type: 'text'
    subtype: 'new'
    text: string
  }
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

Для удаления избранных стикеров воспользуйтесь методом [store.removeStickersFromFavorite](#storeremovestickersfromfavorite).

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

Возвращает купленные или активные стикерпаки.

### Параметры

| Параметр    | Тип    | Описание                                     |
|-------------|--------|----------------------------------------------|
| **type**    | string | `stickers`                                   |
| **filters** | string | Список из `purchased`, `active` и `promoted` |
| extended    | flag   | Возвращать картинки в объектах стикеров      |

Поле `filters` должно включать как минимум одно из предложенных значений,
но может включать два или три значения сразу, перечисляя их через запятую.

Возможные значения поля `filters`:
  * `purchased` — все купленные наборы стикеров
  * `active` — наборы стикеров, отображаемые в списке используемых стикерпаков.
    Эти стикерпаки можно [менять местами](#storereorderproducts),
    [удалять](#storedeactivateproduct) и [восстанавливать](#storeactivateproduct)
  * `promoted` — неизвестно

### Тип возвращаемого значения

```ts
interface StoreGetProducts {
  count: number
  items: SimpleStickerPack[] | VKStickerPack[]
}

// Приходит, если не указать поле extended
interface SimpleStickerPack {
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

Возвращает подсказки для стикеров.

### Параметры

| Параметр      | Тип  | Описание                                       |
|---------------|------|------------------------------------------------|
| aliases       | flag | Возвращать подсказки для сразу нескольких слов |
| need_stickers | flag | Возвращать картинки в объектах стикеров        |

По умолчанию оба параметра включены.

Если указать поле `aliases: 0`, то в ответе в поле `words` всегда будет приходить только одно поле.
Иначе будет приходить сразу несколько полей.

### Тип возвращаемого значения

```ts
interface StoreGetStickersKeywords {
  count: number
  // KeywordsWithoutStickers приходит при указании need_stickers: 0
  dictionary: KeywordsWithStickers[] | KeywordsWithoutStickers[]
}

interface KeywordsWithStickers {
  words: string[]
  // Стикеры, которые есть у пользователя
  user_stickers: VKSticker[]
  // Стикеры, которых нет у пользователя
  promoted_stickers?: VKSticker[]
}

interface KeywordsWithoutStickers {
  words: string[]
  stickers: { pack_id: number, sticker_id: number }[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "count": 3265,
    "dictionary": [{
      "words": [
        "👋",
        "bonjour",
        "ghbdtn",
        "hello",
        "алоха",
        "дароу",
        "дороу",
        "здарова",
        "здравствуй",
        "здравствуйте",
        "здрасте",
        "здрасьте",
        "ну здрасьте",
        "ну привет",
        "прив",
        "привет",
        "приветик",
        "приветики",
        "приветос",
        "приветостер",
        "приветствую",
        "приветули"
      ],
      "user_stickers": [{
        "sticker_id": 6025,
        "images": [
          { "height": 352, "url": "https://vk.com/sticker/1-6025-352", "width": 352 },
          { "height": 256, "url": "https://vk.com/sticker/1-6025-256", "width": 256 },
          { "height": 128, "url": "https://vk.com/sticker/1-6025-128", "width": 128 },
          { "height": 64, "url": "https://vk.com/sticker/1-6025-64", "width": 64 }
        ],
        "images_with_background": [
          { "height": 352, "url": "https://vk.com/sticker/1-6025-352b", "width": 352 },
          { "height": 256, "url": "https://vk.com/sticker/1-6025-256b", "width": 256 },
          { "height": 128, "url": "https://vk.com/sticker/1-6025-128b", "width": 128 },
          { "height": 64, "url": "https://vk.com/sticker/1-6025-64b", "width": 64 }
        ],
        "is_allowed": true
      }]
    }]
  }
  ```
</details>



## store.getStockItemByName

Возвращает стикерпак по его названию.

Название можно получить из ссылки на стикерпак: `https://vk.com/stickers/<name>`.
Подобную ссылку можно найти в объекте стикерпака.

### Параметры

| Параметр | Тип    | Описание            |
|----------|--------|---------------------|
| **type** | string | `stickers`          |
| **name** | string | Название стикерпака |

### Тип возвращаемого значения

```ts
type StoreGetStockItemByName = VKStickerPackStockItem;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "product": {
      "id": 600,
      "type": "stickers",
      "purchased": 0,
      "active": 0,
      "title": "Тоня",
      "stickers": [{
        "sticker_id": 21608,
        "is_allowed": true,
        "images": [
          { "url": "https://vk.com/sticker/1-21608-64", "width": 64, "height": 64 },
          { "url": "https://vk.com/sticker/1-21608-128", "width": 128, "height": 128 },
          { "url": "https://vk.com/sticker/1-21608-256", "width": 256, "height": 256 },
          { "url": "https://vk.com/sticker/1-21608-352", "width": 352, "height": 352 }
        ],
        "images_with_background": [
          { "url": "https://vk.com/sticker/1-21608-64b", "width": 64, "height": 64 },
          { "url": "https://vk.com/sticker/1-21608-128b", "width": 128, "height": 128 },
          { "url": "https://vk.com/sticker/1-21608-256b", "width": 256, "height": 256 },
          { "url": "https://vk.com/sticker/1-21608-352b", "width": 352, "height": 352 }
        ]
      }],
      "icon": [
        { "url": "https://vk.com/sticker/1-21608-512", "width": 512, "height": 512 },
        { "url": "https://vk.com/sticker/1-21608-352", "width": 352, "height": 352 },
        { "url": "https://vk.com/sticker/1-21608-256", "width": 256, "height": 256 },
        { "url": "https://vk.com/sticker/1-21608-128", "width": 128, "height": 128 },
        { "url": "https://vk.com/sticker/1-21608-64", "width": 64, "height": 64 }
      ],
      "previews": [
        { "url": "https://vk.com/sticker/2-600-thumb-22-", "width": 22, "height": 22 },
        { "url": "https://vk.com/sticker/2-600-thumb-34-", "width": 34, "height": 34 },
        { "url": "https://vk.com/sticker/2-600-thumb-44-", "width": 44, "height": 44 },
        { "url": "https://vk.com/sticker/2-600-thumb-68-", "width": 68, "height": 68 },
        { "url": "https://vk.com/sticker/2-600-thumb-102-", "width": 102, "height": 102 }
      ],
      "url": "https://vk.com/stickers/tonya"
    },
    "description": "Холодное тельце, горячее сердце!",
    "author": "Кристина Поплавская",
    "can_purchase": 1,
    "can_gift": 1,
    "free": 0,
    "payment_type": "balance",
    "price": 0,
    "price_str": "Бесплатно",
    "price_buy": 0,
    "price_buy_str": "Бесплатно",
    "price_gift": 10,
    "price_gift_str": "10 голосов",
    "photo_35": "https://vk.com/sticker/2-600-cover-35b-",
    "photo_70": "https://vk.com/sticker/2-600-cover-70b-",
    "photo_140": "https://vk.com/sticker/2-600-cover-140b-",
    "photo_296": "https://vk.com/sticker/2-600-preview-296-1",
    "photo_592": "https://vk.com/sticker/2-600-preview-592-1",
    "background": "https://vk.com/sticker/2-600-background--",
    "demo_photos_560": [
      "https://vk.com/sticker/2-600-demo-560-1",
      "https://vk.com/sticker/2-600-demo-560-2",
      "https://vk.com/sticker/2-600-demo-560-3",
      "https://vk.com/sticker/2-600-demo-560-4"
    ],
    "new": 1,
    "badge": {
      "type": "text",
      "subtype": "new",
      "text": "New"
    },
    "old_price": 10,
    "old_price_str": "10 голосов",
    "old_price_buy": 10,
    "old_price_buy_str": "10 голосов",
    "version_hash": "..."
  }
  ```
</details>



## store.getStockItemByProductId

Возвращает стикерпак по ID.

### Параметры

| Параметр       | Тип    | Описание      |
|----------------|--------|---------------|
| **type**       | string | `stickers`    |
| **product_id** | int    | ID стикерпака |

### Тип возвращаемого значения

```ts
type StoreGetStockItemByProductId = VKStickerPackStockItem;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "product": {
      "id": "1",
      "type": "stickers",
      "purchased": 1,
      "active": 1,
      "purchase_date": 1426970466,
      "title": "Спотти",
      "stickers": [{
        "sticker_id": 19633,
        "is_allowed": true,
        "images": [
          { "url": "https://vk.com/sticker/1-19633-64", "width": 64, "height": 64 },
          { "url": "https://vk.com/sticker/1-19633-128", "width": 128, "height": 128 },
          { "url": "https://vk.com/sticker/1-19633-256", "width": 256, "height": 256 },
          { "url": "https://vk.com/sticker/1-19633-352", "width": 352, "height": 352 }
        ],
        "images_with_background": [
          { "url": "https://vk.com/sticker/1-19633-64b", "width": 64, "height": 64 },
          { "url": "https://vk.com/sticker/1-19633-128b", "width": 128, "height": 128 },
          { "url": "https://vk.com/sticker/1-19633-256b", "width": 256, "height": 256 },
          { "url": "https://vk.com/sticker/1-19633-352b", "width": 352, "height": 352 }
        ]
      }],
      "icon": [
        { "url": "https://vk.com/sticker/1-19633-512", "width": 512, "height": 512 },
        { "url": "https://vk.com/sticker/1-19633-352", "width": 352, "height": 352 },
        { "url": "https://vk.com/sticker/1-19633-256", "width": 256, "height": 256 },
        { "url": "https://vk.com/sticker/1-19633-128", "width": 128, "height": 128 },
        { "url": "https://vk.com/sticker/1-19633-64", "width": 64, "height": 64 }
      ],
      "previews": [
        { "url": "https://vk.com/sticker/2-1-thumb-22-", "width": 22, "height": 22 },
        { "url": "https://vk.com/sticker/2-1-thumb-34-", "width": 34, "height": 34 },
        { "url": "https://vk.com/sticker/2-1-thumb-44-", "width": 44, "height": 44 },
        { "url": "https://vk.com/sticker/2-1-thumb-68-", "width": 68, "height": 68 },
        { "url": "https://vk.com/sticker/2-1-thumb-102-", "width": 102, "height": 102 }
      ],
      "url": "https://vk.com/stickers/spotty"
    },
    "description": "Чемпион по вилянию хвостом, верный друг и надёжная грелка.",
    "author": "Андрей Яковенко",
    "can_purchase": 1,
    "can_gift": 0,
    "free": 1,
    "payment_type": "balance",
    "price": 0,
    "price_str": "Бесплатно",
    "price_buy": 0,
    "price_buy_str": "Бесплатно",
    "photo_35": "https://vk.com/sticker/2-1-cover-35b-",
    "photo_70": "https://vk.com/sticker/2-1-cover-70b-",
    "photo_140": "https://vk.com/sticker/2-1-cover-140b-",
    "photo_296": "https://vk.com/sticker/2-1-preview-296-1",
    "photo_592": "https://vk.com/sticker/2-1-preview-592-1",
    "background": "https://vk.com/sticker/2-1-background--",
    "demo_photos_560": [
      "https://vk.com/sticker/2-1-demo-560-1",
      "https://vk.com/sticker/2-1-demo-560-2",
      "https://vk.com/sticker/2-1-demo-560-3",
      "https://vk.com/sticker/2-1-demo-560-4",
      "https://vk.com/sticker/2-1-demo-560-5",
      "https://vk.com/sticker/2-1-demo-560-6"
    ],
    "version_hash": "..."
  }
  ```
</details>



## store.getStockItemByStickerId

Возвращает стикерпак по ID стикера в нем.

### Параметры

| Параметр       | Тип | Описание   |
|----------------|-----|------------|
| **sticker_id** | int | ID стикера |

### Тип возвращаемого значения

```ts
type StoreGetStockItemByStickerId = VKStickerPackStockItem;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "product": {
      "id": "1",
      "type": "stickers",
      "purchased": 1,
      "active": 1,
      "purchase_date": 1426970466,
      "title": "Спотти",
      "stickers": [{
        "sticker_id": 19633,
        "is_allowed": true,
        "images": [
          { "url": "https://vk.com/sticker/1-19633-64", "width": 64, "height": 64 },
          { "url": "https://vk.com/sticker/1-19633-128", "width": 128, "height": 128 },
          { "url": "https://vk.com/sticker/1-19633-256", "width": 256, "height": 256 },
          { "url": "https://vk.com/sticker/1-19633-352", "width": 352, "height": 352 }
        ],
        "images_with_background": [
          { "url": "https://vk.com/sticker/1-19633-64b", "width": 64, "height": 64 },
          { "url": "https://vk.com/sticker/1-19633-128b", "width": 128, "height": 128 },
          { "url": "https://vk.com/sticker/1-19633-256b", "width": 256, "height": 256 },
          { "url": "https://vk.com/sticker/1-19633-352b", "width": 352, "height": 352 }
        ]
      }],
      "icon": [
        { "url": "https://vk.com/sticker/1-19633-512", "width": 512, "height": 512 },
        { "url": "https://vk.com/sticker/1-19633-352", "width": 352, "height": 352 },
        { "url": "https://vk.com/sticker/1-19633-256", "width": 256, "height": 256 },
        { "url": "https://vk.com/sticker/1-19633-128", "width": 128, "height": 128 },
        { "url": "https://vk.com/sticker/1-19633-64", "width": 64, "height": 64 }
      ],
      "previews": [
        { "url": "https://vk.com/sticker/2-1-thumb-22-", "width": 22, "height": 22 },
        { "url": "https://vk.com/sticker/2-1-thumb-34-", "width": 34, "height": 34 },
        { "url": "https://vk.com/sticker/2-1-thumb-44-", "width": 44, "height": 44 },
        { "url": "https://vk.com/sticker/2-1-thumb-68-", "width": 68, "height": 68 },
        { "url": "https://vk.com/sticker/2-1-thumb-102-", "width": 102, "height": 102 }
      ],
      "url": "https://vk.com/stickers/spotty"
    },
    "description": "Чемпион по вилянию хвостом, верный друг и надёжная грелка.",
    "author": "Андрей Яковенко",
    "can_purchase": 1,
    "can_gift": 0,
    "free": 1,
    "payment_type": "balance",
    "price": 0,
    "price_str": "Бесплатно",
    "price_buy": 0,
    "price_buy_str": "Бесплатно",
    "photo_35": "https://vk.com/sticker/2-1-cover-35b-",
    "photo_70": "https://vk.com/sticker/2-1-cover-70b-",
    "photo_140": "https://vk.com/sticker/2-1-cover-140b-",
    "photo_296": "https://vk.com/sticker/2-1-preview-296-1",
    "photo_592": "https://vk.com/sticker/2-1-preview-592-1",
    "background": "https://vk.com/sticker/2-1-background--",
    "demo_photos_560": [
      "https://vk.com/sticker/2-1-demo-560-1",
      "https://vk.com/sticker/2-1-demo-560-2",
      "https://vk.com/sticker/2-1-demo-560-3",
      "https://vk.com/sticker/2-1-demo-560-4",
      "https://vk.com/sticker/2-1-demo-560-5",
      "https://vk.com/sticker/2-1-demo-560-6"
    ],
    "version_hash": "..."
  }
  ```
</details>



## store.getStockItems

Возвращает:
 - Список всех стикерпаков
 - Список стикерпаков по ID
 - Список стикерпаков из указанного раздела

### Параметры

| Параметр    | Тип    | Описание                                |
|-------------|--------|-----------------------------------------|
| **type**    | string | `stickers`                              |
| product_ids | string | ID стикерпаков через запятую            |
| section     | string | Название раздела со стикерпаками        |
| need_images | flag   | Возвращать картинки в объектах стикеров |

Если не указывать необязательные параметры, то придет список всех доступных стикерпаков.
Если не передать поле `need_images: 0`, то список будет приходить очень долго, потому что данных там очень много.

Если указать поле `product_ids`, то придет указанный список стикерпаков.

Если указать поле `section`, то придет список стикерпаков из указанного раздела.
Список всех разделов можно получить из метода [store.getCatalog](#storegetcatalog).

Поле `need_images` по умолчанию имеет значение `1`.

### Тип возвращаемого значения

```ts
interface StoreGetStockItems {
  count: number
  items: VKStickerPackStockItem[]
}
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  {
    "count": 1,
    "items": [{
      "product": {
        "id": "1",
        "type": "stickers",
        "purchased": 1,
        "active": 1,
        "purchase_date": 1426970466,
        "title": "Спотти",
        "stickers": [{
          "sticker_id": 19633,
          "is_allowed": true,
          "images": [
            { "url": "https://vk.com/sticker/1-19633-64", "width": 64, "height": 64 },
            { "url": "https://vk.com/sticker/1-19633-128", "width": 128, "height": 128 },
            { "url": "https://vk.com/sticker/1-19633-256", "width": 256, "height": 256 },
            { "url": "https://vk.com/sticker/1-19633-352", "width": 352, "height": 352 }
          ],
          "images_with_background": [
            { "url": "https://vk.com/sticker/1-19633-64b", "width": 64, "height": 64 },
            { "url": "https://vk.com/sticker/1-19633-128b", "width": 128, "height": 128 },
            { "url": "https://vk.com/sticker/1-19633-256b", "width": 256, "height": 256 },
            { "url": "https://vk.com/sticker/1-19633-352b", "width": 352, "height": 352 }
          ]
        }],
        "icon": [
          { "url": "https://vk.com/sticker/1-19633-512", "width": 512, "height": 512 },
          { "url": "https://vk.com/sticker/1-19633-352", "width": 352, "height": 352 },
          { "url": "https://vk.com/sticker/1-19633-256", "width": 256, "height": 256 },
          { "url": "https://vk.com/sticker/1-19633-128", "width": 128, "height": 128 },
          { "url": "https://vk.com/sticker/1-19633-64", "width": 64, "height": 64 }
        ],
        "previews": [
          { "url": "https://vk.com/sticker/2-1-thumb-22-", "width": 22, "height": 22 },
          { "url": "https://vk.com/sticker/2-1-thumb-34-", "width": 34, "height": 34 },
          { "url": "https://vk.com/sticker/2-1-thumb-44-", "width": 44, "height": 44 },
          { "url": "https://vk.com/sticker/2-1-thumb-68-", "width": 68, "height": 68 },
          { "url": "https://vk.com/sticker/2-1-thumb-102-", "width": 102, "height": 102 }
        ],
        "url": "https://vk.com/stickers/spotty"
      },
      "description": "Чемпион по вилянию хвостом, верный друг и надёжная грелка.",
      "author": "Андрей Яковенко",
      "can_purchase": 1,
      "can_gift": 0,
      "free": 1,
      "payment_type": "balance",
      "price": 0,
      "price_str": "Бесплатно",
      "price_buy": 0,
      "price_buy_str": "Бесплатно",
      "photo_35": "https://vk.com/sticker/2-1-cover-35b-",
      "photo_70": "https://vk.com/sticker/2-1-cover-70b-",
      "photo_140": "https://vk.com/sticker/2-1-cover-140b-",
      "photo_296": "https://vk.com/sticker/2-1-preview-296-1",
      "photo_592": "https://vk.com/sticker/2-1-preview-592-1",
      "background": "https://vk.com/sticker/2-1-background--",
      "demo_photos_560": [
        "https://vk.com/sticker/2-1-demo-560-1",
        "https://vk.com/sticker/2-1-demo-560-2",
        "https://vk.com/sticker/2-1-demo-560-3",
        "https://vk.com/sticker/2-1-demo-560-4",
        "https://vk.com/sticker/2-1-demo-560-5",
        "https://vk.com/sticker/2-1-demo-560-6"
      ],
      "version_hash": "..."
    }]
  }
  ```
</details>



## store.removeStickersFromFavorite

Удаляет стикеры из избранных.

**Внимание**: Если один из переданных стикеров не находится в избранных, то будет выдана 2102 ошибка API.

Для добавления избранных стикеров воспользуйтесь методом [store.addStickersToFavorite](#storeaddstickerstofavorite).

Для получения избранных стикеров воспользуйтесь методом [store.getFavoriteStickers](#storegetfavoritestickers).

### Параметры

| Параметр        | Тип    | Описание    |
|-----------------|--------|-------------|
| **sticker_ids** | string | ID стикеров |

### Тип возвращаемого значения

```ts
type StoreRemoveStickersFromFavorite = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>



## store.reorderProducts

Перемещает стикерпак в списке стикерпаков на другое место.

### Параметры

| Параметр       | Тип    | Описание                                                     |
|----------------|--------|--------------------------------------------------------------|
| **type**       | string | `stickers`                                                   |
| **product_id** | int    | ID стикерпака                                                |
| before         | int    | ID стикерпака, перед которым будет установлен наш стикерпак  |
| after          | int    | ID стикерпака, после которого будет установлен наш стикерпак |

Необходимо обязательно указать либо параметр `before`, либо параметр `after`.

### Тип возвращаемого значения

```ts
type StoreReorderProducts = 1;
```

### Пример ответа

<details>
  <summary>Открыть</summary>

  ```json
  1
  ```
</details>
