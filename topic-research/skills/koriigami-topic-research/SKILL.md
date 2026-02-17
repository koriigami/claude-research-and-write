---
name: koriigami-topic-research
description: Generate a comprehensive, research-backed list of content topics organized by thematic pillars. Use when a user wants to brainstorm article ideas, plan a content calendar, identify content gaps, or research topics for blog posts, newsletters, or LinkedIn posts. Triggers on phrases like "research topics", "topic ideas", "content ideas", "what should I write about", "article ideas", "content plan".
---

# /koriigami-topic-research — Content Topic Research Skill

Generate a structured, research-backed list of content topics organized by thematic pillars for any domain, audience, and content format.

## Step 1: Gather Context

Before researching, ask the user these questions using the `AskUserQuestion` tool. Present selectable options for each question so the user can pick quickly. Ask all questions in a single `AskUserQuestion` call with multiple questions.

### Question 1: Domain / Niche

Question: "What domain or niche do you want to create content for?"

Options (present these 8 as selectable choices — the user can also type their own):
1. Personal Finance & Investing
2. Health & Fitness
3. AI & Machine Learning
4. SaaS & Startups
5. Mental Health & Wellness
6. Food & Nutrition
7. Web Development & Programming
8. Digital Marketing

The user can always provide a custom domain not in the list.

### Question 2: Author / Brand Profile

Question: "Who is creating this content? Share their credentials and unique expertise."

Present 3 contextual examples based on the domain chosen in Q1, plus a custom option. Examples should match the domain — e.g., if the user chose "Health & Fitness", show:
1. "Certified Personal Trainer — 10 years, strength training specialist"
2. "Registered Dietitian — clinical nutrition, plant-based focus"
3. "Fitness content creator — 500K YouTube subscribers, home workouts"

The user can always provide their own author/brand profile.

### Question 3: Target Audience

Question: "Who is the target audience? Select primary audience or describe your own."

Present 3 contextual options based on the domain + author from Q1-Q2, plus custom. Examples should match — e.g., for "Health & Fitness" + "Personal Trainer":
1. "Beginners aged 25-40, weight loss focused"
2. "Busy professionals who want quick home workouts"
3. "Postpartum mothers returning to fitness"

The user can always describe their own audience.

### Question 4: Content Format

Question: "What content format are you creating? (Select one or more)"

Options (multi-select):
1. Blog articles — Educational, thought-leadership, or how-to posts (1,000-2,500 words)
2. Newsletter — Regular email content (300-800 words per edition)
3. LinkedIn posts — Professional social content (200-400 words)

### Question 5: Scope

Question: "How many topics would you like?"

Options:
1. 25 topics — Quick list, 3-5 pillars
2. 50 topics (Recommended) — Balanced coverage, 6-8 pillars
3. 75 topics — Deep coverage, 8-10 pillars
4. 100 topics — Comprehensive, 10-12 pillars with niche angles

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

### Next Steps Footer
Always end the output file with this section:

```markdown
---

## Next Steps

Pick a topic from this list and write it using `/koriigami-write-article`.
```

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
- [ ] Next Steps footer is present pointing to `/koriigami-write-article`

---

## Reference Files

- See `templates/topic-list.md` for the exact output format template
- See `examples/sample-output.md` for a real-world example of this skill's output
