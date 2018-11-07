+++
title = "Макросы в шаблонах (тег xf:macro)"
menutitle = "xf:macro"
short_desc = "Макросы в шаблонах"
draft = false
layout = "single"
page_author = "me"
page_progress = "10"
show_progress = "true"
+++

{{% bq %}}Как работать с тегом xf:macro - примеры из стилей XenForo 2 и от участников сообщества.{{% /bq %}}

## Примеры из стандартного стиля XenForo 2

### Шаблон post

В шаблоне `post` используется макрос `post` с шаблоном `post_macros`, при этом в макрос и его шаблон с помощью аргументов передаются переменные `$post` (текущий пост) и `$thread` (текущая ветка форума).

```html
<xf:macro template="post_macros" name="post" arg-post="{$post}" arg-thread="{$thread}" />
```

