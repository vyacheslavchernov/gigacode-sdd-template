---
last_updated: 2026-10-14
scope: skill-reference
---

# Examples — Spec Edit

See [SKILL.md](../SKILL.md) -- overview and scenarios.

Примеры хороших и плохих спецификаций.

> **Полные примеры** — в [`guidelines/specification-guidelines.md`](../../../guidelines/specification-guidelines.md) разделы 7.1-7.3.

## Хорошие примеры

### Пример: Обновление существующей спецификации

```yaml
---
last_updated: 2026-10-14
scope: specification
status: DRAFT
---
```

```markdown
# http-cookies-spec — Cookie Management

## Purpose

Управление cookie в HTTP-клиенте. Изолированное хранилище cookie для каждого экземпляра клиента.

## Changes from previous version

### Добавлено
- Метод `getAllCookies()` — возвращает immutable map всех cookie
- Метод `clearCookies(String host)` — очистка cookie для хоста
- `CookiesPolicies` enum с тремя значениями вместо двух

### Изменено
- `getCookies()` теперь возвращает `List<HttpCookie>` вместо `Map`
- Cookie-хранилище использует thread-safe коллекцию

### Удалено
- Метод `getCookie(String name)` — использовать `getCookies()` вместо него

## Preconditions

- HTTP-клиент инициализирован с валидной конфигурацией
- Cookie-политика разрешает приём cookie (по умолчанию `ACCEPT_ALL`)

## Inputs

### CookiesPolicies

| Значение | Описание |
|---|---|
| `ACCEPT_ALL` | Принимать все cookie от серверов |
| `ACCEPT_NONE` | Отклонять все cookie |
| `ACCEPT_ORIGINAL_SERVER` | Принимать только cookie от исходного сервера |

### HttpClient методы

| Метод | Возвращаемый тип | Описание |
|---|---|---|
| `getCookies(String host)` | `List<HttpCookie>` | Cookies для конкретного хоста |
| `getAllCookies()` | `Map<String, List<HttpCookie>>` | Все cookies (immutable map) |
| `clearCookies(String host)` | `void` | Очистить cookies для хоста |

## Behavior

### Сохранение cookie

1. При получении ответа с `Set-Cookie` заголовком:
    - Проверяется cookie-политика
    - Если политика разрешает — cookie сохраняется в хранилище
    - Хранилище: карта по хосту

2. При отправке запроса:
    - Cookies для хоста добавляются как `Cookie` header
    - Если cookies нет — header не добавляется

### Получение cookie

1. `getCookies(host)` — возвращает копию списка cookie для хоста
2. `getAllCookies()` — возвращает **immutable** map
3. Если host не найден — возвращается пустой список / пустая карта

### Очистка cookie

1. `clearCookies(host)` — удаляет все cookies для хоста
2. Если host не найден — исключение не бросается, операция игнорируется

## Business rules

- Каждый клиент имеет **полностью изолированное** хранилище cookie
- Глобальный `CookieHandler` не используется
- `getAllCookies()` всегда возвращает immutable map
- Cookie привязаны к хосту, не к пути

## Errors

| Ситуация | Исключение |
|---|---|
| `host == null` в `getCookies()` | `HttpClientInvalidRequestException` |
| `host == null` в `clearCookies()` | `HttpClientInvalidRequestException` |

## Acceptance criteria

- [ ] `getCookies(host)` возвращает cookies для хоста
- [ ] `getCookies(null)` бросает `HttpClientInvalidRequestException`
- [ ] `getAllCookies()` возвращает immutable map
- [ ] `clearCookies(host)` удаляет cookies для хоста
- [ ] `clearCookies(null)` бросает `HttpClientInvalidRequestException`
- [ ] `clearCookies(unknown-host)` не бросает исключение
- [ ] Cookie изолированы между клиентами
- [ ] Чтение cookie thread-safe
```

**Почему хорошо:**
- Есть секция `Changes from previous version` с чётким описанием изменений
- Статус `DRAFT` — изменения существенные
- Нет деталей реализации (не указано, какая именно thread-safe коллекция используется)
- Все критерии проверяемы

## Плохие примеры

Полные примеры плохих спецификаций — в [`guidelines/specification-guidelines.md`](../../../guidelines/specification-guidelines.md) разделы 7.2-7.3.

**Основные типы ошибок:**

1. **Слишком общая спецификация** — нет чёткого описания поведения, входных данных, ошибок, business rules
2. **Описание реализации вместо поведения** — упоминает классы, методы, фреймворки вместо описания что делает система
3. **Неоднозначные формулировки** — `обычно`, `как правило`, `по возможности`, `примерно`
4. **Детали реализации в примерах** — конкретные классы Java, API вместо абстрактного поведения
