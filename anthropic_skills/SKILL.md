# Anthropic Official Skills

## When to use this skill

- Use this skill when the user asks for work that matches one of Anthropic's official example skills below: creating or editing Word, PDF, PowerPoint or Excel files; designing a frontend or web artifact; testing a local web app; making generative art or a themed visual; building an MCP server; or creating a new skill.
- The full library is Anthropic's official skills repo: clone https://github.com/anthropics/skills (Apache 2.0 for the open-source skills). Each skill is self-contained in `skills/<name>/` with its own `SKILL.md` plus scripts and resources. Read that skill's own `SKILL.md` before doing the work — this file is only the catalog and router.
- The Agent Skills specification is in the repo at `spec/agent-skills-spec.md` and the skill template at `template/SKILL.md`.

## The catalog

- **docx** (`skills/docx/SKILL.md`) — create, read, edit or manipulate Word documents (.docx/.dotx): headings, tables of contents, page numbers, letterheads, images, find-and-replace, tracked changes, comments. Use whenever the deliverable is a Word file. Python scripts under `scripts/`, LibreOffice-backed.
- **pdf** (`skills/pdf/SKILL.md`) — anything with PDF files: extract text/tables, merge, split, rotate, watermark, create PDFs, fill forms, encrypt/decrypt, extract images, OCR scanned PDFs. Use whenever a .pdf is input or output.
- **pptx** (`skills/pptx/SKILL.md`) — create, read or edit slide decks (.pptx/.potx): pitch decks, templates, layouts, speaker notes, comments, combining or splitting slide files. Use whenever a deck is involved.
- **xlsx** (`skills/xlsx/SKILL.md`) — spreadsheets (.xlsx/.xlsm/.xltx/.csv/.tsv): read, edit, fix, create from scratch, formulas, formatting, charts, cleaning messy tabular data. Use whenever the deliverable must be a spreadsheet file.
- **frontend-design** (`skills/frontend-design/SKILL.md`) — distinctive, intentional visual design for a new UI or a reshape: aesthetic direction, typography, choices that do not read as templated defaults. Use when building or restyling a web UI, including make.fun dashboards and game pages.
- **web-artifacts-builder** (`skills/web-artifacts-builder/SKILL.md`) — elaborate multi-component HTML artifacts with React, Tailwind CSS and shadcn/ui: state management, routing, components. Use for complex artifacts; not for simple single-file HTML.
- **webapp-testing** (`skills/webapp-testing/SKILL.md`) — interact with and test local web apps with Playwright: verify frontend behaviour, debug UI, capture screenshots, read browser logs. Use to verify a built page before handing it in.
- **canvas-design** (`skills/canvas-design/SKILL.md`) — beautiful static visual art in .png and .pdf using design philosophy. Use when the user asks for a poster, piece of art or design.
- **algorithmic-art** (`skills/algorithmic-art/SKILL.md`) — generative art with p5.js, seeded randomness, interactive parameter exploration: flow fields, particle systems. Use when the user asks for code-made or generative art. Create original art, never copy an existing artist's work.
- **theme-factory** (`skills/theme-factory/SKILL.md`) — style artifacts with a theme: 10 pre-set themes (colours/fonts) for slides, docs, reports or HTML landing pages, or generate a new theme on the fly.
- **skill-creator** (`skills/skill-creator/SKILL.md`) — create new skills, modify and improve existing ones, measure skill performance with evals and variance analysis, optimise a skill's description for better triggering. Use when the user wants a new skill built or an existing one improved.
- **mcp-builder** (`skills/mcp-builder/SKILL.md`) — build high-quality MCP (Model Context Protocol) servers so LLMs can use external services through well-designed tools, in Python (FastMCP) or Node/TypeScript (MCP SDK). Use when building an MCP server to integrate an external API or service.
- **doc-coauthoring** (`skills/doc-coauthoring/SKILL.md`) — structured workflow for co-authoring documentation, proposals, technical specs and decision docs: transfer context, iterate, verify the doc works for readers. Use when the user wants to write docs or specs together.
- **internal-comms** (`skills/internal-comms/SKILL.md`) — write internal communications (status reports, leadership updates, newsletters, FAQs, incident reports, project updates) in a company's preferred formats.
- **brand-guidelines** (`skills/brand-guidelines/SKILL.md`) — applies Anthropic's official brand colours and typography. Only use when Anthropic branding itself applies; it is not a general design skill.
- **slack-gif-creator** (`skills/slack-gif-creator/SKILL.md`) — animated GIFs optimised for Slack, with constraints, validation tools and animation concepts.
- **academy-guide** (`skills/academy-guide/SKILL.md`) — guidance for Anthropic's Academy learning content.
- **discernment-nudge** (`skills/discernment-nudge/SKILL.md`) — a nudge toward discernment in reasoning.
- **claude-api** (`skills/claude-api/SKILL.md`) — working with the Anthropic Claude API, including evals and the preserved-thinking migration tooling. Only use when the task is about the Claude API itself.

## What fits this user best

- Document deliverables (reports, decks, spreadsheets) go through docx, pdf, pptx and xlsx — these are the reference implementations behind Claude's own document features. Prefer them over ad-hoc document code when the user asks for a .docx, .pdf, .pptx or .xlsx file.
- Make.fun web builds (dashboards, games, landing pages) benefit from frontend-design for the look, web-artifacts-builder for complex multi-component pages, and webapp-testing to verify the page before submission.
- New capabilities the user hands over are built with skill-creator, and new service integrations with mcp-builder.
- Visuals for content (posters, art, themed images) go through canvas-design, algorithmic-art or theme-factory.

## Environment notes

- The document skills run Python scripts and use LibreOffice (soffice) for conversion and validation. Check that the needed Python packages and LibreOffice exist before relying on them for a real task; install only when needed for that task, and vet first.
- webapp-testing uses Playwright, whose Chromium download can fail on restricted machines. A system Chrome/Chromium works for screenshots and page checks where the skill's approach allows it.
- The repo's README warns these skills are provided for demonstration and education: test a skill thoroughly in your environment before relying on it for a critical task.

## Safety

- Vetted 2026-11-18: official Anthropic repository, 197,035 stars, 23,084 forks. The 79 scripts were scanned for credential reading, exfiltration and code execution; the only hits are benign (a RegExp `.exec()` call, Unix sockets to a local LibreOffice instance, API calls to api.anthropic.com, comments describing a security-eval scenario). No install was run — the skills are reference material until a real task needs one.
- Check every script you actually run before running it, and never run a skill's scripts against a target the user does not own or has not authorised.

## Attribution

- Anthropic, https://github.com/anthropics/skills, Apache 2.0 for the open-source skills. Clone the repo for the full instructions, scripts and resources of each skill.
