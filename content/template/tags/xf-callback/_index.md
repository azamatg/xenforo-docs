+++
title = "Выполняет PHP-коллбек"
menutitle = "xf:callback"
linktitle = "xf:callback"
metatitle = "xf:callbackk"
short_desc = "Выполняет PHP-коллбек"
date = 2018-11-10T15:24:12+05:00
draft = "false"
layout = "single"
page_author = "official"
page_progress = "100"
show_progress = "true"
+++

{{% bq %}}Выполняет PHP-коллбек{{% /bq %}}

Пример использования:

```html
<xf:callback class="Vendor\Addon\Class" method="getX" params="['abc']"></xf:callback>
```

## Атрибуты

{{% table_class %}}
| Атрибут | Описание |
| --- | --- |
| `class` | Имя класса, содержащего метод коллбека (именование от корня) |
| `method` | Имя метода для выполнения (см. ниже список методов) |
| `params` | Массив параметров, передаваемых методу |
{{% /table_class %}}

## Методы в коллбеке

Для того, чтобы метод класса можно было вызвать в качестве коллбека, он должен быть именован по определенным правилам, иначе будет сгенерирована ошибка `callback_method_x_does_not_appear_to_indicate_read_only`. То есть класс должен быть "только для чтения", и его имя должно начинаться с одного из следующих префиксов:

- `are`
- `can`
- `count`
- `data`
- `display`
- `does`
- `exists`
- `fetch`
- `filter`
- `find`
- `get`
- `has`
- `is`
- `pluck`
- `print`
- `render`
- `return`
- `show`
- `total`
- `validate`
- `verify`
- `view`
