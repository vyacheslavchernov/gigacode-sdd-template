---
last_updated: 2026-10-15
scope: skill-referense
---

# Templates — Doc Sync

Шаблоны фронтматтеров для разных типов файлов документации.

См. [`SKILL.md`](../SKILL.md) — обзор и сценарии.

---

## Фронтматтеры

### Документ модуля (`docs/modules/*.md`)

```yaml
---
last_updated: 2026-10-15
scope: module
---
```

### Документ пакета (`docs/packages/*/README.md`)

```yaml
---
last_updated: 2026-10-15
scope: package
---
```

### Документ архитектуры (`docs/architecture.md`)

```yaml
---
last_updated: 2026-10-15
scope: architecture
---
```

### Документ тестирования (`docs/testing/*.md`)

```yaml
---
last_updated: 2026-10-15
scope: testing
---
```

### Гайдлайн (`guidelines/*.md`)

```yaml
---
last_updated: 2026-10-15
scope: guidelines
---
```

### Спецификация (`specs/**/*.md`)

```yaml
---
last_updated: 2026-10-15
scope: specification
---
```

### Главный `docs/README.md`

```yaml
---
last_updated: 2026-10-15
scope: module
---
```

### `GIGACODE.md`

```yaml
---
last_updated: 2026-10-15
scope: project
---
```

---

## Правила фронтматтера

- `last_updated` — дата в формате `YYYY-MM-DD`. Обновляется при любом изменении документа.
- `scope` — тип документа: `module`, `package`, `testing`, `architecture`, `guidelines`, `specification`, `project`.
- Фронтматтер всегда в начале файла, между `---`.

> **Подробности:** [`documentation-guidelines.md §2.1`](../../guidelines/documentation-guidelines.md#21-data-poslednego-obnovleniya)
