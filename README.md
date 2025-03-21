# 📥 Импорт резюме в Битрикс24: Расширение для Chrome  
**Упрощение рекрутинга для HR-команд | 300+ установок**  
[![Chrome Extension](https://img.shields.io/badge/Chrome_Web_Store-4.5/5⭐-4285F4?logo=googlechrome&logoColor=white)](https://chromewebstore.google.com/detail/%D0%B8%D0%BC%D0%BF%D0%BE%D1%80%D1%82-%D1%80%D0%B5%D0%B7%D1%8E%D0%BC%D0%B5/mjepbnolegdpfonnhhjjjgffiidibbkc?pli=1)

## 📋 Обзор проекта  
"Импорт резюме в Битрикс24" — это расширение для Chrome, созданное для рекрутеров. Оно позволяет в один клик переносить резюме кандидатов с сайта HeadHunter (HH.ru) в систему Битрикс24, избавляя HR-специалистов от ручного ввода данных и экономя их время при обработке большого числа кандидатов.

## 🏗️ Архитектура системы  
Архитектура проекта объединяет браузерное расширение, серверную часть и внешние сервисы. Вот как это работает:

- **Активация расширения**:  
  Пользователь получает код из приложения "Интеграция HH.ru с Bitrix24" и использует его для активации расширения.

- **Авторизация**:  
  Расширение хранит данные авторизации в куках. Авторизация выполняется только тогда, когда расширение открыто поверх вкладки с резюме на HH.ru. Для этого используется API Chrome `chrome.tabs`, которое позволяет управлять вкладками и переносить куки авторизации из расширения в куки страниц HH.ru. Это необходимо, чтобы расширение могло взаимодействовать с HH.ru от имени пользователя и подтвердить успешность авторизации.

- **Встраивание кнопки**:  
  После успешной авторизации на страницах резюме HH.ru появляется кнопка "Импорт в Битрикс24".

- **Импорт резюме**:  
  При нажатии на кнопку расширение отправляет запрос на серверный эндпоинт, передавая данные резюме и код авторизации. Сервер, исходя из кода, обращается к базе данных, определяет, к какому порталу Bitrix24 принадлежит пользователь, и создает в этом портале сделку с данными кандидата.

### Схема архитектуры  
```bash
[Пользователь]
   │
   ▼
[Chrome Extension]◄──Код активации──►[Bitrix Integration App]
   │  ▲
   │  └──chrome.tabs API──►[Куки HH.ru]
   │
   ▼
[Сервис авторизации]──┐
   │                  │
   ▼                  ▼
[PostgreSQL]      [Bitrix24 API]
   │                     │
   └────────────Данные резюме────►[Сделка в Bitrix]
```

## 🛠️ Моя роль в проекте

Я разработал расширение "Импорт резюме в Битрикс24" с нуля, включая фронтенд и бэкенд — от идеи до публикации в Chrome Web Store. Это был мой первый опыт создания браузерного расширения, который помог мне освоить новые технологии.

### Что я делал

- **Изучение и анализ**:  
  Освоил Chrome Extensions API (`chrome.tabs`, `chrome.webNavigation`) и разобрался со структурой HH.ru для парсинга данных.

- **Архитектура**:  
  Спроектировал систему, объединяющую расширение и сервер для интеграции с Bitrix24 API, с авторизацией и управлением куками.

- **Фронтенд и бэкенд**:  
  - **Фронтенд**: Добавил кнопку "Импорт в Битрикс24" на HH.ru, используя JavaScript, HTML и CSS.  
  - **Бэкенд**: Создал сервис авторизации и эндпоинты для работы с Bitrix24.

- **Тестирование и публикация**:  
  Проверил работу на HH.ru, подготовил расширение для Chrome Web Store и написал документацию.

### Проблемы и решения

- Разобрался с управлением куками через Chrome API.  
- Адаптировал парсинг под изменения HH.ru с помощью гибких селекторов.

### Итог

Расширение запущено и помогает HR-командам экономить время и собирать базу резюме.

### Что я вынес

Научился создавать расширения, работать с API и управлять проектом от начала до конца, укрепив свои навыки разработчика.

## 💻 Технологический стек

**Языки & Фреймворки:**  
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)
![HTML](https://img.shields.io/badge/HTML-E34F26?logo=html5&logoColor=white)
![CSS](https://img.shields.io/badge/CSS-1572B6?logo=css3&logoColor=white)
![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-%23000000?logo=flask&logoColor=white)

**Базы данных:**  
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?logo=postgresql&logoColor=white)

**Инфраструктура:**  
![Chrome Extensions API](https://img.shields.io/badge/Chrome_Extensions_API-4285F4?logo=googlechrome&logoColor=white)

**Инструменты:**  
![Chrome Web Store](https://img.shields.io/badge/Chrome_Web_Store-4285F4?logo=googlechrome&logoColor=white)
![Bitrix24 API](https://img.shields.io/badge/Bitrix24_API-00A2FF?logo=bitrix&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?logo=github&logoColor=white)

## 🔗 Полезные ссылки
- [Расширение в Chrome Web Store](https://chromewebstore.google.com/detail/%D0%B8%D0%BC%D0%BF%D0%BE%D1%80%D1%82-%D1%80%D0%B5%D0%B7%D1%8E%D0%BC%D0%B5/mjepbnolegdpfonnhhjjjgffiidibbkc?pli=1)
- [Документация, скриншоты и примеры использования](https://docs.headtrix.21vek.it/)
