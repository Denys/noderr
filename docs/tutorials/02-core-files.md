# Tutorial 2: Understanding Core Files

> **Learn What Each Noderr File Does and How They Work Together**

---

## Overview

| | |
|---|---|
| **Difficulty** | Beginner |
| **Time Required** | 20-25 minutes |
| **Prerequisites** | Completed Tutorial 1 |

### Learning Objectives

By the end of this tutorial, you will:

- Understand the purpose of each core Noderr file
- Know how the files relate to each other
- Be able to read and interpret file contents
- Understand when each file gets updated

---

## Introduction

Noderr's power comes from its carefully designed file system. Each file has a specific purpose, and together they create a comprehensive project memory that persists across AI sessions.

Think of it like this:
- **noderr_project.md** = Your project's constitution
- **noderr_architecture.md** = Your system's blueprint
- **noderr_tracker.md** = Your progress dashboard
- **noderr_loop.md** = Your development rulebook
- **noderr_log.md** = Your project's history book
- **environment_context.md** = Your platform's instruction manual

Let's explore each one in detail.

---

## The Six Core Files

### File 1: noderr_project.md (The Constitution)

**Purpose**: Defines what you're building and how.

**What it contains**:

```markdown
# Project: [Your Project Name]

## Goal
[What problem does this solve?]

## Scope & Key Features
- Feature 1
- Feature 2
- Feature 3 (MVP)

## Technology Stack
- Frontend: [React, Vue, etc.]
- Backend: [Node.js, Python, etc.]
- Database: [PostgreSQL, MongoDB, etc.]

## Coding Standards
- [Style guide references]
- [Naming conventions]

## Testing Strategy
- Unit tests for [what]
- Integration tests for [what]

## Security Considerations
- [Authentication approach]
- [Data protection measures]
```

**When it's updated**:
- During initial setup (Install & Reconcile)
- When project scope changes significantly
- When technology decisions change

**Why it matters**:
AI reads this first to understand your project context. Without it, AI makes assumptions that may not match your intentions.

> **Tip**: Keep this focused on decisions, not implementation details. "We use JWT for auth" not "here's how JWT works".

---

### File 2: noderr_architecture.md (The Blueprint)

**Purpose**: Visual map of all components and their connections.

**What it contains**:

```markdown
# System Architecture

## Flowchart

​```mermaid
flowchart TD
    UI_Home[/UI_HomePage/] --> API_GetPosts{{API_GetPosts}}
    API_GetPosts --> SVC_Posts[[SVC_PostService]]
    SVC_Posts --> DB_Posts[(DB_PostsTable)]

    UI_Home --> UI_PostCard[/UI_PostCard/]
    UI_PostCard --> API_LikePost{{API_LikePost}}
​```

## Component Legend
- `/slashes/` = UI Components
- `{{braces}}` = API Endpoints
- `[[brackets]]` = Services
- `[(parens)]` = Databases
```

**When it's updated**:
- After adding new components
- After removing components
- After changing relationships between components
- During LOOP_3 (Finalize) phase

**Why it matters**:
This is the single source of truth for system structure. AI uses it to:
- Understand what exists
- Identify what a change might affect
- Ensure new components integrate properly

> **Tip**: Keep diagrams readable. Split into multiple diagrams if the system is large.

---

### File 3: noderr_tracker.md (The Dashboard)

**Purpose**: Real-time progress tracking for all components.

**What it contains**:

```markdown
# Project Tracker

## Current WorkGroupID
`feat-20250109-143022`

## Status Map

| NodeID | Status | Dependencies | Classification |
|--------|--------|--------------|----------------|
| UI_LoginForm | VERIFIED | API_UserAuth | Standard |
| API_UserAuth | WIP | SVC_Auth, DB_Users | Complex |
| SVC_Auth | TODO | DB_Users | Standard |
| DB_Users | VERIFIED | - | Standard |

## Status Legend
- TODO: Not started
- WIP: Work in progress
- VERIFIED: Complete and tested
- ISSUE: Has problems
- NEEDS_SPEC: Missing specification

## Progress
[████████░░] 80% Complete
```

**When it's updated**:
- When starting work on a NodeID (TODO → WIP)
- When completing implementation (WIP → VERIFIED)
- When issues are discovered (→ ISSUE)
- Every loop iteration

**Why it matters**:
This tells AI (and you) exactly where things stand. When resuming work, AI reads this to know what's done and what's next.

