# atlan-tops-files

A shared repository for the Atlan TA Ops team. Houses data reports, dashboards, prompt templates, and automation specs built to support recruiting and people operations work.

---

## What lives here

| Folder | What goes in it |
|---|---|
| `reports/` | HTML dashboards and data outputs. Each report gets its own subfolder. |
| `prompts/` | AI prompt templates — BrightHire, Ashby, Claude, Granola. One file per template. |
| `automations/` | Specs and flow configs for n8n, Zapier, and Ashby automations. |
| `playbooks/` | Process docs, how-tos, and operating guides for TA Ops workflows. |
| `assets/` | Shared CSS, images, or reusable components used across reports. |

---

## Reports

Each report lives in its own subfolder under `reports/` with the following structure:

```
reports/
  brighthire-feedback/
    index.html          ← the live report (deployed via GitHub Pages)
    data/               ← source CSVs or exports used to build it
    README.md           ← what the report covers, data sources, last updated
```

The `index.html` in the root of each report folder is what gets deployed. If you have multiple reports, only one can be the GitHub Pages root — use subfolders and link between them from a central `index.html` at the repo root.

---

## Prompts

One file per template, named clearly. Use markdown files so they're readable in GitHub directly.

```
prompts/
  brighthire-talent-screen.md       ← standard recruiter notes template
  glassdoor-response-playbook.md
  hiring-manager-brief-builder.md
```

Include at the top of each file:
- **Purpose** — what the prompt is for
- **Tool** — where it gets used (BrightHire, Claude, Ashby, etc.)
- **Owner** — who maintains it
- **Last updated** — date

---

## Automations

One file per automation. Use markdown for specs, include the actual flow config (JSON or YAML) where applicable.

```
automations/
  post-interview-slack-nudge.md     ← spec + n8n flow for feedback reminder
  glassdoor-response-agent.md
  recruiter-brief-builder.md
```

Each spec should cover: trigger, steps, tools used, owner, and current status (draft / live / paused).

---

## GitHub Pages

This repo uses GitHub Pages to host HTML reports publicly. The live URL is:

```
https://[your-username].github.io/atlan-ta-ops
```

To deploy a new report:
1. Add your HTML file as `reports/[report-name]/index.html`
2. Commit and push to `main`
3. GitHub Pages rebuilds automatically within ~60 seconds
4. Link to it from the root `index.html` so it's discoverable

To update an existing report, replace the file and push. No other steps needed.

---

## Contributing

**Naming conventions**
- Folders and files: lowercase, hyphens, no spaces (`brighthire-feedback`, not `BrightHire Feedback`)
- Report subfolders: `[tool-or-topic]-[what-it-covers]` (e.g. `brighthire-feedback`, `ashby-pipeline`)
- Prompt files: `[tool]-[use-case].md` (e.g. `brighthire-talent-screen.md`)

**Before pushing**
- Open HTML reports in Chrome locally and confirm they render correctly
- Check that any data files in `data/` don't contain candidate PII before committing
- Update the `README.md` inside the report or prompt folder with the date

**Branching**
- Small updates (copy edits, data refreshes): commit directly to `main`
- New reports or significant changes: create a branch, open a PR, tag Nick for review
