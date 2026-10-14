# Examples -- Skill Edit

See [`SKILL.md`](../SKILL.md) -- overview and scenarios.

## Примеры хороших скиллов

### Пример 1: Компактный скилл (skill-audit)

**Структура:**
```
.gigacode/skills/skill-audit/
├── SKILL.md              # 64 строки
└── references/
    ├── workflows.md
    ├── examples.md
    ├── rules.md
    ├── templates.md
    └── checklists.md
```

**SKILL.md (64 строки):**
- Фронтматтер с name, last_updated, scope, description
- Краткое описание назначения
- Сценарии (2 сценария, по 4 шага каждый)
- Ссылки на references/ (5 файлов)
- Критические правила (7 ALWAYS/NEVER)

**Почему хороший:**
- SKILL.md <= 200 строк (64 строки)
- Детальный контент в references/
- Чёткая структура: цель → сценарии → workflow → правила
- Кросс-ссылки: SKILL.md -> references/ -> SKILL.md
- Консистентный фронтматтер

### Пример 2: Гипотетический скилл с избыточным SKILL.md

**Структура (ПЛОХО):**
```
.gigacode/skills/{long-workflow-skill}/
├── SKILL.md              # 296 строк (ПЛОХО)
```

**Почему плохой:**
- SKILL.md > 200 строк (296 строк)
- Весь контент в одном файле
- Нет references/
- Сложно поддерживать

**Как должно быть:**
```
.gigacode/skills/{long-workflow-skill}/
├── SKILL.md              # ~60 строк (после рефакторинга)
└── references/
    ├── workflows.md      # Детальный workflow (9 шагов)
    ├── examples.md       # Good/bad примеры
    └── checklists.md     # Критерии завершения
```

### Пример 3: Скилл-аудит (spec-audit)

**Идеальная структура:**
```
.gigacode/skills/spec-audit/
├── SKILL.md              # ~50 строк
└── references/
    ├── workflows.md      # 3 уровня проверки
    ├── checklists.md     # Чек-листы аудита
    └── templates.md      # Формат отчёта
```

**SKILL.md:**
```markdown
---
name: spec-audit
last_updated: 2026-10-14
scope: skill
description: Аудит спецификаций — проверка соответствия между кодом, спецификациями, тестами и документацией.
---

# Spec Audit

Аудит соответствия spec ↔ код ↔ тесты ↔ docs.

## Правила проекта

**ОБЯЗАТЕЛЬНО** следуй гайдлайнам:
- [`guidelines/specification-guidelines.md`](../../guidelines/specification-guidelines.md)

## Сценарии

### 1. Аудит спецификации
```
аудит спецификаций {spec-name}
```
1. Найди spec-файл
2. Проверь код ↔ spec
3. Проверь тесты ↔ spec
4. Проверь docs ↔ code

### 2. Аудит модуля
```
аудит модуля {module-name}
```
1. Найди все spec-файлы модуля
2. Проверь соответствие
3. Сгенерируй отчёт

## Workflow

Детальные шаги — в [`references/workflows.md`](references/workflows.md).

## Checklists

Чек-листы аудита — в [`references/checklists.md`](references/checklists.md).

## Templates

Формат отчёта — в [`references/templates.md`](references/templates.md).

## Critical Rules

- **ALWAYS** проверяй все 3 уровня: код↔spec, тесты↔spec, docs↔code
- **ALWAYS** генерируй отчёт в формате templates.md
- **NEVER** пропускай уровни аудита
- **NEVER** додумывай расхождения — фиксируй только проверяемые факты
```

## Структура идеального скилла

```
.gigacode/skills/{skill-name}/
├── SKILL.md              # <= 200 строк, ёмкое описание
└── references/           # Опционально, но рекомендуется
    ├── workflows.md      # Детальные шаги workflow
    ├── examples.md       # Примеры good/bad
    ├── templates.md      # Шаблоны файлов
    ├── checklists.md     # Чек-листы
    └── prompts.md        # Промпты для агентов (опционально)
```

**Соотношение контента:**

| Файл | Содержание | Лимит |
|---|---|---|
| SKILL.md | Что делает, когда вызывать, ссылки | <= 200 строк |
| workflows.md | Как делать — пошагово | Нет лимита |
| examples.md | Как выглядит — примеры | Нет лимита |
| templates.md | Шаблоны для копирования | Нет лимита |
| checklists.md | Чек-листы завершения | Нет лимита |

## Частые ошибки

### Ошибка 1: Слишком длинный SKILL.md

**Плохо:**
```markdown
# Skill Name

Детальный workflow со всеми шагами...
1. Шаг 1 с подробным описанием...
2. Шаг 2 с подробным описанием...
...
296 строк контента в SKILL.md
```

**Хорошо:**
```markdown
# Skill Name

Краткое описание.

## Workflow

Детальные шаги — в [`references/workflows.md`](references/workflows.md).
```

### Ошибка 2: Отсутствие кросс-ссылок

**Плохо:**
```markdown
# SKILL.md
## Workflow
Детальные шаги в references/workflows.md.

# references/workflows.md
# Workflows
Здесь детальные шаги...
(нет ссылки на SKILL.md)
```

**Хорошо:**
```markdown
# SKILL.md
## Workflow
Детальные шаги — в [`references/workflows.md`](references/workflows.md).

# references/workflows.md
# Workflows -- {Skill Name}
See [`SKILL.md`](../SKILL.md) -- overview and scenarios.
```

### Ошибка 3: Дублирование контента

**Плохо:**
```markdown
# SKILL.md
## Business rules
- Правило 1...
- Правило 2...

# references/workflows.md
## Business rules
- Правило 1...
- Правило 2...
```

**Хорошо:**
```markdown
# SKILL.md
## Business rules
Следуй [`guidelines/business-rules.md`](../../guidelines/business-rules.md).

# references/workflows.md
## Business rules
Детали — в [`guidelines/business-rules.md`](../../guidelines/business-rules.md).
```
