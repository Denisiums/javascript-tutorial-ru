# Свойство white-space

Свойство `white-space` позволяет сохранять пробелы и переносы строк.

У него есть два известных значения:

- `white-space: normal` -- обычное поведение
- `white-space: pre` -- текст ведёт себя, как будто оформлен в тег `pre`.

Но браузеры поддерживают и другие, которые также бывают очень полезны.

[cut]

## pre / nowrap

Встречаем первую "сладкую парочку" -- `pre` и `nowrap`.

Оба этих значения меняют стандартное поведение HTML при работе с текстом:

**`pre`**:

- Сохраняет пробелы.
- Переносит текст при явном разрыве строки.

**`nowrap`**

- Не сохраняет пробелы.
- Игнорирует явные разрывы строки (не переносит текст).

Оба этих значения поддерживаются кросс-браузерно.

**Их основной недостаток -- текст может вылезти из контейнера.**

Для примера, рассмотрим следующий фрагмент кода:

```js no-beautify
if (hours > 18) {
      // Пойти поиграть в теннис
}
```

**`white-space: pre`:**

```html autorun height=100
<style>
  div { font-family: monospace; width: 200px; border: 1px solid black; }
</style>

<div style="white-space:pre">if (hours > 18) {
      // Пойти поиграть в теннис
}
</div>
```

Здесь пробелы и переводы строк сохранены. В HTML этому значению `white-space` соответствует тег `PRE`.

**`white-space: nowrap`:**

```html autorun height=100
<style>
  div { font-family: monospace; width: 200px; border: 1px solid black; }
</style>

<div style="white-space:nowrap">if (hours > 18) {
      // Пойти поиграть в теннис
}
</div>
```

Здесь переводы строки проигнорированы, а подряд идущие пробелы, если присмотреться -- сжаты в один (например, перед комментарием `//`).

Допустим, мы хотим разрешить посетителям публиковать код на сайте, с сохранением разметки. Но тег `PRE` и описанные выше значения `white-space` для этого не подойдут!

Злой посетитель Василий Пупкин может написать такой текст, который вылезет из контейнера и поломает вёрстку страницы.

Можно скрыть вылезшее значение при помощи `overflow-x: hidden` или сделать так, чтобы была горизонтальная прокрутка, но, к счастью, есть другие значения `white-space`, специально для таких случаев.

## pre-wrap/pre-line

`pre-wrap`
: То же самое, что `pre`, но переводит строку, если текст вылезает из контейнера.

`pre-line`
: То же самое, что `pre`, но переводит строку, если текст вылезает из контейнера и не сохраняет пробелы.

Оба поведения отлично прослеживаются на примерах:

**`white-space: pre-wrap`:**

```html autorun height=100
<style>
  div { font-family: monospace; width: 200px; border: 1px solid black; }
</style>

<div style="white-space:pre-wrap">if (hours > 18) {
      // Пойти поиграть в теннис
}
</div>
```

Отличный выбор для безопасной вставки кода посетителями.

**`white-space: pre-line`:**

```html autorun height=100
<style>
  div { font-family: monospace; width: 200px; border: 1px solid black; }
</style>

<div style="white-space:pre-line">if (hours > 18) {
      // Пойти поиграть в теннис
}
</div>
```

Сохранены переводы строк, ничего не вылезает, но пробелы интерпретированы в режиме обычного HTML.
