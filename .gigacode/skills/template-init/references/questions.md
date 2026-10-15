---
last_updated: 2026-10-16
---

# Вопросы и инструменты

Уточняющие вопросы для инициализации проекта. Задаются **последовательно**, по одному.

## Вопрос 1: Название проекта

```
Как называется проект?
```

- Ожидаемый формат: kebab-case или camelCase (например: `webfetch`, `my-api-service`)
- Если не указано — предложи сгенерировать на основе описания

## Вопрос 2: Назначение проекта

```
Кратко опиши назначение проекта — что он делает и какую проблему решает?

- 1-2 предложения
- Описывай ценность, а не технологии
```

## Вопрос 3: Язык программирования

```
На каком языке будет писаться проект?
```

Предложи варианты:

| Язык | Версия |
|---|---|
| TypeScript/Node.js | 20+ (LTS) |
| Python | 3.12+ |
| Java | 21+ (LTS) |
| Rust | 1.75+ |
| Go | 1.22+ |
| C++ | 23 (C++23) |
| C# | 12+ / .NET 8+ (LTS) |

Пользователь может предложить и свой вариант.

## Вопрос 4: Инструменты сборки

На основе выбранного языка предложи подходящие инструменты:

### TypeScript/Node.js

- Сборка: `npm` (Recommended), `yarn`, `pnpm`
- Тесты: `vitest` (Recommended), `jest`
- Форматирование: `prettier` + `eslint`
- HTTP-фреймворк (если web): `express`, `fastify`, `hono`

### Python

- Сборка: `uv` (Recommended), `pip`, `poetry`, `pdm`
- Тесты: `pytest` (Recommended)
- Форматирование: `ruff` (Recommended), `black`
- HTTP-фреймворк (если web): `fastapi` (Recommended), `flask`

### Java

- Сборка: `Maven` (Recommended), `Gradle`
- Тесты: `JUnit 5` + `Mockito`
- Форматирование: `spotless`
- Фреймворк (если web): `Spring Boot` (Recommended)

### Rust

- Сборка: `Cargo` (встроен)
- Тесты: `cargo test` (встроен)
- Форматирование: `rustfmt` + `clippy`

### Go

- Сборка: `go mod` (встроен)
- Тесты: `go test` (встроен)
- Форматирование: `gofmt` (встроен)
- HTTP-фреймворк (если web): стандартная библиотека (Recommended)

### C++

- Сборка: CMake (Recommended), Ninja, MSBuild (для Visual Studio)
- Тесты: Google Test (Recommended), Catch2, doctest
- Форматирование: clang-format + clang-tidy

### C#

- Сборка: MSBuild (встроен в .NET SDK), dotnet build (Recommended), NUKE (для сложных сценариев)
- Тесты: xUnit (Recommended), NUnit, MSTest
- Форматирование: .editorconfig + dotnet format (Recommended), StyleCop.Analyzers

Если пользователь указал собственный вариант языка для проекта, собери список рекомендованных инструментов для этого языка по аналогии с вышеприведёнными.

## Вопрос 5: Тип интерфейса

```
Какой интерфейс будет у проекта?
```

Предложи варианты:

| Тип | Описание |
|---|---|
| **CLI** (Recommended) | Командная строка, терминал |
| **GUI** | Графический интерфейс, десктоп или веб |
| **API-only** | Только HTTP API, без UI |

На основе выбора предложи типовые решения:

### CLI

- TypeScript/Node.js: `ink` (React in terminal, Recommended), `commander`, `clack`
- Python: `rich` (Recommended), `click`, `typer`, `textual` (для rich-TUI)
- Java: `clap4j`, `prompt4j`
- Rust: `clap` + `indicatif` (Recommended), `ratatui` (для TUI)
- Go: `cobra`, `bubbletea` (для TUI, Recommended)

### GUI — Web (TypeScript/Node.js)

- Фреймворк: `Next.js` (Recommended), `Vite + React`
- UI-кит: `shadcn/ui` + `Tailwind CSS` (Recommended), `MUI`, `Chakra UI`
- Стиль: минималистичный, современный, чистый

### GUI — Web (Python)

- Фреймворк: `Streamlit` (Recommended для data-приложений), `FastAPI + HTMX`, `Gradio`
- Альтернатива: `Reflex` (Python-native GUI)

### GUI — Desktop (TypeScript/Node.js)

- `Tauri` (Recommended, Rust backend + web frontend)
- `Electron` (тяжёлый, но мощный)

### GUI — Desktop (Python)

- `PyQt6` / `PySide6` (Recommended)
- `CustomTkinter` (лёгкий)
- `Flet` (Flutter для Python)

### GUI — Desktop (Java)

- `JavaFX` (Recommended)
- `Swing` (legacy)

### API-only

- Просто HTTP-сервер без UI-слоя

Если пользователь указал собственный вариант языка для проекта, собери список типовых решений для этого языка с учётом выбранных инструментов.

## Вопрос 6: Дополнительные опции (опционально)

```
Нужно ли добавить:
- CI/CD конфигурацию (GitHub Actions)?
- Dockerfile?
- .gitignore для выбранного стека?
```
