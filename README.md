# FT50 Empirical Research Writing Skill

An OpenCode/Claude Code skill for writing empirical research papers targeting FT50 journals across all management disciplines—finance, marketing, operations, strategy, accounting, OB/HR, and more. Provides structured workflows, discipline-specific conventions, and FT50 formatting requirements.

## Installation

```bash
git clone https://github.com/liyuanbo1024/ft50-empirical-writing.git

# OpenCode
cp ft50-empirical-writing/ft50-empirical-writing.md ~/.config/opencode/skills/

# Claude Code
cp ft50-empirical-writing/ft50-empirical-writing.md ~/.claude/skills/

# Codex
cp ft50-empirical-writing/ft50-empirical-writing.md ~/.codex/skills/

# Cursor
cp ft50-empirical-writing/ft50-empirical-writing.md ~/.cursor/skills/

# Windsurf
cp ft50-empirical-writing/ft50-empirical-writing.md ~/.windsurf/skills/
```

## Quick Start

Load the skill and start writing:

```
/opencode --skill ft50-empirical-writing
"Write the introduction section for a paper on CEO overconfidence and R&D investment,
using a difference-in-differences design with Compustat data."

/opencode --skill ft50-empirical-writing
"Generate a hypothesis development section linking board gender diversity to
ESG disclosure quality, grounded in upper echelons theory and agency theory."

/opencode --skill ft50-empirical-writing
"Polish the results section: add economic significance interpretation, format
regression tables following Journal of Finance style."
```

## File Structure

```
ft50-empirical-writing/
├── ft50-empirical-writing.md   # Core skill definition and prompts
├── references/
│   ├── ft50-style-guide.md     # FT50 journal formatting conventions
│   └── empirical-checklist.md  # Pre-submission quality checklist
├── templates/
│   ├── intro.md                # Introduction section template
│   ├── hypothesis.md           # Hypothesis development template
│   ├── methods.md              # Research design template
│   └── results.md              # Results & discussion template
└── README.md
```

## License

MIT
