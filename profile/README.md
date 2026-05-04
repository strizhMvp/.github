# СТРИЖ

**AI-ассистент для QA-команд** — генерирует manual-тест-кейсы по спецификациям из Confluence и пушит их в Jira Xray Data Center.

---

## Репозитории

| Репозиторий | Описание |
|-------------|----------|
| [strizh-auth-service](../strizh-auth-service) | Аутентификация, пользователи, JWT, профиль |
| [strizh-generation-service](../strizh-generation-service) | Генерация тест-кейсов, LLM-оркестрация, история |
| [strizh-integration-service](../strizh-integration-service) | Confluence + Jira + Xray адаптеры |
| [strizh-admin-service](../strizh-admin-service) | Шаблоны, промпты, настройки, логи |
| [strizh-infra](../strizh-infra) | Docker Compose, K8s манифесты, nginx |
| strizh-frontend *(скоро)* | React + TypeScript UI |

---

## Технологический стек

**Backend:** Python 3.14 / FastAPI / MongoDB / Redis

**Frontend:** React 18 / TypeScript / Vite

**Инфраструктура:** Docker / nginx / k3d / K8s
