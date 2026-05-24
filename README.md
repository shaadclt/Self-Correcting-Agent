# AI Code Generation & Self-Debugging Agent

An autonomous Python coding agent powered by a local LLM using Ollama.  
The agent generates Python code for a given task, executes it, detects runtime errors, and automatically retries with corrected code until the script runs successfully.

---

## Features

- Generate Python scripts using an LLM
- Automatically execute generated code
- Detect runtime errors
- Self-debug using iterative retries
- Uses custom system/debug prompts
- Simple modular architecture

---

## Project Structure

```bash
.
├── agent.py          # Main autonomous agent loop
├── executor.py       # Executes generated Python scripts
├── prompts.py        # System and debugging prompts
├── generated_code.py # Auto-generated script (runtime)
└── README.md
```

---

## How It Works

1. The user provides a programming task.
2. The LLM generates Python code.
3. The generated code is saved as `generated_code.py`.
4. The executor runs the generated script.
5. If the script fails:
   - The error is captured
   - A debugging prompt is created
   - The LLM generates corrected code
6. The process repeats until:
   - The code succeeds
   - Maximum retry limit is reached

---

## Files Overview

### `agent.py`

Main orchestration logic for:
- Prompting the LLM
- Generating code
- Running generated scripts
- Handling retries
- Self-debugging loop

### `executor.py`

Handles safe execution of generated Python files using:
- `subprocess.run`
- Timeout protection
- Error capturing

### `prompts.py`

Contains:
- `SYSTEM_PROMPT`
- `DEBUG_PROMPT`

Used to guide the LLM during:
- Initial code generation
- Automatic debugging

---

## Requirements

- Python 3.9+
- Ollama installed locally
- DeepSeek Coder model downloaded

---

## Install Dependencies

```bash
pip install langchain-community
```

---

## Install Ollama

Download and install Ollama:

https://ollama.com

---

## Pull the Model

```bash
ollama pull deepseek-coder:6.7b
```

---

## Run Ollama

```bash
ollama serve
```

---

## Run the Agent

```bash
python agent.py
```

---

## Example Task

```python
user_task = """
Create a Python script that:
1. Reads a CSV file
2. Calculates average salary
3. Displays the result
"""
```

---

## Example Workflow

```text
Task → Generate Code → Execute → Error? → Debug → Retry
```

---

## Retry Mechanism

The agent retries failed generations automatically.

Default:

```python
MAX_RETRIES = 5
```

---

## Example Output

```text
FINAL WORKING CODE:

<generated python code>

OUTPUT:

Average salary: 55000
```

---

## Technologies Used

- Python
- Ollama
- LangChain
- DeepSeek Coder LLM
- Subprocess Execution

---

## Future Improvements

- Sandboxed execution
- Docker isolation
- Multi-file generation
- Unit test generation
- Web UI
- Memory/context persistence
- API integration
- Code quality scoring

---

## Security Note

This project executes AI-generated Python code locally.

Only run in a trusted environment or sandboxed container.

---

## License

MIT License
