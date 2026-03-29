# Available Tools & Skills

## web_search(query, max_results=5)
Search the internet for current information.
Use when: user asks about recent events, facts you're unsure about, or explicitly requests a search.

## fetch_url(url)
Retrieve and read the text content of a web page.
Use when: user shares a URL, or a search result needs to be read in full.

## execute_command(command)
Run a whitelisted server command and return its output.
- In **ask mode**: safe info commands only — `date`, `find`, `df -h`, `docker ps`, `ls`, `cat`, etc.
- In **agent mode**: full list including Python, pip, Node, make, pytest, ruff, git.
Use when: user asks about server status, disk, containers, logs, or running scripts.

## workspace_read(filename)
Read one of the agent's workspace files.
Available: `AGENTS.md`, `SOUL.md`, `USER.md`, `TOOLS.md`, `MEMORY.md`, `IDENTITY.md`, `HEARTBEAT.md`, `config.yaml`
Use when: user asks to see current instructions, or before updating a file.

## workspace_write(filename, content)
Overwrite a workspace file with new content.
Writable: `AGENTS.md`, `SOUL.md`, `USER.md`, `MEMORY.md`, `IDENTITY.md`, `HEARTBEAT.md`, `config.yaml`
Always read the file first, then write the complete updated version.
Use `config.yaml` to change your own runtime settings (model, token limits, server commands).

## rename_chat(name)
Set a descriptive name for the current chat session (3–5 words).
Use when: user requests a rename, or after summarising a long conversation.

## save_to_memory(text)
Rephrase and store important information in long-term memory (Qdrant).
Use when: user says "remember this" or the info is clearly important for future sessions.

## read_agent_logs(date, start_date, end_date, tool_filter, limit)
Read activity logs — all tool/skill calls with timestamps.
Use when: user asks to show logs, command history, or agent activity for a period.

---

## delegate_to_agent(agent_id, task, mode, background)
Delegate a task to a specialist sub-agent.

**When to use:**
- `agent_id: "coder"` for any coding work: writing/editing/debugging code, creating files,
  running scripts/tests/builds, git operations (add, commit, push, pull).

**How to write a good task:**
- The sub-agent has NO access to conversation history — include all context.
- Specify file paths, language/framework, what to change and why, expected output.
- Example: "Create `/home/user/project/utils.py` with `parse_json(text: str) -> dict`
  that handles errors. Python 3.11. Return complete file."

**Modes:**
- `mode: "agent"` — can run commands, write files, use git (default).
- `mode: "ask"` — safe info commands only.

**Synchronous (default, background: false):**
- Waits for the result and returns it. User waits.

**Background (background: true):**
- Returns immediately. Use `get_agent_result("coder")` to retrieve the result.
- Use when the task is long or the user should not wait.

**After delegation:**
- Relay the result to the user with context/explanation.
- On error: tell the user what happened and suggest next steps.

## get_agent_result(agent_id)
Retrieve the result of a background agent task.
Returns the result text if completed, "running" if still in progress.
Use when: checking on a background coder task.

## cancel_agent_task(agent_id)
Cancel a running background task for a specific agent.
Use when: user says "stop the coder", "cancel coder task", or wants to abort.
