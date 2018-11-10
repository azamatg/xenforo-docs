+++
title = "Добавляет файл JavaScript"
menutitle = "xf:js"
linktitle = "xf:js"
metatitle = "xf:js"
short_desc = "Добавляет файл JavaScript"
date = 2018-11-10T15:36:31+05:00
draft = "false"
layout = "single"
page_author = "official"
page_progress = "100"
show_progress = "true"
+++

{{% bq %}}Добавляет файл JavaScript{{% /bq %}}

Пример использования:

```html
<xf:js src="myaddon/vendor/scripts/myjs_file.js"  />
```

## Атрибуты

{{% table_class %}}
| Атрибут | Описание |
| --- | --- |
| `src` | Название файла (полный путь от папки /js в корне форума) |
| `prod` | Название файла для режима `в работе` (`production`) |
| `dev` | Название файла для режима `в разработке` (`dev`) |
| `min` | (только для режима `production`) Включать минифицированную версию файла (просто заменяет в имени файла `js` на `min.js`) |
| `addon` | (только для режима `dev`) Использовать путь для режима разработки |
{{% /table_class %}}

{{% alert class="danger nomargin_inner_paragraph" %}}
**Внимание!** Вы можете использовать только один из атрибутов `scr`, `prod`, `dev`, их нельзя использовать одновременно.
{{% /alert %}}

## Внутренний JS

Тег `xf:js` также можно использовать для включения JS-скриптов прямо в текст страницы:

```html
<xf:js>
alert("The truth hurts, I know. It's biologically based actually.");
</xf:js>
</xf:css>
```

Все, что указано внутри тега `xf:js`, будет сконвертировано в содержимое HTML-тега `<script>...</script>`.

## Важные примечания

Тег `xf:js` ожидает, что файлы JS находятся в каталоге `/js` (это каталог в корневом каталоге форума). Но вы можете подключать и внешние по отношению к форуму файлы, приведя их полный URL в теге `src`, хотя сами разработчики не рекомендуют так делать, см. [пост на официальном форуме](https://xenforo.com/community/threads/including-external-library-js-and-css.136153/post-1185631).

## Примеры использования

Обратите внимание на шаблон `editor`.