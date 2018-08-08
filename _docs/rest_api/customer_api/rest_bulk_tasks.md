---
title: Задачи для множественных операций
permalink: rest_bulk_tasks.html
sidebar: evorestreference
product: REST API
---

В разделе приведены методы для получения информации о состоянии задач на массовый импорт данных в Облако Эвотор.

## Получить информацию о состоянии задач

    GET /bulks

### Параметры запроса

Имя  | Тип  | Описание
-----|------|--------------
`type`| `string` |  Фильтр сущностей, задачи по которым будут присутствовать в ответе. Возможно указать несколько значений через запятую. Возможные значения: `product`, `product-group`.
`cursor`| `string` | Идентификатор курсора для постраничного чтения данных.
`status`| `string` |  Фильтр задач по состоянию. В ответе будут присутствовать задачи, состояние которых соответствует значению фильтра. Возможно указать несколько значений через запятую. Если параметр не задан -- в ответе будут присутствовать задачи в любом состоянии.

Возможные значения фильтра `status`:

* `ACCEPTED`
* `DECLINED`
* `RUNNING`
* `COMPLETED`
* `FAILED`



### Ответ

```
200 Успешно
```

```json
[
  {
    "items": [
      {
        "id": "219837b5-cc12-401b-9b09-17b6f6e7c024",
        "type": "product",
        "status": "RUNNING",
        "modified_at": "2018-04-25T12:06:21.523+0000"
      }
    ],
    "paging": {
      "next_cursor": "string"
    }
  }
]
```

## Получить подробную информацию о состоянии определённой задачи

    GET /bulks/{bulk-id}

### Ответ

```
200 Успешно
```

```json
{
  "id": "219837b5-cc12-401b-9b09-17b6f6e7c024",
  "type": "product",
  "status": "RUNNING",
  "modified_at": "2018-04-25T12:06:21.523+0000",
  "details": [
    {}
  ]
}
```