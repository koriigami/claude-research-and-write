---
name: topic-research
description: Generate a comprehensive, research-backed list of content topics organized by thematic pillars. Use when a user wants to brainstorm article ideas, plan a content calendar, identify content gaps, or research topics for blog posts, newsletters, or LinkedIn posts. Triggers on phrases like "research topics", "topic ideas", "content ideas", "what should I write about", "article ideas", "content plan".
---

# /topic-research — Content Topic Research Skill

Generate a structured, research-backed list of content topics organized by thematic pillars for any domain, audience, and content format.

## Step 1: Gather Context (Ask These Questions)

Before researching, ask the user these questions **one at a time or grouped logically**. Do not skip any.

### Question 1: Domain / Niche
> What domain or niche is this for?

Examples: "Life coaching", "B2B SaaS marketing", "Personal fitness", "Personal finance", "Web development", "Food & nutrition", "Travel"

### Question 2: Author / Brand Profile
> Who is creating this content? What are their credentials, expertise, and unique differentiators?

This shapes authority positioning and content angles. Examples:
- "Dr. Swapna Vithalkar, PhD — Life Coach & Sex Addiction Specialist, 20+ years, CBT/REBT/DBT/TA"
- "Solo developer who bootstrapped a SaaS to $2M ARR"
- "Certified nutritionist specializing in South Asian dietary patterns"

### Question 3: Target Audience
> Who is the primary audience? Are there any niche sub-audiences worth targeting?

Sub-audiences drive the "niche angle" topics within each pillar. Examples:
- "Global English speakers + Indian diaspora + expats in Europe"
- "Early-stage startup founders + solo developers + technical co-founders"
- "Working professionals aged 25-40 + new parents + people with desk jobs"

### Question 4: Content Format
> What content format are you creating?

Options:
- **Blog articles** — Educational, thought-leadership, or how-to posts (1,000-2,500 words)
- **Newsletter** — Regular email content (300-800 words per edition)
- **LinkedIn posts** — Professional social content (200-400 words)
- User can select multiple formats

### Question 5: Scope
> How many topics would you like? (Default: ~50)

Options: 25, 50, 75, 100. More topics = more pillars and deeper niche coverage.

---

## Step 2: Research

After gathering context, perform thorough web research:

1. **Search for current trends** in the domain (use the current year). Look for:
   - Emerging topics and terminology
   - Recent statistics and data points
   - Industry reports and surveys
   - Trending conversations on the topic

2. **Identify content gaps** — Search for existing content in the domain and note:
   - Topics with high search intent but low-quality existing content
   - Niche intersections that are underserved
   - Audience-specific angles that competitors ignore

3. **Collect source URLs** for every statistic, trend, or claim you reference in topic rationales. Every data point needs a traceable source.

4. **Analyze the competitive landscape** — What are the dominant voices in this space writing about? Where are they NOT writing?

---

## Step 3: Generate Output

Structure the output following the template in `templates/topic-list.md`. Key requirements:

### Pillars
- Generate **5-12 thematic pillars** depending on scope
- Each pillar gets a name and a 1-line italicized description of why it matters
- Pillars should cover the domain comprehensively — foundational topics, trending topics, niche angles, and cross-cutting themes

### Topics Within Pillars
For each topic:
- **Bold title** — Compelling, specific, keyword-rich (60-80 characters for blog, shorter for LinkedIn)
- **Rationale** — 1-2 sentences explaining WHY this topic is valuable. Reference one or more of:
  - SEO potential ("high-volume search query", "low competition keyword")
  - Content gap ("almost no quality content exists on this")
  - Audience resonance ("deeply resonant with [sub-audience]")
  - Timeliness ("emerging [year] trend", "recent research published")
  - Shareability ("provocative", "counterintuitive", "high engagement potential")

### Niche Sub-Audience Angles
If the user specified sub-audiences in Question 3:
- Within relevant pillars, add a "### [Sub-Audience] Angles" subsection
- These are topics that specifically target the sub-audience's unique perspective, challenges, or cultural context

### Series Suggestions
- Identify 2-3 multi-part series opportunities (3-5 parts each)
- Series should span topics that build on each other and sustain engagement

### Content Gap Analysis
At the end, include a "## Biggest Content Gaps Identified" section:
- List the top 5 underserved topics with a brief explanation of why they represent an opportunity
- These should be topics where quality content is genuinely scarce

### Research Sources
End with a "## Research Sources" section listing every URL used during research:
- Format: `- [Source Title](URL)`
- Include all sources referenced in topic rationales
- Include trend reports, industry surveys, and data sources consulted

---

## Step 4: Save the File

- Ask the user where to save the file, or default to the current working directory
- Filename format: `[slug]-article-topics.md` where slug is derived from the domain/brand
- Example: `saas-marketing-article-topics.md`, `fitness-coaching-article-topics.md`

---

## Quality Checklist

Before delivering, verify:
- [ ] Every topic has both a title AND a rationale (no bare titles)
- [ ] Rationales reference concrete data, trends, or strategic reasoning (not vague claims)
- [ ] Sub-audience angles are present if sub-audiences were specified
- [ ] At least 2 multi-part series are suggested
- [ ] Content gaps section identifies genuinely underserved topics
- [ ] All research sources are listed with working URLs
- [ ] The metadata header includes: date, author/brand, content type, target audiences
- [ ] Topic count approximately matches what the user requested

---

## Reference Files

- See `templates/topic-list.md` for the exact output format template
- See `examples/sample-output.md` for a real-world example of this skill's output
