---
name: koriigami-write-article
description: Write a complete, research-backed article with inline citations. Supports blog posts, newsletters, and LinkedIn posts. Use when a user wants to write an article, draft a blog post, create a newsletter edition, compose a LinkedIn post, or says "write about [topic]". Works standalone or with output from /koriigami-topic-research.
---

# /koriigami-write-article — Article Writer Skill

Write a complete, research-backed article with inline citations, following structured templates for blog posts, newsletters, or LinkedIn posts.

## Step 0: Detect Entry Flow

Before asking questions, check if the user is coming from `/koriigami-topic-research`:

### Flow A — From /koriigami-topic-research output
1. Search the current project for any `*-article-topics.md` file
2. If found, read the file header to extract: author/brand, content type, target audiences
3. Ask: "I found [filename]. Which topic would you like to write about?"
4. Skip Questions 2-4 below (context is inherited from the research file)
5. Proceed to Question 5

### Flow B — Standalone
1. No research file found, OR user invokes directly with a topic (e.g., `/write-article Why burnout hits Gen Z earlier`)
2. Ask all questions below starting from Question 1

---

## Step 1: Gather Context

### Question 1: Topic
> What specific topic do you want to write about?

If the user provided a topic in the command (e.g., `/write-article [topic]`), use that directly.

### Question 2: Domain / Niche (Flow B only)
> What domain or niche is this in?

### Question 3: Author / Voice (Flow B only)
> Who is the author? Should the article be written in first person as them? What are their credentials?

### Question 4: Target Audience (Flow B only)
> Who is the primary audience for this piece?

### Question 5: Content Format
> What format?

Options:
- **Blog article** (default) — 1,600-2,000 words, educational/thought-leadership
- **Newsletter** — 300-800 words, focused insight with one takeaway
- **LinkedIn post** — 200-400 words, hook-driven professional content

### Question 6: Target Length
> How long should this be?

Defaults by format:
- Blog: 1,600-2,000 words (7-min read)
- Newsletter: 500-800 words (3-min read)
- LinkedIn: 200-400 words (1-min read)

### Question 7: Tone
> What tone? (Default: Educational, warm)

Options: Educational, Provocative/contrarian, Personal essay, How-to/practical, Data-driven, Conversational

### Question 8: Collaboration Mode
> Will someone else review and personalize this article? (e.g., add their own stories, clinical examples, personal anecdotes)

- If **yes** → Include editorial notes at the end suggesting where to add personal touches
- If **no** → Skip editorial notes

### Question 9: Save Location
> Where should I save the article?

Default: current working directory. The skill creates:
```
[save-location]/
├── [slug].md              ← the article
├── research/
│   └── RESEARCH-[slug].md ← sources and data collected
```

---

## Step 2: Research

Before writing a single word, research the topic thoroughly.

### Research Process
1. **Web search** for current data, statistics, and studies related to the topic
   - Use the current year in searches for recency
   - Prioritize: peer-reviewed research (PMC, PubMed, journal sites), authoritative organizations (WHO, UN, government agencies), reputable surveys and reports, high-quality journalism
2. **Collect 10-20 high-quality sources** with URLs
3. **Extract key data points**: percentages, statistics, study findings, expert quotes
4. **Note the source URL** next to every data point — this is critical for inline citations later

### Save Research File
Write all collected research to `[save-location]/research/RESEARCH-[slug].md`:

```markdown
# Research: [Article Topic]

**Researched:** [Date]
**Topic:** [Full topic description]
**Sources collected:** [N]

---

## Key Statistics & Data Points

- [Statistic] — [Source Name](URL)
- [Statistic] — [Source Name](URL)

## Source Summaries

### [Source Title](URL)
- Key findings: ...
- Relevant quotes: ...
- Data points: ...

### [Source Title](URL)
- Key findings: ...
- Relevant quotes: ...
- Data points: ...

## Additional Context
[Any broader trends, competitive landscape notes, or contextual information]
```

---

## Step 3: Write the Article

Use the format-specific template from `templates/`. Core rules apply to ALL formats:

### Citation Rules (NON-NEGOTIABLE)
- **Every data point** (percentage, statistic, finding) MUST have an inline hyperlink
- Format: `[Source Name](URL)` or `[*Publication Name*](URL)` immediately after the mention
- Do NOT defer citations to a references section at the bottom
- Readers must be able to click through to sources while reading
- Every claim that could be questioned should be backed by a source

