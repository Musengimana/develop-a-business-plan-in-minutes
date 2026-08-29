# Use this business plan skill to develop a business plan for your new idea or business in minutes

![A business plan in minutes. Researched, lender-ready, numbers that check themselves.](docs/banner.png)

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Works with](https://img.shields.io/badge/works%20with-Claude%20·%20Codex%20·%20any%20LLM%20agent-blue)](#works-with-any-llm)
[![Skill format](https://img.shields.io/badge/format-SKILL.md%20open%20standard-orange)](#install-it)
[![Latest release](https://img.shields.io/github/v/release/Musengimana/develop-a-business-plan-in-minutes?label=release)](../../releases/latest)

You describe the business. The skill interviews you once, researches your industry on the live web with citations, writes a complete lender-ready business plan in Word, and builds a real banker's financial forecast in Excel, with a downside and an upside scenario already calculated. Minutes of your time instead of weeks of writing, and every number in the narrative matches the workbook because a machine checks that it does.

This is not a fill-in-the-blanks template. It is a full working method, distilled from a consulting practice that has produced around one hundred business plans, packaged as an installable AI skill that any capable LLM agent can execute end to end.

## What you get

- **A researched first draft, fast.** Industry definition and outlook, target market demographics, competitors, pricing benchmarks, licences and taxes for your jurisdiction, researched on the live web as of today and cited in the plan.
- **A lender-ready Word document.** A professionally structured A4 business plan built from a real template: cover, table of contents, decimal-numbered sections, appendices for assumptions, sources, and scenario analysis. Clean black-and-white formatting that a bank or funding program expects.
- **A real financial forecast in Excel.** The Business Development Bank of Canada (BDC) financial plan workbook, driven by a purpose-built engine: projected sales, cost of sales, operating expenses, income statement, balance sheet, twelve-month cash flow, financing requirements, and automatic accounting ratios. It recalculates itself when you open it in Excel.
- **1,064 protected formulas, proven intact.** The engine writes only into input cells and then verifies, after every single write, that all 1,064 template formulas and all 22 dropdown controls survived. No silently broken spreadsheet math. Ever.
- **Three scenarios, not one guess.** A base case populates the workbook; a downside and an upside case (for example volume down 25 percent, price down 10 percent, key cost up 15 percent) are computed through the live model and reported in a scenario appendix. The scenario drivers come from the risks the research actually found, not generic percentages.
- **An honest paper trail.** Client facts, researched facts, and assumptions are never mixed. Every assumption gets an ID, a rationale, and a confidence level. Every material model input is logged with its source in a Source Log sheet inside the workbook.
- **Editable deliverables, properly named.** You receive `.docx` and `.xlsx` files with the business name and date in the filename, ready for your review and your client's letterhead. Never a locked PDF, never a chat summary.

## Why it is different

Most AI business plans are confident fiction. This skill was engineered against that failure mode:

1. **It refuses to fabricate.** No invented history, customers, contracts, credentials, or financing commitments. Missing history stays blank or marked `Not provided`.
2. **It researches before it writes.** Market sizing is bottom-up where possible, and when only top-down data exists it shows the calculation and its limits.
3. **The numbers police the story.** The forecast logic is designed before the narrative conclusions are written, so the growth story is only as confident as the model supports. Before delivery, a cross-document review reconciles the Word plan and the workbook figure by figure, using extracted values, not memory.
4. **Machines check the work.** A Word document validator, a workbook formula-integrity verifier, and a model-specific audit script all have to pass before anything is delivered. During development, an independent formula audit recomputed the workbook's arithmetic line by line and three formula defects in the original template were found and repaired; the bundled copy is the repaired, verified baseline.
5. **It defaults to real-world conventions.** Canada, CAD, NAICS classification, and federal, provincial, and municipal sources by default, switching jurisdiction and currency cleanly when the client operates elsewhere. One engagement, one currency, always.

## Works with any LLM

The skill uses the open `SKILL.md` agent-skills format: plain instructions, reference guides, templates, and Python scripts in one folder. Any agent that can read files, run Python, and search the web can execute it.

| Agent | Support |
|---|---|
| Claude (claude.ai, desktop, Cowork) | Upload the skill zip once, then just ask for a business plan |
| Claude Code | Drop the folder into your skills directory |
| OpenAI Codex | Install by URL with the skill installer, or copy the folder |
| Cursor and other SKILL.md-aware agents | Point them at the folder |
| Any other LLM agent | Paste the one-paragraph bootstrap prompt below |

Full capability needs three things: file access, a shell with Python 3.10+ (plus `openpyxl`, `lxml`, and LibreOffice for the workbook engine), and live web access for research. An agent without a shell can still follow the method and write the plan; the workbook engine is what needs Python.

## Install it

### Claude on the web or desktop (claude.ai)

1. Download `build-client-business-plans.zip` from the [latest release](../../releases/latest).
2. In Claude, open Settings, then Capabilities (Skills), and upload the zip.
3. Ask: "Write a business plan for my client" and attach your notes.

### Claude Code

```bash
git clone https://github.com/Musengimana/develop-a-business-plan-in-minutes.git
cp -r develop-a-business-plan-in-minutes/build-client-business-plans ~/.claude/skills/
```

Project-level install works the same way into `.claude/skills/` inside your project.

### OpenAI Codex

Using the skill installer from [openai/skills](https://github.com/openai/skills):

```text
$skill-installer install https://github.com/Musengimana/develop-a-business-plan-in-minutes/tree/main/build-client-business-plans
```

Or copy the `build-client-business-plans` folder into your Codex skills directory (typically `~/.codex/skills`).

### Any other LLM agent

Clone or download this repository where your agent can read it, then start with:

> Read the file `build-client-business-plans/SKILL.md` and follow it exactly, including the reference files it names, to produce a first-draft business plan and financial forecast for the client described below. Use the bundled templates. Write into the Excel template only through `scripts/populate_financial_workbook.py`, and run the verification scripts before delivering. Client notes: [your notes here]

## Use it

Give it whatever you have. It is built for incomplete information:

- "Write a business plan for my mobile dog grooming startup in Kingston, Ontario. I have $20,000 saved and I want a $75,000 loan."
- "Here is my Business Model Canvas and three voice-note transcripts from my client. Build the plan and the financials."
- "My client runs an existing bakery and wants to add wholesale. Intake form attached. Plan and forecast, please."

The skill asks one short round of essential questions (at most about eight), then proceeds, labelling anything it had to assume with an assumption ID so you can confirm or correct it later. If you are away, it makes the most defensible choice and records it in the assumption register instead of stalling.

Deliverables land as:

- `<Business Name> - Business Plan Draft - <YYYY-MM-DD>.docx`
- `<Business Name> - Financial Forecast Draft - <YYYY-MM-DD>.xlsx`
- `<Business Name> - Client Intake - <YYYY-MM-DD>.docx` when an intake questionnaire is part of the engagement

## What is inside

```text
build-client-business-plans/
├── SKILL.md                        The complete method an agent follows
├── assets/
│   ├── business-plan-template.docx      Structured A4 plan template with named styles
│   ├── client-intake-template.docx      Client intake questionnaire
│   └── financial-forecast-template.xlsx BDC financial plan workbook (repaired baseline)
├── references/
│   ├── intake-and-assumptions.md        Hybrid intake and assumption-register rules
│   ├── research-standards.md            Live-web research and citation standards
│   ├── document-standards.md            Word formatting standards, enforced
│   ├── business-plan-map.md             Section-by-section drafting map
│   ├── financial-model-map.md           The workbook engine and full input map
│   └── financial-model-audit.md         How the model audit is designed
└── scripts/
    ├── prepare_case.py                  Copies pristine templates into a client folder
    ├── check_financial_template.py      Compatibility gate for the workbook
    ├── populate_financial_workbook.py   The only supported way to write the workbook
    ├── extract_workbook_outputs.py      Reads results and runs scenario extractions
    ├── audit_financial_model.py         Model-specific audit runner
    ├── verify_formula_integrity.py      Proves all 1,064 formulas survived
    └── check_word_document.py           Word deliverable validator
```

## Requirements

- Python 3.10 or newer, with `pip install -r requirements.txt` (openpyxl, lxml)
- LibreOffice (`soffice`) on the PATH, used headlessly to recalculate the workbook
- Live web access for research
- An agent willing to follow instructions exactly (the good ones are)

## Honest limits

The outputs are professional first drafts for review, not audited statements, tax advice, legal advice, or a promise of financing. The skill says so on its own deliverables. It will not invent your trading history, and it will leave personal financial schedules blank unless you supply the data. Forecast horizons beyond three projected years fall back to a formula-driven workbook the skill builds from scratch.

## Licensing and credits

Everything here is MIT licensed (see [LICENSE](LICENSE)) except the BDC financial plan workbook, which is copyright the Business Development Bank of Canada and included with BDC's written permission; BDC's own terms govern that file. Details in [NOTICE.md](NOTICE.md).

Built by [Norman Musengimana](https://github.com/Musengimana), founder of Prosfata Inc., an entrepreneurship and economic development consultant in Kingston, Ontario who has written around one hundred business plans across a career of working with more than three hundred businesses and organizations. This skill is his method, made executable.

If it saves you a week, star the repository so the next founder finds it.
