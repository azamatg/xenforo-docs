---
title: "Условия в шаблонах (примеры)"
draft: false
---

<div class="alert alert-success" role="alert">
  <p><span class="badge badge-info">Перевод</span> Перевод статьи с официального форума - <a href="ttps://xenforo.com/community/resources/conditional-statements-for-xenforo-2.5795/">Conditional Statements for XenForo 2</a></p>
  <div class="progress">
    <div class="progress-bar bg-success" role="progressbar" style="width: 100%;" aria-valuenow="100" aria-valuemin="0" aria-valuemax="100">100%</div>
  </div>
</div>

{{% bq %}}Сборник примеров условий в шаблонах XenForo 2. На основе статьи с официального форума.{{% /bq %}}

## Операторы и расширения

### Теги:

- `xf:if` - если
- `xf:else` - иначе
- `xf:elseif` - иначе_если

### Операторы:

!TODO
Скорее всего, поддерживается весь набор операторов и функций PHP, нужно это проверить и описать здесь. 

- `AND` - И
- `OR` - ИЛИ (например `$xf.visitor.is_admin OR $xf.visitor.is_moderator`)
- `!` - НЕ
- `=` - равно
= `!=` - не равно
- `>` - больше (например `$xf.visitor.like_count|number > 25`)
- `<` - меньше

### Функции

- `in_array($xf.visitor.user_id, [1, 5, 7, 12])` - есть ли первый параметр (например `$xf.visitor.user_id`) в массиве, заданном во втором параметре


## Условия на юзеров (пользователей, посетителей, админов)

Для проверки условий на свойства текущего посетителя (юзера) рекомендуется использовать глобально доступную переменную `$xf.visitor`. В некоторых мануалах встречается переменная `$user`, но она контекстно-зависимая, и есть не во всех шаблонах, и не всегда представляет именно текущего пользователя.

Вы можете получить дамп переменной `xf.visitor` прямо в шаблоне, что даст вам возможность подробно изучить полученный объект:

```html
<pre>{{ dump($xf.visitor) }}</pre>
```

> Полный список параметров переменной `xf.visitor` см. в разделе `xf.visitor` в статье [Переменные в шаблонах XenForo 2](template-variables.md).

### Показать контент только Администраторам

```html
<xf:if is="$xf.visitor.is_admin">
    Показать контент...
</xf:if>
```

### Показать контент только Модераторам

```html
<xf:if is="$xf.visitor.is_moderator">
    Показать контент...
</xf:if>
```

### Показать контент только Администраторам И Модераторам

```html
<xf:if is="$xf.visitor.is_admin OR $xf.visitor.is_moderator">
    Показать контент...
</xf:if>
```

### Показать контент только зарегистрированным пользователям

```html
<xf:if is="$xf.visitor.user_id">
    Показать контент...
</xf:if>
```

### Показать контент только гостям (незарегистрированным)

```html
<xf:if is="$xf.visitor.user_id">
    Показать контент...
</xf:if>
```

### Разделить вывод контента - отдельно для юзеров, отдельно для гостей

```html
<xf:if is="!$xf.visitor.user_id">
  Контент только для гостей
<xf:else />
  Контент только для юзеров
</xf:if>
```

### Показать контент только забаненным юзерам

```html
<xf:if is="$xf.visitor.is_banned">
    Ты забанен! Страдай и крепись! Все будет хорошо! :D
</xf:if>
```

### Показать контент только юзерам, которые набрали лайков больше, чем x

```html
<xf:if is="$xf.visitor.like_count|number > 25">
   Ты набрал 25 лайков, молодец!
</xf:if>
```

### Показать контент только юзерам с количеством постов больше, чем x

```html
<xf:if is="{$xf.visitor.message_count|number} > 100">
   Ты добавил на форум уже 100 постов, ничего себе!
</xf:if>
```

### Показать контент только юзерам, которые набрали очков наград (трофеев) больше, чем x

```html
<xf:if is="$xf.visitor.trophy_points|number > 5">
  5 очков трофеев твои, но дорога только начинается...
</xf:if>
```

### Показать контент конкретному юзеру (с определенным ID)

```html
<xf:if is="$xf.visitor.user_id == 5">
   Это контент только для юзера с ID = 5...
</xf:if>
```

Здесь 5 - ID юзера, которому нужно показать этот контент

### Показать контент нескольким конкретным юзерам

```html
<xf:if is="in_array($xf.visitor.user_id, [1, 5, 7, 12])">
   У нас тут туса намечается, приходите все 4 человека - Димон, Абрам, Васек и Афиноген!
</xf:if>
```

### Показать контент юзеру, только если он состоит в конкретных группах

```html
<xf:if is="{{$xf.visitor.isMemberOf([2, 8])}}">
    Show content...
</xf:if>
```

Здесь 2 и 8 - ID групп, в которых должен быть этот юзер.

### Показать контент только для одной конкретной группы

```html
<xf:if is="{{$xf.visitor.isMemberOf(3)}}">
    Группа "Модераторы", идем в поход на соседний форум!
</xf:if>
```

### Скрыть контент от участников определенных групп

