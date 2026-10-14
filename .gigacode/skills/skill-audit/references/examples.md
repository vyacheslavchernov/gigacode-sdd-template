# Examples — Skill Audit

Примеры до и после рефакторинга.

See [`SKILL.md`](../SKILL.md) -- overview and scenarios.

---

## Before refactoring (spec-impl, 296 lines)

```markdown
# Spec Impl

## Workflow
### Шаг 1: Изучение
1. Read the target spec...
2. Find and read related specs...

### Шаг 2: Определение scope
...

### Шаг 6: Вызов doc-sync
...

### Шаг 7: Auto-fix loop
```max_iterations = 3...```
```

**Problems:**
- 296 lines (limit 200)
- Workflow duplicated in `references/workflows.md`
- Examples in SKILL.md duplicate `references/examples.md`

## After refactoring

```markdown
# Spec Impl

Implementation of code based on specification.

## Scenarios

### 1. New spec implementation
```
implement spec {spec-name}
```
1. Read spec -> determine scope
2. Implement code and tests
3. Call `doc-sync` -> `spec-audit` -> auto-fix loop

### 2. Update by spec
```
update code by spec {spec-name}
```
1. Compare spec with code -> find differences
2. Implement minimal changes
3. Call `doc-sync` -> `spec-audit` -> auto-fix loop

## Workflow

Detailed steps -- in [`references/workflows.md`](references/workflows.md).

## Examples

Spec examples -- in [`references/examples.md`](references/examples.md).

## Additional Materials

- [`references/workflows.md`](references/workflows.md) -- detailed steps, prompts
- [`references/examples.md`](references/examples.md) -- good/bad examples
- [`guidelines/implementation-guidelines.md`](../../guidelines/implementation-guidelines.md) -- implementation rules
```

**Result:** 60 lines (was 296).
