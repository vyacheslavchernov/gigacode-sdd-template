---
last_updated: 2026-10-16
---

# Примеры

## Пример 1: TypeScript + GUI проект

```
Пользователь: инициализируй проект для MCP-сервера веб-скрейпинга

Агент:
1. Название: webfetch
2. Назначение: MCP-сервер для извлечения и структурирования контента из веб-страниц
3. Язык: TypeScript/Node.js
4. Интерфейс: GUI — Web
5. GUI-фреймворк: Next.js + shadcn/ui + Tailwind CSS
6. Инструменты: npm, vitest, prettier, eslint
7. Дополнительно: CI/CD, .gitignore

→ Создана структура проекта в корне (Next.js App Router)
→ Сгенерированы гайдлайны + ui-style-guidelines.md
→ Создан "hello, world" + тест для проверки сборки
→ Проект подготовлен: `npm install` ✓, `npm run build` ✓, `npm run test` ✓
→ Обновлены README.md и GIGACODE.md
```

## Пример 2: Python + CLI проект

```
Пользователь: инициализируй проект для REST API сервиса

Агент:
1. Название: api-gateway
2. Назначение: API-шлюз для маршрутизации запросов к микросервисам
3. Язык: Python
4. Интерфейс: CLI
5. CLI-фреймворк: rich + click
6. Инструменты: uv, pytest, ruff
7. Дополнительно: Dockerfile

→ Создана структура проекта в корне (CLI-скелет)
→ Сгенерированы гайдлайны + ui-style-guidelines.md (CLI-секция)
→ Создан "hello, world" + тест для проверки сборки
→ Проект подготовлен: `uv sync` ✓, `uv run pytest` ✓
→ Обновлены README.md и GIGACODE.md
```

## Пример 3: Java + API-only проект

```
Пользователь: инициализируй проект для системы управления задачами

Агент:
1. Название: task-manager
2. Назначение: REST API для создания и отслеживания задач
3. Язык: Java 21
4. Интерфейс: API-only
5. Инструменты: Maven, JUnit 5, Spring Boot
6. Дополнительно: Dockerfile, CI/CD

→ Создана структура проекта в корне (Spring Boot скелет)
→ Сгенерированы гайдлайны (без ui-style-guidelines — API-only)
→ Создан "hello, world" + тест для проверки сборки
→ Проект подготовлен: `mvn compile` ✓, `mvn test` ✓
→ Обновлены README.md и GIGACODE.md
```
