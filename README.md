# PM OS Setup

PM OS Setup creates a Product Management operating system: a structured workspace with a Chief PM
coordinator, specialist agents, reusable skills, product memory, and automatic indexes.

It is not just a PRD generator. It is a product mindspace your agents can actually navigate.

You give the command. The Chief PM finds the right context, routes the work, applies the right skill,
creates the artifact, and keeps the workspace organized in the background.

Your taste and ways of working become reusable skills. Your docs stay linked. Your product context
stays current. Your agent does not have to rediscover the map every time you ask it to help.

It works with Claude Code, Cursor, Codex, GitHub Copilot, and plain agent chats because the generated
workspace is mostly Markdown. Tool-specific wiring stays minimal by default.

## Quickstart

You do not need to be a developer, but you do need a tool that can run agent skills, such as [Claude Code](https://code.claude.com/docs/en/quickstart) or [Cursor](https://cursor.com/download). If the `npx` command below is not recognized on your machine, install [Node.js](https://nodejs.org/en/download) and try again.

Install the skill from this repo:

```bash
npx skills@latest add manansuneja/pm-os-setup
```

Then run the skill in your agent:

```text
/pm-os-setup Set up a PM workspace for Acme.
```

The agent will ask whether to use the current folder or create a new workspace folder.

## What This Helps PMs Do

- Build a structured product mindspace instead of another folder of loose notes.
- Work through one Chief coordinator that routes to the right specialist automatically.
- Capture your PM taste, standards, and ways of working as reusable skills.
- Turn brainstorms, decisions, meetings, and feature ideas into durable artifacts.
- Keep a living product workspace where agents can find the right context fast.
- Create PRDs and decision docs without manually rebuilding context every time.
- Use indexes so agents know what to read, what to skip, and which skill to apply.

## Beginner Setup

### Claude Code

1. Install Claude Code using the [official quickstart](https://code.claude.com/docs/en/quickstart).
2. Open Claude Code in the folder where you want your PM workspace.
3. Paste this once:
  ```bash
   npx skills@latest add manansuneja/pm-os-setup
  ```
4. Then ask:
  ```text
   /pm-os-setup Set up a PM OS for Acme.
  ```

### Cursor

1. Install Cursor from the [official download page](https://cursor.com/download).
2. Open or create the folder where your PM workspace should live.
3. Open Cursor's terminal and paste:
  ```bash
   npx skills@latest add manansuneja/pm-os-setup
  ```
4. Then use the skill in chat:
  ```text
   /pm-os-setup Set up a PM OS for Acme.
  ```

If your agent tool does not show slash commands, say it in plain English instead:

```text
Use pm-os-setup to set up a PM OS for Acme.
```

## If You Already Have A Workspace Folder

Open that folder in Cursor, Claude Code, Codex, or your terminal, then ask:

```text
/pm-os-setup Set up a PM OS here.
```

The PM OS files are added directly to the current folder.

## If You Need A New Workspace Folder

Run it from the parent folder and include the project name:

```text
/pm-os-setup Set up a new PM OS workspace for Acme.
```

The skill creates a clean folder such as:

```text
acme-workspace/
```

## What It Creates

```text
acme-workspace/
|-- AGENTS.md
|-- CLAUDE.md
|-- INDEX.md
|-- README.md
|-- agents/
|   |-- pm-chief.md
|   `-- sub-agents/...
|-- product-docs/
|   |-- product-vision.md
|   |-- meetings/...
|   |-- prds/...
|   `-- decisions/...
|-- skills/
|   |-- apply-pmos-struct.md
|   |-- summarize-notes.md
|   |-- brainstorm.md
|   |-- to-prd.md
|   `-- ...
`-- _setup/
    |-- README.md
    `-- AGENTS.md
```

Every PM OS content folder also includes an `INDEX.md` so agents can find the right context without
loading the whole workspace.

It does not create nested `pm-os-workspace/`, `pm-os-setup/`, `.agents/`, `.claude/`, or `.github/`
folders during basic setup.

After the scaffold is created, the agent reads `_setup/AGENTS.md` and personalizes the workspace
around your product: product vision, Chief PM behavior, specialist agents, docs, and skills.

That personalization keeps the workspace machinery separate from the product. For example, if your
product is an AI agent or robot, the product docs should describe that product's agents or robots -
not accidentally turn the workspace's Chief PM into the product.

## Why The Structure Stays Clean

The important automation skill is `skills/apply-pmos-struct.md`. The Chief PM is instructed to use
it after any meaningful workspace change, so maintenance becomes part of the work loop instead of a
separate chore for the PM.

That means when your agent creates or changes a meeting summary, PRD, decision, skill, agent, or
product doc, it should also check:

- Did this land in the right folder?
- Is the filename clean and consistent?
- Did the nearest `INDEX.md` get updated?
- Did the root `INDEX.md` change if a new area was added?
- Should `product-docs/product-vision.md` or another product doc be updated?

This is what keeps the PM OS from turning into a pile of Markdown files. You can keep talking,
thinking, deciding, and shipping artifacts while the agents maintain the workspace around the work.

## After Setup

Personalize the workspace:

```text
Read _setup/README.md and help me personalize this PM OS around my product.
Read _setup/AGENTS.md, ask me the setup questions, then update the Chief PM and product vision.
```

Use the starter skills:

- `summarize-notes`: turn messy notes into a useful meeting summary.
- `brainstorm`: explore product direction before converging on a choice.
- `to-prd`: turn a decision or idea into a PRD.
- `document-product-context`: update the product vision, decisions, and durable context.
- `manage-workspace-skills`: create or update reusable PM skills.
- `apply-pmos-struct`: the automatic maintenance pass that keeps folders, filenames, links, indexes,
and product docs clean after changes.

Example working prompts:

```text
Summarize these meeting notes and save the output in the right place.
Help me brainstorm onboarding improvements for Acme and capture the best direction.
Turn this feature idea into a PRD using our product vision as context.
Update the product vision based on this new strategy note.
Create a new skill for how I like launch plans written.
Add a specialist agent for customer research and wire it into your routing table.
Run the workspace structure pass and update any stale INDEX.md files.
```
