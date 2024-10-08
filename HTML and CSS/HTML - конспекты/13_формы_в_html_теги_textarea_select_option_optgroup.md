## Многострочное поле ввода в HTML 📜

### Тег `textarea` 📝

На предыдущем уроке мы уже познакомились с различными вариациями тега `input`. Теперь пришло время обсудить тег `textarea`, который позволяет создавать многострочные поля ввода. Этот элемент является отличным решением, когда необходимо, чтобы пользователь мог вводить значительные объемы текста, например, комментарии или сообщения.

Важно отметить, что тег `textarea` в отличие от тега `input` является парным. Это значит, что у него есть открывающий (`<textarea>`) и закрывающий (`</textarea>`) теги. Если вы добавите текст между этими тегами, он будет отображаться в поле по умолчанию. Это работает аналогично атрибуту `value` в классическом `input`.

Вот простой пример использования тега `textarea`:

```html
<textarea>Введите ваш текст здесь...</textarea>
```

В этом примере, текст "Введите ваш текст здесь..." будет предзаполнен в многострочном поле ввода.

### Настройка размеров поля ввода 📏

По умолчанию браузер позволяет пользователю изменять ширину и высоту поля, просто потянув за правый нижний угол. Это довольно удобно, однако иногда может потребоваться зафиксировать размеры поля. В этом случае на помощь приходит CSS.

Чтобы задать фиксированные размеры для `textarea`, можно использовать свойства `width` и `height`. Например:

```css
textarea {
    width: 300px;  /* Фиксированная ширина */
    height: 150px; /* Фиксированная высота */
    resize: none;  /* Отключает возможность изменения размера */
}
```

С помощью свойства `resize` мы можем контролировать возможность изменения размера поля:

- `none` — отключает возможность изменения размеров,
- `both` — позволяет изменять размеры как по горизонтали, так и по вертикали,
- `horizontal` — разрешает изменение только по горизонтали,
- `vertical` — разрешает изменение только по вертикали.

>[!info]
>### Возможные варианты использования 🎨
>Тег `textarea` можно применять не только для комментариев, но и для ввода адресов, описаний и других многострочных данных. Это делает его универсальным инструментом для сбора информации от пользователей.

### Использование селекторов в HTML 🔍

Помимо `textarea`, в HTML есть и другие теги, такие как селекторы, которые позволяют пользователю выбирать значения из списка. Это может быть полезно для ограничения ввода и ускорения процесса выбора.

Селектор создается с помощью тега `select`, который также включает в себя несколько тегов `option`, представляющих доступные варианты. Пример использования селектора:

```html
<select>
    <option value="option1">Вариант 1</option>
    <option value="option2">Вариант 2</option>
    <option value="option3">Вариант 3</option>
</select>
```

В этом примере пользователь может выбрать один из трех вариантов. Селекторы часто используются в формах, чтобы упростить ввод данных и улучшить пользовательский опыт.

Всё это делает теги `textarea` и `select` важными инструментами для веб-разработчиков, позволяя создать интуитивно понятные и функциональные формы.

---

## Тег select и его возможности 🛠️

Тег `select` в HTML — это мощный инструмент для создания выпадающего списка, который позволяет пользователям выбрать один или несколько заранее определённых вариантов. Он обрамляет в себе дочерние элементы, теги `option`, каждый из которых соответствует конкретной опции ответа. 

### Основные элементы 🎯

Каждый тег `option` требует наличия атрибута **value**. Это значение необходимо серверу для определения выбора пользователя после отправки формы. Например, если у вас есть выбор стран, как это:

```html
<select name="country">
    <option value="us">США</option>
    <option value="ru">Россия</option>
    <option value="jp">Япония</option>
</select>
```

При отправке формы сервер получит значение `us`, `ru` или `jp`, в зависимости от выбора пользователя.

### Множественный выбор и атрибуты 🌟

Чтобы сделать выбор нескольких опций возможным, вы можете добавить атрибут `multiple` к тегу `select`. Это позволяет пользователю выбрать сразу несколько вариантов, удерживая при этом клавишу **Control (Ctrl)** на клавиатуре:

```html
<select name="cities" multiple>
    <option value="moscow">Москва</option>
    <option value="spb">Санкт-Петербург</option>
    <option value="kazan">Казань</option>
</select>
```

По умолчанию в одиночном селекте первой опцией будет выбрана первая опция. Если вам нужно изменить это поведение, добавьте атрибут **selected** к нужному тегу `option`:

```html
<option value="spb" selected>Санкт-Петербург</option>
```

### Как сделать пустым выбор по умолчанию? 🧐

Предположим, вы хотите, чтобы в выпадающем списке по умолчанию ничего не было выбрано. Для этого сначала убедитесь, что у вас нет атрибута **selected** у доступных опций и добавьте пустую опцию в начале:

