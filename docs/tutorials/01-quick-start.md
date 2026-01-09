# Tutorial 1: Quick Start

> **Get Noderr Running in Your First Project**

---

## Overview

| | |
|---|---|
| **Difficulty** | Beginner |
| **Time Required** | 15-20 minutes |
| **Prerequisites** | Git, AI assistant, text editor |

### Learning Objectives

By the end of this tutorial, you will:

- Download and install the Noderr framework
- Set up Noderr in a new or existing project
- Run your first Noderr prompt
- Understand the basic file structure

---

## Introduction

This tutorial gets you from zero to your first Noderr-powered development session. We'll download the framework, configure it for your project, and execute the initial setup prompts.

Don't worry if concepts seem unfamiliar—later tutorials will explain everything in depth. For now, focus on getting things running.

---

## Step-by-Step Instructions

### Step 1: Prerequisites Check

**What you'll do**: Verify your environment is ready for Noderr.

1. Open your terminal
2. Check Git is installed:
   ```bash
   git --version
   ```
   You should see a version number (e.g., `git version 2.39.0`)

3. Ensure you have a text editor ready (VS Code, Cursor, Sublime, etc.)

4. Have your AI assistant ready:
   - Claude (claude.ai or API)
   - ChatGPT (chat.openai.com or API)
   - Cursor IDE (built-in AI)
   - Any other LLM assistant

> **Tip**: If using a web-based AI, ensure you can copy/paste long text blocks easily.

**Expected Result**: All prerequisites confirmed available.

---

### Step 2: Download Noderr

**What you'll do**: Get the Noderr starter files.

1. Go to the Noderr releases page:
   ```
   https://github.com/kaithoughtarchitect/noderr/releases
   ```

2. Download `noderr.starter.zip` from the latest release

3. You should have a ZIP file approximately 50-100KB in size

> **Tip**: Bookmark the releases page—new versions add improved prompts and features.

**Expected Result**: `noderr.starter.zip` downloaded to your computer.

---

### Step 3: Set Up Your Project

**What you'll do**: Create a project directory and add Noderr files.

#### Option A: New Project

1. Create a new project directory:
   ```bash
   mkdir my-awesome-project
   cd my-awesome-project
   ```

2. Initialize git:
   ```bash
   git init
   ```

3. Extract Noderr files into your project:
   ```bash
   # Extract the zip file - you should see a 'noderr' folder appear
   unzip ~/Downloads/noderr.starter.zip
   ```

4. Verify the structure:
   ```bash
   ls -la noderr/
   ```
   You should see:
   ```
   noderr_project.md
   noderr_architecture.md
   noderr_tracker.md
   noderr_loop.md
   noderr_log.md
   environment_context.md
   specs/
   prompts/
   planning/
   ```

#### Option B: Existing Project

1. Navigate to your existing project:
   ```bash
   cd /path/to/your/existing-project
   ```

2. Extract Noderr files:
   ```bash
   unzip ~/Downloads/noderr.starter.zip
   ```

3. Verify the `noderr/` folder was created alongside your existing files

> **Tip**: Noderr lives in its own directory and doesn't conflict with your existing code structure.

**Expected Result**: Your project has a `noderr/` directory with all framework files.

---

### Step 4: Make Initial Commit

**What you'll do**: Save the initial Noderr setup to version control.

1. Add all Noderr files:
   ```bash
   git add noderr/
   ```

2. Create the initial commit:
   ```bash
   git commit -m "Add Noderr framework files"
   ```

> **Tip**: This creates a clean starting point. You can always return here if needed.

**Expected Result**: Git shows a successful commit with Noderr files.

---

### Step 5: Run the Installation Prompt

**What you'll do**: Initialize Noderr for your specific project.

1. Open the installation prompt file:
   ```bash
   # View the file (or open in your editor)
   cat noderr/prompts/NDv1.9__Install_And_Reconcile.md
   ```

2. Copy the **entire contents** of the file

3. Open your AI assistant (Claude, ChatGPT, etc.)

4. Paste the prompt and press Enter/Send

5. The AI will:
   - Read all Noderr files
   - Ask you about your project
   - Help you fill in `noderr_project.md`
   - Generate an initial architecture diagram
   - Configure environment context

6. Follow the AI's questions and provide information about:
   - Your project's purpose
   - Technology stack you're using
   - Main features you plan to build

> **Tip**: Be specific about your tech stack. "React frontend with Node.js backend and PostgreSQL" is better than "web app".

**Expected Result**: AI has populated your Noderr files with project-specific information.

---

### Step 6: Verify the Setup

**What you'll do**: Confirm Noderr is properly configured.

1. Check `noderr_project.md`:
   ```bash
   cat noderr/noderr_project.md
   ```
   Should contain your project details, tech stack, and goals.

2. Check `noderr_architecture.md`:
   ```bash
   cat noderr/noderr_architecture.md
   ```
   Should contain a Mermaid diagram with initial components.

