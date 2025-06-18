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

## 03-prompts.ipynb

This notebook provides a deep dive into various prompting techniques using LangChain. The goal is to understand how to effectively structure prompts to control the behavior and output of Large Language Models (LLMs).

What We Did and Learned:
Environment Setup:

Installed necessary Python packages: langchain-core, langchain-openai, langchain-community, and langsmith.
Configured environment variables for LangSmith to enable tracing and monitoring of our LLM calls.
Initialized a ChatGoogleGenerativeAI model (gemini-2.0-flash) to serve as our LLM.
Basic Prompt Templating:

We learned about the core components of a prompt, especially in a Retrieval Augmented Generation (RAG) context: system rules, external context, and the user's question.
We used ChatPromptTemplate to create dynamic and reusable prompt structures. This allows us to define placeholders like {context} and {query} that are filled in at runtime.
We built a simple pipeline using LangChain Expression Language (LCEL) with the | operator to connect our prompt template to the LLM.

// ...existing code...
pipeline = (
{
"query": lambda x: x["query"],
"context": lambda x: x["context"]
}
| prompt_template
| llm
)
// ...existing code...

We invoked this pipeline with a sample context and query to generate a contextual answer.
Few-Shot Prompting:

We explored few-shot prompting, a technique where we provide the LLM with several examples of desired input-output pairs to guide its response format.
We used the FewShotChatMessagePromptTemplate to structure these examples.
This was demonstrated by forcing the LLM to produce a specific, complex markdown format that it failed to generate with instructions alone.

// ...existing code...
few_shot_prompt = FewShotChatMessagePromptTemplate(
example_prompt=example_prompt,
examples=examples,
)

prompt_template = ChatPromptTemplate.from_messages([
("system", new_system_prompt),
few_shot_prompt,
("user", "{query}"),
])

pipeline = prompt_template | llm
// ...existing code...

Chain of Thought (CoT) Prompting:

We learned about Chain of Thought (CoT) prompting, which instructs the LLM to "think step-by-step" by breaking down a problem before giving a final answer.
We tested this on a numerical reasoning question ("How many keystrokes to type numbers from 1 to 500?").
We observed that explicitly asking the LLM to follow a step-by-step process significantly improved its accuracy, leading to the correct answer (1392) instead of a hallucinated one.
We also noted that many modern LLMs are trained to use CoT by default, but being explicit in the prompt can still enhance performance and reliability.
