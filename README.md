# Mobile OMS

**Mobile OMS** — учебный дипломный проект: мобильная система управления заказами для малого бизнеса.

Приложение предназначено для внутреннего использования сотрудниками и менеджерами. Оно позволяет работать с заказами, отслеживать их статусы, управлять товарами и взаимодействовать с backend API.

## О проекте

Цель проекта — разработать MVP мобильного приложения для управления заказами и каталогом товаров.

Проект демонстрирует:

* разработку кроссплатформенного мобильного приложения;
* проектирование REST API;
* работу с базой данных PostgreSQL;
* использование ORM Prisma;
* реализацию JWT-авторизации;
* базовую бизнес-логику для заказов, товаров и пользователей.

## Статус

Проект находится в стадии MVP / учебной разработки.

Реализована основная структура frontend и backend, модели данных, API для заказов и товаров, авторизация пользователей и базовая работа со статусами заказов.

## Функциональность

* Авторизация пользователей
* Базовая ролевая модель пользователей
* Просмотр списка заказов
* Создание нового заказа
* Просмотр деталей заказа
* Изменение статуса заказа
* Архивация заказов
* Управление товарами
* Создание, редактирование и удаление товаров
* Расчёт суммы заказа
* Хранение данных в PostgreSQL
* Взаимодействие мобильного приложения с backend API

## Технологический стек

### Frontend

* TypeScript
* React Native
* Expo
* Expo Router
* NativeWind
* Axios
* AsyncStorage

### Backend

* Node.js
* Express.js
* TypeScript
* Prisma ORM
* PostgreSQL
* JWT
* bcrypt
* CORS
* dotenv

## Структура проекта

```text
mobile-oms/
├── app/                 # Экраны мобильного приложения
├── assets/              # Статические ресурсы
├── components/          # UI-компоненты
├── contexts/            # React contexts
├── services/            # Сервисный слой для работы с API
├── backend/             # Backend API
│   ├── prisma/          # Prisma schema и миграции
│   └── src/
│       ├── middleware/  # Middleware авторизации
│       ├── routes/      # API routes
│       └── index.ts     # Точка входа backend-приложения
└── OMS.md               # План разработки проекта
```

## Модель данных

В проекте используются основные сущности:

### User

Пользователь системы.

Поля:

* `id`
* `username`
* `password`
* `role`
* `isActive`
* `createdAt`
* `updatedAt`

### Product

Товар в каталоге.

Поля:

* `id`
* `name`
* `price`
* `description`
* `createdAt`
* `updatedAt`

### Order

Заказ клиента.

Поля:

* `id`
* `displayId`
* `customerName`
* `customerPhone`
* `customerEmail`
* `status`
* `totalAmount`
* `note`
* `createdAt`
* `updatedAt`

### OrderItem

Позиция заказа.

Поля:

* `id`
* `orderId`
* `productId`
* `quantity`
* `priceAtPurchase`
* `createdAt`
* `updatedAt`

## Статусы заказов

В системе предусмотрены следующие статусы:

* `NEW` — новый заказ
* `PROCESSING` — заказ в обработке
* `COMPLETED` — заказ выполнен
* `CANCELLED` — заказ отменён
* `ARCHIVED` — заказ архивирован

## API

Backend предоставляет REST API для работы с мобильным приложением.

Основные группы endpoints:

```text
/api           # проверочный endpoint
/api/auth      # авторизация и управление пользователями
/api/products  # управление товарами
/api/orders    # управление заказами
```

### Примеры endpoints

```text
POST /api/auth/login
GET  /api/auth/me

GET    /api/products
POST   /api/products
GET    /api/products/:id
PUT    /api/products/:id
DELETE /api/products/:id

GET  /api/orders
POST /api/orders
GET  /api/orders/:id
PUT  /api/orders/:id/status
```

## Установка и запуск

### Требования

Перед запуском необходимо установить:

* Node.js
* npm
* PostgreSQL
* Expo Go на мобильное устройство или Android/iOS эмулятор

## Запуск backend

Перейдите в директорию backend:

```bash
cd backend
```

Установите зависимости:

```bash
npm install
```

Создайте файл `.env` в директории `backend`:

```env
DATABASE_URL="postgresql://postgres:password@localhost:5432/mobile_oms"
JWT_SECRET="your-secret-key"
PORT=3001
```

Примените миграции Prisma:

```bash
npx prisma migrate dev
```

Запустите backend в режиме разработки:

```bash
npm run dev
```

Backend будет доступен по адресу:

```text
http://localhost:3001
```

Проверочный endpoint:

```text
GET /api
```

## Запуск мобильного приложения

В корневой директории проекта установите зависимости:

```bash
npm install
```

Запустите Expo:

```bash
npm start
```

Запуск на Android:

```bash
npm run android
```

Запуск на iOS:

```bash
npm run ios
```

Запуск web-версии:

```bash
npm run web
```

## Что реализовано

* Спроектирована структура мобильного приложения
* Реализована навигация между экранами
* Создан backend API на Express.js
* Настроена работа с PostgreSQL через Prisma ORM
* Реализованы модели пользователей, товаров, заказов и позиций заказа
* Добавлена JWT-авторизация
* Реализована базовая ролевая модель пользователей
* Добавлена логика создания заказов и расчёта суммы
* Реализовано изменение статусов заказов
* Добавлен сервисный слой для взаимодействия frontend с backend

## Возможные доработки

* Добавить Docker Compose для backend и PostgreSQL
* Добавить полноценную валидацию форм на frontend
* Улучшить обработку ошибок
* Добавить unit-тесты и integration-тесты
* Добавить страницу аналитики по заказам
* Улучшить разграничение прав пользователей
* Добавить загрузку изображений товаров
* Добавить скриншоты интерфейса в README
* Подготовить production-сборку

## Автор

Максим Жикин
Студент направления «Программная инженерия» / «Информатика и вычислительная техника»
