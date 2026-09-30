# 🔬 Multi-Agent AI Research Assistant

An autonomous **Agentic AI research system** that uses multiple
specialized AI components to search the live web, extract relevant
information, generate a structured research report, and evaluate the
quality of the final output.

Instead of relying only on an LLM's existing knowledge, this project
combines **real-time web search, web scraping, LangChain agents, LCEL
chains, shared state, and a Streamlit interface** to create an
end-to-end research workflow.

------------------------------------------------------------------------

## 🚀 Project Overview

The **Multi-Agent AI Research Assistant** accepts a research topic from
the user and automatically performs the major stages of online research.

The system uses specialized components for:

1.  🔎 **Searching** the web for recent and relevant information
2.  📖 **Reading and extracting** useful content from discovered
    webpages
3.  ✍️ **Writing** a structured research report from the collected
    information
4.  🧠 **Reviewing** the generated report and providing feedback

The final workflow is accessible through a simple **Streamlit UI**,
making the research pipeline easy to use without interacting directly
with the terminal.

------------------------------------------------------------------------

## ✨ Key Features

-   🌐 Real-time web research using the **Tavily API**
-   🤖 Multi-agent workflow using **LangChain**
-   🔎 Dedicated Search Agent for information discovery
-   📄 Reader Agent for deeper webpage analysis
-   🕷️ Web content extraction using **Beautiful Soup**
-   ✍️ LLM-powered report generation
-   🧠 Critic Chain for report evaluation and feedback
-   🔗 **LCEL pipelines** for chaining AI operations
-   🧰 Tool calling with custom research tools
-   💾 Shared state for passing information across the research pipeline
-   🖥️ Interactive **Streamlit** user interface
-   🔐 Environment-variable based API key management

------------------------------------------------------------------------

## 🧠 System Architecture

``` text
                    ┌─────────────────────┐
                    │    Research Topic   │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │    Search Agent     │
                    │    Tavily API       │
                    └──────────┬──────────┘
                               │
                    URLs + Search Results
                               │
                               ▼
                    ┌─────────────────────┐
                    │    Reader Agent     │
                    │  Beautiful Soup     │
                    └──────────┬──────────┘
                               │
                     Extracted Web Content
                               │
                               ▼
                    ┌─────────────────────┐
                    │    Writer Chain     │
                    │   LLM + LCEL        │
                    └──────────┬──────────┘
                               │
                       Research Report
                               │
                               ▼
                    ┌─────────────────────┐
                    │    Critic Chain     │
                    │ Review + Feedback   │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │    Final Output     │
                    │    Streamlit UI     │
                    └─────────────────────┘
```

------------------------------------------------------------------------

## ⚙️ How It Works

### 1. Search Agent

The user provides a research topic. The **Search Agent** uses the
Tavily-powered search tool to retrieve relevant web results, including
source titles, URLs, and useful snippets.

### 2. Reader Agent

The URLs discovered during search are passed to the **Reader Agent**. It
uses a custom scraping tool built with **Requests** and **Beautiful
Soup** to extract readable text from webpages for deeper research.

### 3. Writer Chain

The collected search results and extracted webpage content are passed to
the **Writer Chain**. An LLM processes this research context and creates
a structured report.

### 4. Critic Chain

The generated report is passed to the **Critic Chain**, which reviews
the output and provides an evaluation and feedback on the research
report.

### 5. Streamlit Interface

The complete pipeline is connected to a **Streamlit application**,
allowing users to enter a topic and interact with the research system
through a clean graphical interface.

------------------------------------------------------------------------

## 🛠️ Tech Stack

  Technology           Purpose
  -------------------- -------------------------------------------
  **Python**           Core programming language
  **LangChain**        Agent and LLM application framework
  **OpenAI API**       Large Language Model integration
  **Tavily API**       Live web search and information retrieval
  **Beautiful Soup**   Webpage parsing and content extraction
  **Requests**         Fetching webpage content
  **LCEL**             Building composable LLM pipelines
  **ReAct Agents**     Tool-enabled agent workflow
  **Streamlit**        Interactive user interface
  **python-dotenv**    Environment variable management

