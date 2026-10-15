---
last_updated: 2026-10-16
---

# Шаги реализации

Шаги 1–4.5: сбор требований, проверка инструментов, инициализация структуры, подготовка проекта.

---

## Шаг 1: Сбор требований

Задай вопросы последовательно. Зафиксируй ответы:

```json
{
  "name": "project-name",
  "purpose": "short description",
  "language": "typescript|python|java|rust|go",
  "interfaceType": "cli|gui|api-only",
  "guiFramework": "nextjs|tauri|pyqt6|streamlit|...",
  "cliFramework": "ink|rich|clap|cobra|...",
  "buildTool": "npm|uv|maven|cargo|go",
  "testFramework": "vitest|pytest|junit|...",
  "formatting": "prettier|ruff|spotless|...",
  "extraOptions": {
    "ci": false,
    "docker": false,
    "gitignore": true
  }
}
```

## Шаг 2: Проверка установленных инструментов

Проверь доступность ключевых инструментов:

```bash
# TypeScript
node --version && npm --version

# Python
python --version && uv --version || pip --version

# Java
java --version && mvn --version || gradle --version

# Rust
rustc --version && cargo --version

# Go
go version
```

**Если инструмент не установлен:**
1. Сообщи пользователю
2. Предложи инструкцию по установке
3. Предложи продолжить без него (с предупреждением) или отменить

## Шаг 3: Инициализация структуры проекта

**ВАЖНО:** Проект инициализируется **напрямую в текущем рабочем каталоге**. Не создавай отдельную поддиректорию с именем проекта (`project-name/`). Вся структура проекта разворачивается в корне.

Создай структуру на основе выбранного стека:

### TypeScript/Node.js (npm + vitest)

```
├── src/
│   ├── index.ts
│   └── ...
├── tests/
│   ├── unit/
│   └── integration/
├── package.json
├── tsconfig.json
├── vitest.config.ts
├── .eslintrc.json
├── .prettierrc
└── .gitignore
```

### Python (uv + pytest)

```
├── src/
│   └── {package_name}/
│       ├── __init__.py
│       └── ...
├── tests/
│   ├── unit/
│   └── integration/
├── pyproject.toml
├── .ruff.toml
└── .gitignore
```

### Java (Maven + JUnit 5)

```
├── src/
│   ├── main/
│   │   └── java/
│   └── test/
│       └── java/
├── pom.xml
└── .gitignore
```

### Rust (Cargo)

```
├── src/
│   └── lib.rs
│   └── main.rs (если binary)
├── tests/
├── Cargo.toml
└── .gitignore
```

### Go (go mod)

```
├── pkg/
├── internal/
├── cmd/
├── tests/
├── go.mod
├── go.sum
└── .gitignore
```

### CLI (ink / rich / clap / cobra)

```
├── src/
│   ├── index.{ext}
│   ├── cli.{ext}          # настройка CLI-фреймворка
│   └── commands/
│       └── ...
├── tests/
│   ├── unit/
│   └── integration/
├── package.json / pyproject.toml / ...
└── .gitignore
```

### GUI — Web (Next.js / Streamlit / Tauri)

```
├── src/
│   ├── components/
│   │   ├── ui/             # переиспользуемые UI-компоненты
│   │   └── ...
│   ├── pages/ или app/     # Next.js App Router
│   └── styles/
│       └── globals.css
├── public/
├── tests/
│   ├── unit/
│   └── e2e/
├── package.json / pyproject.toml / ...
└── .gitignore
```

### GUI — Desktop (PyQt6 / JavaFX / Tauri)

```
├── src/
│   ├── main/
│   │   └── ui/
│   │       ├── main_window.{ext}
│   │       └── components/
│   └── resources/          # иконки, стили
├── tests/
│   ├── unit/
│   └── integration/
└── ...
```

### API-only

```
├── src/
│   ├── api/
│   │   ├── routes/
│   │   └── middleware/
│   └── index.{ext}
├── tests/
│   ├── unit/
│   └── integration/
└── ...
```

**Правила:**
- Создай минимальный "hello, world" файл в `src/` — простейший код, выводящий `"hello, world"`
- Создай минимальный тестовый файл — тест, который проверяет вывод `"hello, world"`
- НЕ генерируй реальные компоненты приложения (ни UI, ни CLI-команды, ни API-роуты)
- Цель — только убедиться, что проект собирается, запускается и проходит тесты
- `.gitignore` — шаблонный (из существующего), потом расширим под стек

## Шаг 4: Формирование гайдлайнов

Создай два новых файла в `guidelines/`:

### `guidelines/build-run-tests-guidelines.md`

Смотри [`references/guideline-templates.md`](references/guideline-templates.md) — раздел **build-run-tests-guidelines.md**.

### `guidelines/coding-guidelines.md`

Смотри [`references/guideline-templates.md`](references/guideline-templates.md) — раздел **coding-guidelines.md**.

