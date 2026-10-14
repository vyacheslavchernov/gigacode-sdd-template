---
name: doc-sync
last_updated: 2026-10-14
description: Обновление документации проекта в соответствии с изменениями в коде. Триггеры: "обнови документацию", "sync docs", "обнови README модуля", "обнови документацию для {модуль}". Применяется к проектам с аналогичной структурой: docs/, README.md в модулях, спецификаций, GIGACODE.md.
---

# Doc Sync

Обновление документации проекта в соответствии с текущим состоянием кода.

## Что обновляет

1. **`docs/modules/*.md`** — документация модулей
2. **`docs/packages/*/README.md`** — документация пакетов
3. **`docs/architecture.md`** — архитектура, паттерны
4. **`docs/README.md`** — навигация
5. **`README.md`** в корнях модулей — пользовательская документация
6. **`docs/testing/*.md`** — если изменились тесты
7. **`GIGACODE.md`** — если изменилась структура каталогов, гайдлайны, скиллы или команды
8. **`specs/**/*.md`** — если изменилось поведение системы, описанное в спецификациях
9. **`docs/**`** - любое другое содержимое документации затронутое изменениями в коде

## Правила работы

**ВСЕГДА** следуй правилам проекта:
- [`guidelines/documentation-guidelines.md`](../../guidelines/documentation-guidelines.md) — структура, фронтматтер, стиль
- [`guidelines/gigacode-md-guidelines.md`](../../guidelines/gigacode-md-guidelines.md) — правила обновления GIGACODE.md

**Лимиты:** один файл ≤ 200 строк, фронтматтер с `last_updated` и `scope`. GIGACODE.md ≤ 40 строк.

## Сценарии

### 1. Обновление по diff
```bash
git diff HEAD
# или
git diff main...{branch}
```

### 2. Обновление по ветке
```bash
git diff main...{branch} --stat
```

### 3. Обновление модуля
```
обнови документацию для модуля {название}
```

### 4. Полное обновление
Параллельные `Explore`-агенты для всех модулей.

## Workflow

Детальный пошаговый workflow — в [`references/workflows.md`](references/workflows.md).

## Checklists

Чек-лист завершения — в [`references/checklists.md`](references/checklists.md).

## Critical Rules

- **ALWAYS** используй `Explore`-агентов для исследования кода
- **ALWAYS** проверяй чек-лист перед завершением
- **ALWAYS** обнови `last_updated` при изменении файла
- **NEVER** добавляй детали реализации в GIGACODE.md
- **NEVER** ломай существующие кросс-ссылки
