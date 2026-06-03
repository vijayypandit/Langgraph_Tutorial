# 🤖 LangGraph Tutorial Series

> **Mastering Agentic AI Workflows with LangGraph**  
> A comprehensive series of hands-on tutorials exploring the power of LangGraph for building complex, stateful AI applications.

---

## 📋 Table of Contents

| # | Tutorial | Status | Topics | Difficulty |
|---|----------|--------|--------|------------|
| 1 | [BMI Workflow](#1-bmi-workflow) | ✅ Completed | Sequential Flows, State Management | 🟢 Beginner |
| 2 | [Simple LM Integration](#2-simple-lm-integration) | ✅ Completed | Language Models, Graph Integration | 🟢 Beginner |
| 3 | [Prompt Chaining](#3-prompt-chaining) | ✅ Completed | Multi-step Chains, Sequential Flows | 🟡 Intermediate |
| 4 | Batsman Workflow | ✅ Completed | Parallel Workflows, Metric Merge | 🟡 Intermediate |
| 5 | UPSC Essay Workflow | ✅ Completed | Structured Output, Evaluation | 🟡 Intermediate |
| 6 | *Coming Soon* | ⏳ Planned | Memory & State Persistence | 🟠 Advanced |

---

## 🎯 What is LangGraph?

**LangGraph** is a Python framework for building stateful AI workflows with clear execution paths, reusable nodes, and explicit branching.

- Build multi-step workflows as graph structures
- Keep shared state and transitions explicit
- Support sequential, conditional, and parallel execution
- Integrate language models and external tools inside nodes

---

## 🔄 Workflow Patterns

### Sequential Workflow

A sequential workflow follows a single ordered path where each node depends on the previous step.

```
START → validate_input → calculate_bmi → format_result → END
```

Example: `1_bmi_workflow.ipynb`

### Parallel Workflow

A parallel workflow executes multiple independent branches from the same starting state and merges results later.

```
               ┌───────────┐
               │ branch A  │
               ├───────────┤
START ───────▶ │ branch B  │
               ├───────────┤
               │ branch C  │
               └─────┬─────┘
                     │
                     ▼
                merge_results
                     │
                     ▼
                     END
```

- Best when several tasks can run independently.
- Use it when branches do not require each other’s output before execution.
- Example: `4_batsman_workflow.ipynb` uses parallel branches to compute multiple metrics and combine them in one summary.

---

## 📘 Key Terms to Learn

- **Node**: a named computation step in the graph.
- **Edge**: a directed connection that routes execution between nodes.
- **Flow**: the complete execution path from START to END.
- **START**: entry point that initializes initial state.
- **END**: exit point that returns the final state.
- **State**: shared context data that nodes read and update.
- **Parallel branch**: an independent workflow path that runs alongside others.
- **Merge**: combining outputs from parallel branches back into one state.

---

## 🚀 Quick Start

### Prerequisites

- Python 3.10+
- pip or `uv` package manager
- Virtual environment (recommended)

### Installation

```bash
# Activate virtual environment
.\.venv\Scripts\Activate.ps1  # Windows PowerShell
# or
source .venv/bin/activate       # Linux/macOS

# Install dependencies
uv pip install -r requirements.txt
# or
pip install -r requirements.txt
```

### Run the parallel workflow example

Open `4_batsman_workflow.ipynb` in Jupyter or VS Code and run the cells. This notebook demonstrates the parallel workflow pattern with independent branches and result merging.

---

## 📊 Quick Reference: Core Concepts

| Concept | Definition | Role | Example |
|---------|-----------|------|---------|
| **Node** | Unit of computation | Performs work | `def validate(state): ...` |
| **Edge** | Connection between nodes | Routes flow | `graph.add_edge(A, B)` |
| **Flow** | Complete execution path | Journey of state | START → A → B → END |
| **START** | Entry point | Initial state | `graph.add_edge(START, A)` |
| **END** | Exit point | Final result | `graph.add_edge(B, END)` |

---

## 🎓 Complete Graph Pattern

Here's how all concepts work together:

```
          ┌──────────────────────────────────┐
          │   STATE MACHINE PATTERN          │
          └──────────────────────────────────┘
          
    ╔════════════╗
    ║   START    ║ ← Entry point
    ║ (Initialize)
    ╚═════╤══════╝
          │
          │ Edge: Direct
          ▼
    ╔════════════════╗
    ║  Node A        ║ ← Computation Unit
    ║  (Validate)    ║  (Reads & modifies state)
    ╚═════╤══════════╝
          │
          │ Edge: Conditional
          ├─────────────────────────┐
          │                         │
    Success?                    Error?
          │                         │
          ▼                         ▼
    ╔════════════╗           ╔════════════╗
    ║  Node B    ║           ║ Node E     ║
    ║(Process)  ║           ║(Error Log) ║
    ╚═════╤══════╝           ╚═════╤══════╝
          │                         │
          │ Edge: Direct           │
          └──────────┬─────────────┘
                     │
                     ▼
          ╔════════════════╗
          ║  Node C        ║
          ║  (Format)      ║
          ╚═════╤══════════╝
                │
                │ Edge: Direct
                ▼
          ╔════════════╗
          ║    END     ║ ← Exit point
          ║  (Return)  ║  (Final state)
          ╚════════════╝
```

---

## 🚀 Quick Start

### Prerequisites

- Python 3.10+
- pip or `uv` package manager
- Virtual environment (recommended)

### Installation

```bash
# Activate virtual environment
.\.venv\Scripts\Activate.ps1  # Windows PowerShell
# or
source .venv/bin/activate     # Linux/macOS

# Install dependencies
uv pip install -r requirements.txt
# or
pip install -r requirements.txt
```

### Verify Installation

```python
import langgraph
import langchain
print("✅ LangGraph and LangChain installed successfully!")
```

---

## 📚 Tutorials Breakdown

- **`1_bmi_workflow.ipynb`**: Sequential BMI workflow; learn graph basics, state management, and node chaining.
- **`2_simple_lm_ntegration.ipynb`**: Sequential LLM integration; learn prompt-driven nodes and response handling.
- **`3_prompt_chainging.ipynb`**: Prompt chaining with multi-step text workflows.
- **`4_batsman_workflow.ipynb`**: Parallel workflow example; compute branches independently and merge results.
- **`5_UPSC_essay_workflow.ipynb`**: Essay evaluation pipeline with structured output and workflow orchestration.

The notebook files contain the full code examples, while this README highlights the main patterns and the new parallel workflow design.

---

## 📊 Learning Path

```
START
  │
  ├─→ 🟢 Beginner: Sequential Basics (1_bmi_workflow)
  │     └─→ Learn state, nodes, edges
  │
  ├─→ 🟢 Beginner: LM Integration (2_simple_lm_ntegration)
  │     └─→ Add AI to workflows
  │
  ├─→ 🟡 Intermediate: Prompt Chains (3_prompt_chaining)
  │     └─→ Multi-step reasoning
  │
  ├─→ 🟡 Intermediate: Conditional Routing (Coming Soon)
  │     └─→ Dynamic decision making
  │
  └─→ 🟠 Advanced: Agent Loops & Memory (Coming Soon)
        └─→ Autonomous agent systems
```

---

## 🛠️ Tech Stack

| Component | Version | Purpose |
|-----------|---------|---------|
| **LangGraph** | Latest | Workflow orchestration |
| **LangChain** | Latest | LLM abstractions |
| **Python** | 3.10+ | Runtime |
| **OpenAI/Groq/Google** | API | Language models |
| **Jupyter** | Latest | Interactive notebooks |

---

## 🔐 Environment Setup

Create a `.env` file in the project root:

```env
# Language Model APIs
OPENAI_API_KEY=your_key_here
GROQ_API_KEY=your_key_here
GOOGLE_API_KEY=your_key_here

# Optional configurations
LOG_LEVEL=INFO
DEBUG=False
```

---

## 📖 How to Use This Repository

### For Learning

1. **Start with Tutorial 1**: Open `1_bmi_workflow.ipynb` and run cells sequentially
2. **Read the README**: Understand concepts before diving into code
3. **Experiment**: Modify parameters and observe changes
4. **Progress**: Move to next tutorial only after understanding previous one

### For Reference

- Each notebook is **self-contained** with explanations
- Use as **templates** for your own projects
- Adapt **code patterns** to your use cases

### For Development

```bash
# Running a specific notebook
jupyter notebook 1_bmi_workflow.ipynb

# Or use VS Code with Jupyter extension
code .

# Run from command line (if main.py exists)
python main.py
```

---

## 🤝 Best Practices

### ✅ Do's
- ✅ Start with simple workflows before complex ones
- ✅ Always validate state transitions
- ✅ Use meaningful node and edge names
- ✅ Add error handling at each step
- ✅ Document your state schema

### ❌ Don'ts
- ❌ Skip state management setup
- ❌ Create circular dependencies without cycles handling
- ❌ Ignore prompt validation
- ❌ Chain too many steps without checkpoints
- ❌ Hardcode API keys in code

---

## 📞 Common Issues & Solutions

| Issue | Solution |
|-------|----------|
| **Nodes not connecting** | Verify output/input state keys match |
| **LLM not responding** | Check API keys and rate limits |
| **State not updating** | Ensure nodes return updated state |
| **Graph not executing** | Validate graph structure with `.visualize()` |

---

## 🔄 Updating This README

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

## 📚 Additional Resources

### Official Documentation
- [LangGraph Official Docs](https://langchain-ai.github.io/langgraph/)
- [LangChain Documentation](https://python.langchain.com/)
- [OpenAI API Docs](https://platform.openai.com/docs)

### Related Concepts
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

