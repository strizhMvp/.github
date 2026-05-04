# СТРИЖ — QA Test Case Generator

**AI-ассистент для QA-команд.** Принимает ссылку на страницу Confluence, генерирует manual-тест-кейсы через LLM и пушит их напрямую в Jira Xray Data Center.

---

## Что умеет

- Парсит спецификации из **Confluence DC** по URL
- Генерирует тест-кейсы через **LLM** (Qwen, OpenAI-совместимый API) с потоковым выводом
- Пушит результаты в **Jira Xray DC** одним кликом — с выбором папки Test Repository
- Inline-редактирование любого поля перед отправкой
- Настраиваемые шаблоны с кастомными полями — через админ-панель
- Логи взаимодействий с LLM, аудит, история генераций

---

## Архитектура

Проект разбит на независимые микросервисы:

| Сервис | Зона ответственности |
|--------|----------------------|
| [strizh-auth-service](https://github.com/strizhMvp/strizh-auth-service) | Аутентификация, JWT, роли, профиль пользователя |
| [strizh-generation-service](https://github.com/strizhMvp/strizh-generation-service) | Генерация тест-кейсов, LLM-оркестрация, SSE-стриминг |
| [strizh-integration-service](https://github.com/strizhMvp/strizh-integration-service) | Адаптеры к Confluence DC, Jira DC, Xray DC |
| [strizh-admin-service](https://github.com/strizhMvp/strizh-admin-service) | Шаблоны, промпты, настройки LLM, логи |
| [strizh-infra](https://github.com/strizhMvp/strizh-infra) | Docker Compose, K8s-манифесты, nginx, seed-скрипты |
| strizh-frontend *(в разработке)* | React 18 + TypeScript UI |

---

## Технологический стек

**Backend:** Python 3.14 / FastAPI / MongoDB 7 / Redis 7

**Frontend:** React 18 / TypeScript / Vite / TanStack

**Инфраструктура:** Docker / nginx / k3d / Kubernetes

**Интеграции:** Confluence DC / Jira DC / Xray DC / OpenAI-compatible LLM API

---

## Разработка

Правила веток, коммитов и PR: [CONTRIBUTING.md](https://github.com/strizhMvp/.github/blob/main/CONTRIBUTING.md)