> **Tip**: Check this file after each session to verify progress was tracked correctly.

---

### File 4: noderr_loop.md (The Rulebook)

**Purpose**: Defines the development methodology AI must follow.

**What it contains**:

```markdown
# Noderr Development Loop

## Phase 1: Propose & Plan
### Step 1A: Impact Analysis
- Analyze the requested change
- Identify ALL affected NodeIDs
- Create complete Change Set

### Step 1B: Draft Specifications
- Create spec for each NodeID
- Define interfaces, dependencies, logic
- PAUSE for user approval

## Phase 2: Implement & Verify
### Step 2A: Implementation
- Build all Change Set nodes
- Run tests
- Initial self-verification

### Step 2B: Independent Audit
- Read-only verification
- Calculate completion percentage
- Report gaps

## Phase 3: Finalize
- Update specs to as-built
- Update architecture diagram
- Create log entry
- Git commit

## Rules
- Never skip phases
- Never implement without approved specs
- Never mark done without verification
```

**When it's updated**:
- Rarely—this is the methodology itself
- Only if you customize the workflow

**Why it matters**:
This is the "operating system" for AI development. It ensures consistent, quality-focused work regardless of which AI session you're in.

> **Tip**: Read this file yourself to understand what AI is supposed to do at each phase.

---

### File 5: noderr_log.md (The History)

**Purpose**: Chronological record of all significant events.

**What it contains**:

```markdown
# Operational Log

## Entry Types
- SystemInitialization
- SpecApproved
- ARC-Completion
- MicroFix
- Decision
- Issue
- RefactorCompletion

## Log Entries

### [2025-01-09 14:30:22] SystemInitialization
- WorkGroupID: init-20250109-143022
- Action: Project initialized with Noderr framework
- Nodes: UI_Home, API_GetPosts, SVC_Posts, DB_Posts

### [2025-01-09 15:45:00] ARC-Completion
- WorkGroupID: feat-20250109-154500
- Feature: User authentication
- Nodes: UI_Login, API_Auth, SVC_Auth, DB_Users
- Verification: 100%
- Notes: JWT implementation with refresh tokens

### [2025-01-09 16:20:00] Issue
- NodeID: API_Auth
- Type: Security
- Description: Token expiry not enforced
- Resolution: Added middleware check
```

**When it's updated**:
- After every significant action
- During LOOP_3 (Finalize) phase
- When issues are discovered
- When decisions are made

**Why it matters**:
This is your project's memory. When debugging or understanding "why did we do it this way?", the log provides answers.

> **Tip**: Review the log periodically to track project evolution and remember past decisions.

---

### File 6: environment_context.md (The Platform Manual)

**Purpose**: Platform-specific commands and configurations.

**What it contains**:

```markdown
# Environment Context

## Platform Detection
- OS: macOS / Linux / Windows
- Shell: bash / zsh / PowerShell

## Package Management
```bash
# Install dependencies
npm install          # Node.js
pip install -r requirements.txt  # Python
```

## Database Commands
```bash
# PostgreSQL
psql -U user -d dbname

# MongoDB
mongosh
```

## Development Server
```bash
npm run dev          # Start dev server
npm run build        # Production build
npm test             # Run tests
```

## Common Operations
```bash
# Create migration
npm run migrate:create name

# Run migrations
npm run migrate:up
```
```

**When it's updated**:
- During initial setup
- When adding new tools or services
- When deployment process changes

**Why it matters**:
AI uses this to run the correct commands for your specific environment. No more "I'm not sure if you're on Mac or Windows" guessing.

> **Tip**: Keep this updated as your tooling evolves. Add any custom scripts or commands you use frequently.

---

## How Files Work Together

```
                    ┌─────────────────────┐
                    │  noderr_project.md  │
                    │   (What to build)   │
                    └──────────┬──────────┘
                               │
                               ▼
                    ┌─────────────────────┐
                    │ noderr_architecture │
                    │  (How it connects)  │
                    └──────────┬──────────┘
                               │
              ┌────────────────┼────────────────┐
              │                │                │
              ▼                ▼                ▼
    ┌─────────────────┐ ┌─────────────┐ ┌──────────────────┐
    │ noderr_tracker  │ │ noderr_loop │ │ environment_ctx  │
    │ (Where we are)  │ │ (How to do) │ │ (Platform cmds)  │
    └────────┬────────┘ └──────┬──────┘ └────────┬─────────┘
             │                 │                  │
             └────────────────┬┘                  │
                              │                   │
                              ▼                   │
                    ┌─────────────────────┐       │
                    │    noderr_log.md    │◄──────┘
                    │  (What happened)    │
                    └─────────────────────┘
```

