---
last_updated: 2026-10-15
scope: -referense
---

# Examples — Doc Sync

Примеры «до» и «после» обновления документации.

См. [`SKILL.md`](../SKILL.md) — обзор и сценарии.

---

## Пример 1: Обновление документа модуля

**Контекст:** В модуль `http-client` добавлен новый пакет `impl/retries` с классом `RetryPolicy`.

### До

```yaml
---
last_updated: 2026-10-10
scope: module
---
```

# HTTP Client Starter

Spring Boot starter для HTTP-клиента...

## Пакеты

- [`config`](../packages/http/config.md) — автоконфигурация фреймворка
- [`impl`](../packages/http/impl.md) — основные реализации

## Зависимости

- **Compile**: `http-client-lib`, `logger-lib`

---

### После

```yaml
---
last_updated: 2026-10-15
scope: module
---
```

# HTTP Client Starter

Spring Boot starter для HTTP-клиента...

## Пакеты

- [`config`](../packages/http/config.md) — автоконфигурация фреймворка, `HttpClientBuilder`, `HttpClientConfig`
- [`impl`](../packages/http/impl.md) — основные реализации: `HttpClient`, `HttpClientImpl`
- [`impl/retries`](../packages/http/impl/retries.md) — политика повторных попыток, `RetryPolicy`

## Зависимости

- **Compile**: `http-client-lib`, `logger-lib`, `retry-lib`

---

## Пример 2: Обновление GIGACODE.md

**Контекст:** Добавлен новый скилл `doc-sync`.

### До

```markdown
## Доступные скиллы

| Скилл | Назначение |
|---|---|
| `spec-edit` | Создание и обновление спецификаций |
| `spec-impl` | Реализация кода по спецификации |
```

### После

```markdown
## Доступные скиллы

| Скилл | Назначение |
|---|---|
| `doc-sync` | Обновление документации проекта |
| `spec-edit` | Создание и обновление спецификаций |
| `spec-impl` | Реализация кода по спецификации |
```

---

## Пример 3: Обновление документа пакета

**Контекст:** В пакет добавлен новый публичный метод `executeAsync()` в классе `HttpClientImpl`.

### До

```yaml
---
last_updated: 2026-10-08
scope: package
---
```

# ru.vych.http.impl

Основные реализации HTTP-клиента.

## Публичные классы

### `HttpClientImpl`

Реализация поверх встроенного HTTP-клиента. Поддерживает GET/POST.

---

### После

```yaml
---
last_updated: 2026-10-15
scope: package
---
```

# ru.vych.http.impl

Основные реализации HTTP-клиента.

## Публичные классы

### `HttpClientImpl`

Реализация поверх встроенного HTTP-клиента. Поддерживает GET/POST, асинхронные запросы через `executeAsync()`, кастомные хедеры, cookie-политики, редиректы. UUID-трейсинг для каждого запроса.

---

## Общие правила

1. **Обновляй `last_updated`** при любом изменении
2. **Минимальные изменения** — не переписывай документ целиком, только затронутые части
3. **Сохраняй стиль** — язык, форматирование, структура заголовков
4. **Проверяй кросс-ссылки** — после изменений убедись, что все ссылки корректны

> **Детали:** [`documentation-guidelines.md §5`](../../guidelines/documentation-guidelines.md#5-stil-napisaniya)
