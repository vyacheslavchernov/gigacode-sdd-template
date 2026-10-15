---
name: template-init
last_updated: 2026-10-16
description: Интерактивная инициализация нового проекта на базе SpecDriven-шаблона. Запрашивает название, назначение, язык, инструменты сборки — затем формирует структуру проекта, гайдлайны и обновляет GIGACODE.md. Триггеры "инициализируй проект", "template-init", "new project setup".
---

# Template Init

Интерактивная инициализация нового проекта на базе SpecDriven-шаблона.

## Сценарий

```
инициализируй проект для {описание}
```

1. Задай уточняющие вопросы (см. [`references/questions.md`](references/questions.md))
2. Инициализируй структуру проекта
3. Сформируй гайдлайны
4. Подготовь проект к работе (установи зависимости, собери, запусти тесты)
5. Обнови README.md и GIGACODE.md
6. Предоставь результат пользователю

## Уточняющие вопросы

Задай вопросы **последовательно**, по одному. Жди ответа перед следующим вопросом.

Смотри [`references/questions.md`](references/questions.md) — вопросы 1-6 и списки инструментов для языков/интерфейсов.

## Workflow

### Шаг 1: Сбор требований

Смотри [`references/implementation-steps.md`](references/implementation-steps.md) — Шаг 1 (JSON-структура ответов).

### Шаг 2: Проверка установленных инструментов

Смотри [`references/implementation-steps.md`](references/implementation-steps.md) — Шаг 2 (команды проверки).

### Шаг 3: Инициализация структуры проекта

Смотри [`references/implementation-steps.md`](references/implementation-steps.md) — Шаг 3 (структуры для всех стеков).

**ВАЖНО:** Проект инициализируется **напрямую в текущем рабочем каталоге**. Не создавай отдельную поддиректорию с именем проекта.

### Шаг 4: Формирование гайдлайнов

Смотри [`references/implementation-steps.md`](references/implementation-steps.md) — Шаг 4. Шаблоны гайдлайнов — [`references/guideline-templates.md`](references/guideline-templates.md).

### Шаг 4.5: Подготовка проекта к работе

Смотри [`references/implementation-steps.md`](references/implementation-steps.md) — Шаг 4.5 (зависимости, сборка, тесты).

### Шаг 5: Обновление README.md

Смотри [`references/final-steps.md`](references/final-steps.md) — Шаг 5.

### Шаг 6: Обновление GIGACODE.md

Смотри [`references/final-steps.md`](references/final-steps.md) — Шаг 6.

Детальные правила обновления `GIGACODE.md` — в [`guidelines/gigacode-md-guidelines.md`](../../guidelines/gigacode-md-guidelines.md).

### Шаг 7: Обновление .gitignore

Смотри [`references/final-steps.md`](references/final-steps.md) — Шаг 7.

### Шаг 8: Предоставление результата

Смотри [`references/final-steps.md`](references/final-steps.md) — Шаг 8 (формат отчёта).

## Примеры

Смотри [`references/examples.md`](references/examples.md) — примеры для TypeScript+GUI, Python+CLI, Java+API-only.

## Правила

- **Задавай вопросы последовательно**, по одному
- **Не додумывай** — если пользователь не ответил на вопрос, спроси повторно или предложи вариант по умолчанию
- **Проверяй установленные инструменты** перед инициализацией
- **Предлагай инструкции по установке** если инструмент отсутствует
- **Подставляй реальные значения** в гайдлайны — не оставляй placeholder'ов
- **Проект должен быть готов к работе** — зависимости установлены, сборка прошла, тесты прошли (простой "hello, world" + тест)
- **НЕ генерируй реальный код приложения** — только минимальную заглушку для проверки сборки
- **Не создавай поддиректорию с именем проекта** — вся структура разворачивается **напрямую в текущем рабочем каталоге** (корне)
- **Не ломай** существующую структуру SpecDriven-шаблона
- **Сохраняй** `specs/`, `docs/`, `.gigacode/` без изменений
