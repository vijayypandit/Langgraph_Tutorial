"""
Replace README content with a concise, indexed, beginner-friendly version.
"""


# 📚 LangGraph Tutorial Series — Beginner-Friendly

This repository contains a short series of hands-on notebooks that demonstrate LangGraph workflow patterns. The README is streamlined for learners: a clear, indexed Table of Contents, quick setup, and the current progress update.

## 📖 Table of Contents (Indexed)

1. [1_bmi_workflow.ipynb](1_bmi_workflow.ipynb) — 🩺 Sequential BMI example (Beginner)
2. [2_simple_lm_ntegration.ipynb](2_simple_lm_ntegration.ipynb) — 🧠 Simple LLM integration (Beginner)
3. [3_prompt_chainging.ipynb](3_prompt_chainging.ipynb) — 🔗 Prompt chaining examples (Intermediate)
4. [4_batsman_workflow.ipynb](4_batsman_workflow.ipynb) — 🏏 Parallel workflow example (Intermediate)
5. [5_UPSC_essay_workflow.ipynb](5_UPSC_essay_workflow.ipynb) — 📝 Essay pipeline (Intermediate)
6. [6_quadratic_equation.ipynb](6_quadratic_equation.ipynb) — ➗ Math workflow example (Beginner)
7. [7_review_reply_workfllow.ipynb](7_review_reply_workfllow.ipynb) — 💬 Conditional reply workflow (Intermediate)
8. [8_X_Post_Generation.ipynb](8_X_Post_Generation.ipynb) — 🐦 Iterative post generation (Intermediate)
9. [9_basic_chatbot.ipynb](9_basic_chatbot.ipynb) — 🤖 Basic chatbot (In progress)
10. [10_persistance.ipynb](10_persistance.ipynb) — 🧠 Persistence + checkpoint memory (Intermediate)

## 📘 Persistence Tutorial (Notebook 10)

**File:** [`10_persistance.ipynb`](10_persistance.ipynb)

#### 📝 What it teaches
- How to save and inspect workflow state using LangGraph checkpointing
- How `InMemorySaver` records short-term memory snapshots
- How `thread_id` isolates separate workflow executions

#### 🔧 Core concepts
1. `InMemorySaver()` is used as a checkpointer when compiling the graph.
2. `workflow.invoke(..., config={'configurable': {'thread_id': 1}})` runs the workflow and stores state under `thread_id = 1`.
3. `workflow.get_state(config)` returns the latest persisted state snapshot.
4. `workflow.get_state_history(config)` returns the timeline of saved snapshots for that session.

#### 💡 Why it matters
- Persists intermediate workflow state across nodes
- Gives visibility into the "short-term memory" of a graph execution
- Enables multiple concurrent sessions with separate state histories

#### 🧠 Short-term memory flow

```
[Input data] -> workflow.invoke(...)
      |
      v
[StateGraph execution]
      |
      +--> generate_joke node
      |         |
      |         +--> LLM call
      |         +--> save checkpoint snapshot
      |
      +--> generate_explanation node
                |
                +--> LLM call
                +--> save checkpoint snapshot
      |
      v
[InMemorySaver checkpoints]
      |
      +--> thread_id=1: current state + history
      +--> thread_id=2: separate state + history
```

## 🗂️ Other files

- [main.py](main.py) — ⚙️ optional runtime/demo runner
- [requirements.txt](requirements.txt) — 📦 Python dependencies
- [pyproject.toml](pyproject.toml) — 🧾 project metadata
- [essay.txt](essay.txt) — ✍️ sample input used by tutorials

## 📌 Project Status

- Notebooks 1–8: ✅ complete and ready to open.
- Notebook 9 (`9_basic_chatbot.ipynb`): 🔧 in development — building a basic chatbot that ties together earlier patterns.
- Notebook 10 (`10_persistance.ipynb`): ✅ complete — demonstrates checkpoint persistence and short-term workflow memory.

## ⚡ Quick Start

