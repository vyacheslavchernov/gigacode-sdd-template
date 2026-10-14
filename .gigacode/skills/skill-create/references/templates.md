# Templates -- Skill Create

See [`SKILL.md`](../SKILL.md) -- overview and scenarios.

## Шаблон SKILL.md

```yaml
---
name: {skill-name}
last_updated: {YYYY-MM-DD}
scope: skill
description: {краткое описание назначения, триггеры}
---
```

```markdown
# {Skill Name}

{Краткое описание назначения скилла — 1-2 предложения.}

## Правила проекта

**ОБЯЗАТЕЛЬНО** следуй гайдлайнам:
{Список ссылок на релевантные для скилла гайдлайны}

## Сценарии

### 1. {Основной сценарий}

```
{триггер-команда}
```

1. {Шаг 1}
2. {Шаг 2}
3. {Шаг 3}

### 2. {Дополнительный сценарий}

```
{триггер-команда}
```

1. {Шаг 1}
2. {Шаг 2}

## Уточняющие вопросы

{Список вопросов, которые скилл задаёт пользователю}

## Workflow

Детальный пошаговый workflow — в [`references/workflows.md`](references/workflows.md).

## Examples

Примеры использования — в [`references/examples.md`](references/examples.md).

## Checklists

Чек-листы — в [`references/checklists.md`](references/checklists.md).

## Critical Rules

- **ALWAYS** {правило}
- **NEVER** {запрет}
```

## Шаблон references/workflows.md

```markdown
# Workflows -- {Skill Name}

See [`SKILL.md`](../SKILL.md) -- overview and scenarios.

## Workflow: {Название workflow}

### Шаг 1: {Название шага}
1. {Действие}
2. {Действие}

### Шаг 2: {Название шага}
1. {Действие}
2. {Действие}
```

## Шаблон references/examples.md

```markdown
# Examples -- {Skill Name}

See [`SKILL.md`](../SKILL.md) -- overview and scenarios.

## Хороший пример

```yaml
---
name: example-skill
scope: skill
---
```

```markdown
# Example Skill

Краткое описание...

## Сценарии
...
```

**Почему хороший:**
- SKILL.md <= 200 строк
- Есть ссылки на references/
- Критические правила ALWAYS/NEVER
- Уточняющие вопросы

## Плохой пример

```markdown
# Bad Skill

Описание...
```

**Почему плохой:**
- SKILL.md > 200 строк
- Нет структуры сценариев
- Нет критических правил
- Нет ссылок на references/
```

## Шаблон references/checklists.md

```markdown
# Checklists -- {Skill Name}

See [`SKILL.md`](../SKILL.md) -- overview and scenarios.

## Создание скилла

- [ ] Название уникально (нет конфликта с существующими)
- [ ] SKILL.md <= 200 строк
- [ ] Фронтматтер консистентен (name, last_updated, scope, description)
- [ ] Есть сценарии использования
- [ ] Есть уточняющие вопросы
- [ ] Есть ссылки на guidelines/
- [ ] Есть ссылки на references/ (если есть)
- [ ] Есть кросс-ссылки references/ -> SKILL.md
- [ ] Зарегистрирован в GIGACODE.md
- [ ] Пройден аудит skill-refactor

## Аудит скилла

- [ ] SKILL.md <= 200 строк
- [ ] Нет дублирования с references/
- [ ] Нет дублирования с docs/guidelines
- [ ] Все ссылки рабочи
- [ ] Фронтматтер консистентен
- [ ] Терминология согласована
```

## Фронтматтер

**Обязательные поля:**

| Поле | Тип | Описание |
|---|---|---|
| `name` | string | Уникальное название скилла (snake_case) |
| `last_updated` | date | Дата последнего изменения (YYYY-MM-DD) |
| `scope` | string | Всегда `skill` |
| `description` | string | Краткое описание + триггеры |

**Опциональные поля:**

| Поле | Тип | Описание |
|---|---|---|
| `author` | string | Автор скилла |
| `version` | string | Версия скилла (semver) |
| `depends_on` | array | Зависимости от других скиллов |