```html
<select name="options">
    <option value="">Не выбрано</option>
    <option value="option1">Опция 1</option>
    <option value="option2">Опция 2</option>
</select>
```

Теперь, если вы добавите атрибут **required** к тегу `select`, браузер выдаст предупреждение, если пользователь попытается отправить форму, не выбрав ни одной опции.

### Добавление атрибута disabled 🚫

Чтобы уменьшить вероятность выбора опции "Не выбрано", вы можете добавить атрибут **disabled** к этой опции. Однако при этом следующая опция может стать выбранной по умолчанию:

```html
<option value="" disabled selected>Не выбрано</option>
```

Это может быть решено, добавив снова атрибут **selected**:

```html
<option value="" selected disabled>Не выбрано</option>
```

Теперь при загрузке страницы пользователь видит опцию "Не выбрано", и она недоступна для клика. Это отлично подходит для случаев, когда необходимо убедиться, что пользователь делает осознанный выбор.

### Стилизация тега select 🎨

Несмотря на всю полезность тега `select`, его стилизация в браузерах может быть ограничена. Мы не можем изменять внешний вид выпадающего списка или стрелочки, что часто разочаровывает дизайнеров. Обычно, чтобы создать кастомный `select`, используются готовые библиотеки или пишется собственный код с применением JavaScript.

С помощью кастомной разметки и JavaScript можно создать уникальный и интуитивно понятный интерфейс, что делает процесс выбора более интересным и удобным для пользователей.

> [!info]
> ### Зачем это нужно? 💡
> Кастомизация элементов управления, таких как `select`, помогает создать более привлекательный и адаптивный интерфейс, что увеличивает удобство использования и может повысить уровень взаимодействия с пользователем.

---

## Тег `<optgroup>` и его использование 🌟

Тег `<optgroup>` в HTML становится своего рода «помощником» при создании удобных и структурированных списков опций внутри элемента `<select>`. Он позволяет визуально группировать несколько элементов `<option>`, что значительно упрощает восприятие и выбор нужного значения пользователем.

### Как работает `<optgroup>`? 🛠️

При создании выпадающего списка с опциями, `<optgroup>` помогает сгруппировать их по определённым категориям. Например, если у вас есть список фруктов и овощей, вы можете использовать этот тег, чтобы выделить эти две группы.

Вот простой пример:

```html
<select>
  <optgroup label="Фрукты">
    <option value="apple">Яблоко</option>
    <option value="banana">Банан</option>
  </optgroup>
  <optgroup label="Овощи">
    <option value="carrot">Морковь</option>
    <option value="broccoli">Брокколи</option>
  </optgroup>
</select>
```

В этом примере видим, что мы создали две группы: **Фрукты** и **Овощи**. Каждая из них содержит свои опции. Пользователь, открывая этот список, сразу понимает, что он может выбирать между двумя категориями.

>[!info]
>### Зачем нужен тег `<optgroup>`? 🌿
>Использование `<optgroup>` делает ваши формы более организованными и понятными для пользователя. Это особенно полезно, когда у вас много опций.

### Стилизация элементов с помощью CSS 🎨

Хотя `<optgroup>` и `<option>` не поддерживают все стили CSS, вы все равно можете изменить внешний вид элемента `<select>`, чтобы сделать его более привлекательным и удобным для пользователя. Например, вы можете изменить шрифты, цвета и отступы:

```css
select {
  font-family: Arial, sans-serif;
  font-size: 16px;
  padding: 5px;
  border: 1px solid #ccc;
}

optgroup {
  font-weight: bold;
  color: #555;
}
```

Хотя сам тег `<optgroup>` не поддается детальной стилизации, его использование в структуре вашего HTML помогает организовать ваш контент более интуитивно.

>[!warning]
>Не забывайте, что не все браузеры могут одинаково интерпретировать стили для `<option>` и `<optgroup>`. Тестировать ваши формы на разных устройствах и браузерах — хорошая практика.

### Практические примеры использования 📚

Если вы разрабатываете форму для выбора страны и города, использование `<optgroup>` будет очень полезным. Например, вы можете сгруппировать страны по континентам:

```html
<select>
  <optgroup label="Европа">
    <option value="france">Франция</option>
    <option value="germany">Германия</option>
  </optgroup>
  <optgroup label="Азия">
    <option value="japan">Япония</option>
    <option value="china">Китай</option>
  </optgroup>
</select>
```

Такой подход не только упрощает выбор нужной опции, но и делает интерфейс более аккуратным и понятным для пользователя.

### Заключение

Хотя тег `<optgroup>` не так часто используется в реальной практике, его знание расширяет ваши навыки в веб-разработке и позволяет создавать более удобные интерфейсы. На следующем занятии мы посмотрим на другие теги и атрибуты форм, которые могут значительно улучшить пользовательский опыт!