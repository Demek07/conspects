## Грид-лейаут в CSS: современный подход к верстке сеток 🌐

Грид-лейаут, или, как его называют на простом языке, гриды, — это один из наиболее продвинутых инструментов CSS, который позволяет создавать сложные сетки с минимальными усилиями. Если раньше для верстки требовалось много строк кода, то теперь все сводится к нескольким простым свойствам. В этом уроке мы подробно рассмотрим, как работает грид-лейаут, и чем он отличается от флекс-верстки.

### Гриды и флексы: разные подходы 🤔

Хотя гриды и флексы решают схожие задачи, они имеют разные подходы. Гриды представляют собой более современную технологию, но это не значит, что они взаимозаменяемы. На практике я часто комбинирую оба подхода, ведь в зависимости от конкретной задачи один из них может оказаться более удобным.

### Основные термины из мира гридов 📚

- **Грид-контейнер** — это элемент, к которому применено свойство `display` со значением `grid` или `inline-grid`.  
- **Грид-элементы** — это дочерние элементы грид-контейнера, на которые действуют правила грид-лейаута.  
- **Грид-линии** — горизонтальные и вертикальные линии, формирующие структуру сетки.  
- **Грид-ячейка** — пространство между соседствующими грид-линиями.  
- **Грид-полоса** — пространство, ограниченное двумя соседними горизонтальными или вертикальными грид-линиями.  
- **Грид-область** — пространство, ограниченное четырьмя грид-линиями.  

>[!info]  
>### Полезный совет 💡  
>Для лучшего понимания грид-сеток, используйте инструменты разработчика (DevTools) и вкладку layout. Включите отображение грид-контейнера, чтобы видеть грид-линии с порядковыми номерами.  

### Свойства грид-лейаута ⚙️

Для создания грид-сетки необходимо задать размеры колонок и строк. Это делается с помощью следующих свойств:

- **`grid-template-columns`** — задает количество и размеры колонок.  
- **`grid-template-rows`** — задает количество и размеры строк.  

Рассмотрим использование свойства `grid-template-columns`. Например, можно задать три колонки, каждая из которых имеет ширину, вычисляемую автоматически:

```css
.container {
    display: grid;
    grid-template-columns: auto auto auto;
}
```

Если необходимо использовать фиксированные единицы измерения, можно задать их в процентах или вьюпорт-единицах:

```css
.container {
    display: grid;
    grid-template-columns: 50% 50%;
}
```

### Именование грид-линий 📛

Можно также задавать имена для грид-линий, что значительно упростит понимание кода. Это делается следующим образом:

```css
.container {
    display: grid;
    grid-template-columns: [line1] 100px [line2] 1fr [line3];
}
```

Эти имена можно будет увидеть в DevTools, а также применять при позиционировании грид-элементов.

### Использование функции Repeat 🔄

Функция `repeat()` позволяет задавать повторяющиеся значения. Например:

```css
.container {
    display: grid;
    grid-template-columns: repeat(3, 150px);
}
```

Эта запись эквивалентна:

```css
.container {
    display: grid;
    grid-template-columns: 150px 150px 150px;
}
```

### Единица измерения fr: дробь пространства 📏

Новая единица измерения `fr` (fraction) позволяет делить пространство на равные части. Например, если задать:

```css
.container {
    display: grid;
    grid-template-columns: 1fr 1fr 50px;
}
```

Это означает, что первая и вторая колонки поделят оставшееся пространство, а третья колонка займет фиксированные 50 пикселей.

### Функция minmax 📏

Функция `minmax()` позволяет задать диапазон размеров для колонки:

```css
.container {
    display: grid;
    grid-template-columns: minmax(200px, 35%);
}
```

Это означает, что ширина колонки будет варьироваться от 200 пикселей до 35% ширины грид-контейнера.

### Задание высоты строк 🎚️

С помощью свойства `grid-template-rows` можно задать высоту строк аналогично тому, как мы делали это с колонками. Например:

```css
.container {
    display: grid;
    grid-template-rows: 40px 80px auto;
}
```

### Шаблоны областей grid-template-areas 🗺️

Еще одно интересное свойство — `grid-template-areas`, которое позволяет указывать шаблон сетки. В значении свойства через пробел в кавычках указываются строки с названиями областей:

```css
.container {
    display: grid;
    grid-template-areas: 
        "header header header"
        "sidebar content content"
        "footer footer footer";
}
```

После задания шаблона для грид-контейнера, дочерние элементы можно будет распределять по областям с помощью свойства `grid-area`.

### Промежутки между элементами 🌌

Свойства `row-gap`, `column-gap` и обобщенное `gap` также применимы для грид-контейнеров. Например:

```css
.container {
    display: grid;
    gap: 20px; /* Промежуток 20px между всеми элементами */
}
```

