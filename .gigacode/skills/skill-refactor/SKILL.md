---
name: skill-refactor
last_updated: 2026-10-14
scope: skill
description: Аудит и рефакторинг скиллов — проверка структуры, дублирования и согласованности файлов скилла. Триггеры: "рефакторинг скилла", "skill refactor", "проверь структуру скилла", "skill structure audit". Проверяет: SKILL.md <-> references/*, дублирование с docs/, перенос больших блоков, согласованность.
---

# Skill Refactor

Аудит и рефакторинг структуры скиллов -- проверка на дублирование, разделение больших блоков, согласованность файлов.

## Цель

Каждый скилл должен быть компактным (SKILL.md <= 200 строк) и содержать только ссылки на детализированные файлы в `references/`. Детальный контент (workflow, примеры, шаблоны) -- в отдельных файлах.

## Сценарии

### 1. Аудит скилла
```
аудит скилла {skill-name}
```
1. Проверь размер SKILL.md (<= 200 строк)
2. Проверь дублирование с references/ и docs/guidelines
3. Проверь согласованность фронтматтера и кросс-ссылок
4. Сгенерируй отчёт

### 2. Рефакторинг скилла
```
рефакторинг скилла {skill-name}
```
1. Проведи аудит (см. сценарий 1)
2. Перенеси контент в references/ по правилам
3. Обнови SKILL.md -- оставь только ссылки
4. Добавь кросс-ссылки

## Workflow

Детальные шаги аудита и рефакторинга -- в [`references/workflows.md`](references/workflows.md).

## Rules

Правила разделения SKILL.md, что оставлять/удалять, кросс-ссылки -- в [`references/rules.md`](references/rules.md).

## Examples

Примеры до и после рефакторинга -- в [`references/examples.md`](references/examples.md).

## Templates

Формат отчёта аудита, согласованность фронтматтера -- в [`references/templates.md`](references/templates.md).

## Checklists

Чек-лист аудита -- в [`references/checklists.md`](references/checklists.md).

## Critical Rules

- **ALWAYS** check SKILL.md size (limit 200 lines)
- **ALWAYS** check for duplicates before refactoring
- **ALWAYS** add cross-links when refactoring
- **NEVER** delete content without approval
- **NEVER** break existing links
- **APPLY** refactoring only on user request
- **PRESENT** audit report before applying changes
