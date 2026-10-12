# Structured AI Workflow

A practical workflow for building software with an AI coding agent without relying on one giant prompt or one long chat.

The workflow uses four persistent Markdown files:

```text
REQUIREMENTS.md  →  WHAT are we building?
DESIGN.md        →  HOW will we build it?
BUILD.md         →  WHERE are we now?
AGENTS.md        →  HOW should the agent work?
```

Then the coding agent works through the project **one verified increment at a time**.

This repository uses a fictional resume-to-portfolio project as the example, but the same workflow can be reused for many software projects.

---

## 🎥 Video Tutorial

This repository accompanies an **Arprax Academy** tutorial on building software with a structured AI-agent workflow.

▶️ **Watch the full tutorial:**  
Coming soon

📺 **Arprax Academy:**  
https://www.youtube.com/@ArpraxAcademy

The video walks through the complete process:

```text
REQUIREMENTS.md → DESIGN.md → BUILD.md → AGENTS.md → Build → Verify → Deploy
```

After the YouTube video is published, replace **Coming soon** with the final video URL.

---

## Recommended Setup

For this tutorial:

```text
IDE            VS Code
Coding Agent   GitHub Copilot Agent
Model          Auto
Versioning     Git + GitHub
Deployment     GitHub Pages
```

The workflow itself is not tied to Copilot. The same `REQUIREMENTS.md`, `DESIGN.md`, and `BUILD.md` can be used with Cursor, Claude Code, Continue, or another capable coding agent.

`AGENTS.md` is the canonical project-instructions file in this repository. If another tool uses a different native rule format, either tell that agent to read `AGENTS.md` or adapt the same instructions to the tool's preferred location.

---

# 0. Start the Repository

For this tutorial, the final site is:

```text
https://samplecandidate.github.io
```

For that exact URL, the GitHub user or organization must be named:

```text
samplecandidate
```

and the repository must be:

```text
samplecandidate.github.io
```

Recommended order:

```text
Create GitHub repository
        ↓
Clone it locally
        ↓
Open the folder in VS Code
        ↓
Add Sample_Candidate_Resume.pdf
        ↓
Start the AI workflow
```

During development, let the agent create **local Git commits**, but do not authorize it to push remotely until the project is finished and verified.

---

# 1. Create `REQUIREMENTS.md`

Start a fresh Agent chat.

Use the following prompt:

```text
Help me turn the project below into something clear enough to build.

Interview me one question at a time. Use each answer to decide what to ask next.

Explore the user, goal, important behavior, scope, constraints, and what a successful result should look like.

If something matters but is unclear, ask me instead of assuming.

Do not write code yet.

<PROJECT>
Turn the attached fictional resume (@Sample_Candidate_Resume.pdf) into a professional portfolio website.

The audience is recruiters and hiring managers. Use the resume as the factual source and do not invent credentials or accomplishments. The finished site should eventually work on GitHub Pages.
</PROJECT>
```

The agent should now interview you one question at a time.

When the interview is complete, ask it to create the file:

```text
Create REQUIREMENTS.md from the requirements we just agreed on.

Use our conversation and the source material as the basis.

Do not invent new requirements.

Create the actual file in the workspace.

Do not implement the application yet.
```

---

# 2. Create `DESIGN.md`

Start a **fresh Agent chat**.

Use:

```text
Read REQUIREMENTS.md and turn it into a practical implementation design.

Choose the simplest suitable technical approach.

First break the project into sensible stages, then break those stages into smaller increments.

For each increment, write a standalone prompt that I can give directly to a coding agent.

Each coding prompt should:

- have one clear objective
- build on the working project
- be small enough to verify safely
- include the relevant constraints
- include how the agent should verify its work

Avoid large jumps in complexity and avoid disconnected code.

Create the complete result as DESIGN.md.

Do not implement the application yet.
```

`DESIGN.md` now contains the architecture plus the implementation increments the coding agent will follow later.

---

# 3. Create `BUILD.md`

Start another **fresh Agent chat**.

Use:

