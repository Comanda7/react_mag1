<div align="center">

#  TechStore

### Интернет-магазин электроники

*Многостраничное приложение на чистом JavaScript  без фреймворков, без сборщиков*

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org/docs/Web/CSS)
[![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/docs/Web/JavaScript)
[![localStorage](https://img.shields.io/badge/Storage-localStorage-22c55e?style=for-the-badge)](https://developer.mozilla.org/docs/Web/API/Window/localStorage)

</div>

---

##  Содержание

- [О проекте](#-о-проекте)
- [Функционал](#-функционал)
- [Структура проекта](#-структура-проекта)
- [Описание файлов](#-описание-файлов)
  - [HTML страницы](#html-страницы)
  - [JavaScript модули](#javascript-модули)
  - [CSS стили](#css-стили)
- [Технологии](#-технологии)
- [Запуск](#-запуск)
- [Данные](#-данные)

---

##  О проекте

**TechStore**  полноценный интернет-магазин электроники, реализованный как многостраничное
приложение с разделением кода по модулям.

Все данные хранятся в `localStorage` браузера и синхронизируются между страницами в реальном
времени  без сервера, без базы данных, без сборки.

---

##  Функционал

| Раздел | Возможности |
|--------|-------------|
| **Каталог** | Фильтрация по категориям, поиск, сортировка по цене, пагинация (8 шт./стр.) |
| **Избранное** | Добавление / удаление, перенос в корзину |
| **Корзина** | Управление количеством (+/), удаление позиций, пересчёт суммы |
| **Заказ** | Оформление с формой доставки, сохранение в историю |
| **Профиль** | История заказов, список избранного, текущая корзина |
| **Аутентификация** | Регистрация / вход / выход через `localStorage` |
| **Админ-панель** | Статистика, таблицы товаров, заказов, категорий |

---

##  Структура проекта

```
TechStore/
│
├── 📄 HTML страницы
│   ├── index.html ──────────────── Каталог товаров (главная)
│   ├── favorites.html ──────────── Избранные товары
│   ├── cart.html ───────────────── Корзина покупок
│   ├── checkout.html ───────────── Оформление заказа
│   ├── profile.html ────────────── Личный кабинет
│   ├── about.html ──────────────── О нас
│   ├── contacts.html ───────────── Контакты
│   │
│   └── 🔐 Админ-панель
│       ├── admin.html ──────────── Общая статистика
│       ├── admin-products.html ─── Таблица всех товаров
│       ├── admin-orders.html ────── История заказов
│       └── admin-categories.html ── Статистика по категориям
│
├── 📜 JavaScript модули
│   ├── data.js ─────────────────── Данные + CRUD для localStorage
│   ├── common.js ───────────────── Шапка, бургер, счётчики
│   ├── catalog.js ──────────────── Фильтры, поиск, пагинация
│   ├── favorites.js ────────────── Логика избранного
│   ├── cart.js ─────────────────── Логика корзины
│   ├── checkout.js ─────────────── Оформление заказа
│   ├── profile.js ──────────────── Личный кабинет
│   ├── auth.js ─────────────────── Регистрация и авторизация
│   ├── admin.js ────────────────── Статистика админки
│   ├── admin-products.js ───────── Таблица товаров
│   ├── admin-orders.js ─────────── Таблица заказов
│   ├── admin-stock.js ──────────── Остатки на складе
│   └── admin-categories.js ─────── Таблицы по категориям
│
└── 🎨 CSS
    └── styles.css ──────────────── Все стили приложения
```

> **Кликните на название файла ниже, чтобы перейти к его описанию** 

---

##  Описание файлов

### HTML страницы

<details>
<summary><a name="file-index-html"></a><b> index.html</b>  Каталог товаров (главная страница)</summary>

---

Главная страница магазина. Отображает карточки товаров с фильтрацией, поиском и пагинацией.

**Подключает:** `catalog.js`, `common.js`

**Функции страницы:**
- Фильтрация по 3 категориям: телефоны, ноутбуки, аксессуары
- Живой поиск по названию в реальном времени
- Сортировка по цене (по возрастанию / убыванию)
- Пагинация  8 товаров на страницу
- Кнопки  и  прямо в карточке товара

---
</details>

<details>
<summary><a name="file-favorites-html"></a><b> favorites.html</b>  Список избранных товаров</summary>

---

Страница с товарами, добавленными в избранное.

**Подключает:** `favorites.js`, `common.js`

**Функции страницы:**
- Отображение сетки сохранённых товаров
- Удаление товара из избранного
- Быстрое добавление в корзину без перехода в каталог

---
</details>

<details>
<summary><a name="file-cart-html"></a><b> cart.html</b>  Корзина покупок</summary>

---

Страница корзины с таблицей выбранных товаров.

**Подключает:** `cart.js`, `common.js`

**Функции страницы:**
- Таблица товаров с изображениями и ценами
- Кнопки **+** / **** для изменения количества
- Удаление отдельных позиций
- Автоматический пересчёт итоговой суммы
- Кнопка Оформить заказ  переход на `checkout.html`

---
</details>

<details>
<summary><a name="file-checkout-html"></a><b> checkout.html</b>  Оформление заказа</summary>

---

Страница оформления заказа с формой данных доставки.

**Подключает:** `checkout.js`, `common.js`

**Функции страницы:**
- Форма с полями: имя, телефон, адрес доставки
- Просмотр итоговой суммы перед подтверждением
- Сохранение заказа в `localStorage`  переход в профиль

---
</details>

<details>
<summary><a name="file-profile-html"></a><b> profile.html</b>  Личный кабинет</summary>

---

Личный кабинет авторизованного пользователя.

**Подключает:** `profile.js`, `common.js`

**Функции страницы:**
- История всех оформленных заказов с детализацией по товарам
- Список товаров в избранном
- Текущее содержимое корзины
- Кнопка выхода из аккаунта

---
</details>

<details>
<summary><a name="file-about-html"></a><b> about.html</b>  О нас</summary>

---

Статичная информационная страница.

**Подключает:** `common.js`

Содержит: описание магазина, преимущества, статистику (товаров, брендов, клиентов).

---
</details>

<details>
<summary><a name="file-contacts-html"></a><b> contacts.html</b>  Контакты</summary>

---

Страница контактной информации.

**Подключает:** `common.js`

Содержит: адрес, телефон, email, форму обратной связи.

---
</details>

<details>
<summary><a name="file-admin-html"></a><b> admin.html</b>  Дашборд администратора</summary>

---

Главная страница панели администратора с общей статистикой.

**Подключает:** `admin.js`, `common.js`

**Отображает:**
- Всего товаров в каталоге
- Количество заказанных позиций
- Товаров в корзинах пользователей
- Товаров в избранном

---
</details>

<details>
<summary><a name="file-admin-products-html"></a><b> admin-products.html</b>  Управление товарами</summary>

---

Детальная таблица всех товаров магазина.

**Подключает:** `admin-products.js`, `common.js`

**Функции:** полная таблица с ID, названием, категорией, ценой, статистикой продаж.

---
</details>

<details>
<summary><a name="file-admin-orders-html"></a><b> admin-orders.html</b>  История заказов</summary>

---

Полная история заказов всех пользователей.

**Подключает:** `admin-orders.js`, `common.js`

**Функции:** таблица заказов с датой, пользователем, составом и суммой.

---
</details>

<details>
<summary><a name="file-admin-categories-html"></a><b> admin-categories.html</b>  Категории</summary>

---

Три отдельные таблицы по категориям товаров.

**Подключает:** `admin-categories.js`, `common.js`

**Разделы:**  Телефоны   Ноутбуки   Аксессуары

---
</details>

---

### JavaScript модули

<details>
<summary><a name="file-data-js"></a><b> data.js</b>  Центральный модуль данных</summary>

---

Ядро приложения. Содержит все данные и функции работы с `localStorage`.

**Данные:** массив из **60 товаров** (по 20 в каждой категории). Каждый товар: `id`, `name`, `category`, `price`, `image`, `stock`.

```js
// Данные товаров
const products = [
    // Сотовые телефоны (20 товаров)
    { id: 1,  name: 'iPhone 15 Pro',      category: 'phones',      price: 129990, image: '📱', stock: 15 },
    { id: 2,  name: 'Samsung Galaxy S24', category: 'phones',      price:  89990, image: '📱', stock: 20 },
    // ...
    { id: 21, name: 'MacBook Pro 16"',    category: 'laptops',     price: 249990, image: '💻', stock:  8 },
    // ...
    { id: 41, name: 'AirPods Pro 2',      category: 'accessories', price:  24990, image: '🎧', stock: 50 },
    // ...60 позиций
];

// CRUD для localStorage
function getCart()      { return JSON.parse(localStorage.getItem('cart')      || '[]') }
function saveCart(c)    { localStorage.setItem('cart', JSON.stringify(c)) }
function getFavorites() { return JSON.parse(localStorage.getItem('favorites') || '[]') }
function saveFavorites(f){ localStorage.setItem('favorites', JSON.stringify(f)) }
function getOrderHistory(){ return JSON.parse(localStorage.getItem('orderHistory') || '[]') }
function getProductStats(){ return JSON.parse(localStorage.getItem('productStats') || JSON.stringify(initProductStats())) }
function saveProductStats(s){ localStorage.setItem('productStats', JSON.stringify(s)) }
```

**CRUD-функции:**

| Функция | Описание |
|---------|----------|
| `getProducts()` | Получить все товары |
| `getCart()` / `saveCart()` | Читать / сохранять корзину |
| `getFavorites()` / `saveFavorites()` | Читать / сохранять избранное |
| `getOrderHistory()` / `saveOrder()` | Читать / добавить заказ |
| `getProductStats()` / `saveProductStats()` | Читать / сохранять статистику |

---
</details>

<details>
<summary><a name="file-common-js"></a><b> common.js</b>  Общий код для всех страниц</summary>

---

Подключается на каждой странице. Отвечает за общие UI-элементы: шапка, счётчики, бургер-меню, кнопка выхода.

```js
// Обновление счётчиков корзины и избранного в шапке
function updateBadges() {
    const cart      = getCart();
    const favorites = getFavorites();
    const cartCount = cart.reduce((sum, item) => sum + item.quantity, 0);

    const cartBadge = document.getElementById('cartBadge');
    const favBadge  = document.getElementById('favBadge');

    if (cartBadge) cartBadge.textContent = cartCount > 0 ? cartCount : '';
    if (favBadge)  favBadge.textContent  = favorites.length > 0 ? favorites.length : '';
}

// Создание карточки товара (используется в catalog.js, favorites.js)
function createProductCard(product) {
    const favorites = getFavorites();
    const isFav     = favorites.includes(product.id);
    return `
        <div class="product-card">
            <div class="product-image">${product.image}</div>
            <h3>${product.name}</h3>
            <p class="product-price">${product.price.toLocaleString('ru-RU')} ₽</p>
            <div class="product-actions">
                <button onclick="toggleFavorite(${product.id})">${isFav ? '❤️' : '🤍'}</button>
                <button onclick="addToCart(${product.id})">🛒 В корзину</button>
            </div>
        </div>
    `;
}
```

---
</details>

<details>
<summary><a name="file-catalog-js"></a><b> catalog.js</b>  Логика каталога</summary>

---

Вся бизнес-логика главной страницы: фильтрация, поиск, сортировка, пагинация (8 шт./стр.), рендер карточек через `innerHTML`.

```js
let currentPage     = 1;
const itemsPerPage  = 8;
let currentCategory = 'all';
let searchQuery     = '';
let sortOrder       = '';

function getFilteredProducts() {
    let filtered = products;
    if (currentCategory !== 'all')
        filtered = filtered.filter(p => p.category === currentCategory);
    if (searchQuery)
        filtered = filtered.filter(p => p.name.toLowerCase().includes(searchQuery.toLowerCase()));
    if (sortOrder === 'asc')  filtered = [...filtered].sort((a, b) => a.price - b.price);
    if (sortOrder === 'desc') filtered = [...filtered].sort((a, b) => b.price - a.price);
    return filtered;
}

function renderProducts() {
    const filtered   = getFilteredProducts();
    const totalPages = Math.ceil(filtered.length / itemsPerPage);
    const start      = (currentPage - 1) * itemsPerPage;
    const pageItems  = filtered.slice(start, start + itemsPerPage);

    document.getElementById('productsGrid').innerHTML =
        pageItems.map(p => createProductCard(p)).join('');
    renderPagination(totalPages);
}

function renderPagination(totalPages) {
    const el = document.getElementById('pagination');
    if (totalPages <= 1) { el.innerHTML = ''; return; }
    el.innerHTML = `
        <button ${currentPage===1?'disabled':''} onclick="goToPage(${currentPage-1})">&lt;</button>
        <button class="active">${currentPage} / ${totalPages}</button>
        <button ${currentPage===totalPages?'disabled':''} onclick="goToPage(${currentPage+1})">&gt;</button>
    `;
}
```

---
</details>

<details>
<summary><a name="file-auth-js"></a><b> auth.js</b>  Аутентификация</summary>

---

Полная система авторизации через `localStorage`. Инжектирует модальное окно входа/регистрации в DOM.

```js
;(function () {
  function getUsers() { return JSON.parse(localStorage.getItem('auth_users') || '[]') }
  function getUser()  { return JSON.parse(localStorage.getItem('auth_user')  || 'null') }
  function saveUser(u){ localStorage.setItem('auth_user', JSON.stringify(u)) }

  function authLogin(email, password) {
    const found = getUsers().find(u => u.email === email && u.password === password)
    if (!found) return 'Неверный email или пароль'
    saveUser(found)
    return null
  }

  function authRegister(name, email, password) {
    const users = getUsers()
    if (users.find(u => u.email === email)) return 'Этот email уже зарегистрирован'
    const newUser = { id: Date.now(), name, email, password }
    users.push(newUser)
    localStorage.setItem('auth_users', JSON.stringify(users))
    saveUser(newUser)
    return null
  }

  function authLogout() { localStorage.removeItem('auth_user') }

  // Модальное окно вставляется в body через innerHTML
  // Кнопка «Войти» / имя пользователя добавляются в шапку
})()
```

---
</details>

<details>
<summary><a name="file-cart-js"></a><b> cart.js</b>  Логика корзины</summary>

---

Управление содержимым корзины: рендер таблицы, кнопки `+`/`−`, удаление, пересчёт итога.

```js
function updateQuantity(productId, delta) {
    let cart = getCart();
    const item = cart.find(i => i.id === productId);
    if (item) {
        item.quantity += delta;
        if (item.quantity <= 0) cart = cart.filter(i => i.id !== productId);
        saveCart(cart);
        renderCart();
        updateBadges();
    }
}

function renderCart() {
    const cart     = getCart();
    const tbody    = document.getElementById('cartTableBody');
    const emptyMsg = document.getElementById('emptyCart');

    if (!cart.length) {
        emptyMsg.style.display = 'block';
        return;
    }
    tbody.innerHTML = cart.map((item, i) => {
        const p   = products.find(p => p.id === item.id);
        const sum = p.price * item.quantity;
        return `<tr>
            <td>${i+1}</td><td>${p.name}</td>
            <td>${p.price.toLocaleString('ru-RU')} ₽</td>
            <td>
                <button onclick="updateQuantity(${p.id},-1)">−</button>
                <span>${item.quantity}</span>
                <button onclick="updateQuantity(${p.id},+1)">+</button>
            </td>
            <td>${sum.toLocaleString('ru-RU')} ₽</td>
            <td><button onclick="removeFromCart(${p.id})">🗑️</button></td>
        </tr>`;
    }).join('');
    document.querySelector('.cart-total').textContent =
        'Итого: ' + calculateTotal().toLocaleString('ru-RU') + ' ₽';
}
```

---
</details>

<details>
<summary><a name="file-favorites-js"></a><b> favorites.js</b>  Логика избранного</summary>

---

Отображает сетку товаров из избранного. При пустом списке — заглушка. Использует `createProductCard` из `common.js`.

```js
function renderFavorites() {
    const favorites        = getFavorites();
    const favoriteProducts = products.filter(p => favorites.includes(p.id));
    const grid             = document.getElementById('favoritesGrid');
    const emptyMsg         = document.getElementById('emptyFavorites');

    if (!favoriteProducts.length) {
        grid.innerHTML     = '';
        emptyMsg.style.display = 'block';
        return;
    }
    emptyMsg.style.display = 'none';
    grid.innerHTML = favoriteProducts.map(p => createProductCard(p)).join('');
}

document.addEventListener('DOMContentLoaded', renderFavorites);
```

---
</details>

<details>
<summary><a name="file-checkout-js"></a><b> checkout.js</b>  Оформление заказа</summary>

---

Отображает сводку корзины, маску телефона, обработку формы. После отправки — сохраняет заказ в `localStorage`, очищает корзину.

```js
function handleCheckout(e) {
    e.preventDefault();
    const formData = new FormData(e.target);
    const cart     = getCart();

    const order = {
        id:      Date.now(),
        date:    new Date().toLocaleDateString('ru-RU'),
        status:  'Новый',
        name:    formData.get('name'),
        phone:   formData.get('phone'),
        address: formData.get('address'),
        items:   cart.map(item => {
            const p = products.find(p => p.id === item.id);
            return { id: p.id, name: p.name, image: p.image, price: p.price, quantity: item.quantity };
        }),
        total: calculateTotal(),
    };

    // Сохранение в историю заказов
    const orders = getOrderHistory();
    orders.push(order);
    localStorage.setItem('orderHistory', JSON.stringify(orders));

    // Очистка корзины
    saveCart([]);
    updateBadges();

    window.location.href = 'profile.html';
}

// Маска для поля телефона: +7 (XXX) XXX-XX-XX
function formatPhoneNumber(input) {
    let v = input.value.replace(/\D/g, '');
    if (v[0] === '8') v = '7' + v.slice(1);
    if (v[0] !== '7') v = '7' + v;
    let fmt = '+7';
    if (v.length > 1) fmt += ' (' + v.slice(1, 4);
    if (v.length >= 5) fmt += ') ' + v.slice(4, 7);
    if (v.length >= 8) fmt += '-' + v.slice(7, 9);
    if (v.length >= 10) fmt += '-' + v.slice(9, 11);
    input.value = fmt;
}
```

---
</details>

<details>
<summary><a name="file-profile-js"></a><b> profile.js</b>  Личный кабинет</summary>

---

Отображает данные пользователя, историю заказов с таблицами по каждому заказу, текущее избранное и корзину.

```js
function renderOrderHistory() {
    const orders      = getOrderHistory();
    const container   = document.getElementById('orderHistory');
    if (!orders.length) {
        container.innerHTML = '<p class="empty-message">История заказов пуста</p>';
        return;
    }
    container.innerHTML = [...orders].reverse().map(order => `
        <div class="order-item">
            <div class="order-header">
                <h4>Заказ #${order.id}</h4>
                <span class="order-date">${order.date}</span>
                <span class="order-status ${getStatusClass(order.status)}">${order.status || 'Новый'}</span>
            </div>
            <table class="order-table">
                <thead><tr><th>№</th><th>Товар</th><th>Цена</th><th>Кол-во</th><th>Сумма</th></tr></thead>
                <tbody>
                    ${order.items.map((item, i) => `
                        <tr>
                            <td>${i+1}</td>
                            <td>${item.image} ${item.name}</td>
                            <td>${item.price.toLocaleString('ru-RU')} ₽</td>
                            <td>${item.quantity}</td>
                            <td>${(item.price*item.quantity).toLocaleString('ru-RU')} ₽</td>
                        </tr>
                    `).join('')}
                </tbody>
            </table>
            <div class="order-total">Итого: <strong>${order.total.toLocaleString('ru-RU')} ₽</strong></div>
        </div>
    `).join('');
}
```

---
</details>

<details>
<summary><a name="file-admin-js"></a><b> admin.js / admin-*.js</b>  Скрипты администратора</summary>

---

Пять отдельных скриптов для страниц администратора. Каждый читает данные из `localStorage` и рендерит HTML-таблицы.

| Файл | Страница |
|------|----------|
| `admin.js` | Сводная статистика |
| `admin-products.js` | Таблица всех товаров |
| `admin-orders.js` | Таблица заказов |
| `admin-stock.js` | Остатки на складе |
| `admin-categories.js` | Таблицы по категориям |

```js
// admin.js — сводная статистика
function renderAdminStats() {
    const stats   = getProductStats();
    const orders  = JSON.parse(localStorage.getItem('orderHistory') || '[]');

    let totalOrdered = 0, totalPurchased = 0, totalInCart = 0, totalInFavorites = 0;

    orders.forEach(order => {
        const status = order.status || 'Новый';
        order.items.forEach(item => {
            if (status === 'Новый' || status === 'В обработке')     totalOrdered   += item.quantity;
            if (status === 'Подтверждён' || status === 'Доставлен') totalPurchased += item.quantity;
        });
    });
    Object.values(stats).forEach(s => {
        totalInCart      += s.inCart      || 0;
        totalInFavorites += s.inFavorites || 0;
    });

    document.getElementById('totalProducts').textContent    = products.length;
    document.getElementById('totalOrdered').textContent     = totalOrdered;
    document.getElementById('totalPurchased').textContent   = totalPurchased;
    document.getElementById('totalInCart').textContent      = totalInCart;
    document.getElementById('totalInFavorites').textContent = totalInFavorites;
}

// admin-products.js — таблица товаров
function renderProductsTable() {
    const rows = products.map((p, i) => `
        <tr>
            <td>${i+1}</td><td>${p.image}</td><td>${p.name}</td>
            <td>${p.category}</td>
            <td>${p.price.toLocaleString('ru-RU')} ₽</td>
            <td>${p.stock}</td>
        </tr>
    `).join('');
    document.getElementById('productsTableBody').innerHTML = rows;
}
```

---
</details>

---

### CSS стили

<details>
<summary><a name="file-styles-css"></a><b> styles.css</b>  Единый файл стилей</summary>

---

Один CSS-файл для всего приложения (~800 строк). Mobile-first, breakpoint 768px.

```css
/* CSS-переменные */
:root {
    --primary:   #3b82f6;
    --success:   #10b981;
    --danger:    #ef4444;
    --bg:        #f9fafb;
    --card-bg:   #ffffff;
    --text:      #111827;
    --text2:     #6b7280;
    --border:    #e5e7eb;
    --shadow:    0 1px 3px rgba(0,0,0,.1);
}

/* Карточка товара */
.product-card {
    background:    var(--card-bg);
    border-radius: 12px;
    border:        1px solid var(--border);
    padding:       1rem;
    transition:    transform .2s, box-shadow .2s;
}
.product-card:hover {
    transform:  translateY(-4px);
    box-shadow: 0 8px 24px rgba(0,0,0,.12);
}

/* Кнопки */
.btn            { padding: .5rem 1rem; border-radius: 8px; cursor: pointer; transition: opacity .2s; }
.btn-primary    { background: var(--primary); color: #fff; }
.btn-primary:hover { opacity: .85; }

/* Адаптивная сетка */
.product-grid {
    display:               grid;
    grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
    gap:                   1.25rem;
}
@media (max-width: 768px) {
    .product-grid { grid-template-columns: 1fr 1fr; }
    .navbar       { display: none; }
    .burger       { display: block; }
}
```

---
</details>

---

##  Технологии

| Технология | Версия | Использование |
|-----------|--------|---------------|
| HTML5 |  | Структура всех страниц |
| CSS3 |  | Стили, анимации, адаптивность |
| JavaScript | ES6+ | Вся логика приложения |
| localStorage API |  | Хранение данных без сервера |

---

##  Запуск

Никаких зависимостей и сборки не требуется.

```bash
# 1. Клонировать репозиторий
git clone https://github.com/Comanda7/react_mag1.git

# 2. Открыть папку
cd react_mag1
```

Затем открыть `index.html` в любом браузере  и готово.

> Навигация между страницами работает через обычные HTML-ссылки (`<a href="...">`).

---

##  Данные

- **60 товаров**  по 20 в каждой из трёх категорий
- Данные генерируются при первом запуске и сохраняются в `localStorage`
- Полная синхронизация между всеми страницами без сервера
- Данные сохраняются между сессиями браузера

---

<div align="center">

**TechStore** &nbsp;&nbsp; 2025 &nbsp;&nbsp; Vanilla JS

</div>