Если же необходимо задать разные значения для вертикальных и горизонтальных промежутков, можно сделать так:

```css
.container {
    display: grid;
    row-gap: 15px;
    column-gap: 10px;
}
```

Теперь вы готовы использовать грид-лейаут в своих проектах, создавая красивые и адаптивные сетки с легкостью!

---

## Свойства выравнивания в CSS Grid 🌐

Погружаясь в мир CSS Grid, мы сталкиваемся с мощными инструментами для выравнивания элементов. **Свойства `justify-content` и `align-items`** играют ключевую роль в этом процессе, позволяя задавать выравнивание как по горизонтали, так и по вертикали. По умолчанию оба свойства имеют значение **normal**, что может быть не всегда удобно.

### Горизонтальное выравнивание 🔄

Свойство `justify-content` предоставляет несколько значений для управления расположением элементов в грид-контейнере:

- **start**: элементы выравниваются по левой стороне контейнера.
- **end**: содержимое прижимается к правой стороне.
- **center**: элементы располагаются по центру.
- **stretch**: элементы растягиваются на всю ширину контейнера (по умолчанию).
- **space-between**: первая и последняя колонки находятся на краях, а промежуточные распределяются равномерно.
- **space-around**: промежутки между колонками равны, расстояние от краев до колонок — в два раза меньше.
- **space-evenly**: расстояние между колонками и от краев до колонок одинаковое.

Пример кода для использования `justify-content`:

```css
.container {
    display: grid;
    justify-content: space-between;
}
```

### Вертикальное выравнивание ⬆️

Свойство `align-items` позволяет выровнять элементы по вертикали:

- **normal**: элементы занимают высоту, указанную в `grid-template-rows`, или высоту их содержимого.
- **start**: элементы выравниваются по верху.
- **end**: элементы располагаются внизу.
- **center**: элементы выравниваются по центру.
- **stretch**: элементы растягиваются на всю высоту грид-ячейки.

Пример использования `align-items`:

```css
.container {
    display: grid;
    align-items: center;
}
```

### Сокращенное свойство для выравнивания 🛠️

Вы можете использовать обобщенное свойство `place-items`, которое объединяет `align-items` и `justify-content` в одно значение:

```css
.container {
    display: grid;
    place-items: center; /* Выровнять по центру и по вертикали, и по горизонтали */
}
```

### Позиционирование грид-элементов 📍

Каждый грид-контейнер имеет **грид-линии**, которые задают структуру сетки. Вы можете увидеть их в DevTools, перейдя на вкладку Layout и отметив нужный контейнер. Это поможет визуализировать, как располагаются элементы в сетке.

Представим, что у нас есть грид-контейнер с четырьмя элементами, который делится на три равные колонки и строки высотой 50 пикселей. Каждый элемент занимает свою ячейку, имея четкие границы. 

### Изменение размеров ячеек 📏

Допустим, мы хотим, чтобы третий элемент занимал два столбца и две строки. Для этого мы добавим класс **Big** и используем следующие свойства:

- **grid-column-start**: задает начало по горизонтали.
- **grid-column-end**: задает конец по горизонтали.
- **grid-row-start**: задает начало по вертикали.
- **grid-row-end**: задает конец по вертикали.

Пример кода:

```css
.big {
    grid-column-start: 2;
    grid-column-end: 4;
    grid-row-start: 1;
    grid-row-end: 3;
}
```

### Упрощение записи с использованием имен 🏷️

Вы можете дать удобные имена грид-линиям в свойствах `grid-template-columns` и использовать их в `grid-column` и `grid-row`. Это делает код более читаемым и управляемым.

Пример:

```css
.container {
    display: grid;
    grid-template-columns: [start] 1fr [line1] 1fr [line2] 1fr [end];
}

.item {
    grid-column: line1 / line2; /* Использование имен линий */
}
```

### Использование span для гибкости 🌌

Ключевое слово **span** позволяет элементу занимать несколько ячеек. Например, `grid-column: span 2;` займет два столбца. Это удобно, когда вы не хотите указывать точные номера линий.

### Растяжение на всю ширину 📏

Если нужно растянуть элемент на всю ширину, вы можете использовать значение (-1, 1), что автоматически растянет элемент на все колонки, независимо от их количества.

### Порядок элементов 🔀

Свойство `order` также применимо к грид-элементам, меняя их порядок. Например, значение -1 переместит элемент на верхнюю позицию, а 1 — на последнюю.

### Заключение 🎮

Для закрепления полученных знаний о грид-лейауте рекомендую попробовать браузерную игру **Grid Garden**. Она поможет отточить навыки работы с гридами через 28 увлекательных уровней.

В следующем уроке мы рассмотрим свойства переполнения, видимости и обрезки, которые также важны в работе с CSS.