```text
Read REQUIREMENTS.md and DESIGN.md.

Create BUILD.md as the implementation progress tracker for this project.

Use the implementation stages and increments already defined in DESIGN.md.
Do not redesign the project and do not duplicate the full coding prompts.

For each increment include:
- checkbox/status
- short outcome
- verification summary

Organize the document into:
- CURRENT
- NEXT
- COMPLETED

Put only Increment 1.1 under CURRENT.
Put all remaining increments under NEXT.
COMPLETED should initially be empty.

The coding agent will update this file after each increment is successfully verified.

Do not write application code.
```

`BUILD.md` is the project's persistent state.

At any moment, the agent should be able to read it and answer:

```text
What am I working on now?
What comes next?
What has already been verified?
```

---

# 4. Create `AGENTS.md`

Start another **fresh Agent chat**.

Use:

```text
Inspect this workspace.

Read REQUIREMENTS.md and BUILD.md.

From DESIGN.md, read only the project architecture, technical constraints,
repository structure, and implementation workflow. You do not need to load
all standalone coding prompts.

Then create a project rule AGENTS.md.

The rule should contain only persistent guidance a coding agent needs:

- project purpose
- architecture and stack
- factual-content constraints
- important development constraints
- verification expectations
- how BUILD.md tracks CURRENT/NEXT/COMPLETED

Keep it concise.

Use the workspace file-creation tool to create the file.

Do not merely return the rule as a Markdown code block.
```

`AGENTS.md` is different from the other three files:

```text
REQUIREMENTS.md  describes the product
DESIGN.md        describes the technical approach
BUILD.md         describes project state
AGENTS.md        governs agent behavior
```

---

# 4.1 Add Scope and Evidence Rules

During testing, two important failure modes appeared:

1. an agent implemented future increments too early
2. an agent claimed work was verified when the relevant verification had not actually happened

Add the following sections to `AGENTS.md`.

## Scope Discipline

```markdown
## Scope Discipline

The CURRENT increment is a hard implementation boundary.

- Implement only requirements explicitly requested by the current increment.
- Do not implement, scaffold, anticipate, or prepare code for future increments.
- Do not add components, styles, JavaScript, files, dependencies, or content merely because they will be useful later.
- Existing requirements and DESIGN.md describe the overall project, but they do not authorize implementing future work.
- If the current increment does not request something, leave it for a later increment.
- Prefer the smallest change that completely satisfies the current increment.
```

## Evidence and Trust Rules

```markdown
## Evidence and Trust Rules

Never claim that a file was created, edited, tested, or verified unless the corresponding tool action actually succeeded.

Before marking an increment complete:

1. Confirm every required file exists by reading it with the available file tools.
2. Inspect the actual resulting content, not previously generated chat text.
3. Perform only verification that can actually be observed with available tools.
4. Never claim browser, console, network, visual, or runtime verification unless that check was actually performed.
5. If a required tool call fails or is unavailable, report the increment as BLOCKED. Do not infer success.
6. Never update BUILD.md to COMPLETED without evidence that the implementation exists and satisfies the increment.
7. The CURRENT increment is a hard scope boundary. Do not implement future increments.
```

---

# 4.2 Add Safety Boundaries

A coding agent can have substantial access to files, terminals, Git, browsers, and external tools.

Give it autonomy **inside the project**, not unrestricted authority over the computer or external accounts.

Add:

```markdown
## Safety Boundaries

- Work only inside this repository.
- Do not delete files or directories outside this repository.
- Do not install system-level software.
- Do not install packages unless they are genuinely required by the application.
- Do not change Git user.name or Git user.email.
- Local Git commits are allowed as project checkpoints.
- Do not push to a remote repository unless explicitly authorized.
- Never expose or commit passwords, tokens, API keys, or other secrets.
- Ask before destructive operations or actions that modify external systems or accounts.
```

The reasoning is simple:

```text
Repository boundary  → protects the rest of the computer
Install boundary     → prevents unnecessary machine changes
Git identity rule    → keeps commits attributed correctly
Local commits        → provides rollback points
No automatic push    → publication stays a human decision
Secret rule          → protects credentials from source control
```

---

# 5. Build the Project

Now start a **fresh Agent chat**.

Use:

```text
Work through this project one increment at a time until BUILD.md is complete.

For each cycle:

1. Read BUILD.md and identify the single increment under CURRENT.
2. Read only the corresponding increment instructions from DESIGN.md.
3. Use REQUIREMENTS.md and the project instructions for constraints.
4. Implement only that CURRENT increment.
5. Perform the verification defined for that increment.
6. If verification fails:
   - fix the problem
   - verify again
   - do not advance until it passes
7. If verification passes:
   - update BUILD.md
   - move the completed increment to COMPLETED
   - promote the next increment to CURRENT
8. Create a Git commit checkpoint for the verified increment.
9. Continue with the newly promoted CURRENT increment.

Important:

- Never implement more than one increment at a time.
- Never mark an increment complete without actual verification evidence.
- Do not skip increments.
- Stop immediately if you encounter a blocker that cannot be resolved safely.
- Stop when BUILD.md has no remaining CURRENT or NEXT increments.
```

The agent now follows this loop:

```text
Read BUILD.md
      ↓
Find CURRENT
      ↓
Read matching DESIGN increment
      ↓
Implement only CURRENT
      ↓
Verify
      ↓
Failed? ──→ Fix ──→ Verify again
      ↓
Passed
      ↓
Update BUILD.md
      ↓
Local Git checkpoint
      ↓
Promote NEXT
      ↓
Repeat
```

---

# Why Use Fresh Chats?

Use a fresh chat for each major planning stage:

```text
Chat 1 → REQUIREMENTS.md
Chat 2 → DESIGN.md
Chat 3 → BUILD.md
Chat 4 → AGENTS.md
Chat 5 → Development
```

The goal is to make the **repository**, rather than a huge chat history, carry the project context.

A fresh agent can reconstruct the project from:

```text
REQUIREMENTS.md
DESIGN.md
BUILD.md
AGENTS.md
```

This reduces context drift and makes the workflow easier to resume later.

---

# Using Other Coding Agents

The workflow is intentionally independent of a specific AI product.

Keep these files as the project source of truth:

```text
REQUIREMENTS.md
DESIGN.md
BUILD.md
AGENTS.md
```

## VS Code + GitHub Copilot

Recommended for this tutorial:

```text
VS Code
GitHub Copilot Agent
Model: Auto
```

Keep `AGENTS.md` at the repository root.

A Copilot-specific project may also use:

```text
.github/copilot-instructions.md
```

but that is not necessary for this tutorial.

## Cursor

Keep the same project documents.

Use `AGENTS.md` when supported by your Cursor setup, or adapt its contents into Cursor's native project-rule system.

## Claude Code

Keep `AGENTS.md` as the canonical human-readable project instructions.

If your Claude Code setup expects `CLAUDE.md`, either explicitly tell Claude to read `AGENTS.md` or mirror the same persistent guidance into `CLAUDE.md`.

## Continue

Continue can use the same planning documents.

Its native project rules can live under:

```text
.continue/rules/
```

For example:

```text
.continue/rules/project.md
```

Use the contents of `AGENTS.md` as the basis for that rule.

> The filename or AI product can change. The engineering workflow does not.

---

# Optional: Human-Gated Development

If you do not want the agent to complete the entire project in one run, use:

```text
Read BUILD.md and the project instructions.

Work only on the CURRENT increment.

Read the corresponding increment instructions from DESIGN.md.
Use REQUIREMENTS.md when you need to confirm scope or constraints.

Implement only that increment.

Perform the verification defined for it.

If verification fails:
- fix the problem
- verify again
- do not advance until it passes

If verification succeeds:
- update BUILD.md
- move the completed increment to COMPLETED
- promote the next increment to CURRENT
- create a local Git checkpoint

Do not implement the newly promoted increment.

Stop after updating BUILD.md.
```

Then start a fresh chat for the next increment.

This mode is useful when the project is high-risk, the agent is weaker, or human approval is important.

---

# Recovery Prompts

## If the Agent Implements Future Work

```text
Stop.

You implemented beyond the scope of the CURRENT increment.

Read BUILD.md and the CURRENT increment in DESIGN.md again.

Treat CURRENT as a hard implementation boundary.

Revert only the out-of-scope changes introduced for future increments while preserving valid CURRENT work.

Then rerun CURRENT verification.

Do not advance until CURRENT passes.
```

## If the Agent Claims Verification Without Evidence