```html
<xf:if is="{{!$xf.visitor.isMemberOf([2, 7])}}">
     Кто нам денег не прислал, у того контент пропал!
</xf:if>
```

### Скрыть контент от участников конкретной группы

```html
<xf:if is="{{!$xf.visitor.isMemberOf(8)}}">
    Участники группы с ID = 8 этот контент не увидят...
</xf:if>
```

### Показать/скрыть контент для "репрессированных" юзеров

```html
<xf:if is="{$xf.visitor.Option.is_discouraged}">
     Show content...
</xf:if>
```

### Показать/скрыть контент только для юзеров с установленным аватаром типа Gravatar

```html
<xf:if is="{$xf.visitor.gravatar}">
  Show content...
</xf:if>
```

### Показать/скрыть контент только для команды форума

```html
<xf:if is="{$xf.visitor.is_staff}">
    Show content...
</xf:if>
```

### Показать/скрыть контент для юзеров с неподтвержденным email

```html
<xf:if is="{$xf.visitor.isAwaitingEmailConfirmation()}">
  Show content...
</xf:if>
```

### Показать контент только юзерам с заполненным полем "Местоположение" (`location`)

```html
<xf:if is="{$xf.visitor.location}">
    Show content...
</xf:if>
```

### Показать контент только юзерам с заполненным полем "Сайт" (`website`)

```html
<xf:if is="{$xf.visitor.website}">
    Show content...
</xf:if>
```

### Показать контент только юзерам с наличием подписи

```html
<xf:if is="{$xf.visitor.signature}">
    Show content...
</xf:if>
```

### Показать контент только активированным юзерам

```html
<xf:if is="{$xf.visitor.user_state} == 'valid'">
    Show content...
</xf:if>
```

### Показать контент только юзерам, ожидающим подтверждения по почте

```html
<xf:if is="{$xf.visitor.user_state} == 'email_confirm_edit'">
    Show content...
</xf:if>
```

### Показать контент только юзерам, чей email не прошел проверку

```html
<xf:if is="{$xf.visitor.user_state} == 'email_bounce'">
    Show content...
</xf:if>
```


## Условия уровня конкретных постов

### Показать контент сразу после первого поста в теме

```html
<xf:if is="$post.position % $xf.options.messagesPerPage == 0">
    Show content...
</xf:if>
```

### Показать контент после 5-го поста на каждой странице темы

```html
``<xf:if is="$post.position % $xf.options.messagesPerPage == 5">
    Show content...
</xf:if>
```

## Условия уровня главной страницы, контейнеров и форумов

### Как показать контент на страницах, у которых отображается сайдбар (боковая панель)?

```html
<xf:if is="$sidebar">
    Show content...
</xf:if>
```

### Как показать/скрыть контент только на главной странице?

```html
<xf:if is="$template == 'forum_list'">
     Show content...
</xf:if>
```

### Показать/скрыть контент только при создании поста

```html
<xf:if is="$template == 'forum_post_thread'">
    Show content...
</xf:if>
```

### Показать/скрыть контент только при создании ресурса

```html
<xf:if is="$template == 'xfrm_category_add_resource'">
   Show content..
</xf:if>
```

### Показать/скрыть контент только на странице поиска

```html
<xf:if is="$template == 'search_form'">
    Show content..
</xf:if>
```

### Показать/скрыть контент только на странице "Что нового?"

```html
<xf:if is="$template == 'whats_new'">
   Show content..
</xf:if>
```

### Показать/скрыть контент только на странице конкретной личной переписки

```php
<xf:if is="$template == 'conversation_view'">
    Show content..
</xf:if>
```

### Показать/скрыть контент только на странице со списком личных переписок

```html
<xf:if is="$template == 'conversation_list'">
   Show content..
</xf:if>
```

### Показать/скрыть контент только на главной странице менеджера ресурсов

```html
<xf:if is="$template == 'xfrm_overview'">
    Show content..
</xf:if>
```

### Показать скрыть контент только на странице просмотра ресурса

```html
<xf:if is="$template == 'xfrm_resource_view'">
   Show content..
</xf:if>
```

### Показать/скрыть контент на странице просмотра темы

```html
<xf:if is="$template == 'thread_view'">
   Show content..
</xf:if>
```

### Показать/скрыть контент на странице со списком тем

```html
<xf:if is="$template =='forum_view'">
   Show content..
</xf:if>
```

### Показать/скрыть контент только в определенных форумах
 
```html
<xf:if is="in_array({$forum.node_id}, [X,Y,Z])">
  Show content..
</xf:if>
```

### Показать/скрыть контент только на определенном форуме

```html
<xf:if is="$forum.node_id == x">
               Show content..
</xf:if>
```

### Показать баннер под первым постом на каждой странице темы

```html
<xf:if is="{$post.position} % {$xf.options.messagesPerPage} == 1">
        Show content..
</xf:if>
```

### Показать баннер в первом посте на каждой странице темы

```html
<xf:if is="{$post.position} % {$xf.options.messagesPerPage} == 0">
               Show content..
</xf:if>
```


## Ссылки

- [Conditional Statements for XenForo 2](https://xenforo.com/community/resources/conditional-statements-for-xenforo-2.5795/)
