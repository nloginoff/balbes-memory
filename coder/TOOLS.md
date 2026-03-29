# Available Tools & Skills

## web_search(query, max_results=5)
Search the internet for documentation, library versions, error solutions.
Use when: need current API docs, library examples, or researching best practices.
```
web_search(query="fastapi background tasks python 3.12", max_results=5)
```

## fetch_url(url)
Fetch and read content from a URL (docs, GitHub READMEs, error pages).
Use when: have a specific URL to read.
```
fetch_url(url="https://docs.python.org/3/library/asyncio-task.html")
```

## execute_command(command)
Run server commands from the whitelist.

**⚠️ IMPORTANT: Do NOT use `cd /path && command` — compound commands are blocked.**
Instead:
- Use `git -C /path/to/repo command` for git in specific directories
- Use full absolute paths in Python: `python /home/balbes/projects/dev/script.py`
- Use `-C` flag for make: `make -C /path target`

Examples:
```
execute_command(command="git -C /home/balbes/projects/dev status")
execute_command(command="git -C /home/balbes/projects/dev log --oneline -10")
execute_command(command="git -C /home/balbes/projects/dev add .")
execute_command(command="git -C /home/balbes/projects/dev commit -m 'fix: ...'")
execute_command(command="git -C /home/balbes/projects/dev push")
execute_command(command="python /home/balbes/projects/dev/script.py")
execute_command(command="pytest /home/balbes/projects/dev/tests/")
```

Available in **agent mode**: Python, pip, Node, npm, make, pytest, ruff, mypy, git.
Available in **ask mode**: safe info only — date, find, df, ls, cat, git status/log/diff/branch.

## workspace_read(filename)
Read a file from the agent's workspace directory.
Available: `AGENTS.md`, `SOUL.md`, `USER.md`, `TOOLS.md`, `MEMORY.md`, `config.yaml`
Use when: recalling project-specific context or configuration.
```
workspace_read(filename="MEMORY.md")
```

## workspace_write(filename, content)
Write or update a file in the agent's workspace.
Writable: `AGENTS.md`, `SOUL.md`, `USER.md`, `MEMORY.md`, `IDENTITY.md`, `config.yaml`
Use when: persisting project decisions, updating MEMORY.md, changing own config.
```
workspace_write(filename="MEMORY.md", content="# Project Notes\n\n- Stack: FastAPI + Redis...")
```

## rename_chat(name)
Rename the current chat session to a descriptive name.
```
rename_chat(name="FastAPI Auth Refactor")
```

## save_to_memory(text)
Store important long-term fact in Qdrant memory.
Use sparingly — only for facts critical across many future sessions.

## read_agent_logs(date, tool_filter, limit)
Read your own activity logs for a given date or range.
