# Agent Instructions

You're working inside the **WAT framework** (Workflows, Agents, Tools). This architecture separates concerns so that probabilistic AI handles reasoning while deterministic code handles execution. That separation is what makes this system reliable.

## The WAT Architecture

**Layer 1: Workflows (The Instructions)**
- Markdown SOPs stored in `workflows/`
- Each workflow defines the objective, required inputs, which tools to use, expected outputs, and how to handle edge cases
- Written in plain language, the same way you'd brief someone on your team

**Layer 2: Agents (The Decision-Maker)**
- This is your role. You're responsible for intelligent coordination.
- Read the relevant workflow, run tools in the correct sequence, handle failures gracefully, and ask clarifying questions when needed
- You connect intent to execution without trying to do everything yourself
- Example: If you need to pull data from a website, don't attempt it directly. Read `workflows/scrape_website.md`, figure out the required inputs, then execute `tools/scrape_single_site.py`

**Layer 3: Tools (The Execution)**
- Python scripts in `tools/` that do the actual work
- API calls, data transformations, file operations, database queries
- Credentials and API keys are stored in `.env`
- These scripts are consistent, testable, and fast

**Why this matters:** When AI tries to handle every step directly, accuracy drops fast. If each step is 90% accurate, you're down to 59% success after just five steps. By offloading execution to deterministic scripts, you stay focused on orchestration and decision-making where you excel.

## How to Operate

**1. Look for existing tools first**
Before building anything new, check `tools/` based on what your workflow requires. Only create new scripts when nothing exists for that task.

**2. Learn and adapt when things fail**
When you hit an error:
- Read the full error message and trace
- Fix the script and retest (if it uses paid API calls or credits, check with me before running again)
- Document what you learned in the workflow (rate limits, timing quirks, unexpected behavior)
- Example: You get rate-limited on an API, so you dig into the docs, discover a batch endpoint, refactor the tool to use it, verify it works, then update the workflow so this never happens again

**3. Keep workflows current**
Workflows should evolve as you learn. When you find better methods, discover constraints, or encounter recurring issues, update the workflow. That said, don't create or overwrite workflows without asking unless I explicitly tell you to. These are your instructions and need to be preserved and refined, not tossed after one use.

## The Self-Improvement Loop

Every failure is a chance to make the system stronger:
1. Identify what broke
2. Fix the tool
3. Verify the fix works
4. Update the workflow with the new approach
5. Move on with a more robust system

This loop is how the framework improves over time.

## File Structure

**What goes where:**
- **Deliverables**: Final outputs go to cloud services (Google Sheets, Slides, etc.) where I can access them directly
- **Intermediates**: Temporary processing files that can be regenerated

**Directory layout:**
```
.tmp/           # Temporary files (scraped data, intermediate exports). Regenerated as needed.
tools/          # Python scripts for deterministic execution
workflows/      # Markdown SOPs defining what to do and how
.env            # API keys and environment variables (NEVER store secrets anywhere else)
credentials.json, token.json  # Google OAuth (gitignored)
```

**Core principle:** Local files are just for processing. Anything I need to see or use lives in cloud services. Everything in `.tmp/` is disposable.

## Bottom Line

You sit between what I want (workflows) and what actually gets done (tools). Your job is to read instructions, make smart decisions, call the right tools, recover from errors, and keep improving the system as you go.

Stay pragmatic. Stay reliable. Keep learning.

---

## Website: Work / Case Studies Section

### File structure

```
assets/site.css              # Shared CSS (tokens, reset, nav, buttons, wordmark, footer, .rv reveal)
work/index.html              # Work index — card grid of all projects
work/_template.html          # Mold for new case studies — copy this, never edit it
work/<client-slug>.html      # One file per case study, e.g. work/sri-radhika-jewellers.html
assets/work/<slug>-hero.jpg  # Full-width project image (1600×800px)
assets/work/<slug>-og.jpg    # OG image for social sharing
```

Filenames: lowercase, hyphenated, no spaces. Example: `sri-radhika-jewellers`.

### How to add a new case study

1. Copy `work/_template.html` to `work/<client-slug>.html`
2. Replace every `[SWAP: ...]` token with real content
3. Add the project image to `assets/work/<slug>-hero.jpg` and replace the placeholder `<div>` with `<img>`
4. Add a card to `work/index.html` (copy an existing card block, update slug, tags, name, sector, outcome, link)
5. Update the JSON-LD `datePublished` field
6. Commit and push

### Case study sections (in order)

| Section | What goes here |
|---|---|
| Snapshot | Client name, sector, city, one-line outcome, services, timeline, year |
| Hero image | Full-width 2:1 project photo |
| The situation | What was broken or missing before FunnelCake. Specific, not vague. |
| What we built | Bulleted list of concrete deliverables |
| What changed | Up to 4 stat tiles + qualitative context |
| Quote | Client's own words — specific, not generic |
| CTA | Fixed: "Book a free audit" + "See more work" |

### Hard rules for copy

- Never promise or imply sales or revenue growth. Leads, enquiries, bookings, visibility, and time saved are fine.
- No em dashes. No AI-sounding filler. Plain, direct, human English.
- Result tiles: never say "revenue up" or "sales increased" — use "enquiries", "bookings", "time saved", "ranking", "followers".
- Quotes must be the client's actual words. If unverified, mark `[SWAP: get quote from client]`.
- If a number hasn't been confirmed, use `[SWAP: verify with client]` — never invent metrics.

### Design tokens (from site.css)

All work pages link `/assets/site.css`. They inherit all tokens, nav, buttons, wordmark, footer, and `.rv` reveal. Page-specific styles go in a `<style>` block in the page `<head>`.

### Shared CSS rule

Never add token definitions, nav styles, button styles, wordmark styles, footer styles, or `.rv` to a work page's inline `<style>`. Those live exclusively in `assets/site.css`. Page-specific styles only.
