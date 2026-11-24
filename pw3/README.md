# Практична робота № 3 — Верстка простого сайту компанії «World Trivia»

## 1. Мета роботи

Закріпити навички створення багатосекційної вебсторінки на HTML5 і CSS3:
семантична розмітка, стилізація, Flexbox, адаптивний дизайн і доступність.

## 2. Короткі теоретичні відомості

Семантичні елементи HTML5 (`header`, `nav`, `main`, `section`, `footer`) описують
призначення блоків сторінки, що покращує доступність і індексацію. CSS
керує шрифтами, кольорами та відступами (`font-family`, `color`,
`background-color`, `margin`, `padding`). Flexbox (`display: flex`,
`justify-content`, `align-items`) зручно вирівнює елементи меню та карток.
Доступність передбачає `alt` для зображень, пов’язані `<label>` і `<input>`,
`aria-label` та прихований текст для скрінрідерів.

## 3. Суть завдання

Створити сайт компанії «World Trivia» з шапкою, навігацією, основним вмістом,
секціями Home, Trivia, Categories, Scores, Subscribe, Contact і футером.

## 4. Звіт по роботі

Структура проєкту:

```text
pw3/
├── index.html
├── css/style.css
├── assets/quiz.svg
├── assets/globe.svg
├── assets/trophy.svg
└── README.md
```

Реалізовано:

- семантичну структуру сторінки (`header`, `nav`, `main`, `section`, `footer`);
- меню з `list-style: none`, `padding: 0`, `display: flex`,
  `justify-content: space-around`, `margin: 10px`, білими посиланнями,
  `text-decoration: none` і підкресленням при наведенні;
- загальні стилі: Arial, sans-serif; 16px; `#333`; фон `#f4f4f4`;
  темна шапка `#333`;
- секцію Home з `<h1>`, абзацом, `padding: 20px`, `margin: 20px 0`,
  синім заголовком `#0654b3` і `line-height: 1.6`;
- секцію Trivia з трьома картками: Flexbox, `align-items: center`,
  зображення завширшки 150px, `margin-right: 20px`, `border-radius: 5px`;
- секцію Categories з гнучким списком посилань кольору `#0654b3` та hover-ефектом;
- таблицю Scores зі стовпцями Rank, Name, Score, Country, Category, Date,
  `width: 100%`, `border-collapse: collapse`, відступами 8px і темними заголовками;
- контактну форму з полями name, email, message, пов’язаними `<label>`,
  Flexbox (`flex-direction: column`), відступами 10px та hover-ефектом кнопки;
- секцію Subscribe з кнопкою «Puzzle of the Day», hover-ефектом і анімацією
  пульсації через `@keyframes`;
- доступність: `alt`, `aria-label`, `skip-link` і клас `sr-only`;
- адаптивність для планшетів і телефонів через медіазапити;
- повагу до налаштування `prefers-reduced-motion`.

Перевірки:

- HTML — [Nu Html Checker (W3C)](https://validator.w3.org/nu/): без помилок;
- CSS — [W3C CSS Validator](https://jigsaw.w3.org/css-validator/): 0 помилок, 0 попереджень;
- доступність — Lighthouse (axe): Accessibility 100, Best Practices 100, SEO 100;
- інтерактивні елементи (посилання, кнопки, поля форми) і відсутність
  горизонтального переповнення перевірено у браузері.

## 5. Відповіді на контрольні питання

1. **Які структурні елементи HTML5 використовуються?**  
   `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<aside>`, `<footer>`.

2. **Як реалізовано горизонтальне меню?**  
   Список `<ul>` із властивостями `display: flex` і `justify-content: space-around`.

3. **Які властивості Flexbox використовуються для вирівнювання?**  
   `display: flex`, `justify-content`, `align-items`, `flex-wrap`, `flex`.

4. **Вимоги до таблиці результатів?**  
   Ширина 100%, `border-collapse: collapse`, відступи в комірках 8px,
   темний фон заголовків і білий текст у них; стовпці Rank, Name, Score,
   Country, Category, Date.

5. **Які елементи використовуються для контактної форми?**  
   `<form>`, `<label>`, `<input type="text">`, `<input type="email">`,
   `<textarea>`, `<button type="submit">`.

6. **Як забезпечено доступність зображень і кнопок?**  
   Усі зображення мають описовий `alt`; кнопки мають видимий текст і `aria-label`,
   який його доповнює; форми мають пов’язані `<label>`; є `skip-link` і `sr-only`.

7. **Які етапи тестування виконано?**  
   Валідація HTML (W3C) і CSS (CSS Validator), перевірка доступності
   (Lighthouse/axe), перевірка посилань, зображень, форми та адаптивності.

8. **Оформлення звіту.**  
   Мета, теорія, суть завдання, звіт, відповіді на питання та висновок —
   у цьому файлі.

## 6. Висновок

Сайт «World Trivia» повністю відповідає вимогам практичної роботи № 3:
є семантична структура, стилі CSS3, Flexbox, адаптивність, доступність
і всі шість обов’язкових секцій. Робота розташована в репозиторії:
<https://github.com/okaliuzhniak2023-creator/TK_LABS2/tree/main/pw3>.
