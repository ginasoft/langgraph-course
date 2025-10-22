# LangGraph🦜🕸️

## 🚀 What You'll Build

- **Agentic RAG** – Retrieval-Augmented Generation with self-correction & adaptive routing
- **ReAct Agent** – Reasoning + Acting loop implemented in LangGraph
- **Reflection & Reflexion Agents** – Agents that critique and improve themselves
- **Multi-Step Graphs** – Complex flows with conditionals, parallelism, and web-search tools

## 📋 Prerequisites

Before starting this course, you should have:

- **Python 3.9+** installed on your system
- Basic understanding of Python programming
- Familiarity with AI/LLM concepts (helpful but not required)
- An OpenAI API key or access to other LLM providers

## 🛠️ Installation

### 1. Clone the Repository

```bash
git clone <repository-url>
cd langgraph-course
```

### 2. Create a Virtual Environment

**On Windows:**
```bash
python -m venv venv
venv\Scripts\activate
```

**On macOS/Linux:**
```bash
python -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install --upgrade pip
pip install langgraph langchain langchain-openai langchain-community
pip install tavily-python  # For web search capabilities
pip install jupyter notebook  # If using Jupyter notebooks
```

### 4. Set Up Environment Variables

Create a `.env` file in the project root:

```bash
OPENAI_API_KEY=your_openai_api_key_here
TAVILY_API_KEY=your_tavily_api_key_here  # Optional, for web search
```

Or export them directly:

**On Windows:**
```bash
set OPENAI_API_KEY=your_openai_api_key_here
set TAVILY_API_KEY=your_tavily_api_key_here
```

**On macOS/Linux:**
```bash
export OPENAI_API_KEY=your_openai_api_key_here
export TAVILY_API_KEY=your_tavily_api_key_here
```

## 📚 Course Structure

This course is organized into modules, each focusing on a specific LangGraph concept:

```
langgraph-course/
├── 01-agentic-rag/          # RAG with self-correction
├── 02-react-agent/          # ReAct pattern implementation
├── 03-reflection-agents/    # Self-improving agents
├── 04-multi-step-graphs/    # Complex workflows
└── examples/                # Additional examples and templates
```

## 🎯 What is LangGraph?

LangGraph is a library for building stateful, multi-actor applications with LLMs. It extends LangChain with:

- **State Management** – Maintain context across multiple steps
- **Cyclical Flows** – Create loops and conditional branches
- **Human-in-the-Loop** – Interrupt and resume agent execution
- **Persistence** – Save and restore agent state

## 🚦 Quick Start

### Example: Simple LangGraph Flow

```python
from langgraph.graph import StateGraph, END
from typing import TypedDict

# Define state
class State(TypedDict):
    message: str
    count: int

# Define nodes
def process_message(state: State) -> State:
    return {
        "message": state["message"].upper(),
        "count": state["count"] + 1
    }

# Build graph
workflow = StateGraph(State)
workflow.add_node("process", process_message)
workflow.set_entry_point("process")
workflow.add_edge("process", END)

# Compile and run
app = workflow.compile()
result = app.invoke({"message": "hello", "count": 0})
print(result)
```

## 📖 Learning Path

1. **Start with Agentic RAG** – Learn how to build intelligent retrieval systems
2. **Master ReAct Agents** – Understand the reasoning and acting loop
3. **Explore Reflection** – Build agents that improve through self-critique
4. **Build Complex Graphs** – Combine concepts into sophisticated workflows

## 🔑 Key Concepts

### State Management
LangGraph maintains state as data flows through your graph, enabling context-aware processing.

### Nodes and Edges
- **Nodes**: Functions that process state
- **Edges**: Connections that determine flow between nodes

### Conditional Routing
Route between different paths based on state or LLM decisions.

### Cycles and Loops
Create iterative processes where agents can refine their outputs.

## 🧪 Running Examples

Each module contains examples that can be run directly:

```bash
# Navigate to a module
cd 01-agentic-rag

# Run the example
python main.py
```

Or use Jupyter notebooks:

```bash
jupyter notebook
```

## 🔧 Troubleshooting

### Common Issues

**Import Errors:**
```bash
pip install --upgrade langgraph langchain
```

**API Key Issues:**
- Ensure your `.env` file is in the project root
- Check that API keys are valid and have sufficient credits
- Install `python-dotenv` if using `.env` files: `pip install python-dotenv`

**Memory Issues:**
- Use streaming for large responses
- Implement checkpointing for long-running agents

## 📚 Additional Resources

- [LangGraph Documentation](https://langchain-ai.github.io/langgraph/)
- [LangChain Documentation](https://python.langchain.com/)
- [OpenAI API Documentation](https://platform.openai.com/docs)
- [Tavily Search API](https://tavily.com/)

## 🤝 Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

Built with:
- [LangGraph](https://github.com/langchain-ai/langgraph)
- [LangChain](https://github.com/langchain-ai/langchain)
- [OpenAI](https://openai.com/)

---

Happy Learning! 🎉