**Reading Order for AI**:
1. `noderr_project.md` - Understand the project
2. `noderr_architecture.md` - See the structure
3. `noderr_tracker.md` - Know current status
4. `noderr_loop.md` - Follow the methodology
5. `environment_context.md` - Use correct commands
6. `noderr_log.md` - Reference as needed

---

## Practical Exercise

### Your Task

Examine a configured Noderr project and answer questions about its state.

### Setup

If you completed Tutorial 1's exercise, use that project. Otherwise, use the sample content below.

### Sample Tracker Content

```markdown
# Project Tracker

## Current WorkGroupID
`feat-20250109-100000`

## Status Map

| NodeID | Status | Dependencies | Classification |
|--------|--------|--------------|----------------|
| UI_TaskList | VERIFIED | API_GetTasks | Standard |
| UI_TaskForm | WIP | API_CreateTask | Standard |
| UI_TaskItem | TODO | - | Standard |
| API_GetTasks | VERIFIED | SVC_Tasks | Standard |
| API_CreateTask | WIP | SVC_Tasks | Standard |
| API_DeleteTask | TODO | SVC_Tasks | Standard |
| SVC_Tasks | VERIFIED | DB_Tasks | Complex |
| DB_Tasks | VERIFIED | - | Standard |
```

### Questions

1. How many NodeIDs are currently being worked on (WIP)?
2. What percentage of the project is complete (VERIFIED)?
3. Which NodeID should likely be worked on next?
4. What does `UI_TaskForm` depend on?
5. If we wanted to add "edit task" functionality, which existing NodeIDs might be affected?

### Answers

<details>
<summary>Click to reveal answers</summary>

1. **2 NodeIDs** are WIP: `UI_TaskForm` and `API_CreateTask`

2. **50% complete** (4 VERIFIED out of 8 total)

3. **UI_TaskItem** should be next - it has no dependencies and is a UI component that likely complements the already-verified `UI_TaskList`

4. `UI_TaskForm` depends on `API_CreateTask`

5. For "edit task" functionality, affected NodeIDs would likely include:
   - `UI_TaskItem` (add edit button/mode)
   - New: `API_UpdateTask`
   - `SVC_Tasks` (add update method)
   - Possibly `UI_TaskForm` (reuse for editing)

</details>

---

## Common Issues & Solutions

| Issue | Cause | Solution |
|-------|-------|----------|
| Architecture diagram doesn't render | Invalid Mermaid syntax | Use a Mermaid live editor to validate |
| Tracker shows outdated status | AI didn't update after work | Manually update or re-run finalize |
| Log entries missing | Skipped LOOP_3 phase | Always complete the full loop |
| Environment commands wrong | Platform changed | Update environment_context.md |
| Files conflict in git | Multiple sessions edited | Merge carefully, keep latest status |

---

## Key Takeaways

- **Each file has ONE job** - Don't mix concerns between files
- **Files form a system** - They reference and depend on each other
- **AI reads ALL files** - Incomplete or contradictory files confuse AI
- **You can read them too** - These are human-readable by design
- **Keep them updated** - Stale files lead to stale AI understanding

---

## Next Steps

Now that you understand what each file does, learn how to use them in the development process:

**[Tutorial 3: The Development Loop](03-development-loop.md)** - Master the 5-phase workflow that ties everything together.

---

## Quick Reference

### File Purposes

| File | Purpose | Update Frequency |
|------|---------|------------------|
| `noderr_project.md` | Project definition | Rarely |
| `noderr_architecture.md` | System structure | Per feature |
| `noderr_tracker.md` | Progress status | Per task |
| `noderr_loop.md` | Methodology | Never (usually) |
| `noderr_log.md` | Event history | Per action |
| `environment_context.md` | Platform commands | As needed |

### Status Values

| Status | Meaning |
|--------|---------|
| `TODO` | Not started |
| `WIP` | Work in progress |
| `VERIFIED` | Complete and tested |
| `ISSUE` | Has problems |
| `NEEDS_SPEC` | Missing specification |
