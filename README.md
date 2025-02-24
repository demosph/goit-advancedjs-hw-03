# Завдання. Пошук зображень

Створи застосунок пошуку зображень за ключовим словом і їх перегляду в галереї.
Додай оформлення елементів інтерфейсу згідно з макетом.

## Форма пошуку

Форма пошуку міститься в HTML-документі. Користувач буде вводити рядок для
пошуку в текстове поле, а за сабмітом форми необхідно виконувати HTTP-запит із
цим пошуковим рядком.

При натисканні на кнопку відправки форми, додайте перевірку вмісту текстового
поля на наявність порожнього рядка, щоб користувач не міг відправити запит, якщо
поле пошуку порожнє.

## HTTP-запити

Для бекенду використовуй публічний API сервіс Pixabay. Зареєструйся, отримай
свій унікальний ключ доступу і ознайомся з документацією.

Список параметрів рядка запиту, які тобі обов'язково необхідно вказати:

- `key` — твій унікальний ключ доступу до API.
- `q` — слово для пошуку. Те, що буде вводити користувач.
- `image_type` — тип зображення. Потрібні тільки фотографії, тому постав
  значення photo.
- `orientation` — орієнтація фотографії. Постав значення `horizontal`.
- `safesearch` — фільтр за віком. Постав значення `true`.

У відповіді буде об’єкт із декількома властивостями, в одному з яких буде масив
зображень, що задовольнили критерії параметрів запиту.

Якщо бекенд повертає порожній масив, значить, нічого підходящого не було
знайдено. У такому разі показуй повідомлення з текстом
`"Sorry, there are no images matching your search query. Please try again!"`.
Для повідомлень використовуй бібліотеку iziToast.

## Галерея і картки зображень

Елемент галереї (список однотипних елементів) міститься в HTML-документі, і в
нього необхідно додавати розмітку карток зображень після HTTP-запитів.

Кожне зображення описується об'єктом, з якого тобі цікаві тільки такі
властивості:

- `webformatURL` — посилання на маленьке зображення для списку карток у галереї
- `largeImageURL` — посилання на велике зображення для модального вікна
- `tags` — рядок з описом зображення. Підійде для атрибута `alt`
- `likes` — кількість вподобайок
- `views` — кількість переглядів
- `comments` — кількість коментарів
- `downloads` — кількість завантажень

Перед пошуком за новим ключовим словом необхідно повністю очищати вміст галереї,
щоб не змішувати результати запитів.

## Бібліотека `SimpleLightbox`

Додай відображення великої версії зображення з бібліотекою SimpleLightbox для
повноцінної галереї.

- У розмітці необхідно буде обгорнути кожну картку зображення в посилання, як
  зазначено в документації в секції «Markup».
- Бібліотека містить метод `[refresh()]`
  `(<https://github.com/andreknieriem/simplelightbox#public-methods>)`, який
  обов'язково потрібно викликати щоразу після додавання нових елементів до
  галереї.
