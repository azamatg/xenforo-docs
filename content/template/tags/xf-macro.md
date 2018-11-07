---
title: "Макросы в шаблонах (тег xf:macro)"
draft: false
---

<div class="alert alert-warning" role="alert">
  <p>
    <span class="badge badge-info">Своя разработка</span>
    <span class="badge badge-warning">В работе</span> 
    Страница на начальной стадии заполнения, ведутся работы.
  </p>
  <div class="progress">
    <div class="progress-bar bg-warning" role="progressbar" style="width: 5%;" aria-valuenow="5" aria-valuemin="0" aria-valuemax="100">5%</div>
  </div>
</div>

{{% bq %}}Как работать с тегом xf:macro - примеры из стилей XenForo 2 и от участников сообщества.{{% /bq %}}

## Примеры из стандартного стиля XenForo 2

### Шаблон post

В шаблоне `post` используется макрос `post` с шаблоном `post_macros`, при этом в макрос и его шаблон с помощью аргументов передаются переменные `$post` (текущий пост) и `$thread` (текущая ветка форума).

```html
<xf:macro template="post_macros" name="post" arg-post="{$post}" arg-thread="{$thread}" />
```