Example of correct citation:
> A [2022-2023 study published in *ScienceDirect*](https://www.sciencedirect.com/science/article/pii/S1477893925001346) found that **77.3% of expatriates experienced loneliness**, compared to just 46.9% of people who stayed in their home countries.

Example of INCORRECT citation:
> 77.3% of expatriates experienced loneliness (Source: ScienceDirect, 2023).

### Writing Quality Standards
- **Short paragraphs** — 2-3 sentences maximum
- **Bold key phrases** for skimmers
- **Data embedded naturally** — statistics should flow within sentences, not feel like a report
- **Accessible language** — explain complex concepts plainly
- **Emotional accuracy** — vivid but not melodramatic
- **Cultural nuance** — acknowledge tensions without judgment
- **Practical grounding** — concrete steps, not vague advice

---

## Step 3a: Blog Article Structure

Follow the template in `templates/article-blog.md`:

1. **Title** — 60-80 characters, includes primary keyword
2. **Subtitle** — 140 characters max, includes secondary keyword, states the value proposition
3. **Opening hook** (150-200 words) — Relatable scenario, vivid detail, or compelling question. Draw the reader in emotionally before presenting data.
4. **Body** — 3-4 H2 sections, 300-400 words each:
   - Each section makes one clear point backed by evidence
   - Use inline citations for every statistic
   - Include sub-headers (H3) sparingly for complex sections
   - Bold key phrases for scanning
5. **Practical takeaways** (200-300 words) — Numbered actionable steps (3-5). Use frameworks relevant to the author's expertise. Each step should be concrete enough to act on today.
6. **Closing** (100-150 words) — Warm, hopeful, not salesy. Reaffirm the reader's experience. Soft CTA (seek support, reflect, take one step).
7. **SEO metadata**:
   - SEO Title: 60-80 chars with primary keyword
   - SEO Description: 160 chars with secondary keyword + key benefit
   - Tags: 5 max (2-3 specific + 1-2 broad)

---

## Step 3b: Newsletter Structure

Follow the template in `templates/article-newsletter.md`:

1. **Subject line** — Curiosity-driven or benefit-driven, under 50 chars
2. **Preview text** — 90 chars, complements (not repeats) the subject line
3. **Hook** — 2-3 sentences that create urgency or relevance
4. **Core insight** (300-500 words) — One central idea explored with 1-2 key data points and inline citations
5. **One actionable takeaway** — A single, concrete thing the reader can do this week
6. **CTA** — Reply, share, read more, book a call — one clear next step

---

## Step 3c: LinkedIn Post Structure

Follow the template in `templates/article-linkedin.md`:

1. **Hook line** — First line that stops the scroll. Bold claim, surprising stat, or provocative question.
2. **Body** — 3-5 short paragraphs (1-3 sentences each):
   - One key data point with inline citation
   - Personal or professional angle
   - Insight that challenges conventional thinking
3. **Closing** — Question to drive engagement OR clear CTA
4. **Formatting**: Use line breaks liberally. One thought per line for mobile readability.

---

## Step 4: Editorial Notes (if collaborative mode = yes)

Add a section at the end of the article:

```markdown
---

### Editorial Notes for [Author Name]

The article flows from [structure summary]. Here are suggestions for where your personal and clinical experiences would strengthen the piece:

1. **Opening scenario** (paragraphs X-Y): [Suggestion for personal anecdote or client story]

2. **"[Section Name]" section:** [Suggestion for where lived experience adds weight]

3. **[Framework/Method] section:** [Suggestion for real dialogue or session example]

4. **Practical steps:** [Where to add "In my experience..." clinical authority]

5. **Closing:** [Suggestion for personal connection statement]
```

Guidelines for editorial notes:
- Reference specific paragraph numbers or section names
- Suggest types of anecdotes (anonymized client stories, personal experiences, clinical vignettes)
- Explain WHY each insertion point would strengthen the piece
- Be specific: "If you have a story about X, it would work here" > "Add a personal touch"

---

## Step 5: Save the Article

Save the article to `[save-location]/[slug].md`

Confirm with the user:
- Article saved to: [path]
- Research file saved to: [path]
- Word count: [N]
- Sources cited: [N]

---

## Quality Checklist

Before delivering, verify:
- [ ] Every statistic has an inline hyperlinked source (not a footnote, not a reference section)
- [ ] Opening hook is vivid and emotionally engaging (not generic)
- [ ] Paragraphs are 2-3 sentences max (no walls of text)
- [ ] Key phrases are bolded for skimmers
- [ ] Practical steps are concrete and actionable (not vague platitudes)
- [ ] Closing is warm and hopeful (not salesy)
- [ ] Word count is within target range for the format
- [ ] Research file exists with all sources documented
- [ ] SEO metadata is present (blog format)
- [ ] Editorial notes are present (if collaborative mode)
- [ ] Article reads naturally — data supports the narrative, doesn't dominate it

---

## Reference Files

- See `templates/article-blog.md` for blog article template
- See `templates/article-newsletter.md` for newsletter template
- See `templates/article-linkedin.md` for LinkedIn post template
- See `examples/sample-article.md` for a real-world example of this skill's output
