# Привет! Я eclipse 👋

Изучаю Go и развиваюсь в backend-разработке. Мне нравится разбираться, как устроены сервисы внутри: работа с базами данных, обработка ошибок, тестирование и поведение системы при сбоях.

Сейчас собираю портфолио из проектов, в которых можно попробовать всё это на практике. Кроме Go, пишу на C++ и интересуюсь разработкой под Windows.

## С чем работаю

- **Языки:** Go, C++, TypeScript, JavaScript
- **Backend:** REST API, `net/http`, SQL, pgx
- **Frontend:** React, Vite
- **LLM:** Yandex AI Studio, Responses API, JSON Schema, RAG, embeddings
- **Базы данных и кеш:** PostgreSQL, pgvector, Redis
- **Разработка под Windows:** Win32 API, GDI, WIC
- **Инструменты:** Docker, Docker Compose, Git, GitHub Actions, CMake, MSVC
- **Тестирование:** Go `testing` и `httptest`, интеграционные тесты, проверка гонок, Playwright, CTest, ASan/UBSan

## Мои проекты

### 🔗 [LinkForge](https://github.com/eclipse-vlr/linkforge)

Сервис сокращения ссылок на Go. Создаёт короткие ссылки, перенаправляет по ним и считает переходы. В проекте использую PostgreSQL, кеш Redis, SQL-миграции, ограничение запросов и защиту создания ссылок через API-ключ. Логику ссылок, HTTP и работу с хранилищами разделил на пакеты.

Проверяю работу с настоящими PostgreSQL и Redis, отказ кеша и корректную остановку сервера. В CI есть тесты с проверкой гонок, поиск уязвимостей зависимостей и проверка Docker-образа. Через GitHub Actions готовлю сборки для Linux, Windows и macOS.

[Документация API](https://github.com/eclipse-vlr/linkforge/blob/master/docs/api.md) · [Сборка и тесты](https://github.com/eclipse-vlr/linkforge/actions/workflows/go.yml) · [Релиз v0.1.2](https://github.com/eclipse-vlr/linkforge/releases/tag/v0.1.2)

### 📨 [SupportFlow](https://github.com/eclipse-vlr/SupportFlow)

Локальное рабочее место поддержки на Go с Алисой AI. Модель определяет категорию и приоритет обращения, готовит краткое описание и черновик ответа. Оператор может поправить текст, подтвердить его и скопировать для отправки клиенту. Есть поиск обращений, оценка черновиков и закрытие решённых вопросов.

Интеграция с Yandex AI Studio через Responses API и JSON Schema. Для ответа подбираются статьи из локальной базы знаний; черновик проверяется на известные дефекты и при необходимости один раз переписывается моделью. Очередь хранится в PostgreSQL: есть фоновые обработчики, повторные попытки, история правок и защита от перезаписи из старой вкладки. Проверяю работу с настоящей БД и тестами с `-race`; результаты отдельной проверки модели сохраняю в JSON-отчётах.

[Как запустить](https://github.com/eclipse-vlr/SupportFlow#запуск) · [Проверка модели](https://github.com/eclipse-vlr/SupportFlow/blob/master/docs/evaluation.md)

### 🖥️ [PC Club Admin](https://github.com/eclipse-vlr/pc-club-admin)

Система для сотрудников компьютерного клуба. Помогает принимать и сдавать смены, проходить чек-листы, сверять кассу и сохранять историю действий. Проект вырос из реальных рабочих задач. Пока это тестовая версия, не готовая для настоящего учёта денег.

Backend написан на Go с PostgreSQL, интерфейс — на React и TypeScript. Есть роли сотрудников, CSV-выгрузки и заполнение Excel на Google Drive, проверенное на тестовой копии. В CI проверяю работу с БД, браузерные сценарии и восстановление резервной копии.

[Демонстрация](https://github.com/eclipse-vlr/pc-club-admin/blob/main/docs/demo.md) · [Сборка и тесты](https://github.com/eclipse-vlr/pc-club-admin/actions/workflows/ci.yml)

### 📄 [DocMind](https://github.com/eclipse-vlr/docmind)

Backend на Go для вопросов по документам. Загружает TXT, Markdown и PDF, извлекает текст в отдельном worker, разбивает его на фрагменты и ищет подходящий контекст через embeddings и pgvector. Ответ возвращается с проверенными ссылками на фрагменты и номерами страниц PDF.

Реализованы адаптеры Alice AI и embeddings Yandex AI Studio, локальный режим без внешних API, повторная индексация и восстановление обработки после сбоя. Проверяю транзакции, конкурентную обработку и источники ответов с настоящей БД PostgreSQL; API провайдера подменяется в тестах. Пока это локальный MVP без авторизации и OCR.

[Запуск и API](https://github.com/eclipse-vlr/docmind#запуск)

### 📋 [TaskFlow](https://github.com/eclipse-vlr/taskflow)

Учебный сервис фоновых задач на Go и PostgreSQL. HTTP API сохраняет задачи, ограниченный пул воркеров выполняет `sleep`, а планировщик назначает повторы и восстанавливает задачи после истечения lease. Есть ручной повтор неудавшихся задач и отмена ожидающих; устаревшая попытка не может перезаписать результат новой.

В CI запускаю интеграционные тесты с PostgreSQL и проверкой гонок на Go 1.26 и 1.27. Выполнение не гарантирует однократность; авторизации и отмены уже запущенных задач пока нет.

[Сборка и тесты](https://github.com/eclipse-vlr/taskflow/actions/workflows/ci.yml)

### 🎯 [TriggerLab](https://github.com/eclipse-vlr/TriggerLab)

Приложение на C++20 для тренировок в Kovaak’s и Aimlabs под Windows. Находит выбранный цвет возле прицела и выполняет клик. Ядро анализа отделено от Windows-интерфейса; сборка и тесты запускаются в GitHub Actions. Есть RGB/HSV, профили, проверка свежести кадров и восстановление повреждённых настроек. Переносимое ядро проверяю на Linux с ASan/UBSan, Windows-сборку — нативными тестами и проверкой готового ZIP.

[Релиз v0.4.5](https://github.com/eclipse-vlr/TriggerLab/releases/tag/v0.4.5) · [Сборка и тесты](https://github.com/eclipse-vlr/TriggerLab/actions/workflows/ci.yml)

### 🧩 [Алгоритмы на Go](https://github.com/eclipse-vlr/leetcode-go)

Решаю задачи с LeetCode, разбираю разные подходы и пишу тесты. Так лучше понимаю структуры данных и алгоритмы, которые пригодятся в backend-разработке.

## Что изучаю сейчас

Конкурентность в Go, архитектуру backend-сервисов, SQL и алгоритмы. Стараюсь закреплять теорию кодом, а не только читать о ней.

## Связаться со мной

Рассматриваю предложения на позицию **Junior Go Backend Developer**.

**Telegram:** [@eclipsevlr](https://t.me/eclipsevlr)
