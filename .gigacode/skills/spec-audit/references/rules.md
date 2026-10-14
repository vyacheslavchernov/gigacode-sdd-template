# Rules — Spec Audit

## Три уровня проверки

### 1. Код ↔ Спецификация

Проверяет, что реализация соответствует спецификации:
- Все публичные методы/классы из spec реализованы в коде
- Поведение кода соответствует описанному в spec (Behavior, Business rules)
- Исключения в spec бросаются в коде
- Acceptance criteria из spec проверены на соответствие коду
- Нет в spec, но нет в коде
- Нет в коде, но есть в spec (и не является NEEDS_CLARIFICATION)

### 2. Тесты ↔ Спецификация

Проверяет, что спецификация покрыта тестами:
- Каждый acceptance criterion имеет хотя бы один тест
- Основные сценарии (Behavior) покрыты тестами
- Ошибки и исключения из spec проверены тестами
- Граничные случаи покрыты тестами

### 3. Документация ↔ Код + Тесты

Проверяет, что документация актуальна:
- `docs/modules/*.md` описывает реальный публичный API
- `docs/packages/*/README.md` соответствует коду
- `README.md` модулей — примеры и конфигурация актуальны
- Нет расхождений между spec и docs

## Критические расхождения

**FAIL** если:
- Публичный метод из spec не реализован в коде
- Поведение кода противоречит spec (не то же самое)
- Исключение из spec не бросается в коде
- Acceptance criterion не покрыт тестом (кроме NEEDS_CLARIFICATION)

## Статусы аудита

| Статус | Описание |
|---|---|
| **PASS** | Нет расхождений, всё покрыто |
| **WARN** | Есть мелкие расхождения или непокрытые критерии |
| **FAIL** | Есть критические расхождения (missing API, wrong behavior, untested errors) |

## NEEDS_CLARIFICATION

Если в spec есть `NEEDS_CLARIFICATION`:
- Отметь его в отчёте
- Не считай за расхождение — это ожидаемое состояние
- Отрази в разделе "Непокрыто" с пометкой "NEEDS_CLARIFICATION"

## Ссылки на гайдлайны проекта

- [`guidelines/specification-guidelines.md`](../../../guidelines/specification-guidelines.md) — правила написания спецификаций, структура, ID, NEEDS_CLARIFICATION, статусы спецификаций
- [`guidelines/implementation-guidelines.md`](../../../guidelines/implementation-guidelines.md) — правила реализации, тесты, документация, завершение
- [`guidelines/documentation-guidelines.md`](../../../guidelines/documentation-guidelines.md) — структура docs/, фронтматтер, стиль