### `guidelines/ui-style-guidelines.md`

Смотри [`references/guideline-templates.md`](references/guideline-templates.md) — раздел **ui-style-guidelines.md**.

Создаётся **только если** `interfaceType` — `cli` или `gui`. Для `api-only` — пропускается.

## Шаг 4.5: Подготовка проекта к работе

**Проект должен быть готов к написанию спецификаций.** После создания структуры и гайдлайнов необходимо убедиться, что проект собирается, запускается и проходит тесты.

### 1. Установка зависимостей

Выполни команду установки зависимостей для выбранного стека:

```bash
# TypeScript/Node.js
npm install

# Python (uv)
uv sync

# Python (pip)
pip install -r requirements.txt

# Python (poetry)
poetry install

# Python (pdm)
pdm install

# Java (Maven)
mvn compile

# Java (Gradle)
gradle build -x test

# Rust
cargo build

# Go
go mod download
```

**Если установка завершилась ошибкой:**
1. Сообщи пользователю об ошибке
2. Предложи решение (проверить `package.json`/`pyproject.toml`/`pom.xml` и т.д.)
3. Предложи продолжить с предупреждением или отменить

### 1.5. Проверка и обновление зависимостей

После установки проверь вывод на предупреждения об устаревании, уязвимостях и deprecated-пакетах:

```bash
# TypeScript/Node.js
npm audit
npm outdated

# Python (pip)
pip list --outdated
pip-audit  # если установлен

# Java (Maven)
mvn versions:display-dependency-updates
mvn versions:display-plugin-updates

# Rust
cargo outdated

# Go
go list -m -u all
```

**Если найдены предупреждения:**

1. **Уязвимости (`npm audit`, `pip-audit`)** — критично. Предложи обновить:
   ```bash
   npm audit fix
   pip install --upgrade vulnerable-package
   ```
   Если `audit fix` меняет Major-версии — спроси пользователя перед применением.

2. **Устаревшие зависимости (`npm outdated`, `cargo outdated`, `go list -m -u all`)** — предложи обновить до последней совместимой версии:
   ```bash
   npm update
   cargo update
   go get -u ./...
   ```

3. **Deprecated-пакеты** — если пакет помечен как deprecated, предложи замену:
   - `moment` → `date-fns` или `dayjs`
   - `request` → `node-fetch` или `axios`
   - `uuid@v3` → `uuid@v9+`
   - И другие известные замены для выбранного стека

4. После обновления — **повтори установку и сборку**, чтобы убедиться, что ничего не сломалось.

**Если предупреждений нет** — переходи к шагу «Сборка проекта».

### 2. Сборка проекта

Выполни команду сборки:

```bash
# TypeScript/Node.js
npm run build

# Python (uv) — проверка типов
uv run mypy src || uv run ruff check src

# Java (Maven)
mvn compile

# Java (Gradle)
gradle compileJava

# Rust
cargo build

# Go
go build ./...
```

**Если сборка завершилась ошибкой:**
1. Сообщи пользователю об ошибке
2. Покажи вывод с ошибкой
3. Предложи исправить или продолжить с предупреждением

**Если сборка прошла, но в выводе есть предупреждения** (deprecated API, устаревшие опции компилятора, устаревшие зависимости):
1. Проанализируй предупреждения — это ошибки или просто warning?
2. Если warning от зависимостей — см. шаг 1.5 (обновить зависимости)
3. Если warning от компилятора/фреймворка — исправь или добавь в `coding-guidelines.md` как известное ограничение

### 3. Запуск приложения (опционально, для web/API)

Для проектов с серверной частью запусти dev-сервер и убедись, что он стартует:

```bash
# TypeScript (fastify/express)
npm run dev

# Python (fastapi)
uv run uvicorn src.main:app --reload
```

Проверь, что сервер запустился без ошибок (посмотри логи, не упал ли сразу).
После проверки останови сервер.

**Необязательно** для CLI-библиотек и утилит.

### 4. Запуск тестов

Выполни все тесты:

```bash
# TypeScript/Node.js
npm run test

# Python (pytest)
uv run pytest

# Java (Maven)
mvn test

# Java (Gradle)
gradle test

# Rust
cargo test

# Go
go test ./...
```

**Если тесты прошли** — проект готов к работе.
**Если тесты упали:**
1. Сообщи пользователю (покажи краткий вывод)
2. Если это заглушки — пропусти и предупреди
3. Если реальные тесты упали — предложи исправить или продолжить с предупреждением

### Итог шага

Проект считается **готовым к работе** только если:
- [x] Зависимости установлены без ошибок
- [x] Нет критических уязвимостей (`npm audit`, `pip-audit` — clean)
- [x] Устаревшие зависимости обновлены или заменены на актуальные аналоги
- [x] Сборка проходит (без критических warning)
- [x] Тесты проходят (или это заглушки)
- [x] (Опционально) Приложение запускается
