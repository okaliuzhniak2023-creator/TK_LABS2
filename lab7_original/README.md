# Лабораторна робота №7

**Тема:** Використання CSS Flexbox, Grid Layout, transitions та animations для верстки сторінки новин

**Варіант:** 3 — `header#featured_container`

## Мета роботи

Закріпити навички створення адаптивної верстки веб-сторінок із використанням Flexbox, Grid Layout і медіа-запитів. На прикладі головної сторінки сайту <https://lpnu.ua/> проаналізувати принципи реалізації адаптивного макета та відтворити фрагмент сторінки — блок новин.

## Завдання

1. Дослідити в Chrome DevTools структуру головної сторінки <https://lpnu.ua/>.
2. Зверстати блок `header#featured_container` (3-й варіант), використовуючи **Flexbox**.
3. Зверстати блок `main` із блоком «Новини університету» (`div.main-container`), використовуючи **CSS Grid**.
4. Додати медіа-запити для трьох брейкпоінтів:
   - Mobile — до `767px` — 1 колонка;
   - Tablet — `768px–1023px` — 2 колонки;
   - Desktop — `1024px` і більше — 4 колонки.
5. Перевірити адаптивність у браузері.
6. Додати посилання на `lab7/index.html` у меню `ip_labs/index.html`.
7. Оформити звіт і відповісти на питання вихідного контролю.

## Що зроблено

Створено сторінку `lab7/index.html` із фрагментом головної сторінки Львівської політехніки:

- `header#featured_container` — чотири featured-новини з зображеннями, градієнтним затемненням, заголовками та hover-ефектами. Картки розташовані **флекс-контейнером** (`.featured-flex`), тому простір між ними розподіляється автоматично, а кількість колонок змінюється на трьох брейкпоінтах.
- `main.main-container` — блок «Новини університету» з 12 новинами. Сітка реалізована через `display: grid` і `grid-template-columns`, кількість колонок — 1 / 2 / 4 залежно від ширини екрана.
- Додано **transitions**: зміна прозорості зображень, зникнення градієнта `shadow_featured`, зміна кольору заголовків, підняття картки новини.
- Додано **animations**: плавна поява карток `fade-in-up` з каскадною затримкою для featured-блоку.
- Усі зображення збережено локально в `lab7/images/`, щоб сторінка не залежала від стороннього сайту.
- У `ip_labs/index.html` додано пункт меню «Лабораторна робота №7».

## Структура

```text
lab7/
├── index.html
├── css/
│   └── styles.css
├── images/
│   ├── featured-rector-report.jpg
│   ├── featured-institutes.jpg
│   ├── featured-excursion.jpg
│   ├── featured-rankings.jpg
│   ├── news-1.jpg … news-12.jpg
└── README.md
```

## Ключові фрагменти реалізації

### Flexbox для `header#featured_container`

```css
.featured-flex {
    display: flex;
    flex-wrap: wrap;
    align-items: stretch;
    gap: 2.5rem;
}

.featured-card {
    flex: 1 1 100%;          /* mobile — 1 колонка */
    min-width: 0;
}

@media (min-width: 768px) and (max-width: 1023px) {
    .featured-card {
        flex-basis: calc(50% - 1.25rem);   /* tablet — 2 колонки */
    }
}

@media (min-width: 1024px) {
    .featured-card {
        flex-basis: calc(25% - 1.875rem);  /* desktop — 4 колонки */
    }
}
```

### Grid для сітки новин

```css
.news-grid {
    display: grid;
    grid-template-columns: 1fr;            /* mobile — 1 колонка */
    gap: 3rem;
}

@media (min-width: 768px) and (max-width: 1023px) {
    .news-grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));   /* tablet */
    }
}

@media (min-width: 1024px) {
    .news-grid {
        grid-template-columns: repeat(4, minmax(0, 1fr));   /* desktop */
    }
}
```

### Transitions та animations

```css
.featured-card img {
    opacity: 0.85;
    transition: opacity 1s ease-out;
}

.shadow_featured {
    transition: opacity 2s ease-out;
}

#featured_container h2 span {
    transition: background-color 2s ease-out;
}

.news-card > a {
    transition: transform 0.35s ease, box-shadow 0.35s ease;
}

@keyframes fade-in-up {
    from { opacity: 0; transform: translateY(18px); }
    to   { opacity: 1; transform: translateY(0); }
}
```

## Брейкпоінти

| Пристрій | Ширина екрана | Колонок у header | Колонок у новинах |
|---|---|---|---|
| Mobile | до `767px` | 1 | 1 |
| Tablet | `768px–1023px` | 2 | 2 |
| Desktop | `1024px` і більше | 4 | 4 |

## Git

```bash
git checkout -b lab7
git add lab7 ip_labs/index.html
git commit -m "lab7: featured container with flexbox and news grid with CSS Grid"
git checkout master
git merge lab7
git push origin master
git push origin lab7
```

## Відповіді на питання вихідного контролю

**4.1. Які властивості CSS Flexbox використали в роботі?**

`display: flex`, `flex-wrap: wrap`, `flex: 1 1 100%`, `flex-basis`, `align-items: stretch`, `align-items: flex-end`, `gap`, а також `min-width: 0` для коректного стискання флекс-елементів. Вони використані для розташування карток `header#featured_container` у 1, 2 або 4 колонки та для вирівнювання заголовка в нижній частині картки.

**4.2. Яким чином реалізовано сітку новин на сторінці https://lpnu.ua/? Чим відрізняється від Вашої реалізації?**

На оригінальному сайті сітка новин реалізована засобами **Bootstrap 3 Grid**: контейнер `.container`, рядки `.row` і колонки `.col-12 .col-sm-6 .col-md-3`, які використовують `float: left` та відсоткові ширини. У моїй реалізації використано сучасний **CSS Grid Layout**: `display: grid`, `grid-template-columns: repeat(4, minmax(0, 1fr))`, `gap`. Це дає чистішу розмітку без float і clearfix, простіше керування відступами та точніше адаптивне перемикання кількості колонок через медіа-запити.

**4.3. Які брейкпоінти екрану додали на сторінці?**

Три брейкпоінти:

- `@media (max-width: 767px)` — Mobile, 1 колонка;
- `@media (min-width: 768px) and (max-width: 1023px)` — Tablet, 2 колонки;
- `@media (min-width: 1024px)` — Desktop, 4 колонки.

Додатково `@media (min-width: 1200px)` збільшує розміри заголовків для великих екранів, як на оригінальному сайті.

**4.4. Які властивості CSS модуля Grid Layout використали в роботі?**

`display: grid`, `grid-template-columns`, `repeat()`, `minmax()`, `1fr`, `gap`. Також для розміщення карток використано природний автоматичний потік сітки; за потреби можна було б застосувати `grid-column`, `grid-row` і `grid-template-areas`.

## Висновок

У ході лабораторної роботи досліджено структуру головної сторінки <https://lpnu.ua/> у Chrome DevTools і відтворено фрагмент сторінки: блок `header#featured_container` та блок «Новини університету». Для header застосовано Flexbox, для новин — CSS Grid Layout. Додано три адаптивні брейкпоінти (1, 2 і 4 колонки), а також transitions та CSS-анімації для hover-ефектів і плавної появи карток. Сторінка коректно відображається на мобільних пристроях, планшетах і настільних комп'ютерах та візуально відповідає оригінальному блоку новин Львівської політехніки.
