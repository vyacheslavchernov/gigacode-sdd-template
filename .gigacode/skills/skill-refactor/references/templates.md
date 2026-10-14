# Templates — Skill Refactor

Шаблоны отчётов и правила согласованности.

See [`SKILL.md`](../SKILL.md) -- overview and scenarios.

---

## Формат отчёта аудита

```
# Skill Refactor Report: {skill-name}

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