------------------------------------------------------------------------

## 📂 Project Structure

``` text
multi-agent-system/
│
├── app.py                 # Streamlit user interface
├── pipeline.py            # Main research pipeline
├── agents.py              # Search/Reader agents and AI chains
├── tools.py               # Tavily search and web scraping tools
├── requirements.txt       # Project dependencies
├── .env                   # API keys (do not upload to GitHub)
├── .gitignore             # Files excluded from Git
└── README.md              # Project documentation
```

> File names may be adjusted if your local implementation uses a
> slightly different structure.

------------------------------------------------------------------------

## 🔧 Installation & Setup

### 1. Clone the Repository

``` bash
git clone <your-repository-url>
cd multi-agent-system
```

### 2. Create a Virtual Environment

Using `uv`:

``` bash
uv venv
```

Activate the environment according to your operating system.

### 3. Install Dependencies

``` bash
pip install -r requirements.txt
```

If you are using `uv` for package installation:

``` bash
uv pip install -r requirements.txt
```

### 4. Configure Environment Variables

Create a `.env` file in the project root:

``` env
OPENAI_API_KEY=your_openai_api_key
TAVILY_API_KEY=your_tavily_api_key
```

> ⚠️ **Never commit your `.env` file or API keys to GitHub.**

Add `.env` to `.gitignore`:

``` gitignore
.env
.venv/
__pycache__/
```

------------------------------------------------------------------------

## ▶️ Running the Application

Start the Streamlit interface with:

``` bash
streamlit run app.py
```

Streamlit will launch the application in your browser.

Enter a research topic and run the research pipeline.

Example:

``` text
Impact of Artificial Intelligence on the Healthcare Industry
```

The system will search for information, extract relevant webpage
content, generate a research report, and evaluate the final response.

------------------------------------------------------------------------

## 🔄 Research Workflow

``` text
User Query
    ↓
Search Agent
    ↓
Tavily Web Search
    ↓
Relevant URLs & Snippets
    ↓
Reader Agent
    ↓
Beautiful Soup Web Scraping
    ↓
Extracted Research Content
    ↓
Writer Chain
    ↓
Structured Research Report
    ↓
Critic Chain
    ↓
Evaluation & Feedback
    ↓
Final Output
```

------------------------------------------------------------------------

## 🎯 What This Project Demonstrates

This project demonstrates practical experience with:

-   Agentic AI architecture
-   Multi-agent collaboration
-   Large Language Model integration
-   Tool calling
-   ReAct-style agents
-   Real-time information retrieval
-   Web scraping and content extraction
-   Prompt engineering
-   LangChain
-   LCEL pipelines
-   Shared-state workflow management
-   API integration
-   Streamlit application development
-   Modular Python project design

------------------------------------------------------------------------

## 🔐 Security

API keys should always be stored in environment variables.

Do **not** write API keys directly inside Python files and do not push
the `.env` file to a public repository.

If an API key is accidentally committed to GitHub, revoke it immediately
and generate a new key.

------------------------------------------------------------------------

## 🔮 Possible Future Improvements

The current architecture can be extended with features such as:

-   Research history
-   Exporting reports
-   Additional research tools
-   More specialized research agents
-   Source management and citation improvements
-   Persistent research storage
-   Enhanced UI/UX
-   Deployment as a hosted web application

These are potential extensions and are not part of the current
implementation.

------------------------------------------------------------------------

## 💡 Why This Project?

Traditional chatbots typically respond directly to a prompt using an
LLM. This project explores a more advanced **agentic workflow**, where
different components are responsible for different research tasks.

By separating **searching, reading, writing, and reviewing**, the
project demonstrates how multiple AI components and external tools can
be orchestrated into a complete research application.

------------------------------------------------------------------------

## 👩‍💻 Author

**Radhika Sihra**

If you find this project useful, consider giving the repository a ⭐.

------------------------------------------------------------------------

## 📄 License

This project is intended for educational and portfolio purposes. Add a
license file if you plan to distribute or reuse the project under a
specific open-source license.