3. Check `noderr_tracker.md`:
   ```bash
   cat noderr/noderr_tracker.md
   ```
   Should show initial NodeIDs with `TODO` status.

> **Tip**: If any file looks empty or unchanged, re-run the installation prompt.

**Expected Result**: All three files contain project-specific content.

---

### Step 7: Start Your First Work Session

**What you'll do**: Begin active development with Noderr.

1. Open the session start prompt:
   ```bash
   cat noderr/prompts/NDv1.9__Start_Work_Session.md
   ```

2. Copy the entire contents

3. In a **new conversation** with your AI assistant, paste the prompt

4. The AI will:
   - Read all Noderr files
   - Report current project status
   - Show what's in progress
   - Ask what you want to work on

5. Tell the AI what feature or task you want to tackle

> **Tip**: Start with something small for your first task. "Add a login page" is better than "build the entire authentication system".

**Expected Result**: AI understands your project and is ready to guide you through development.

---

### Step 8: Commit Your Configuration

**What you'll do**: Save your customized Noderr setup.

1. Review changes:
   ```bash
   git status
   git diff noderr/
   ```

2. Stage and commit:
   ```bash
   git add noderr/
   git commit -m "Configure Noderr for project: [your project name]"
   ```

**Expected Result**: Your configured Noderr setup is saved in git.

---

## Practical Exercise

### Your Task

Set up Noderr for a sample "Task Manager" application:

### Requirements

- [ ] Download and extract Noderr starter files
- [ ] Initialize in a new directory called `task-manager`
- [ ] Run the installation prompt with these details:
  - **Project**: Task Manager web app
  - **Stack**: React, Node.js/Express, SQLite
  - **Features**: Create tasks, mark complete, delete tasks
- [ ] Verify all core files are populated
- [ ] Start a work session and ask the AI to propose a Change Set for "user can create a new task"

### Solution

<details>
<summary>Click to reveal solution</summary>

```bash
# 1. Create project
mkdir task-manager
cd task-manager
git init

# 2. Extract Noderr
unzip ~/Downloads/noderr.starter.zip

# 3. Initial commit
git add noderr/
git commit -m "Add Noderr framework files"

# 4. Run installation prompt
# Copy contents of noderr/prompts/NDv1.9__Install_And_Reconcile.md
# Paste to AI assistant
# Answer questions:
#   - Project: Simple task manager for personal use
#   - Stack: React frontend, Express backend, SQLite database
#   - Features: CRUD operations for tasks

# 5. Verify files have content
cat noderr/noderr_project.md
cat noderr/noderr_architecture.md
cat noderr/noderr_tracker.md

# 6. Commit configuration
git add noderr/
git commit -m "Configure Noderr for Task Manager project"

# 7. Start work session
# Copy contents of noderr/prompts/NDv1.9__Start_Work_Session.md
# Paste to AI assistant
# Tell AI: "I want to implement the ability for users to create a new task"

# The AI should propose a Change Set including:
# - UI_TaskForm (or similar)
# - API_CreateTask
# - SVC_TaskService
# - DB_TasksTable
```

</details>

---

## Common Issues & Solutions

| Issue | Cause | Solution |
|-------|-------|----------|
| AI doesn't read files | File paths incorrect | Ensure AI can access your project directory |
| Empty config files | Prompt not fully executed | Re-run installation prompt in new conversation |
| "I don't have access to files" | Web AI limitation | Use an AI with file system access (Cursor, Claude with tools) |
| Architecture diagram syntax error | Invalid Mermaid | Ask AI to regenerate the diagram |
| Git commit fails | No git init | Run `git init` in project directory |

---

## Key Takeaways

- **Noderr is a methodology**, not a software dependency
- **Core files define** your project, architecture, and progress
- **Prompts are your commands** to the AI assistant
- **Everything is versioned** in git for history and rollback
- **Start small** with your first task to learn the workflow

---

## Next Steps

Now that Noderr is installed and configured, continue to:

**[Tutorial 2: Understanding Core Files](02-core-files.md)** - Learn what each Noderr file does and how they work together.

---

## Quick Reference

### Files Created
```
noderr/
├── noderr_project.md      ← Your project definition
├── noderr_architecture.md ← Visual component map
├── noderr_tracker.md      ← Progress dashboard
├── noderr_loop.md         ← Development protocol
├── noderr_log.md          ← Event history
├── environment_context.md ← Platform commands
├── specs/                 ← Component specifications
├── prompts/               ← AI workflow commands
└── planning/              ← Strategic documents
```

### Key Prompts Used
- `NDv1.9__Install_And_Reconcile.md` - First-time setup
- `NDv1.9__Start_Work_Session.md` - Begin development

### Commands Checklist
- [ ] `git init` - Initialize repository
- [ ] `unzip noderr.starter.zip` - Extract files
- [ ] `git add noderr/` - Stage files
- [ ] `git commit -m "message"` - Save changes
