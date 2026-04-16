# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

<!--
  Starter context file from Advanced Prompt Engineering for Journalists
  Course site: https://mooc.amditis.tech
  Instructor: Joe Amditis, Center for Cooperative Media, Montclair State University

  Edit every section below to match your beat. The more specific you are,
  the better Claude's output will be. Delete these comments when you're done.
-->

## About this repo

This is a journalism course workspace for the Knight Center MOOC "Advanced Prompt Engineering for Journalists." It contains:

- `CLAUDE.md` — this context file, read by Claude at the start of every session
- `sample-docs/` — press releases, meeting minutes, interview notes for exercises
- `skills/` — custom skill files invoked with `/skill-name` in the Claude Code prompt
- `scripts/` — shell scripts that pipe documents through `claude -p` for batch processing
- `mcp-configs/` — MCP server configuration examples (copy to `~/.claude/mcp.json` to activate)
- `beat-archive/` — your document archive for the Module 4 RAG exercise

## Skills

Skills in `skills/` are Markdown files that act as reusable prompt templates. Invoke them by typing `/` followed by the filename (without `.md`) — for example, `/newsroom-style` or `/my-first-skill`.

To create a new skill:

```bash
cp skills/my-first-skill.md skills/your-skill-name.md
# edit the copy, then invoke with /your-skill-name
```

## Scripts

Scripts use `claude -p` (non-interactive, single-prompt mode):

```bash
# Summarize a single article
./scripts/summarize-article.sh sample-docs/sample-article.html

# Batch-process multiple files
./scripts/batch-process.sh sample-docs/
```

Make scripts executable if needed: `chmod +x scripts/*.sh`

## MCP configuration

To connect Claude to local files, copy and edit the example config:

```bash
cp mcp-configs/filesystem-example.json ~/.claude/mcp.json
# Replace YOUR_USERNAME and the path, then restart Claude Code
```

---

## Beat

fish is an independent data journalist (kinda retired) focused on mostly Colorado politics. she uses Jupyter Lab with Python/Pandas to process and analyze data, excel to analyze and summarize data, Postgresql for large datasets (voter data) and SQLite for quick tables and Datasette.

i'll be working on [this site](https://followingthemoneyco.com/) during the election year to provide journalists and the public with state-level campaign finance data that's more easily useable than the Secretary of State's site. that's part of some volunteer work i'm doing with Colorado News Collaborative to help journalists in the state with their election coverage.

And i'm encouraging news organization to use [QuizTheVote](https://www.quizthevote.com/), an open-source, no-coding quiz platform that matches voters with candidates based on public policy, not political party or persona.


Key people and institutions:
- [Federal Election Commission, federal campaign finance](https://www.fec.gov/data/elections/?cycle=2026&state=CO)
- [Colorado Secretary of State TRACER, state level campaign finance](https://tracer.sos.colorado.gov/PublicSite/homepage.aspx)
- [Colorado SOS Election page, general information](https://www.coloradosos.gov/pubs/elections/main.html)
- [Ballot measure information, information on ballot measures](https://www.coloradosos.gov/pubs/elections/Initiatives/InitiativesHome.html)


## Style

- AP style for all writing
- No Oxford comma
- Spell out numbers under 10
- Dollar amounts: $2.3 million, not $2,300,000

<!-- Add your publication's house style rules here.

     Examples:
     - Use "council member," not "councilman/councilwoman"
     - Refer to the governor by last name on second reference, never first name
     - Always include party affiliation and district on first reference for legislators
     - Our publication capitalizes "City Council" but lowercases "the council"
-->

## Source standards

- Attribute all claims to named sources
- Flag unverified claims separately from verified ones
- If a source makes a factual claim (dates, dollar amounts, vote counts), note whether it can be verified independently

<!-- Add rules specific to your beat. How do you handle anonymous sources?
     What verification steps does your publication require?

     Examples:
     - We don't grant anonymity without editor approval
     - Budget figures must be cross-checked against official documents
     - When summarizing public meetings, include the vote count for every motion
-->

## Terminology

<!-- Add beat-specific terms that Claude should use correctly.

     Examples:
     - The annual budget process is called the "appropriations cycle" — never
       call it "budget season"
     - The state legislature is the "General Assembly," not "state congress"
     - A "resolution" is non-binding; an "ordinance" has the force of law
-->
- Prioritize in campaign finance reports:
  - Total raised, specifying the reporting time frame at least once
  - Total spent
  - Cash on hand at the end of the reporting period, such as "at the end of March"
- When using the term "dark money" or "dark money groups" also say that such groups "are typically nonprofits that don't disclose their donors."
- For more definitions, refer to [MoneyInPolitics](https://moneyinpolitics.wtf/)
- The Colorado Secretary of State oversees elections broadly
- Each county clerk oversees elections in their county. A list of those county clerks[is here](https://static1.squarespace.com/static/6259a2140535307f29d7bcb4/t/69c89094b8a8c109b6adc23c/1774751892564/CountyClerkRosterWebsite.pdf)


## Avoid

<!-- Add patterns you don't want in your output.

     Examples:
     - Don't use "slammed" or "blasted" for political disagreements — use
       "criticized," "objected to," or "voted against"
     - Avoid "comprehensive," "leveraging," and "seamlessly"
     - Don't write "officials say" without naming the official
     - Avoid passive voice for attribution: write "the mayor said," not
       "it was said by the mayor"
-->
- Use "raised" but not "hauled in" or "raked in"
- Don't use "slammed" or "blasted" for political disagreements — use
       "criticized," "objected to," or "voted against"


## Lessons learned

<!-- Add rules here when the AI makes a mistake or misinterprets an instruction.
     These accumulate over time and prevent repeated errors.

     Examples:
     - "Claude kept writing 'the Board of Education' when our district calls
       it the 'School Committee' — always use School Committee"
     - "Claude assumed the fiscal year starts in January. Our city's fiscal
       year starts July 1 — never assume calendar year for budgets"
     - "Claude summarized a 5-4 vote as 'the council approved' without
       noting the close margin. Always flag split votes"
-->
