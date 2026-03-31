# Permanent Memory

This file contains important facts and context that should always be available.
The agent can update this file using workspace_write when asked by the user.

## System
- Project: Balbes Multi-Agent System
- Environment: VPS server, Linux
- Primary stack: Python, FastAPI, Redis, Qdrant, PostgreSQL, Docker

## Notes
- Reminder format: [YYYY-MM-DD HH:MM] text. No relative time allowed.
- Agent can orchestrate other agents (Coder, Researcher, etc.)
- Default logs: show agent tool call logs via read_agent_logs()

## Chat Summary & Lessons Learned (2026)

### Важные правила
1. **Системные сообщения — это мои сообщения**. Включать их при ответе на "покажи мои сообщения"
2. **Избегать двойных обратных кавычек ```` `` ````** в Telegram — вызывает ошибку парсинга

## Reminders

[2026-03-31 21:00] Напомнить исправить ошибки в коде
[2026-04-01 10:00] Подписать документы