```text
Do not mark this increment complete.

You claimed verification without evidence that the relevant tool actually ran.

Read AGENTS.md and follow the Evidence and Trust Rules.

Run the required verification using the available tools.

If a required verification cannot be performed, report the increment as BLOCKED.

Do not update BUILD.md to COMPLETED without evidence.
```

## If Context Becomes Confused

Start a fresh Agent chat:

```text
Read AGENTS.md and BUILD.md.

Use BUILD.md as the source of truth for current implementation state.

Work only on CURRENT.

Read the corresponding DESIGN.md increment and consult REQUIREMENTS.md only when necessary.

Do not rely on assumptions from previous chat history.
```

---

# 6. Final Verification

When `BUILD.md` has no remaining CURRENT or NEXT items:

```text
BUILD.md indicates that implementation is complete.

Perform a final end-to-end audit of the project against:

- REQUIREMENTS.md
- DESIGN.md
- AGENTS.md
- the actual implementation files

Do not assume earlier verification is sufficient.

Verify the final integrated project.

Check:
- required functionality
- factual/content correctness
- required files and assets
- links and downloads
- responsive behavior
- browser/runtime errors
- broken resource requests
- unnecessary external requests
- deployment readiness

If you find a problem:
1. identify the root cause
2. fix it
3. rerun the relevant verification

Do not push to GitHub yet.

Report the actual verification evidence.
```

---

# 7. Push the Verified Project

After final verification passes:

```text
The project has passed final verification.

You are now authorized to push the verified project to the configured GitHub remote.

Before pushing:

1. inspect Git status
2. confirm the current branch
3. confirm the configured remote
4. confirm there are no secrets or unintended files staged
5. confirm the verified work is committed

Rules:

- do not change Git user.name or Git user.email
- do not force-push
- do not rewrite Git history
- do not delete remote branches
- do not modify GitHub account settings
- push only the current verified branch

If everything is safe, push it.

Afterward report:
- branch pushed
- remote used
- latest commit
- whether the push succeeded
```

---

# 8. Deploy with GitHub Pages

For this simple static portfolio:

1. Open the repository on GitHub.
2. Open **Settings**.
3. Open **Pages**.
4. Under **Build and deployment**, select **Deploy from a branch**.
5. Select:

```text
Branch: main
Folder: /(root)
```

6. Save.
7. Wait for deployment to complete.

For this tutorial:

```text
Repository
samplecandidate.github.io

Live site
https://samplecandidate.github.io
```

---

# 9. Verify the Live Site

After deployment:

```text
The site is now deployed at:

https://samplecandidate.github.io

Perform a live deployment verification.

Check:
- the home page loads successfully
- the expected page title is correct
- the required sections appear
- the primary CTA works
- the resume/download asset works
- internal navigation works
- empty optional content remains hidden
- there are no unexpected console errors
- there are no broken resource requests
- the deployed result matches the verified local project

If you find a deployment-specific problem:
- identify the root cause
- fix it locally
- rerun local verification
- create a local Git checkpoint

Do not push another change until I explicitly authorize it.

Report PASS or FAIL with actual evidence.
```

---

# Complete Workflow

```text
Create GitHub repository
        ↓
Clone locally
        ↓
Add source material
        ↓
REQUIREMENTS.md
        ↓
DESIGN.md
        ↓
BUILD.md
        ↓
AGENTS.md
        ↓
Scope + Evidence + Safety rules
        ↓
Incremental development
        ↓
Verification
        ↓
BUILD update
        ↓
Git checkpoint
        ↓
Repeat until complete
        ↓
Final integrated audit
        ↓
Explicit push authorization
        ↓
GitHub
        ↓
GitHub Pages
        ↓
Live verification
```

---

# Core Principle

This workflow is not about finding a perfect AI model or writing a magical prompt.

It is about giving an AI coding agent a lightweight software-engineering process:

```text
Understand
    ↓
Design
    ↓
Build incrementally
    ↓
Verify with evidence
    ↓
Record state
    ↓
Continue
```

The model can change.

The IDE can change.

The coding agent can change.

The engineering process remains.

---

## About

Created for **Arprax Academy** — practical tutorials on AI, software engineering, and developer tools.

YouTube: https://www.youtube.com/@ArpraxAcademy

