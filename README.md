# 🔄 Импорт резюме в Битрикс24: Расширение для Chrome  
**Упрощение рекрутинга для HR-команд**  
[![Chrome Extension](https://img.shields.io/badge/Chrome_Web_Store-4.5/5⭐-4285F4?logo=googlechrome&logoColor=white)](https://chromewebstore.google.com/detail/%D0%B8%D0%BC%D0%BF%D0%BE%D1%80%D1%82-%D1%80%D0%B5%D0%B7%D1%8E%D0%BC%D0%B5/mjepbnolegdpfonnhhjjjgffiidibbkc?pli=1)

## 📋 Обзор проекта  
"Импорт резюме в Битрикс24" — это расширение для Chrome, созданное для рекрутеров. Оно позволяет в один клик переносить резюме кандидатов с сайта HeadHunter (HH.ru) в систему Битрикс24, избавляя HR-специалистов от ручного ввода данных и экономя их время при обработке большого числа кандидатов.

## 🏗️ Архитектура системы  
Архитектура проекта объединяет браузерное расширение, серверную часть и внешние сервисы. Вот как это работает:

- **Активация расширения**:  
  Пользователь получает код из приложения "Интеграция HH.ru с Bitrix24" и использует его для активации расширения. Этот код нужен для идентификации пользователя и дальнейшей работы с его порталом Bitrix24.

- **Авторизация**:  
  Расширение хранит данные авторизации в куках. Авторизация выполняется только тогда, когда расширение открыто поверх вкладки с резюме на HH.ru. Для этого используется API Chrome `chrome.tabs`, которое позволяет управлять вкладками и переносить куки авторизации из расширения в куки страниц HH.ru. Это необходимо, чтобы расширение могло взаимодействовать с HH.ru от имени пользователя и подтвердить успешность авторизации.

- **Встраивание кнопки**:  
  После успешной авторизации на страницах резюме HH.ru появляется кнопка "Импорт в Битрикс24". Она вмонтирована в интерфейс сайта и готова к использованию.

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
   │  ▲                  │
   └──┼─────────Данные резюме────►[Сделка в Bitrix]
```
