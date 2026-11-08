# Станислав · Junior Go Backend Developer

Разрабатываю учебные backend-сервисы на Go: HTTP API, хранение данных в PostgreSQL, фоновые задачи и проверки поведения при сбоях. Ищу удалённую или гибридную работу; мой часовой пояс — UTC+3.

**Telegram:** [@eclipsevlr](https://t.me/eclipsevlr)

## С чем работаю

Go, HTTP/REST, PostgreSQL, SQL, Docker и GitHub Actions — в проектах ниже.
Тестирование: модульные и интеграционные тесты, `go test -race`.
Redis и pgx использую в LinkForge; React/TypeScript — в PC Club Admin,
LLM-инструменты — в SupportFlow и DocMind. C++/Win32 — дополнительное направление в TriggerLab.

## Основные проекты

### [LinkForge](https://github.com/eclipse-vlr/linkforge)

Сервис на Go создаёт короткие ссылки, перенаправляет по ним и хранит счётчики переходов в PostgreSQL.
Redis кеширует исходные URL. При сбое кеша сервис читает их из PostgreSQL.
Есть интеграционные проверки с PostgreSQL/Redis, CI и готовые сборки.
[API](https://github.com/eclipse-vlr/linkforge/blob/master/docs/api.md) · [CI](https://github.com/eclipse-vlr/linkforge/actions/workflows/go.yml) · [Релиз](https://github.com/eclipse-vlr/linkforge/releases/latest)

### [PC Club Admin](https://github.com/eclipse-vlr/pc-club-admin)

Передача смен между сотрудниками компьютерного клуба: роли, чек-листы, замечания, тестовая сверка кассы и журнал действий.
Приём проверяет версию передачи, пересчёт и личный PIN; ответственность меняется в транзакции PostgreSQL.
Есть локальная демонстрация на вымышленных данных; реальный денежный учёт требует проверки правил и пилота.
Систему проверили администратор (приём смены) и управляющий (наблюдение из личного кабинета).
[Видео · 1:27](https://github.com/eclipse-vlr/pc-club-admin/blob/main/assets/demo/walkthrough.webm) · [Сценарий и скриншоты](https://github.com/eclipse-vlr/pc-club-admin/blob/main/docs/demo.md) · [CI](https://github.com/eclipse-vlr/pc-club-admin/actions/workflows/ci.yml)

### [SupportFlow](https://github.com/eclipse-vlr/SupportFlow)

Приложение для поддержки: категория обращения, подбор статьи и черновик ответа с проверкой оператором.
Очередь хранится в PostgreSQL; есть повторы и защита от перезаписи из старой вкладки.
Запуск по умолчанию — деморежим без платного API; интерфейс и результаты небольшой синтетической проверки модели доступны в репозитории.
[Запуск и превью](https://github.com/eclipse-vlr/SupportFlow#запуск) · [Оценка модели и ограничения](https://github.com/eclipse-vlr/SupportFlow/blob/master/docs/evaluation.md) · [CI](https://github.com/eclipse-vlr/SupportFlow/actions/workflows/ci.yml)

## Дополнительные проекты

- [TaskFlow](https://github.com/eclipse-vlr/taskflow) — учебная очередь на Go/PostgreSQL: lease, токен попытки, повторы и восстановление небольшими партиями. Обработчик `sleep`; выполнение может повторяться, отмена доступна только до начала работы.
- [DocMind](https://github.com/eclipse-vlr/docmind) — вопросы по TXT, Markdown и PDF, pgvector и проверка источников. Есть локальный режим без внешней модели; авторизации и OCR нет.
- [TriggerLab](https://github.com/eclipse-vlr/TriggerLab) — C++20/Win32: распознавание цвета для тренировок, захват свежих кадров и управление вводом. [Готовая Windows-сборка](https://github.com/eclipse-vlr/TriggerLab/releases/tag/v0.4.5).
- [Алгоритмы на Go](https://github.com/eclipse-vlr/leetcode-go) — дополнительная учебная практика.

## Что изучаю сейчас

Конкурентность в Go и SQL; закрепляю их в очередях задач и интеграционных тестах.
