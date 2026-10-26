# docs-system

A Claude Code plugin that turns the documentation of any project into a system: one standard for structure and style, a header with lifecycle and quality status on every file, Obsidian-style `[[links]]`, an index that lets an AI find a file by reading only its first lines.

Плагин для Claude Code: превращает документацию любого проекта в систему. Единый стандарт структуры и стиля, шапка со статусом жизненного цикла и качества в каждом файле, ссылки `[[...]]` как в Obsidian, индекс, по которому нейросеть находит нужный файл, читая только его первые строки.

## Install / Установка

```
/plugin marketplace add el1ster/docs-system
/plugin install docs-system@docs-system
```

Then reload plugins (`/reload-plugins`) or restart the session.

## Skills / Скиллы

| Command | What it does / Что делает |
|---|---|
| `/docs-system:init` | Creates the docs system in a new, empty or code-only project. / Создаёт систему документации |
| `/docs-system:audit` | Rates every existing doc, changes nothing. / Оценивает документы, ничего не меняя |
| `/docs-system:plan` | Writes a plan for structure and quality from the audit. / Пишет план по итогам аудита |
| `/docs-system:restructure` | Executes an approved plan. / Исполняет утверждённый план |
| `/docs-system:maintain` | Keeps index, links and statuses healthy. / Поддерживает индекс, ссылки, статусы |
| `/docs-system:verify` | Tests whether an AI finds the rules; adds a pointer to `CLAUDE.md` / `AGENTS.md` / `GEMINI.md` if not. / Проверяет видимость правил |

Typical flow for a messy project: `audit` → `plan` → (your approval) → `restructure` → `verify`.

## Safety / Безопасность

- `audit` is read-only; it writes only a report to `docs/_audit/`.
- `restructure` runs only from a plan you approved, never deletes (obsolete files go to `docs/archive/`), and works per stage.
- No commits or pushes unless you ask.

## The standard / Стандарт

Lives in [`docs-system/standard/`](docs-system/standard): required document set, folder layout, header fields and statuses, quality rubric (6 criteria, 0–12), templates, and the AI-pointer protocol. It is a synthesis of common practices (Diátaxis, ADR, Keep a Changelog, docs-as-code), not a formal specification. Edit it to fit your project.

## License

MIT
