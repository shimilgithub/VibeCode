# VibeCode - Multi-Agent AI Code Builder

VibeCode is an AI tool that turns your ideas into working software. Just describe what you want in plain English, and it creates the project for you.
## Description

VibeCode acts as a mini engineering team using a multi-agent system.You give it an idea, and it figures out what needs to be done, creates a step-by-step plan, writes the code, and saves the finished project on your computer.
## Features

*   **Planner Agent:** Converts user prompts into a structured engineering project plan (app name, tech stack, features, and required files).
*   **Architect Agent:** Breaks down the high-level plan into explicit, step-by-step implementation tasks.
*   **Coder Agent:** A LangGraph tool-using agent that reads existing files, writes new code, and ensures integration.
*   **Local File Output:** All generated code is safely saved into a `generated_project` directory on your machine.
*   **Customizable Recursion Limit:** Allows you to increase the execution limits for larger, more complex projects.

## Tech Stack

*   **Python:** >= 3.13
*   **Frameworks:** LangGraph, LangChain, Pydantic
*   **LLM Provider:** Groq (using `openai/gpt-oss-120b` via Groq)

## Repository Structure
* **main.py:** The main entry point and command-line interface. It accepts a natural language prompt, handles optional arguments (like the recursion limit), and triggers the compiled LangGraph agent to start the generation process.
* **graph.py:** The main orchestration file. It defines the three primary nodes (planner_agent, architect_agent, coder_agent) and compiles the LangGraph state machine.
* **states.py:** Contains the Pydantic data models that ensure typed, structured data is passed between the agents.
* **prompts.py:** Contains system prompts that instruct the LLM on how to behave for each specific role.
* **tools.py:** Defines the file-system operations (write_file, read_file, list_files, get_current_directory) that the Coder Agent uses to write the actual code into the generated_project folder.

## Installation

1.  **Clone the repository** 
```bash
git clone https://github.com/shimilgithub/VibeCode.git
cd VibeCode
```

2.  **Install dependencies** using `pip`:
```bash
    pip install -r requirements.txt
```

3.  **Set up environment variables:**
    Create a `.env` file in the root directory and add your Groq API key:
```env
    GROQ_API_KEY=your_api_key_here
```

## Usage

Run the main application script:

```bash
python main.py
```
When prompted, enter the description of the project you want to build:

```bash
Enter your project prompt: Build a colourful modern todo app in html css and js
```
Optional Arguments:

You can adjust the LangGraph recursion limit for larger projects using the -r flag

```bash
python main.py -r 150
```