# Checklists — Skill Refactor

Чек-листы для аудита скиллов.

See [`SKILL.md`](../SKILL.md) -- overview and scenarios.

---

## Чек-лист аудита скилла

**ПЕРЕД сообщением пользователю -- проверь каждый пункт:**

```
Аудит скилла {skill-name}:
- [ ] SKILL.md <= 200 строк
- [ ] Нет дублирования контента из references/* (и наоборот)
- [ ] Нет дублирования контента из docs/, guidelines/, GIGACODE.md
- [ ] Большие логические блоки вынесены в references/ (workflow, examples, templates)
- [ ] SKILL.md содержит только ссылки на references/* + ёмкое описание
- [ ] Все файлы references/* ссылаются обратно на SKILL.md
- [ ] Нет противоречий между файлами скилла
- [ ] Фронтматтер (YAML) консистентен во всех файлах
```
