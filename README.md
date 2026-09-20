# LangChain Runnable

Learn LangChain **Runnables** from scratch — from a fake `NakliLLM` + `NakliPrompt` chain to real `RunnableSequence`, `RunnableParallel`, `RunnablePassthrough`, `RunnableBranch`, and `RunnableLambda` with Groq.

## Contents

| File | What it covers |
|------|----------------|
| `1_runnable_sequence_intro.ipynb` | Builds `Runnable` from scratch: Fake LLM (`predict`), Fake Prompt (`format`), Fake Chain (`run`), then standardized `invoke()`, custom `RunnableConnector`, and chaining chains |
| `runnable_sequence.py` | `RunnableSequence(prompt1, model, parser, prompt2, model, parser)` — joke -> explain |
| `runnable_parallel.py` | `RunnableParallel` — tweet + LinkedIn post in parallel |
| `runnable_passthrough.py` | `RunnablePassthrough` — keep `joke` while adding `explanation` |
| `runnable_branch.py` | `RunnableBranch` — summarize only if report > 300 words, else passthrough |
| `runnable_lambda.py` | `RunnableLambda(word_count)` + `RunnableParallel` — joke + word count |

## Setup

Requires Python >= 3.10.

```bash
pip install -e ".[notebook]"
```

Create a `.env` file in the project root:

```env
GROQ_API_KEY=your_key_here
```

## Run

```bash
python runnable_sequence.py
python runnable_parallel.py
python runnable_passthrough.py
python runnable_branch.py
python runnable_lambda.py
```

Open the intro notebook:

```bash
jupyter notebook 1_runnable_sequence_intro.ipynb
```

## Model

All `.py` examples use:

```python
from langchain_groq import ChatGroq
model = ChatGroq(model="openai/gpt-oss-20b")
```

## Key Idea

Different components use different methods (`format`, `predict`, `run`). `Runnable` standardizes everything to `invoke()`, so any prompt, model, parser, or custom function can be chained with `|` or `RunnableSequence`.
