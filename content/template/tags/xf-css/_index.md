+++
title = "Добавляет CSS или LESS - xf:css"
menutitle = "xf:css"
linktitle = "xf:css"
metatitle = "Добавляет CSS или LESS - xf:css"
short_desc = "xf:css"
date = 2018-11-10T15:36:31+05:00
draft = "false"
layout = "single"
page_author = "official"
page_progress = "100"
show_progress = "true"
+++

{{% bq %}}Добавляет CSS или LESS в виде файла или шаблона{{% /bq %}}

Пример использования:

```html
<xf:css src="mycss_file.css"  />
```

## Атрибуты

{{% table_class %}}
| Атрибут | Описание |
| --- | --- |
| `src` | Название шаблона или файла |
{{% /table_class %}}

## Внутренний CSS

Тег `xf:css` также можно использовать для включения стилей прямо в текст страницы:

```html
<xf:css>
html, body {
 font-family: "Roboto", sans-serif;
}
</xf:css>
```

Все, что указано внутри тега `xf:css`, будет сконвертировано в содержимое HTML-тега `<style>...</style>`.

## Важное примечание

Сами разработчики XenForo категорически не рекомендуют использовать включение CSS/JS в виде внешних файлов. Вместо этого рекомендуется создать соответствующий шаблон для нужного файла (в админке форума) и использовать имя этого шаблона для включения данного CSS.

См. соответствующую ссылку на официальном форуме: https://xenforo.com/community/threads/including-external-library-js-and-css.136153/post-1185631