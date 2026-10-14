# Templates — Spec Audit

## Формат отчёта

```
# Spec Audit Report: {spec-id}

## Summary
- Spec: {path}
- Scope: {full project / module / specific file}
- Date: {date}

## 1. Код ↔ Спецификация

### Соответствует
- [x] {element} — {comment}

### Расхождения
- [ ] {element} — spec: {что должно быть}, code: {что есть}

## 2. Тесты ↔ Спецификация

### Покрыто
- [x] {acceptance criterion} → {test-file}

### Не покрыто
- [ ] {acceptance criterion} — нет теста

## 3. Документация ↔ Код + Тесты

### Соответствует
- [x] {doc-file} — {comment}

### Расхождения
- [ ] {doc-file} — docs: {что написано}, code: {что есть}

## Итого
- Расхождений код↔spec: {N}
- Непокрытых acceptance criteria: {N}
- Расхождений docs↔code: {N}
- Статус аудита: {PASS / WARN / FAIL}

## Обновление статуса спецификации

| Статус аудита | Новый статус spec | Действие |
|---|---|---|
| **PASS** | `IMPLEMENTED_STABLE` | Проект соответствует spec — обновить статус в файле spec |
| **WARN** | `IMPLEMENTED_NEED_WORK` | Есть расхождения — обновить статус в файле spec |
| **FAIL** | `IMPLEMENTED_NEED_WORK` | Критические расхождения — обновить статус в файле spec |

**Правила:**
- Если в spec есть `NEEDS_CLARIFICATION` — статус не меняй (остаётся `DRAFT`)
- Статус обновляй только если пользователь запросил
- Укажи новый статус в отчёте

```
## Статус спецификации
- Текущий: {DRAFT | IMPLEMENTED_STABLE | IMPLEMENTED_NEED_WORK}
- Новый: {DRAFT | IMPLEMENTED_STABLE | IMPLEMENTED_NEED_WORK}
- Причина: {почему такой статус}
```

## Статус аудита

- **PASS** — нет расхождений, всё покрыто
- **WARN** — есть мелкие расхождения или непокрытые критерии
- **FAIL** — есть критические расхождения (missing API, wrong behavior, untested errors)