### ✅ Prerequisites

- Python 3.10+
- A virtual environment (recommended)

### 💾 Install

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

### ▶️ Run

- Open notebooks in order with Jupyter or VS Code (recommended):
      - `code .` then open the notebooks from the Explorer
- To run a single notebook from the command line (requires nbconvert or jupyter):
      - `jupyter notebook 1_bmi_workflow.ipynb`

## 🎓 How to Learn from this Repo

- Start with `1_bmi_workflow.ipynb` and follow notebooks sequentially.
- Each notebook is self-contained — read the annotated cells and run them interactively.
- Use `main.py` as a compact reference or demo if available.

## 🛠️ Minimal Tech Notes

- These examples use LangGraph-style workflow patterns and may call LLMs (set API keys in `.env` before running notebook cells that use remote models).

## 🤝 Want to Contribute or Improve

- Open a PR with notebook improvements or clearer explanations.
- If you add a new tutorial, add its entry to the Table of Contents above.

---

If you'd like, I can (a) shorten further to a one-page guide, (b) add anchor links per notebook section, or (c) open and update `9_basic_chatbot.ipynb` with progress notes. Which would you prefer?

| Issue | Solution |
|-------|----------|
| **Nodes not connecting** | Verify output/input state keys match |
| **LLM not responding** | Check API keys and rate limits |
| **State not updating** | Ensure nodes return updated state |
| **Graph not executing** | Validate graph structure with `.visualize()` |

---

## 🔁 Updating This README

**When adding new tutorials:**

1. Add entry to [Table of Contents](#table-of-contents)
2. Create new section with template below:

```markdown
### N. Tutorial Name

**File:** [`N_filename.ipynb`](N_filename.ipynb)

#### 📝 Description
Brief overview...

#### 🔧 What We Did
- Bullet points...

#### 💡 How We Did It
1. Step by step...

#### 📦 Use Cases
- Use case 1...

#### 🎓 Difficulty: **Level** 🟢/🟡/🟠
```

3. Update [Learning Path](#learning-path) diagram
4. Add to tech stack if new technologies introduced

---

## 🔗 Additional Resources

### 🔎 Official Documentation
- [LangGraph Official Docs](https://langchain-ai.github.io/langgraph/)
- [LangChain Documentation](https://python.langchain.com/)
- [OpenAI API Docs](https://platform.openai.com/docs)

### 📚 Related Concepts
- Graph Theory & State Machines
- Prompt Engineering Best Practices
- LLM API Usage Patterns
- Async/Concurrent Workflows

---

## 📈 Project Statistics

```
📊 Repository Stats:
├── Tutorials: 3 (Completed) + 3 (Planned) = 6 Total
├── Lines of Code: Growing 📈
├── Coverage: Sequential Flows ✅
├── Next Phase: Conditional Routing 🔄
└── Advanced Features: Planned 📋
```

---

## 👨‍💻 Author & Contribution

Created as a comprehensive learning resource for LangGraph and agentic AI workflows.

**Current Focus**: Sequential Flows and LM Integration  
**Next Phase**: Conditional Routing & Loops  
**Long-term**: Advanced Agent Patterns & Memory Systems

---

## 📝 License

This repository is provided for educational purposes.

---

## 🎯 Key Takeaways

| Topic | Key Concept |
|-------|-------------|
| **Sequential Flows** | Chain operations in order with clear state transitions |
| **State Management** | Track data through workflow lifecycle |
| **LLM Integration** | Seamlessly embed AI into deterministic workflows |
| **Scalability** | Build from simple to complex workflows incrementally |
| **Production Ready** | LangGraph provides patterns suitable for production use |

---

<div align="center">

### 🚀 Ready to Master LangGraph?

**Start with Tutorial 1** → Understand fundamentals → Build your own workflows

**Happy Learning! 🎓**

</div>

---

**Last Updated**: May 28, 2026  
**Series Status**: 🟢 Active Development  
**Next Update**: When new content is added

