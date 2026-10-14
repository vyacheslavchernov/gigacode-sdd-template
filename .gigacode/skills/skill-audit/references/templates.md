---
last_updated: 2026-10-14
scope: skill-reference
---

# Templates — Skill Audit

Шаблоны отчётов и правила согласованности.

See [`SKILL.md`](../SKILL.md) -- overview and scenarios.

---

## Формат отчёта аудита

```
# Skill Audit Report: {skill-name}

## Summary
- SKILL.md: {N} строк (лимит: 200)
- Файлов references/: {N}
- Дубликатов внутри скилла: {N}
- Дубликатов с docs/guidelines: {N}

## Issues

### Size
- [ ]/OK SKILL.md: {N} строк {>(=) 200}

### Duplicates (internal)
- [ ] {section in SKILL.md} дублирует {file in references/}
- [ ] {file A in references/} дублирует {file B in references/}

### Duplicates (external)
- [ ] {section} дублирует {guidelines/docs file}

### Missing references
- [ ] SKILL.md ссылается на {file} -- файл не найден
- [ ] {file in references/} не ссылается на SKILL.md

### Inconsistencies
- [ ] Различия в терминологии: SKILL.md "{A}" vs references/ "{B}"
- [ ] Фронтматтер inconsistent: SKILL.md {X} vs references/ {Y}

## Recommendations

1. Перенести секцию "{section}" из SKILL.md в references/workflows.md
2. Заменить дублирующий текст на ссылку на {file}
3. Добавить кросс-ссылку из {references/} в SKILL.md
4. Унифицировать фронтматтер

## Refactored (if applied)

### Changes
- Created `references/workflows.md` ({N} строк)
- Created `references/examples.md` ({N} строк)
- SKILL.md: {old} -> {new} строк
- Added cross-links

### Diff summary
- Removed from SKILL.md: {N} строк
- Added to references/: {N} строк
```

---

## Согласованность

### Фронтматтер

Все файлы скилла должны иметь консистентный фронтматтер:

**Корневой SKILL.md** — обязательные поля:
```yaml
---
name: {skill-name}
last_updated: YYYY-MM-DD
scope: skill  # или skill-reference
description: {краткое описание + триггеры}
---
```

**Файлы references/** — только метаданные:
```yaml
---
last_updated: YYYY-MM-DD
scope: skill-reference
---
```

> **Правило:** Поля `name` и `description` обязательны только для корневого `SKILL.md`. Файлы `references/*` содержат только `last_updated` и `scope: skill-reference`.

### Названия

- SKILL.md: `# {Skill Name}` (из фронтматтера `name`)
- references/workflows.md: `# Workflows -- {Skill Name}`
- references/examples.md: `# Examples -- {Skill Name}`
- references/templates.md: `# Templates -- {Skill Name}`

### Контент

- SKILL.md описывает **что** делает скилл и **когда** вызывать
- references/workflows.md описывает **как** -- детальные шаги
- references/examples.md показывает **как выглядит** -- примеры
- references/templates.md содержит **шаблоны** для копирования
- references/prompts.md содержит **промты** для суб-агентов

---

## Форматы отчётов суб-агентов

Каждый суб-агент (task-агент) возвращает структурированный отчёт. Промты для агентов -- в [`prompts.md`](prompts.md).

### Отчёт сборки списка файлов

```
# File Inventory Report: {skill-name}

## Skill Overview
- **Назначение:** {краткое описание}
- **Сценарии:** {список}
- **Ключевые правила:** {основные правила}

## Files
### SKILL.md
- **Путь:** .gigacode/skills/{skill-name}/SKILL.md
- **Строк:** {N}
- **Секции:** {список заголовков #}
- **Описание:** {что содержит}

### references/{filename}
- **Путь:** .gigacode/skills/{skill-name}/references/{filename}
- **Строк:** {N}
- **Секции:** {список заголовков #}
- **Описание:** {что содержит}

## Summary
- **Всего файлов:** {N}
- **Общее количество строк:** {N}
```

### Отчёт проверки дублирования (внутренняя)

```
# Duplicate Check Report (Internal): {skill-name}

## Summary
- **Дубликатов найдено:** {N}

## Issues
### SKILL.md ↔ references/*
- [ ] {section in SKILL.md} дублирует {file in references/}
  - **Контекст:** {фрагмент текста}
  - **Рекомендация:** {заменить на ссылку / перенести контент}

### references/* ↔ references/*
- [ ] {file A} дублирует {file B}
  - **Контекст:** {фрагмент текста}
  - **Рекомендация:** {объединить файлы}

## Clean
{если дубликатов нет, написать "Дубликатов не обнаружено"}
```

### Отчёт проверки дублирования (внешняя)

```
# Duplicate Check Report (External): {skill-name}

## Summary
- **Ссылок на docs/guidelines:** {N}
- **Дубликатов найдено:** {N}

## Issues
### Дублирование с guidelines/
- [ ] {section} дублирует {guidelines-file}
  - **Контекст:** {фрагмент текста}
  - **Рекомендация:** {заменить на ссылку}

### Дублирование с docs/
- [ ] {section} дублирует {docs-file}
  - **Контекст:** {фрагмент текста}
  - **Рекомендация:** {заменить на ссылку}

## Clean
{если дубликатов нет, написать "Дубликатов не обнаружено"}
```

### Отчёт проверки ссылок

```
# Link Check Report: {skill-name}

## Summary
- **Всего ссылок:** {N}
- **Рабочих ссылок:** {N}
- **Сломанных ссылок:** {N}
- **Дубликатов контента:** {N}

## Broken Links
- [ ] {link} -- файл не найден: {path}

## Content Duplicates
- [ ] {section} дублирует {file}
  - **Рекомендация:** {заменить на ссылку}

## Clean Links
{список рабочих ссылок}
```

### Отчёт проверки согласованности

```
# Consistency Check Report: {skill-name}

## Summary
- **Проблем фронтматтера:** {N}
- **Сломанных кросс-ссылок:** {N}
- **Различий в терминологии:** {N}
- **Противоречий:** {N}

## Frontmatter Issues
- [ ] {file}: {описание проблемы}

## Broken Cross-Links
- [ ] {source} → {target} -- файл не найден
- [ ] {file} не ссылается на SKILL.md

## Terminology Differences
- [ ] SKILL.md "{term A}" vs {file} "{term B}"

## Contradictions
- [ ] {location 1} vs {location 2}: {описание}

## Clean
{если проблем нет, написать "Проблем не обнаружено"}
```

### Отчёт рефакторинга

```
# Refactoring Report: {skill-name}

## Task
{description}

## Changes
- **Файл:** {path}
  - **Тип:** {создан/изменён/удалён}
  - **Строк до:** {N}
  - **Строк после:** {N}
  - **Описание изменений:** {что изменилось}

## Summary
- **Всего изменено файлов:** {N}
- **Создано файлов:** {N}
- **Изменено файлов:** {N}
- **Удалено файлов:** {N}
```
