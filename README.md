# Claude Research and Write

Two Claude Code skills for research-backed content creation: **`/topic-research`** and **`/write-article`**.

## What's Included

### `/topic-research`
Generate a comprehensive, research-backed list of content topics organized by thematic pillars.

**What it does:**
- Asks about your domain, credentials, audience, and content format
- Performs live web research for current trends, statistics, and content gaps
- Generates 25-100 topics organized into thematic pillars
- Each topic includes a rationale (SEO potential, content gap, audience resonance)
- Identifies niche sub-audience angles, multi-part series, and biggest content gaps
- Appends all research source URLs

### `/write-article`
Write a complete article with inline citations, following structured templates.

**What it does:**
- Works standalone OR picks up context from `/topic-research` output
- Performs web research and saves sources to a separate research file
- Writes blog articles (1,600-2,000 words), newsletters (500-800 words), or LinkedIn posts (200-400 words)
- Every statistic gets an inline hyperlinked citation — no footnotes, no reference sections
- Optional editorial notes for collaborative workflows (suggests where to add personal anecdotes)

**Output structure:**
```
your-directory/
├── article-slug.md
├── research/
│   └── RESEARCH-article-slug.md
```

## Installation

1. Clone or download this repo
2. Copy the skill folders into your Claude Code skills directory:

```bash
# Copy both skills
cp -r topic-research ~/.claude/skills/
cp -r write-article ~/.claude/skills/

# Or for project-specific installation
cp -r topic-research .claude/skills/
cp -r write-article .claude/skills/
```

3. The skills are now available as `/topic-research` and `/write-article` in Claude Code

## Usage

### Research topics first, then write

```
You: /topic-research
Claude: What domain or niche is this for?
You: B2B SaaS marketing
Claude: Who is creating this content?
You: I'm a solo founder who bootstrapped to $2M ARR...
[...continues through questions, then generates 50+ topics]

You: /write-article
Claude: I found saas-marketing-article-topics.md. Which topic would you like to write about?
You: Topic 12 — "Why Your Free Trial Is Killing Your Conversion Rate"
[...writes full article with research and citations]
```

### Write a standalone article

```
You: /write-article Why remote teams burn out differently than office teams
Claude: What domain or niche is this in?
You: Workplace psychology / HR
[...asks remaining questions, researches, writes]
```

## Content Formats

| Format | Length | Structure |
|--------|--------|-----------|
| Blog article | 1,600-2,000 words | Title, subtitle, opening hook, 3-4 H2 sections with data, practical takeaways, closing, SEO metadata |
| Newsletter | 500-800 words | Subject line, hook, core insight with 1-2 data points, one takeaway, CTA |
| LinkedIn post | 200-400 words | Hook line, 3-5 short paragraphs, one data point, engagement CTA |

## Citation Standard

These skills enforce strict inline citations:

**Correct:**
> A [study published in *ScienceDirect*](https://example.com) found that **77.3% of expatriates** experienced loneliness.

**Incorrect:**
> 77.3% of expatriates experienced loneliness. (Source: ScienceDirect, 2023)

Every data point gets a clickable source link inline. No footnotes. No reference sections at the bottom. Readers click through while reading.

## Collaborative Mode

When writing articles for someone else to personalize (a client, subject matter expert, etc.), enable collaborative mode. The skill adds editorial notes suggesting:

- Where to insert personal anecdotes or client stories
- Which sections benefit from lived experience
- Specific prompts for the collaborator ("If you have a story about X...")

## Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) CLI
- Web search capability (for live research)

## License

MIT
