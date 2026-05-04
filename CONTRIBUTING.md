# Правила разработки СТРИЖ

## Структура веток

```
main  -- production-ready. Только через PR из dev. Прямые пуши запрещены.
  dev -- интеграционная. Только через PR из feature/fix/chore/refactor.
        feature/<название>
        fix/<название>
        chore/<название>
        refactor/<название>
```

Работа всегда ведётся в отдельной ветке, созданной от `dev`.

---

## Начало работы над задачей

```bash
git checkout dev
git pull origin dev
git checkout -b feature/название-задачи
```

---

## Именование веток

| Префикс | Когда использовать |
|---------|-------------------|
| `feature/` | Новая функциональность |
| `fix/` | Исправление бага |
| `chore/` | Инфра, зависимости, конфиги |
| `refactor/` | Рефакторинг без изменения поведения |
| `docs/` | Документация |

Примеры:
```
feature/auth-login-endpoint
feature/confluence-page-fetch
fix/jwt-token-expiry
chore/docker-compose-setup
```

---

## Коммиты - Conventional Commits

Формат: `<тип>(<область>): <что сделано>`

| Тип | Когда |
|-----|-------|
| `feat` | Новая функциональность |
| `fix` | Исправление бага |
| `chore` | Инфра, зависимости |
| `refactor` | Рефакторинг |
| `test` | Тесты |
| `docs` | Документация |

Примеры:
```
feat(auth): добавить эндпоинт JWT-логина
fix(generation): обработать пустой ответ LLM
chore(infra): добавить MongoDB и Redis в docker-compose
test(auth): юнит-тесты для bcrypt-хеширования
```

---

## Правила Pull Request

1. PR открывается из твоей ветки в **`dev`** (не в `main`)
2. Название PR - в формате Conventional Commits
3. Описание: что сделано и как проверить
4. CI должен пройти: lint + type check + tests + docker build
5. Нужен **1 аппрув** от второго разработчика
6. Merge: **Squash and merge**
7. После мержа - ветку удалить

---

## Merge dev в main

- Только через PR с аппрувом
- **Merge commit** (не squash) - сохраняет историю
- Только после тестирования на dev-окружении
- Ставим тег версии: `v0.1.0`, `v0.2.0`, ...

```bash
git tag v0.1.0
git push origin v0.1.0
```

---

## Hotfix - срочный фикс в продакшне

```bash
git checkout main
git pull origin main
git checkout -b hotfix/описание-проблемы

# Фиксишь, коммитишь, пушишь
git push origin hotfix/описание-проблемы

# Открываешь PR в main (с аппрувом)
# После мержа в main - ОБЯЗАТЕЛЬНО мержишь и в dev
```

---

## Что запрещено

- Прямой пуш в `main` или `dev`
- `git push --force` в `main` или `dev`
- Мерж без аппрува
- Мерж при упавшем CI
- Коммит секретов, паролей, `.env` файлов
