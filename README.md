# Claude Research and Write

Two Claude Code skills for research-backed content creation: **`/koriigami-topic-research`** and **`/koriigami-write-article`**.

## What's Included

### `/koriigami-topic-research`
Generate a comprehensive, research-backed list of content topics organized by thematic pillars.

**What it does:**
- Presents interactive options for domain, author, audience, format, and scope
- Performs live web research for current trends, statistics, and content gaps
- Generates 25-100 topics organized into thematic pillars
- Each topic includes a rationale (SEO potential, content gap, audience resonance)
- Identifies niche sub-audience angles, multi-part series, and biggest content gaps
- Appends all research source URLs

### `/koriigami-write-article`
Write a complete article with inline citations, following structured templates.

**What it does:**
- Works standalone OR picks up context from `/koriigami-topic-research` output
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

### Option 1: Claude Code Plugin (Official)

Register the marketplace and install individual skills:

```
/plugin marketplace add koriigami/claude-research-and-write
/plugin install koriigami-topic-research@claude-research-and-write
/plugin install koriigami-write-article@claude-research-and-write
```

### Option 2: npx (via skills.sh)

```bash
npx skills add koriigami/claude-research-and-write
```

After installation, the skills are available as `/koriigami-topic-research` and `/koriigami-write-article` in Claude Code.

## Usage

### Research topics first, then write

```
You: /koriigami-topic-research
Claude: [Presents interactive options for domain, author, audience, format, scope]
You: [Select options or type custom answers]
Claude: [Researches trends and generates 50+ topics organized by pillars]

You: /koriigami-write-article
Claude: I found saas-marketing-article-topics.md. Which topic would you like to write about?
You: Topic 12 — "Why Your Free Trial Is Killing Your Conversion Rate"
Claude: [Researches topic, writes full article with inline citations]
```

### Write a standalone article

```
You: /koriigami-write-article Why remote teams burn out differently than office teams
Claude: What domain or niche is this in?
You: Workplace psychology / HR
Claude: [Asks remaining questions, researches, writes]
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
