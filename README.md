# Google-ADK-examples
Example to create and use Google ADK to create agents


# Agent Development Kit (ADK) for Python

A comprehensive framework for building, testing, and running AI agents using Python. The ADK streamlines the process of creating intelligent agents that can utilize tools, manage state, and interact with Large Language Models (LLMs) like Gemini, Chatgpt, claude, etc.

## 📋 Prerequisites

Before you begin, ensure you have the following installed:
*   **Python**: Version 3.10 or later
*   **pip**: Python package installer

## 🚀 Installation

### 1. Install the Package
Install the ADK using pip:

```bash 
pip install google-adk
```

### 2. Set up a Virtual Environment (Recommended)

It is highly recommended to use a virtual environment to manage dependencies.

Create the environment:

```
python -m venv .venv
```


Activate the environment:

```

Windows (CMD): .venv\Scripts\activate.bat[1]

Windows (PowerShell): .venv\Scripts\Activate.ps1[1]

MacOS / Linux: source .venv/bin/activate[1]
```

### ⚡ Quick Start

## 1. Create an Agent Project

Use the ADK CLI to generate the scaffolding for a new agent project:

```
adk create my_agent
```


This creates a directory my_agent/ with the following structure:

* agent.py: Main control code for the agent

* .env: Configuration file for API keys.

* __init__.py: Package initialization.

## 2. Configure API Key

This project requires a Gemini API key. If you don't have one, get it from Google AI Studio.

Create a .env file in your project directory and add your key:

```
# Inside my_agent/ directory
echo 'GOOGLE_API_KEY="YOUR_API_KEY"' > .env
```



## 3. Update Agent Code

Open my_agent/agent.py and define your agent. Below is an example of a simple agent equipped with a custom tool to tell the time:

```
from google.adk.agents.llm_agent import Agent

# Mock tool implementation
def get_current_time(city: str) -> dict:
    """Returns the current time in a specified city."""
    return {"status": "success", "city": city, "time": "10:30 AM"}

# Define the agent
root_agent = Agent(
    model='gemini-2.5-flash',
    name='root_agent',
    description="Tells the current time in a specified city.",
    instruction="You are a helpful assistant that tells the current time in cities. Use the 'get_current_time' tool for this purpose.",
    tools=[get_current_time],
)
```



### 🏃 Usage

You can run your agent in two modes: via the terminal (CLI) or through a local web interface.

Option A: Command-Line Interface (CLI)

Run the agent interactively in your terminal:

```
adk run my_agent
```

Option B: Web Interface

Launch a local development server to test your agent with a chat UI.

Important: Run this command from the parent directory containing your agent folder.

```
# If your agent is in ./my_agent/
adk web --port 8000
````

Open your browser to: http://localhost:8000

Select your agent from the dropdown and start chatting.

### ⚠️ Caution: The ADK Web interface is intended for development and debugging purposes only. Do not use it for production deployments.
