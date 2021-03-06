# Часті питання

## Чому БЕМ?

* [У чому відмінність БЕМ від OOCSS, AMCSS, SMACSS, SUITCSS?](#У-відмінність-БЕМ-від-oocss-amcss-smacss-suitcss)
* [У чому різниця між БЕМ і Web Components?](#- Різниця-між-БЕМ-і-web-components)
* [У чому різниця між БЕМ і Bootstrap?](#- Різниця-між-БЕМ-і-bootstrap)

## Блоки та елементи

* [В якому разі створювати блок, у якому — елемент?](#У-будь-разі-створювати блок--якому--елемент)
* [Чому в БЕМ не рекомендується створювати елементи елементів (block__elem1__elem2)?](#Почему-в-БЭМ-не-рекомендуется-создавать-элементы-элементов-block__elem1__elem2)
* [Навіщо писати ім'я блоку в іменах модифікаторів і елементів?](#Навіщо писати-ім'я-блоку в іменах-модифікаторів-і-елементів)
* [Як зробити глобальні модифікатори для блоків?](#Як зробити-глобальні-модифікатори-для-блоків)
* [Навіщо створювати окремі директорії і файли для кожного блоку і технології?](#Навіщо створювати окремі-директорії і файли-для-кожного блоку-і-технології)

## JavaScript

* [Навіщо використовувати i-bem.js якщо можна писати на jQuery?](#Навіщо використовувати-i-bemjs-якщо можна-писати-на-jquery)

## CSS

* [Чому небажано використовувати вкладені селектори?](#Чомусь небажано використовувати вкладені-селектори)
* [Чому в БЕМ не рекомендується використовувати комбіновані селектори для створення CSS-правил до модификатору?](#Почему-в-БЭМ-не-рекомендуется-использовать-комбинированные-селекторы-для-создания-css-правил-к-модификатору)
* [Можна об'єднувати тег і клас в селекторі (наприклад, button.button)?](#Можна об'єднувати-тег-та-клас-у-селекторі-Наприклад-buttonbutton)
* [Чому в БЕМ не використовують користувальницькі теги (custom tag) для блоків?](#Чому-у-БЕМ-не-використовують-користувальницькі теги-custom-tags-для-блоків)
* [Чому не можна робити загальний скид стилів (reset)?](#Чомусь не можна робити-загальний-скидання-стилів-reset)
* [Чому не можна писати block_mod замість block block_mod, якщо ім'я модифікатора вже містить всю інформацію про блоке?](#Почему-нельзя-писать-block_mod-вместо-block-block_mod-если-имя-модификатора-уже-содержит-всю-информацию-о-блоке)
* [Чому не можна вказувати назву CSS-властивості в імені модифікатора: .block__element_border-color_grey?](#Почему-нельзя-указывать-название-css-свойства-в-имени-модификатора-block__element_border-color_grey)


**Не знайшли відповідь?** — [Задайте питання команді на форумі](https://ru.bem.info/forum/)

## У чому відмінність БЕМ від OOCSS, AMCSS, SMACSS, SUITCSS?

1. БЕМ працює не тільки з CSS, але і з JavaScript.
1. БЕМ більше схожий з Web Components, ніж з перерахованими рішеннями для CSS. ([В чому різниця між БЕМ і Web Components?](#- Різниця-між-БЕМ-і-web-components))
1. БЕМ надає комплексне рішення по створенню архітектури проекту і допомагає організувати процеси розробки. Детальніше читайте у розділі [Застосування методології для вирішення завдань веб-розробки](../method/solved-problems/solved-problems.ru.md).

>Докладніше про [методології БЕМ](https://ru.bem.info/method/).

Можна використовувати БЕМ тільки на рівні CSS. Для цього досить просто слідувати [рекомендацій методології](../method/naming-convention/naming-convention.ru.md).

## У чому різниця між БЕМ і Web Components?

Підтримка браузерів

* Web Components [не підтримується](http://caniuse.com/#search=Web%20Components) в Safari, iOS Safari, Internet Explorer, Firefox.
* БЕМ працює у всіх браузерах.

Інкапсуляція

* У Web Components реалізована через Shadow DOM.
* У БЕМ — з допомогою [елементів](../method/key-concepts/key-concepts.ru.md#Елемент) блоку.

Робота шаблонів

* У Web Components шаблони завжди виконуються в браузері. Це може вимагати додаткових рішень проблем з індексацією.
* В БЭМ генерация шаблона возможна на этапе разработки. Це дозволяє віддавати готовий HTML. Шаблони можуть виконуватися як в браузері, так і на сервері.


* Web Components использует императивный принцип — интерполяцию строк.
* БЕМ використовує декларативний підхід, який дозволяє гнучко управляти шаблонизацией і уникати повторень. Докладно про різницю між декларативним та імперативним підходами дивіться у доповіді [Сергія Бережного](https://ru.bem.info/authors/berezhnoy-sergey/) — [Шаблонизаторы](https://events.yandex.ru/lib/talks/553/).

Замість імпорту HTML — збірка

* Web Components використовує імпорт HTML (HTML Imports), який працює безпосередньо в браузері. Для об'єднання HTML-файлів використовується інструмент [Vulcanize](http://webcomponents.org/articles/introduction-to-html-imports/#aggregating-network-requests).
* БЕМ використовує збирачі: [ENB](https://ru.bem.info/tools/bem/enb-bem/) або [bem-tools](https://ru.bem.info/tools/bem/bem-tools/).

Замість Custom Elements — абстракція над DOM-деревом

* У Web Components використовуються Custom Elements. Такий підхід дозволяє розмістити на одному DOM-вузол лише один компонент.
* У БЕМ існує поняття [БЕМ-дерева](../method/key-concepts/key-concepts.ru.md#БЕМ-дерево). БЭМ использует [миксы](../method/key-concepts/key-concepts.ru.md#Микс) — размещение нескольких БЭМ-сущностей на одном DOM-узле.

## У чому різниця між БЕМ і Bootstrap?

У термінах БЕМ [Bootstrap](http://getbootstrap.com/) — це набір зверстаних блоків. БЕМ — не бібліотека елементів інтерфейсу, а методологія, що дозволяє:

* створювати архітектуру проекту;
* розробляти веб-додатки незалежними блоками;
* спрощувати підтримку проектів.

Бібліотека блоків, зроблених на БЕМ — [bem-components](https://ru.bem.info/libs/bem-components/). Існують також і [інші](https://ru.bem.info/libs/) БЕМ-бібліотеки.

## В якому випадку створювати блок, у якому — елемент?

1. Если фрагмент кода может использоваться повторно и не зависит от реализации других компонентов страницы, необходимо создавать [блок](../method/key-concepts/key-concepts.ru.md#Блок).
1. Если фрагмент кода не может использоваться самостоятельно, без родительской сущности (блока), в большинстве случаев создается [элемент](../method/key-concepts/key-concepts.ru.md#Элемент).

Виняток становлять елементи, реалізація яких для спрощення розробки вимагає поділу на більш дрібні частини — подэлементы. БЕМ-методологія [не рекомендує створювати елементи елементів](#Чому-у-БЕМ-не рекомендовано створювати елементи-елементів-block__elem1__elem2). В подобном случае вместо элемента необходимо создавать служебный блок.

## Чому у БЕМ не рекомендується створювати елементи елементів (block__elem1__elem2)?

Наявність елементів елементів обмежує можливість змінювати внутрішню структуру блоку: елементи можна поміняти місцями, видалити або додати без коригування існуючого коду.

У методології БЕМ вкладену структуру підтримують тільки блоки (`block__elem`). Ім'я блоку задає простір імен, що [гарантує залежність](../method/naming-convention/naming-convention.ru.md#Ім'я елемента) елементів від блоку.

Блок може мати вкладену структуру елементів в DOM-дереві:

```html
<div class="block">
    <div class="block__elem1">
        <div class="block__elem2">
            <div class="block__elem3"></div>
        </div>
    </div>
</div>
```

Однак ця ж структура блоку в методології БЕМ завжди буде представлена плоским списком елементів:

```css
.block {}
.block__elem1 {}
.block__elem2 {}
.block__elem3 {}
```

Це дозволяє змінювати DOM-структуру блоку без внесення виправлень в коді кожного окремого елемента:

```html
<div class="block">
    <div class="block__elem1">
        <div class="block__elem2"></div>
    </div>
    <div class="block__elem3"></div>
</div>
```

Структура блоку змінюється, а правила для елементів і їх назви залишаються колишніми.

## Навіщо писати ім'я блоку в іменах модифікаторів і елементів?

Ім'я блоку в іменах [БЕМ-сутностей](../method/key-concepts/key-concepts.ru.md#БЕМ-сутність) забезпечує:

* [Простір імен](#Простір імен)
* [Мікси](#Мікси)
* [Пошук в коді](#Пошук-коді)

____________________________________________

**Важливо!** Методологія БЕМ [допускає вибір](../method/naming-convention/naming-convention.ru.md#Альтернативні схеми-іменування) зручної стратегії іменування, але вимагає дотримання консистентности в назвах. Так, например, все варианты верны: `context`, `ctx` или `c`, `attributes`, `attrs` или `as`. Необхідно вибрати один з них і використовувати у всьому проекті.
_____________________________________________

### Простір імен

Ім'я блоку задає простір імен і забезпечує унікальність імен елементів і модифікаторів. Це дозволяє обмежити вплив елементів і модифікаторів одного блоку на реалізацію іншого.

### Мікси

[Микс](../method/key-concepts/key-concepts.ru.md#Микс) — это совмещение разных БЭМ-сущностей на одном DOM-узле. При міксі модифікатора ім'я блоку вказує, до якого блоку застосувати модифікатор. Якщо назва блоку не вказати модифікатор застосувати до всіх миксуемым БЕМ-сутностей.

Наприклад, розглянемо мікс пункту меню (`menu__item`) і кнопки (`button`):

```html
<div class="menu__item button"></div>
```

Додамо модифікатор `active` у скороченій формі запису (без імені блоку):

```html
<div class="menu__item button active"></div>
```

У такому вигляді HTML-розмітка не дає зрозуміти, до чого відноситься модифікатор: до пункту меню (`menu__item.active`) або до кнопки (`button.active`). Ім'я блоку (`button_active`) явно вказує на БЕМ-сутність, до якої буде застосовано модифікатор.

Також запис `<div class="block mod">` не дає зрозуміти, які БЕМ-сутності використовуються в роботі. Наприклад, із запису `<div class="checkbox button">` не можна однозначно визначити, це мікс модифікатора і блоку або мікс двох блоків.

Повне ім'я модифікатора `<div class="block block_mod">` показує, про яких сутності йдеться: `<div class="checkbox checkbox_button">`.

### Пошук в коді

Явні та унікальні імена полегшують пошук необхідної сутності в коді і файловій системі.

Порівняємо результати глобального пошуку при налагодженні проекту. Знайдемо модифікатор `active`. У скороченому вигляді (`active`) в результати пошуку потраплять всі можливі комбінації і HTML-фрагменти, де зустрічається `active`. У запису, рекомендованої методологією, сама назва вже буде містити уточнюючий параметр у вигляді імені блоку (`button_active`). Так як ім'я модифікатора унікально, в результати пошуку потраплять тільки потрібні фрагменти коду.

## Як зробити глобальні модифікатори для блоків?

У БЕМ відсутнє поняття глобальних модифікаторів, так як модифікатор завжди відноситься до однієї конкретної [БЕМ-сутності](../method/key-concepts/key-concepts.ru.md#БЕМ-сутність).

Якщо потрібно винести CSS властивість за межі одного блоку і застосовувати його до різних БЕМ-сутностей в проекті, необхідно створювати окремий блок, реалізований в технології CSS.

БЕМ дозволяє поєднувати реалізацію різних блоків з допомогою [міксів](../method/key-concepts/key-concepts.ru.md#Мікс):

```html
<div class="block1 block2"></div>
```

## Навіщо створювати окремі директорії і файли для кожного блоку і технології?

Файлова система БЕМ-проекту поділяється на вкладені директорії і файли для [зручності розробки і підтримки проекту](../method/filesystem/filesystem.ru.md#Реалізація-блоку-поділяється на окремі файли).

Дотримуватися [рекомендованої структури файлової системи](../method/filesystem/filesystem.ru.md#Організація файлової системи-БЕМ-проекту) не обов'язково. Ви можете використовувати будь-яку альтернативну структуру проекту, відповідну [принципам організації файлової системи БЕМ](../method/filesystem/filesystem.ru.md#Принципи організації файлової системи-БЕМ-проекту), наприклад:

**flex-схема**

* Блоку відповідає окрема директорія.
* Елементи і модифікатори реалізовані в окремих файлах.

```files
blocks/
  input/
      input_layout_horiz.css
      input_layout_vertical.css
      input__elem.css
      input.css
      input.js
  button/
```

* Блоку відповідає окрема директорія.
* Елементи і модифікатори реалізовані у файлах блоку.

```files
blocks/
  input/
      input.css
      input.js
  button/
```

* Директорії для блоків не використовуються.
* Елементи і модифікатори реалізовані у файлах блоку.

```files
blocks/
  input.css
  input.js
  button.css
  button.js
```

**flat-схема**

* Директорії для блоків не використовуються.
* Опціональні элеметы і модифікатори реалізовані в окремих файлах.

```files
blocks/
  input_type_search.js
  input_type_search.bemhtml.js
  input__box.bemhtml.js
  input.css
  input.js
  input.bemhtml.js
  button.css
  button.js
  button.bemhtml.js
  button.png
```

## Навіщо використовувати i-bem.js якщо можна писати на jQuery?

[i-bem.js](https://ru.bem.info/technology/i-bem/) це спеціалізований фреймворк для розробки проектів на JavaScript в термінах блоків, елементів і модификаторв.

`i-bem.js` не призначений для заміни фреймворку загального призначення, такого як jQuery.

`i-bem.js` дозволяє:

* розробляти веб-інтерфейс в термінах блоків, елементів, модифікаторів;
* інтегрувати JavaScript-код з шаблонами і CSS-правил в стилі БЕМ;
* описувати логіку роботи блоку як набір станів.

## Чому небажано використовувати вкладені селектори?

Ключова ідея БЕМ — незалежність блоків. [Вкладені селектори](http://htmlbook.ru/css/selector/descendant) збільшують зв'язаність коду і роблять його повторне використання неможливим. Це суперечить принципам БЕМ.

Методологія БЕМ допускає використання таких селекторів, але рекомендує по-максимуму його скоротити.

Наприклад, вкладеність доречна, щоб змінювати елементи в залежності від стану блоку або заданої йому теми:

```css
.nav_hovered .nav__link
{
    text-decoration: underline;
}
```
```css
.nav_theme_islands .nav__item
{
    line-height: 1.5;
}
```

## Чому у БЕМ не рекомендується використовувати комбіновані селектори для створення CSS-правил до модификатору?

Об'єднані селектори ускладнюють перевизначення блоку, оскільки мають більш високу специфічність у CSS, ніж поодинокі. Специфічність комбінованого селектора модифікатора блоку (`.block1.mod`) і для переопределенного блоку (`.block2 .block1`) однакова. Перевизначення блоку буде залежати тільки від порядку оголошення правил у декларації.

Розглянемо приклад:

```html
<div class="header">
  <button class="button active">
</div>
```
Правила модификатора `active` для кнопки записываются как комбинированный селектор `.button.active`. При перевизначенні кнопки з допомогою батьківського блоку `header`, створюється селектор `.header .button`. Специфічність обох селекторів однакова, значить застосування CSS-правил визначається порядком їх оголошення в декларації.

Використання імені блоку в назві модифікатора забезпечує більш високий пріоритет CSS-правил при перевизначенні блоку.
Селектор `.header .button` завжди буде мати пріоритет вище, ніж `.button_active`.

>[Причини використання імені блоку імені модифікатора](#Навіщо писати-ім'я-блоку в іменах-модифікаторів-і-елементів)

## Можна об'єднувати тег і клас в селекторі? Наприклад, button.button.

Поєднання тега і класу в селекторі підвищує специфічність CSS-правил. При додаванні модифікатора правила блоку не зможуть бути перевизначені, так як специфічність селектора блоку вище.

Розглянемо приклад:

```html
 <button class="button">
```

Записуємо для нього CSS-правила в селекторі `button.button`.

Додамо модифікатор:

```html
 <button class="button button_active">
```

Селектор `.button_active` не перевизначити властивості блоку, записані як `button.button`, так як специфічність `button.button` вище. Для успішного перевизначення селектор модифікатора блоку також повинен бути скомбінований з тегом `button.button_active`.

В результаті розвитку проекту можуть з'явиться блоки з селекторами `input.button`, `span.button` і, наприклад, `a.button`. У такому разі всі модифікатори блоку `button` і вкладені в нього елементи зажадають чотири різні декларації для кожного випадку.

## Чому у БЕМ не використовують користувальницькі теги (custom tags) для блоків?

>Блоки можуть виражатися в HTML з допомогою користувацьких тегів, до яких створюються CSS-правила. У такому разі класи можна буде використовувати тільки для модифікаторів: `<button class="mod"/>`.

Користувальницькі теги можуть застосовуватися для створення селекторів до блокам, але є ряд обмежень:

* Неможливо використовувати [мікси](../method/key-concepts/key-concepts.ru.md#Мікс).
* Не будь блок можна виразити користувальницьким тегом. Наприклад, для всіх посилань необхідний тег `<a>`, а для полів — `<input>`.

## Чому не можна робити загальний скид стилів (reset)?

Блок — незалежний компонент. На нього не повинні впливати CSS-правила, створені для всієї сторінки. Це порушує незалежність блоків і ускладнює їх повторне використання.

Загальний скид стилів по суті реалізується з допомогою [глобальних CSS-правил](#Як зробити-глобальні-модифікатори-для-блоків), які в більшості випадків пишуться [селекторам на тег](#Чому-у-БЕМ-не-використовують-користувальницькі теги-custom-tags-для-блоків), що небажано використовувати в БЕМ-проекті.

Якщо скинути стилі все-таки необхідно, БЕМ це робиться в кожному блоці.

Розглянемо приклад. Якщо в проекті блоки меню і список виражені в HTML з допомогою тегу `<ul>`, значить кожен блок повинен надавати скидання CSS `<ul>`. Повторів у виводі коді можна уникнути за допомогою CSS-оптимізатора.

Якщо в проекті не використовується CSS-оптимізатор, який об'єднує селектори з однаковим набором правил, можна застосувати CSS-препроцесор. Тоді для кожного нового блоку можна робити скидання правил, [міксуючи](../method/key-concepts/key-concepts.ru.md#Мікс) чистий код. Наприклад, в SASS це буде виглядати так:

```css
.menu {
    @include reset-list;
}
.menu__item {
    @include reset-list-item;
}
...
.list {
    @include reset-list;
}
.list__item {
    @include reset-list-item;
}
```

Такий спосіб слід використовувати тільки при відсутності оптимізатора.

## Чому не можна писати block_mod замість block block_mod, якщо ім'я модифікатора вже містить всю інформацію про блоці?

Поєднання декількох модифікаторів на одному і тому ж блоці (наприклад, `<div class="block_theme_christmas block_size_big">`) призведе до дублювання коду, що реалізує базову функціональність (логіку і стилі) блоку.

## Чому не можна вказувати назву CSS-властивості в імені модифікатора: .block__element_border-color_grey?

* При зміні зовнішнього вигляду блоку або елемента доведеться міняти не тільки CSS-код, але і назви селекторів. Наприклад, якщо колір кордону зміниться з сірого (`grey`) на червоний (`red`), потрібно буде змінити шаблони і, цілком ймовірно, JavaScript-код.
* При додаванні інших властивостей (фону, відступів), ім'я перестане відповідати вмісту модифікатора.

Методологія БЕМ рекомендує вибирати імена модифікаторів, спираючись на семантику, а не візуальне оформлення.
