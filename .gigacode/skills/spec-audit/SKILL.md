---
last_updated: 2026-10-14
name: spec-audit
description: Аудит спецификаций — проверка соответствия между кодом, спецификациями, тестами и документацией. Триггеры "аудит спецификаций", "spec audit", "проверь соответствие спецификации", "аудит модуля {название}". Проверяет код ↔ спецификация, тесты ↔ спецификация, документация ↔ код + тесты.
---

# Spec Audit

Аудит соответствия между спецификациями, кодом, тестами и документацией.

## Три уровня проверки

1. **Код ↔ Спецификация** — реализация соответствует spec (API, поведение, исключения)
2. **Тесты ↔ Спецификация** — acceptance criteria и поведение покрыты тестами
3. **Документация ↔ Код + Тесты** — docs актуальны и соответствуют коду

## Workflow

### Шаг 1: Определение scope

```
аудит всего проекта → все specs/
аудит модуля {name} → specs/{domain}/
аудит spec файла → specs/{domain}/{file}.md
```

### Шаг 2: Исследование спецификации

Прочитай spec-файл. Извлеки:
- **Публичный API** — методы, классы, параметры из секций `Inputs`
- **Поведение** — секция `Behavior` (пошаговые сценарии)
- **Бизнес-правила** — секция `Business rules`
- **Ошибки** — секция `Errors` (ситуации и исключения)
- **Acceptance criteria** — чек-лист в `Acceptance criteria`

### Шаг 3-5: Проверка и формирование отчёта

Детальные шаги — в [`references/workflows.md`](references/workflows.md).

## Ссылки на детали

- [`references/workflows.md`](references/workflows.md) — детальные workflow для каждого уровня проверки
- [`references/rules.md`](references/rules.md) — правила проверки, статусы, NEEDS_CLARIFICATION
- [`references/templates.md`](references/templates.md) — формат отчёта, статусы аудита
- [`references/examples.md`](references/examples.md) — примеры типичных расхождений и результатов аудита
- [`references/checklists.md`](references/checklists.md) — чек-лист аудита

## Правила проекта

- [`guidelines/specification-guidelines.md`](../../../guidelines/specification-guidelines.md) — структура спецификаций, ID, NEEDS_CLARIFICATION, статусы
- [`guidelines/implementation-guidelines.md`](../../../guidelines/implementation-guidelines.md) — правила реализации, тесты, завершение
- [`guidelines/documentation-guidelines.md`](../../../guidelines/documentation-guidelines.md) — структура docs/, фронтматтер, стиль
