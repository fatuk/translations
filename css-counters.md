# Развлечение с CSS счетчиками
## 6 ноября, 2014 / автор [Will Boyd](https://plus.google.com/+WillBoyd41)

CSS счетчики это одна из тех штук, о которых говорят: "о, прикольно, а я и не знал, что CSS такое может!".
У таких фич есть богатый потенциал. Проще говоря, с их помощью можно производить вычисления в CSS не используя JavaScript.

### Базовый счетчик

Вот для начала простой пример нумерации страниц:

<p data-height="268" data-theme-id="0" data-slug-hash="KkudD" data-default-tab="result" data-user="lonekorean" class='codepen'>See the Pen <a href='http://codepen.io/lonekorean/pen/KkudD/'>Pagination CSS Counter</a> by Will Boyd (<a href='http://codepen.io/lonekorean'>@lonekorean</a>) on <a href='http://codepen.io'>CodePen</a>.</p>
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>

Числа, которые вы видите не прописаны жестко в HTML. Они сгенерированы в CSS при помощи вот таких стилей:

<script src="https://gist.github.com/lonekorean/d0c417b1a187e80d024e.js"></script>

Когда попадается элемент `body`, он инициализирует счетчик *pages*. Затем когда попадаются элементы `a`, каждый на единицу значение счетчика `pages`.

### Несколько счетчиков

Если у вас несколько счетчиков, просто дайте им разные имена. В следующем примере два счетчика: `sections` и `boxes`:

<p data-height="268" data-theme-id="0" data-slug-hash="ksFnK" data-default-tab="result" data-user="lonekorean" class='codepen'>See the Pen <a href='http://codepen.io/lonekorean/pen/ksFnK/'>Overlapping CSS Counters</a> by Will Boyd (<a href='http://codepen.io/lonekorean'>@lonekorean</a>) on <a href='http://codepen.io'>CodePen</a>.</p>
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>

Соответствующий CSS:

<script src="https://gist.github.com/lonekorean/71e50ff99432df7a40c2.js"></script>

Здесь вы видите синтаксис одновременной инициализации нескольких счетчиков (строка 2). Чтобы выделить счетчик `boxes` укажем его отображение большими римскими цифрами `upper-roman`. Полный список опций отображения совпадает с `list-style-type`, [читать здесь](https://developer.mozilla.org/en-US/docs/Web/CSS/list-style-type)

### Подсчет выбранных элементов

Сейчас немного развлечемся. Свойства счетчика могут распологаться в псевдоселекторах таких как `:checked`. Это позволяет счетчикам реагировать на пользовательский выбор посредством чекбоксов. Вот пример, который считает сколько чекбоксов было выбрано:

<p data-height="268" data-theme-id="0" data-slug-hash="wKbzv" data-default-tab="result" data-user="lonekorean" class='codepen'>See the Pen <a href='http://codepen.io/lonekorean/pen/wKbzv/'>Selection CSS Counter</a> by Will Boyd (<a href='http://codepen.io/lonekorean'>@lonekorean</a>) on <a href='http://codepen.io'>CodePen</a>.</p>
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>

CSS не далеко ушел от предыдущих примеров. Единственное отличие в том, что мы считаем псевдоселекторы (`input:checked`), и выводим счетчик только один раз в определенный элемент -- `.total`:

<script src="https://gist.github.com/lonekorean/fc467f130d46f3cbde88.js"></script>


### Контроль над инкрементами

Счетчики не обязаны прибавлять по единице. Инкремент может быть каким угодно, даже отицательным. Опираясь на наш предыдущий пример мы указываем значение инкремента для каждого селектора:

<p data-height="268" data-theme-id="0" data-slug-hash="yhtlb" data-default-tab="result" data-user="lonekorean" class='codepen'>See the Pen <a href='http://codepen.io/lonekorean/pen/yhtlb/'>CSS Counter Game</a> by Will Boyd (<a href='http://codepen.io/lonekorean'>@lonekorean</a>) on <a href='http://codepen.io'>CodePen</a>.</p>
<script async src="//assets.codepen.io/assets/embed/ei.js"></script>

Синтаксис достаточно прост:

<script src="https://gist.github.com/lonekorean/be125ee5a8e3a44e2dc0.js"></script>

Мы также можем задать начальное значение счетчика:

<script src="https://gist.github.com/lonekorean/d66e6da69b124f0a8710.js"></script>

### Потенциальные проблемы

Элементы, которые имеют `display: none` не будут учитываться счетчиком. Если требуется посчитать скрытый элемент, то придется скрыть его иначе, например так:

<script src="https://gist.github.com/lonekorean/d6b10a1a962cf4d9d9be.js"></script>

Может вы заметили, что именно это я и сделал в последних двух примерах. Я скрыл чекбоксы, убрав их из виду, но счетчик продолжал их считать.

### Послесловие

Поддержка CSS счетчиков браузерами [фантастическая](http://caniuse.com/#search=css%20counters). Все помечено зеленым.

На сколько бы ни были хороши CSS счетчики, на забывайте про наших старых друзей `<ol>` и `<li>`.
Они все еще великолепно подходят для базовых нумерованных списков. Но в сложных ситуациях лучше использовать CSS счетчики, особенно если учесть, что они работают с любыми элементами и дают больше свободы в плане синтаксиса и семантики.

UPD: Я должен был упомянуть о поддержке на устройствах. CSS счетчики опираются на генерируемый контент в псевдоэлементах. Некоторые читалки отображают его, некоторые нет. Исходя из этого, важные данные лучше не выводить в псевдоэлентах. Эти демо были созданы, чтобы в интересной манере научить пользоваться CSS счетчиками, но я бы не стал их использовать в реальном проекте как есть.


#### Оригинал статьи [Fun Times with CSS Counters](http://codersblock.com/blog/fun-times-with-css-counters/)