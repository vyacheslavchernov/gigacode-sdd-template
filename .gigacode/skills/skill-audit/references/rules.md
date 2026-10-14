---
last_updated: 2026-10-14
scope: skill-reference
---

# Rules — Skill Audit

Правила рефакторинга скиллов.

See [`SKILL.md`](../SKILL.md) -- overview and scenarios.

---

## 1. Разделение SKILL.md

Перенеси в `references/` следующие секции из SKILL.md:

| Секция в SKILL.md | Куда перенести |
|---|---|
| Детальный workflow (пошаговые шаги) | `references/workflows.md` |

| Примеры (хорошие/плохие) | `references/examples.md` |
| Шаблоны (файлы, YAML, отчёты) | `references/templates.md` |
| Чек-листы и таблицы статусов | `references/checklists.md` |
| Сценарии с большим количеством шагов | Оставить в SKILL.md как краткое описание + ссылка на workflows.md |

## 2. Что ОСТАВЛЯТЬ в SKILL.md

- Фронтматтер (`name`, `description`, `last_updated`)
- Одно-двухпредложное описание назначения скилла
- Список сценариев (кратко, 1 строка на сценарий)
- Ссылки на `references/*`
- Ссылки на `guidelines/*` проекта
- Критические правила (ВСЕГДА/НИКОГДА)
- Краткий чек-лист завершения (если <= 10 строк)

## 3. Что УДАЛЯТЬ из SKILL.md

- Полные пошаговые workflow (-> workflows.md)
- Полные примеры с кодом (-> examples.md)
- Шаблоны файлов (-> templates.md)

- Развёрнутые чек-листы (-> checklists.md)

## 4. Кросс-ссылки

Каждый тип контента — отдельная секция в SKILL.md. Ссылки на `references/*` размещаются в соответствующих секциях:

**SKILL.md -> references/:**

```markdown
## Workflow

Детальный пошаговый workflow — в [`references/workflows.md`](references/workflows.md).

## Шаблоны

Шаблоны файлов и фронтматтеров — в [`references/templates.md`](references/templates.md).

## Примеры

Примеры до и после рефакторинга — в [`references/examples.md`](references/examples.md).

## Checklists

Чек-лист аудита — в [`references/checklists.md`](references/checklists.md).
```

> **Правило:** Если файл `references/prompts.md` не нужен — секцию `## Prompts` не создавай. Каждая секция в SKILL.md должна ссылаться на существующий файл в `references/`.

**references/ -> SKILL.md:**

```markdown
# Workflows -- {Skill Name}

See [`SKILL.md`](../SKILL.md) -- overview and scenarios.
```

## 5. Область действия

Работай **только** с каталогом скилла, который указан в запросе пользователя.

**Исключения:**
- Явное указание примеров (другие скиллы как reference)
- Необходимость обратиться к документации проекта (`docs/`) или гайдлайнам (`guidelines/`) для проверки дублирования конте