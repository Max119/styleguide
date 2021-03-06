# styleguide

* Не должно быть пробелов вконце строки
* Для переносов используется символ `\n` (LF)
* **ВАЖНО**, избегайте использования `!important`. Допускается использование `!important` в крайних случаях для переопредления стилей из атрибута style
* Для написания классов используются английские слова и термины. Транслитом названия классов и атрибутов не пишутся. 
* Определение переменных, миксин и т.д. создаются в специально отведенных для этого файлах:
  `assets/sass/_parts/_variables.scss` для переменных,
  `assets/sass/_parts/_mixins.scss` для миксинов и функций
* Уровень вложенности **не более 3**  

**Для отступов используем 4 пробела**
```scss
//неправильно
.class-name {
  color: #fff;
}

//правильно
.class-name {
    color: #fff;
}
```

**Селекторы, свойства, @-правила, названия переменных, миксин, функций, #-цвета — все записывается в нижнем регистре. Слова в названиях разделяются дефисом `-`**
````scss
//неправильно
$Color-Red: #1A1A1A;

.Block_First,
.BlockSecond{
    .LINE {
        color: $Color-Red;
    }
}

//правильно
$сolor-red: #1a1a1a;

.block-first,
.block-second{
    .line {
        color: $color-red;
    }
}
````

**Один пробел перед открывающейся скобкой `{` и новая строка после нее. Закрывающая `}` скобка на новой строке. После открывающей и до закрывающей скобки не должно быть пробелов**
```scss
//неправильно
.class-name{
    color: #fff;}
  
//неправильно
.class-name{color: #fff;}  

//неправильно
.class-name {color: #fff; } 

//неправильно
.class-name {

    color: #fff; 
    
} 

//правильно
.class-name {
    color: #fff;
}
```

**При перечислении селекторов каждый селектор пишется с новой строки**
```scss
//неправильно
.class-name-1, .class-name-2 {
    color: #fff;
}

//правильно
.class-name-1,
.class-name-2 {
    color: #fff;
}
```

**Каждое свойство с новой строки. Между свойствами не должно быть пустых строк. Не должно быть дублирующихся свойств.**
```scss
//неправильно
.class-name-1 {
    color: #fff; background-color: #000;
}

//неправильно
.class-name-1 {
    background-color: #f5f5f5;
    color: #fff; 
    
    background-color: #000;
}

//правильно
.class-name-1 {
    color: #fff; 
    background-color: #000;
}
```

**Перед `:` и `,` не должно быть пробелов, а после ставится один пробел.**
```scss
//неправильно
.class-name-1 {
    color : #fff;
    box-shadow: 0 0 10px 0 #000 ,0 5px 15px #ccc;
}

//правильно
.class-name-1 {
    color: #fff;
    box-shadow: 0 0 10px 0 #000, 0 5px 15px #ccc;
}
```

**Не используйте селекторы #id для описания стилей, а так же максимально избегать использования селекторов тегов и вложенности**
```scss
//неправильно
#block-1, 
#block-1 ul {
    color: #000;
}

//правильно
.block-1,
.list-1 {
    color: #000;
}
```

**Записываем ведущий ноль в значениях от -1 до 1**
```scss
//неправильно
.class-name-1 {
    font-size: .5em;
}

//правильно
.class-name-1 {
    font-size: 0.5em;
}
```

**Использовать сокращения для HEX-значений где это возможно**
```scss
//неправильно
.class-name-1 {
    color: #cccccc;
}

//правильно
.class-name-1 {
    color: #ccc;
}
```

**Не указывать единицы измерения для нулевых значений (кроме времени, `transition: all 0.3s;`)**
```scss
//неправильно
.class-name-1 {
    margin: 0px;
}

//правильно
.class-name-1 {
    margin: 0;
}
```

**Где возможно используется сокращеная форма значения свойств**
```scss
//неправильно
.class-name-1 {
    font-size: 15px;
    font-family: serif;
    font-weight: bold;
}

//правильно
.class-name-1 {
    font: bold 15px serif;
}
```

**Не должно быть вендорных префиксов, кроме случаев когда нет свойства без префикса**
```scss
//неправильно
.class-name-1 {
    -webkit-box-shadow: 0 0 10px 0 #000;
    
    @media (-webkit-min-device-pixel-ratio: 2), (min-resolution: 192dpi) {
        width: 100%;
    }
}

//правильно
.class-name-1 {
    box-shadow: 0 0 10px 0 #000;
        
    /* stylelint-disable */
    @media (-webkit-min-device-pixel-ratio: 2), (min-resolution: 192dpi) {
        width: 100%;
    }
    /* stylelint-enable */
}
```

**При записи rgba цвет задается #-значением или переменной**
```scss
//неправильно
.class-name-1 {
    color: rgba(0, 0, 0, 0.5);
}

//правильно
.class-name-1 {
    color: rgba(#000, 0.5);
}

//правильно
$color-black: #000;

.class-name-1 {
    color: rgba($color-black, 0.5);
}
```

**Псевдоэлементы записываются с помощью `::`**
```scss
//неправильно
.class-name-1:before {
    content: "text";
}

//правильно
.class-name-1::before {
    content: "text";
}
```

**CSS-правила отделяются друг от друга пустой строкой**
```scss
//неправильно
.class-name-1 {
    color: #000;
    @media (max-width: 1200px) {
        display: none;
    }
}
.class-name-2 {
    font-size: 16px;
}

//правильно
.class-name-1 {
    color: #000;
    
    @media (max-width: 1200px) {
        display: none;
    }
}

.class-name-2 {
    font-size: 16px;
}
```

**Строки, пути, значения атрибутов, названия шрифтов записываются в двойных кавычках.**
```scss
//неправильно
@import '../block-1';

.link[href='^#'] {
    content: 'text';
    font-family: Roboto, sans-serif;
    background: url(../path-top-picture/picture.png);
}

//правильно
@import "../block-1";

.link[href="^#"] {
    content: "text";
    font-family: "Roboto", sans-serif;
    background: url("../path-top-picture/picture.png");
}
```


**Комментарии**
* Предпочитайте однострочные комментарии многострочным.
* Комментарий должен находится на отдельной строке.
* Избегайте комментариев в конце строки.
* Пишите детальные комментарии для неочевидных вещей

**Порядок свойств:**
Свойста должны быть сгруппированы в следующем порядке:
1. Позиционирование
2. Блочная модель
3. Типографика
4. Оформление
5. Анимация
6. Разное

**Порядок правил**

* CSS-переменные.
* `$`-переменные.
* `@include` без контента
* Свойства
* `&::before`
* `&::after`
* Различные селекторы
* `&:link`
* `&:visited`
* `&:focus`
* `&:hover`
* `&:active`
* `&:first-child`
* `&:last-child`
* `&:nth-child()`
* `&[attr]`
* `&.modifier`
* `&--modifier`
* `@include` с контентом
* `@media`

**Именование классов:**
1. Имена классов в нижнем регистре, слова разделяются знаком тире -
2. Имена классов должны быть максимально короткими, но при этом не потеряв смысл
3. Использовать **js-*** классы для элементов, которые будут задействованы в javascript
4. Классы состояний начинаются на перфикс **is-*** (например: is-active, is-hidden).

**BEM именование классов**
* `block-name` — это "блок" и он представляет из себя компонент верхнего уровня.
* `block-name__element-name` — это "элемент" и он является дочерним компонентом `.block-name`. Из "элементов" состоит "блок".
* `block-name--featured` — это "модификатор" и он предствляет различные состояния "блока" `.block-name`.