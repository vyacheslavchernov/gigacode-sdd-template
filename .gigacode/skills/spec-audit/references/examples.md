# Examples — Spec Audit

Примеры результатов аудита — в [`references/workflows.md`](references/workflows.md) (секция "Пример отчёта").

---

## Примеры типичных расхождений

### Расхождение: missing API

```
Spec: "Метод log() поддерживает перегрузку без message"
Code: реализован только метод log(message, level)
Тип: missing
```

### Расхождение: wrong behavior

```
Spec: "Фильтры применяются последовательно к каждому аппендеру"
Code: фильтры применяются один раз перед отправкой на все аппендеры
Тип: wrong
```

### Расхождение: untested error

```
Spec: "При недоступности сервера бросается ConnectionException"
Tests: нет теста на ConnectionException
Тип: not covered
```

## Примеры корректного аудита

### PASS — всё соответствует

```
Код ↔ Spec: 0 расхождений
Тесты ↔ Spec: 100% покрытие
Docs ↔ Code: 0 расхождений
Статус: PASS
```

### WARN — мелкие расхождения

```
Код ↔ Spec: 1 расхождение (доп. метод в коде, не описанный в spec)
Тесты ↔ Spec: 1 непокрытый граничный случай
Docs ↔ Code: 0 расхождений
Статус: WARN
```

### FAIL — критические расхождения

```
Код ↔ Spec: missing публичный метод из spec
Тесты ↔ Spec: 2 непокрытых acceptance criterion
Docs ↔ Code: 0 расхождений
Статус: FAIL
```

## Ссылки на детали спецификаций

Примеры структуры good/bad спецификаций — в [`guidelines/specification-guidelines.md`](../../../guidelines/specification-guidelines.md#7-примеры).
