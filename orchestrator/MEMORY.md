# Permanent Memory

This file contains important facts and context that should always be available.
The agent can update this file using workspace_write when asked by the user.

## System
- Project: Balbes Multi-Agent System
- Environment: VPS server, Linux
- Primary stack: Python, FastAPI, Redis, Qdrant, PostgreSQL, Docker

## Reminders
- [2024-03-28 14:43] Выпить воды
- [2026-03-29 16:32] Выпить воды

## Notes
- Reminder format: [YYYY-MM-DD HH:MM] text. No relative time allowed.
- Agent can orchestrate other agents (Coder, Researcher, etc.)
- Default logs: show agent tool call logs via read_agent_logs()

## Chat Summary & Lessons Learned (2026)

### Что было сделано
- Проверка статуса Docker: работают qdrant, rabbitmq, redis, postgres (агенты не в Docker)
- Диагностика ошибки 429 Rate Limit на модели stepfun/step-3.5-flash:free
- Исправлена ошибка парсинга Telegram entities (проблема с ```` `` ````)

### Важные правила
1. **Системные сообщения — это мои сообщения**. Включать их при ответе на "покажи мои сообщения"
2. **Не искать модели в интернете** — проверять локальную конфигурацию агента
3. **Избегать двойных обратных кавычек ```` `` ````** в Telegram — вызывает ошибку парсинга
4. **Модель stepfun/step-3.5-flash:free имеет лимиты** — 429 ошибки при частых запросах

### Доступные модели
- StepFun Step 3.5 Flash (бесплатная, с лимитами)
- MiniMax M2.5, GLM-4.5 Air, Trinity Mini, GPT OSS 20B (бесплатные)
- Llama 3.1 8B, Llama 3.3 70B (дешёвые)
- Kimi K2.5, Gemini 3 Flash (средние)
- GLM-5 Turbo, Claude Sonnet 4.6, GPT-5.4 (премиум)