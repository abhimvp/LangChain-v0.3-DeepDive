# LangChain-v0.3-DeepDive

Detailed exploration of various topics, such as agents, LangChain Expression Language (LCEL), streaming, and conversational memory ..etc.

- [Learning Resource](https://youtu.be/Cyv-dgv80kE?si=pQ0qdWamDjEys5Hr) & refer Offline notes as well.
- [Resource Repo](https://github.com/aurelio-labs/langchain-course)

## Local Setup

```bash
abhis@Tinku MINGW64 ~/Desktop/LangChain-v0.3-DeepDive (main)
$ uv python install 3.12.7
uv venv --python 3.12.7
Installed Python 3.12.7 in 5.81s
 + cpython-3.12.7-windows-x86_64-none
Using CPython 3.12.7
Creating virtual environment at: .venv
Activate with: source .venv/Scripts/activate

abhis@Tinku MINGW64 ~/Desktop/LangChain-v0.3-DeepDive (main)
$ source .venv/Scripts/activate

(LangChain-v0.3-DeepDive)
abhis@Tinku MINGW64 ~/Desktop/LangChain-v0.3-DeepDive (main)
$ uv init .
Initialized project `langchain-v0-3-deepdive` at `C:\Users\abhis\Desktop\LangChain-v0.3-DeepDive`

abhis@Tinku MINGW64 ~/Desktop/LangChain-v0.3-DeepDive (main)
$ uv add --dev ipykernel

# If you need to manipulate the project's environment from within the notebook, you may need to add uv as an explicit development dependency
abhis@Tinku MINGW64 ~/Desktop/LangChain-v0.3-DeepDive (main)
$ uv add --dev uv

# From there, you can use !uv add pydantic to add pydantic to the project's dependencies,

```

- download each file from resource when working on.

## 01-intro.ipynb

- i will be using GEMINI API KEY and it's libraries.
- To get GEMINI_API_KEY - go to [apiKey-docs](https://aistudio.google.com/app/apikey), and [Gemini Developer API docs](https://ai.google.dev/gemini-api/docs)

- Took my time to understand things.

## 02-langsmith.ipynb

- `Langsmith` - an observability service for the langchain-ecosystem.
