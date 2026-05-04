# STRIZH

QA Test Case Generator - AI assistant for QA teams.

Generates manual test cases from Confluence specifications and pushes them to Jira Xray Data Center.

---

## Repositories

| Repository | Description |
|------------|-------------|
| [strizh-auth-service](../strizh-auth-service) | Authentication, users, JWT, profile |
| [strizh-generation-service](../strizh-generation-service) | Test case generation, LLM orchestration, history |
| [strizh-integration-service](../strizh-integration-service) | Confluence + Jira + Xray adapters |
| [strizh-admin-service](../strizh-admin-service) | Templates, prompts, settings, logs |
| [strizh-infra](../strizh-infra) | Docker Compose, K8s manifests, nginx |
| strizh-frontend *(soon)* | React + TypeScript UI |

---

## Tech Stack

**Backend:** Python 3.14 / FastAPI / MongoDB / Redis

**Frontend:** React 18 / TypeScript / Vite

**Infrastructure:** Docker / nginx / k3d / K8s
