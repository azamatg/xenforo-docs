---
title: "Функции в шаблонах"
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

Вызов функции в шаблоне:

```html
{{ phrase('new') }}
```

## Простой список функций с краткими описаниями

- `phrase()`
- `link()`
- `number()`
- `date_time()`
- `bb_code()`
- `page_title()`
