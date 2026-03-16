---
name: content-skill
description: Create high-quality, SEO/AEO-optimized blog content for TestDino with deep topic research, competitive analysis, verified TestDino documentation, WordPress shortcode formatting, and strategic internal linking. Use when writing blog posts, technical articles, or marketing content.
---

# MASTER CONTENT PROTOCOL FOR TESTDINO BLOG CREATION

## Purpose
This is the single source of truth for creating high-quality, SEO/AEO-optimized blog content for TestDino. It ensures:
- Deep topic research and competitive analysis
- Structured, scannable content
- Fact-checked TestDino references from official sources
- Strategic internal linking from existing blog inventory
- Quality assurance at every stage

---

## 🚨 CRITICAL RULE: TestDino Documentation First

**BEFORE writing ANY statement about TestDino features, capabilities, or implementation:**

1. **MUST check official sources in this order:**
   - Primary: https://docs.testdino.com/
   - Secondary: https://www.npmjs.com/package/@testdino/playwright
   - Changelog: https://changelog.testdino.com/

2. **Only write what you can verify** from these sources
3. **Never assume or invent** TestDino features
4. **If uncertain**, exclude the statement or mark for verification

**Examples:**
- ✅ "TestDino provides AI-powered root cause analysis" (if verified in docs)
- ❌ "TestDino offers Slack integration" (unless confirmed in docs)
- ❌ "TestDino supports 50+ test frameworks" (unless verified)

---

## WORKFLOW STAGES

1. **Research Phase** → Understand topic, competition, gaps
2. **TOC Generation** → Create structured outline
3. **TestDino Documentation Review** → Gather verified product facts
4. **Content Writing** → Execute with research + verified facts
4.5. **WordPress Component Formatting** → Apply shortcodes, HTML, markers
5. **Internal Linking** → Add contextual links from sitemap
6. **Final QA** → Run all checklists

---

# PHASE 1: RESEARCH

## Goal
Create a research blueprint that allows any writer to:
- Understand the topic deeply
- See how top-ranking blogs are structured
- Identify gaps worth covering
- Decide what to prioritize and skip
- Produce content that can compete for first-page rankings

**This phase is thinking-first. No drafting. No filler. No copy-paste writing.**

---

## Research Inputs Required

Before starting, gather:

```
Blog Topic: [TestDino MCP: Improve your testing workflow]
Primary Keyword: [testino mcp]
Secondary Keywords (6-8): [ai, model context, workflows, test automation, debugging, flaky tests]
Long Tail Keywords (5-7): [how to setup testdino mcp, ai debugging, test analysis]
Meta Title (55-65 chars): [TestDino MCP: Improve your testing workflow]
Meta Description (150-160 chars): [Learn how to use TestDino MCP to improve your testing workflow with AI-powered debugging and test analysis.]
URL Slug: [/testdino-mcp]
Target Audience: [QA engineers, test automation specialists, software developers using Playwright, DevOps engineers monitoring CI/CD pipelines, QA managers analyzing test failures]
Blog Angles (2-3 strategic angles): [1. What is MCP?, 2. What is TestDino MCP, 3. How to use TestDino MCP?, 4. How TestDino MCP helps in debugging failing test cases, 5. Anlyzing test cases using TestDIno MCP, 6. Practical Example, 7. Conclusion, 8. FAQs]
LSI Semantic Keywords (10-15): [test failure analysis, debugging automation tests, ai test analysis, test insights, ai test flakiness, ai test debugging]
AEO H2 (1): [What is TestDino MCP?]
AEO H2 (2): [How to Use TestDino MCP to Analyze flaky test cases?]
```

---

## Research Method

### Step 1: Seed Prompt to AI Research Tool

> Analyze this topic as if the goal is to rank on the first Google SERP for both the primary keyword and the blog topic.  
> Use reasoning, not summaries.  
> Do not repeat content from sources.  
> Explain WHY pages rank, not just WHAT they say.

### Step 2: Reference Blog Selection Rules

**Only consider blogs that:**
- Rank on page 1 for the primary keyword OR close variants
- Have clear structure (TOC, H2/H3 hierarchy)
- Are written for practitioners, not beginners only
- Are updated or still relevant

**Ignore:**
- Thin affiliate posts
- Over-marketed product pages
- Blogs with vague or generic advice

---

## Competitive Analysis Framework

For each reference blog, extract:

### 1. Search Intent Match
- What problem does the blog solve first?
- Is it written for decision-makers or practitioners?
- Is it tactical or conceptual?

### 2. Structure Pattern
- Number of H2s used
- Common H2 themes across ranking blogs
- Depth per H2 (short vs deep)
- Where examples are placed

### 3. Content Signals That Help Ranking
Identify:
- Checklists
- Tables
- Visual explanations
- Real-world workflows
- Clear do/don't sections
- Practical defaults (numbers, limits, rules)

**These are ranking signals, not decoration.**

### 4. What They Skip or Under-explain
Look for:
- Missing edge cases
- No guidance on trade-offs
- No ownership or accountability advice
- No failure scenarios
- No operational steps

**These gaps are priority targets.**

---

## Deciding What to Write

**Use this rule:**

- If **3+ ranking blogs** explain something the same way → Cover it, but shorter and clearer
- If **1-2 blogs** mention it briefly → Expand it with depth and examples
- If **no ranking blog** explains it clearly → Make it a core differentiator

**Do not add sections just to increase word count.**

---

## SEO + AEO Writing Rules (Applied at Research Stage)

### SEO Focus
- Each H2 must target one clear intent
- Avoid overlapping H2s
- One main idea per section
- Prefer practical phrasing over theory

### AEO Focus
- First 2 H2s must be direct questions
- Answers should be short, clear, and standalone
- FAQs must be usable as featured snippets
- Avoid long intros before answering

### Exclusions
- No geo targeting
- No city, country, or regional modifiers
- No local examples unless globally valid

---

## How to Research Code Sections

When the blog includes code:

1. **Identify where readers expect code:**
   - Setup
   - Configuration
   - Defaults
   - Anti-patterns

2. **Check how ranking blogs handle code:**
   - Inline vs block
   - Commented vs raw
   - Minimal vs verbose

3. **Improve by:**
   - Using smallest working examples
   - Adding comments only where logic is non-obvious
   - Explaining why, not just how
   - Showing safe defaults, not edge experiments

**Code exists to clarify decisions, not to show skill.**

---

## AEO FAQ Generation (AI-Driven)

The AI must infer FAQs based on:
- Primary keyword intent
- Secondary and long-tail keywords
- Common questions implied in ranking blogs
- Gaps found during competitive analysis

### Rules for FAQ Selection

- FAQs must be real questions users would search
- Each FAQ should map to a specific pain, decision, or confusion
- Avoid generic definitions already covered in H2s
- Prefer "how", "when", "should", "what happens if", "best practice" formats
- FAQs must be short, direct, and suitable for featured snippets

**These FAQs will be placed:**
- At the end of the blog
- After the conclusion
- After all core H2 sections

---

## Branding Decision Rules

**Brand mentions are allowed only if:**
- They solve a problem already discussed
- They appear after value is delivered
- They are optional, not mandatory

**If branding feels forced → Do not include it.**

### CTA Decision:
- If the blog is educational or SOP-style → No CTA
- If the blog addresses operational pain → Soft CTA allowed
- Never mix signals

**Answer must be yes or no. No hybrids.**

---

## Visual and Table Research

From ranking blogs, note:
- Average number of visuals (charts, diagrams, flows)
- What data they visualize
- Where visuals appear (early vs mid)

**General guidance:**
- 1 visual per major concept
- Tables only when comparison or checks are needed
- Avoid decorative images

---

## Research Output Required

The research phase must produce:

```
✅ Why the topic is worth writing
✅ Which angles matter most
✅ Which sections to prioritize
✅ What to skip
✅ Suggested H2 and H3 structure (limited)
✅ How to differentiate without increasing length
✅ Tone recommendation
✅ SEO and AEO alignment confirmation
```

**If any of the above is missing, research is incomplete.**

---

## Research Exit Criteria

Research is complete only when:
- Topic intent is clear
- Competitive gaps are identified
- Structure is decided
- Differentiation is defined
- Writing direction is unambiguous

---

# PHASE 2: TOC GENERATION

## Purpose
Generate a complete, SEO and AEO optimized Table of Contents based on the research file. The TOC must be final, production-ready, and follow strict constraints.

---

## Hard Constraints (Must Follow)

- **DO NOT use H1** – WordPress handles the page title separately
- Output one **Blog Title H2** (primary heading), then **6 to 7 Section H2s** including Conclusion
- All H2s appear in the WordPress TOC sidebar
- Do not exceed 7 section H2s (plus the blog title H2)
- Each H2 must be **≤ 60 characters** (recommend ≤ 50 chars)
- Each H2 may have **1–3 H3s**
- Do not exceed 3 H3s per H2

### Exception for Step-by-Step Guides:
- If an H2 explicitly represents a step-by-step section (e.g., "How to set up X (step-by-step)"):
  - It may have **4–8 H3s**
  - Each H3 must be a numbered step: "Step 1 – Short action phrase"
  - Every H3 must still be ≤ 60 characters
  - Do not create step H3s under more than **one H2** unless research strongly justifies multiple workflows

### Additional Rules:
- H3s must be ≤ 60 characters
- First two H2s must be phrased as direct user questions (AEO rule)
- Keep hierarchy sensible
- Do not add extra sections just to grow word count
- No geo targeting (no city, country, or local phrasing)

---

## Required TOC Output Format

**Note:** WordPress handles the page title separately. The first H2 in your content serves as the blog title and primary heading. All H2s appear in the WordPress TOC sidebar.

```markdown
## H2: Final blog title, include primary keyword if natural (This is the PRIMARY heading - no H1 used)

1. **H2: [heading text ≤60 chars]** (Section headings - appear in TOC)  
   - *Cue:* 1 short writing cue (10–18 words) — explain what to cover and the angle.  
   - *SEO target:* list 1 primary or secondary keyword to use in this section.  
   - *AEO snippet:* 1 sentence answer suitable for a featured snippet (for H2s 1 and 2 only).  
   - *H3s:*  
     - **H3: [heading text]** — 1 short cue (optional, repeat for up to 3 H3s)  
   - *Visuals:* suggest 0–2 visuals (type and purpose)  
   - *Code/table:* yes/no, and brief note what it should show

[Repeat for H2s 2–7]

---

**FAQs (AEO ready):**
- [Question 1, <90 chars]
- [Question 2, <90 chars]
- [Question 3, <90 chars]
- [Question 4, <90 chars]
- [Question 5, <90 chars]

**Images & Tables Plan:**
- [Visual 1: Section name - what data/concept it shows]
- [Visual 2: Section name - what data/concept it shows]
- [Visual 3: Section name - what data/concept it shows]

**CTA Rule:** [Yes/No - brief reason why]
```

---

## TOC Generation Guidance

- Use research to extract competitor TOC patterns and missed gaps
- Prioritize gaps that match practitioner needs
- For each H2, pick one clear intent
- Avoid overlap among H2s
- Make H2 headings scannable, action-oriented, include keyword when natural
- For first two H2s, AEO snippet must answer the question directly in one plain sentence
- When a concept might confuse readers, add explanatory H3 immediately under that H2
- For procedural "how-to", use exactly one H2 as step-by-step guide with numbered H3s
- For code sections, prefer minimal runnable snippet with comment on why that config matters
- For tables, suggest one "checklist" table and one "comparison or quick defaults" table
- FAQs must be inferred by AI from research, not provided by writer

---

## TOC Strict Output Rules

**If any heading exceeds 60 chars → Output must fail**  
**If fewer than 6 H2s are proposed → Output must fail**  
**If FAQs are not exactly 5 questions → Output must fail**

---

# PHASE 3: TESTDINO DOCUMENTATION REVIEW

**This phase happens BEFORE writing any content.**

## Objective
Gather all verified TestDino facts that will be referenced in the blog.

---

## Process

1. **Visit official documentation sources:**
   - https://docs.testdino.com/
   - https://www.npmjs.com/package/@testdino/playwright
   - https://changelog.testdino.com/

2. **Extract and document:**
   - Features mentioned in the blog topic
   - Capabilities relevant to the content
   - Configuration examples
   - Integration steps
   - Screenshots or visual assets available

3. **Create a verified facts sheet:**

```
TestDino Verified Facts for [Blog Topic]:

Feature: [Feature name]
Source: [URL from official docs]
Quote/Description: [Exact text or paraphrased fact]

Feature: [Feature name]
Source: [URL from official docs]
Quote/Description: [Exact text or paraphrased fact]

[Repeat for all TestDino references needed]
```

4. **Note what's NOT available:**
   - Features you wanted to mention but couldn't verify
   - Mark these for exclusion or verification request

---

## Documentation Review Exit Criteria

- All TestDino features/capabilities to be mentioned are verified
- Sources are documented
- Unverified claims are excluded
- Facts sheet is ready for content writing phase

---

# PHASE 4: CONTENT WRITING

## Goal
Write a professional, SEO and AEO optimized blog based on:
- The approved TOC
- Research data
- Verified TestDino facts

Target word count: **2000+ words** (adjust based on TOC depth)

**🚨 OUTPUT FORMAT:** All content MUST be formatted using WordPress HTML and shortcode components as defined in Phase 4.5. Do NOT output plain markdown.

---

## Tone of Voice

Use a mix of:
- **Professional**: explain concepts accurately
- **Conversational**: keep readability high
- **Technical where required**: explain data, code, concepts
- **Non-salesy**: mention brand or product only where it fits naturally

**Write like you are teaching a sharp colleague.**

---

## Readability Rules

- Paragraphs must be **2–3 sentences max**
- Short sentences
- Use lists and tables where it helps clarity
- Avoid long blocks of text
- Use simple English
- Avoid vague statements and fluff

---

## SEO Rules

1. **Use the Primary Keyword:**
   - In the title
   - Once in the first paragraph
   - In 1–2 section headers
   - Once in the conclusion

2. **Use Secondary Keywords:**
   - Naturally across the body where relevant
   - Do not force over-use

3. **Use Long Tail Keywords:**
   - Inside explanations or examples

4. **External References:**
   - Include links when mentioning data sources
   - Use official documentation for all tool references

---

## AEO / Q&A Rules

For every question header (AEO H2):
- Provide a **direct one-sentence answer** first
- Follow with **1–2 sentences** that explain the answer in context

**Example:**

```
What is X?
X is … (direct answer).
Here is why … (explanation).
```

Keep answers specific and concise.

---

## How to Use Research Points

When you reference research:
1. Introduce the data in 1 sentence
2. Add the statistic or fact
3. Explain what the data means

**Example:**

> According to research, X% of teams do Y ([Source]).
> This shows that …

**Always explain WHY the data matters to the reader.**

---

## TestDino Reference Rules

### When to Mention TestDino

Mention TestDino only when:
- It solves a problem already discussed in the section
- The mention adds value to the reader
- It appears after delivering value, not before
- It's optional, not mandatory

### How to Mention TestDino

- Use verified facts from your TestDino facts sheet only
- Link to official documentation: https://docs.testdino.com/
- Keep mentions natural and conversational
- Never force-fit TestDino into every section

**Example:**

✅ **Good:**
> "For teams running hundreds of Playwright tests in CI, tracking flaky patterns manually becomes impossible. Tools like TestDino offer AI-powered flaky test detection that surfaces patterns across runs ([docs](https://docs.testdino.com/))."

❌ **Bad:**
> "You need a test management tool. TestDino is the best solution for this. Sign up today."

---

## Infographics & Where to Place Them

Add only **2 or 3 infographics** and place them immediately after you explain context.

**Format:**

```
Infographic – Title: {{Short title}}
Data to show: {{List of data values}}
Chart type: {{Bar / Pie / Line}}
```

Then write **1–2 sentences** interpreting the visual.

**Do not place an infographic without explanation.**

---

## Tables & Where to Place Them

Insert tables when comparing values or summarizing metrics:

```markdown
Table – Info Points
| Metric      | Description | Source          |
|-------------|-------------|-----------------|
| X           | …           | [Link]({{URL}}) |
| Y           | …           | [Link]({{URL}}) |
```

Follow with one sentence explaining the table.

---

## Code Snippet Rules

Only include code when relevant to the section topic:
- Keep code under **20 lines**
- Add a brief comment at top explaining purpose
- Follow with **1–2 sentences** explaining what the code does

**Example:**

```javascript
// Example: filter failed tests
tests.filter(test => test.status === "failed")
```

---

## CTA Rule Protocol

**Decide CTA based on your research and CTA guidelines.**

### If CTA = Yes:

- Place one CTA only
- Place CTA near or at the end of conclusion
- Make it concise and relevant

**Format:**

```
Title: [Creative with some humor]
Subtitle: [Focuses on the main issue]
Button: [Where to redirect, what should it say]
```

**Example:**

```
Title: I Can Do This All Day
Subtitle: Your tests shouldn't have to. Stop the infinite retries with Stability Tracking.
Button: Stand Your Ground
```

### If CTA = No:

- Do not insert CTA anywhere
- Continue with natural conclusion

---

## Introduction Guidelines

Write the intro first:

1. **1st sentence:** What this blog is about (use primary keyword)
2. **2nd sentence:** What problem or question it answers
3. **3rd sentence:** What the reader will learn

**Keep it focused and concise.**

---

## Body Section Guidelines

For each TOC item:

### Step 1: Section Header
Use the exact header text from TOC.

### Step 2: Section Intro (2–3 sentences)
Explain what this section covers.

### Step 3: Supporting Lines (2–4 total)
Use:
- Researched data
- Examples
- Lists
- Code (if applicable)
- Visuals (if applicable)

### Step 4: Mini Conclusion or Transition
Wrap up the section with 1–2 sentences linking to the next idea.

---

## FAQ Section

Include all FAQs from your research.

For each:
- Direct answer first (1 sentence)
- Then explain in 1–2 sentences

**Keep answers short and useful.**

---

## Conclusion Guidelines

Write **2–3 short paragraphs:**

1. Summarize key points
2. Reinforce the benefit to reader
3. Include TestDino mention once (natural, not heavy) if CTA = Yes
4. If CTA = Yes, place it as the final element

**Keep the conclusion tight and valuable.**

---

# PHASE 4.5: WORDPRESS COMPONENT FORMATTING

## 🚨 CRITICAL: Do NOT Add Blocks/Banners Unless Explicitly Requested

**The following components should NEVER be added automatically:**
- ❌ `[info_banner]` – Only if user explicitly requests
- ❌ `[notice_block]` – Only if user explicitly requests
- ❌ `[tip_block]` – Only if user explicitly requests
- ❌ `[quote_block]` – Only if user explicitly requests
- ❌ `[testimonial_block]` – Only if user explicitly requests

**Always include these components:**
- ✅ `[code_light]` – Required for ALL code snippets
- ✅ `[faq_item]` – Required for ALL FAQ questions
- ✅ `[cta_regular]` – Only if CTA = Yes in research phase

Every blog must be formatted for direct WordPress publishing. Plain markdown is NOT acceptable. Use the component library below for reference.

---

## 🚨 HEADING STRUCTURE (CRITICAL)

**WordPress automatically generates a Table of Contents (TOC) from H2 tags.**

| Tag | Usage | Appears in TOC? |
|-----|-------|-----------------|
| `<h1>` | ❌ DO NOT USE | N/A |
| `<h2>` | Blog title + Section headings | ✅ YES |
| `<h3>` | Subsections under H2 | ❌ No |
| `<h4>` | Minor headings (rare) | ❌ No |

**Structure Example:**
```
<h2>Blog Title Here</h2>           ← Primary heading (appears in TOC)
Introduction paragraphs...

<h2>What is X?</h2>                ← Section heading (appears in TOC)
Content...
  <h3>Subsection</h3>              ← Does NOT appear in TOC
  Content...

<h2>How to Do Y?</h2>              ← Section heading (appears in TOC)
Content...

<h2>Conclusion</h2>                ← Section heading (appears in TOC)
```

**Why no H1?** WordPress CMS injects the page title as H1 automatically. Using H1 in content creates duplicate H1s and hurts SEO.

---

## Available Components Reference

### Basic HTML Elements

**🚨 HEADING HIERARCHY RULE:**
- **DO NOT use `<h1>`** – WordPress handles the page title separately
- **`<h2>`** = Blog title (primary heading) + Section headings (displayed in TOC)
- **`<h3>`** = Subsections under H2
- **`<h4>`** = Minor headings under H3 (rare)

```html
<!-- Headings (NO H1 - WordPress handles page title) -->
<h2>Blog Title / Section Heading</h2>  <!-- Primary - appears in TOC -->
<h3>Subsection Heading</h3>
<h4>Minor Heading</h4>

<!-- Text Formatting -->
<strong>Bold text</strong>
<em>Italic text</em>

<!-- Lists -->
<ul>
    <li>Unordered list item</li>
</ul>

<ol>
    <li>Ordered list item</li>
</ol>

<!-- Preformatted (for inline code references) -->
<pre>inline code</pre>
```

**Important:** All `<h2>` tags automatically appear in the WordPress Table of Contents (TOC) sidebar. Structure your H2s as the main navigable sections.

### WordPress Shortcode Components (Reference Only)

**🚨 REMINDER: Do NOT use info_banner, notice_block, tip_block, or quote_block unless the user explicitly requests them.**

#### 1. Info Banner (ONLY IF REQUESTED)
**Use for:** Key takeaways, important highlights, section summaries
```
[info_banner title="Banner Title" icon="https://testdino.com/wp-content/uploads/2026/01/fluent_info-sparkle-48-filled-3.svg" bg="#DBEAFE" border="#BFDBFE" color="#1E3A8A"]Content here[/info_banner]
```

**Color Presets:**
- Blue (info): bg="#DBEAFE" border="#BFDBFE" color="#1E3A8A"
- Green (success): bg="#F0FDF4" border="#BBF7D0" color="#166534"
- Purple (feature): bg="#FDF4FF" border="#F5D0FE" color="#86198F"
- Amber (highlight): bg="#FFFBEB" border="#FDE68A" color="#92400E"

#### 2. Notice Block (ONLY IF REQUESTED)
**Use for:** Warnings, important notes, cautions, prerequisites
```
[notice_block bg="#FEF3C7" border="#FCD34D" color="#92400E" icon="https://testdino.com/wp-content/uploads/2026/01/fi_768818.svg"]Warning or notice content[/notice_block]
```

**Color Presets:**
- Warning (amber): bg="#FEF3C7" border="#FCD34D" color="#92400E"
- Info (blue): bg="#F0F6FF" border="#C8DEFD" color="#032759"
- Danger (red): bg="#FEF2F2" border="#FECACA" color="#991B1B"

#### 3. Tip Block (ONLY IF REQUESTED)
**Use for:** Pro tips, best practices, quick insights
```
[tip_block title="Tip Title" icon="https://testdino.com/wp-content/uploads/2026/01/fi_841743.svg"]Tip content here[/tip_block]
```

#### 4. Code Light (ALWAYS REQUIRED FOR CODE)
**Use for:** All code snippets, terminal commands, configuration files
```
[code_light title="filename.js"]
<pre><code>// Your code here
const example = "code";</code></pre>
[/code_light]
```

**Title examples:** `mcp.json`, `Terminal`, `playwright.config.ts`, `Installation`

#### 5. Quote Block (ONLY IF REQUESTED)
**Use for:** Impactful statements, key insights, memorable phrases
```
[quote_block title="Attribution Name" theme="light"]Quote content[/quote_block]
```

#### 6. Testimonial Block (ONLY IF REQUESTED)
**Use for:** User testimonials, expert opinions
```
[testimonial_block name="Person Name" designation="Title" image="IMAGE_URL" theme="light"]Testimonial content[/testimonial_block]
```

#### 7. CTA Regular (ONLY IF CTA = YES)
**Use for:** Call-to-action at end of blog (only if CTA = Yes in research phase)
```
[cta_regular title="Catchy Title" description="Supporting description" button_text="Button Text" button_link="https://app.testdino.com/auth/signup" background="linear-gradient(90deg, #171717 0%, #4D4D4D 100%)" dragon_image="https://testdino.com/wp-content/uploads/2026/01/Group-626031.svg"]
```

#### 8. FAQ Item (ALWAYS REQUIRED FOR FAQs)
**Use for:** Each FAQ question in the FAQ section
```
[faq_item question="Question text here?" open="Yes"]Answer content here.[/faq_item]
```
- First FAQ: `open="Yes"` (expanded by default)
- Remaining FAQs: `open="No"` (collapsed by default)

#### 9. YouTube Section (ONLY IF REQUESTED)
**Use for:** Embedding video content when relevant
```
[youtube_section video="YOUTUBE_URL" image="THUMBNAIL_URL"]
```

---

## Component Placement Rules

### 🚨 CRITICAL: Do NOT Add Components Unless Explicitly Requested

**Components (info_banner, notice_block, tip_block, quote_block, testimonial_block) should ONLY be used when:**
- The user explicitly requests them
- The user specifies which content should be wrapped in components
- The user provides a component-formatted draft to convert

**Always Include (When Applicable):**

| Component | When to Use |
|-----------|-------------|
| Code Light | Wrap ALL code snippets (this is always required for code) |
| FAQ Items | FAQ section at end (required for FAQs) |
| CTA Regular | End of conclusion (only if CTA = Yes in research) |

**Do NOT automatically add these components:**
- ❌ Info Banner – Only if user explicitly requests
- ❌ Notice Block – Only if user explicitly requests
- ❌ Tip Block – Only if user explicitly requests
- ❌ Quote Block – Only if user explicitly requests
- ❌ Testimonial Block – Only if user explicitly requests

### Spacing Rules (When Components ARE Used):

- Do NOT stack multiple components consecutively without text between them
- Each component should be preceded by `*Inside [Component Name]:*` marker

---

## Output Format with Component Markers

**CRITICAL:** When outputting the blog, precede each component with a marker line for clarity.

### Marker Format:
```
*Inside [Component Name]:*

[component shortcode here]
```

### Example Output Pattern:

```
<!-- Blog Title (Primary Heading - NO H1 used) -->
<h2>TestDino MCP: Complete Setup Guide</h2>

Introduction paragraph here. No components in this section.

<!-- Section Heading (appears in TOC) -->
<h2>How to Set Up TestDino MCP</h2>

Setting up TestDino MCP takes under 5 minutes. Here's the complete process.

<h3>Step 1 – Generate Your Personal Access Token</h3>

Log in to TestDino and navigate to <strong>Settings → Personal Access Tokens</strong>. Save your Personal Access Token securely. You cannot view it again after creation.

<h3>Step 2 – Install via NPX</h3>

Run the following command in your terminal:

*Inside Code Light:*

[code_light title="Terminal"]
<pre><code>npx testdino-mcp</code></pre>
[/code_light]

NPX always runs the latest version without manual updates.
```

**Note:** Notice blocks, tip blocks, info banners, and quote blocks are NOT included by default. Only add them if the user explicitly requests components.

---

## Section Guidelines

### Introduction (After Blog Title H2)
- NO components in introduction section
- Use plain `<h2>` for blog title, then paragraphs only
- The blog title H2 is the primary heading (no H1 used)

### Body Sections
- Code Lights for ALL code snippets (always required)
- Other components (info_banner, notice_block, tip_block, quote_block) ONLY if explicitly requested by user

### FAQ Section
- Use `[faq_item]` for EVERY question
- First item: `open="Yes"`
- All others: `open="No"`

### Conclusion
- CTA Regular ONLY if CTA = Yes in research phase

---

## WordPress Component Checklist

Before finalizing, verify:

**HTML Structure:**
- [ ] NO `<h1>` tags used (WordPress handles page title separately)
- [ ] Blog title uses `<h2>` as primary heading
- [ ] All section headings use `<h2>` (these appear in TOC)
- [ ] All subsections use `<h3>` or `<h4>`
- [ ] All lists use `<ul><li>` or `<ol><li>` HTML tags
- [ ] All bold text uses `<strong>` tags
- [ ] All italic text uses `<em>` tags

**Required Components:**
- [ ] All code snippets wrapped in `[code_light]`
- [ ] All 5 FAQs use `[faq_item]` shortcode
- [ ] First FAQ has `open="Yes"`, others have `open="No"`
- [ ] CTA uses `[cta_regular]` if CTA = Yes

**Optional Components (ONLY if explicitly requested by user):**
- [ ] Info Banners – ONLY if user requested
- [ ] Notice Blocks – ONLY if user requested
- [ ] Tip Blocks – ONLY if user requested
- [ ] Quote Blocks – ONLY if user requested

**Formatting:**
- [ ] Each component preceded by `*Inside [Name]:*` marker
- [ ] No consecutive components without text between them
- [ ] No components in introduction section

---

# PHASE 5: INTERNAL LINKING

## Objective
Add contextual internal links from TestDino's existing blog inventory to strengthen SEO and provide value to readers.

**Source:** https://testdino.com/post-sitemap.xml

---

## Internal Linking Rules

### Linking Guidelines

1. **Minimum:** 0 links (if nothing fits naturally)
2. **Maximum:** 2 links per blog
3. **Only link when:**
   - It's topically relevant
   - It adds value to the reader
   - The anchor text is natural and already exists in your content

### How to Add Internal Links

1. **Review the sitemap:** Identify blogs that relate to the current topic
2. **Find natural anchor text:** Use existing phrases in your content
3. **Link contextually:** Place links where they support the reader's journey

**Example:**

```
Before:
"Proper test organization helps teams scale Playwright suites efficiently."

After:
"Proper [test organization](https://testdino.com/playwright-test-organization) helps teams scale Playwright suites efficiently."
```

### What NOT to Do

❌ Force links where they don't fit  
❌ Create new anchor text just to add a link  
❌ Link to tangentially related content  
❌ Add links in the introduction  
❌ Add more than 2 links total

---

## Internal Linking Process

1. **Access sitemap:** https://testdino.com/post-sitemap.xml
2. **Identify 2-3 candidate blogs** that relate to your topic
3. **Scan your written content** for natural anchor text opportunities
4. **Add 0-2 links** where they fit organically
5. **Verify links** are working and contextually appropriate

---

# PHASE 6: FINAL QA CHECKLIST

Run all checks before publishing.

---

## Research Phase Checklist

- [ ] Topic intent is clear
- [ ] Competitive gaps are identified
- [ ] Structure is decided based on ranking blogs
- [ ] Differentiation strategy is defined
- [ ] SEO and AEO alignment confirmed
- [ ] FAQ questions inferred by AI (not user-provided)
- [ ] CTA decision made (Yes/No with reason)

---

## TOC Generation Checklist

- [ ] Blog title H2 is clear and includes primary keyword naturally
- [ ] NO H1 used (WordPress handles page title separately)
- [ ] 6-7 section H2s total (including Conclusion) – these appear in TOC
- [ ] All H2s are ≤ 60 characters
- [ ] First 2 section H2s are phrased as direct questions
- [ ] Each H2 has 1-3 H3s (exception: one step-by-step H2 may have 4-8)
- [ ] All H3s are ≤ 60 characters
- [ ] Step-by-step H3s follow "Step N – Action" format
- [ ] No geographic targeting in any heading
- [ ] Exactly 5 FAQs generated, each <90 characters
- [ ] Images & Tables plan created (3 items mapped to sections)
- [ ] CTA rule documented (Yes/No with reason)

---

## TestDino Documentation Review Checklist

- [ ] All TestDino features mentioned are verified from official docs
- [ ] Sources documented for each fact
- [ ] Unverified claims excluded
- [ ] TestDino facts sheet created for writing phase
- [ ] Official documentation links ready (docs.testdino.com, npmjs, changelog)

---

## Content Writing Checklist

### Structure
- [ ] Introduction uses primary keyword in first paragraph
- [ ] All H2/H3 headings match TOC exactly
- [ ] Each section has 2-3 sentence intro
- [ ] Paragraphs are 2-3 sentences max
- [ ] Transitions link sections logically
- [ ] Conclusion summarizes key points in 2-3 paragraphs

### SEO
- [ ] Primary keyword used in: title, intro, 1-2 headers, conclusion
- [ ] Secondary keywords used naturally (not forced)
- [ ] Long-tail keywords in explanations/examples
- [ ] No keyword stuffing
- [ ] No geographic targeting

### AEO
- [ ] First 2 H2s answer questions directly (1 sentence first)
- [ ] FAQ section includes all 5 questions from TOC
- [ ] Each FAQ has direct answer + 1-2 sentence explanation
- [ ] Answers are featured snippet-ready

### Readability
- [ ] Tone is professional yet conversational
- [ ] No long blocks of text
- [ ] Simple English used throughout
- [ ] No vague statements or fluff
- [ ] Technical accuracy maintained

### TestDino References
- [ ] All TestDino mentions verified from official docs
- [ ] Links to docs.testdino.com included
- [ ] Mentions appear after value delivery
- [ ] Mentions are natural, not forced
- [ ] No unverified claims about TestDino features

### Visuals
- [ ] 2-3 infographics placed with context
- [ ] Each infographic has 1-2 sentence interpretation
- [ ] Tables used for comparisons/metrics only
- [ ] Each table followed by explanatory sentence

### Code
- [ ] Code snippets ≤ 20 lines
- [ ] Comments explain purpose (not every line)
- [ ] 1-2 sentences explain what code does
- [ ] Code shows safe defaults

### CTA
- [ ] If CTA = Yes: placed near/at end of conclusion
- [ ] If CTA = Yes: includes Title, Subtitle, Button
- [ ] If CTA = No: no CTA included anywhere

### WordPress Components
- [ ] NO `<h1>` tags used (WordPress handles page title)
- [ ] Blog title and sections use `<h2>` (primary heading, appears in TOC)
- [ ] Subsections use `<h3>` or `<h4>`
- [ ] All lists use HTML tags (`<ul><li>` or `<ol><li>`)
- [ ] All text formatting uses HTML (`<strong>`, `<em>`)
- [ ] All code snippets wrapped in `[code_light]` shortcode
- [ ] All 5 FAQs use `[faq_item]` shortcode
- [ ] First FAQ has `open="Yes"`, remaining have `open="No"`
- [ ] CTA uses `[cta_regular]` shortcode (if CTA = Yes)
- [ ] Info/Notice/Tip/Quote blocks ONLY if explicitly requested by user
- [ ] Each component preceded by `*Inside [Component Name]:*` marker
- [ ] No components placed in introduction section
- [ ] No consecutive components without text between them

---

## Internal Linking Checklist

- [ ] Sitemap reviewed (testdino.com/post-sitemap.xml)
- [ ] 0-2 internal links added (not forced)
- [ ] Links are topically relevant
- [ ] Anchor text is natural (already existed in content)
- [ ] Links add value to reader
- [ ] No links in introduction
- [ ] All links tested and working

---

## Final Quality Checklist

- [ ] Word count is 2000+ words (or appropriate for TOC depth)
- [ ] All external references linked with sources
- [ ] No grammatical errors
- [ ] No spelling mistakes
- [ ] All headings are scannable
- [ ] Content delivers on introduction promise
- [ ] Meta title (55-65 chars) and meta description (150-160 chars) ready
- [ ] URL slug matches recommended format
- [ ] Content provides unique value vs competitors
- [ ] TestDino positioning is appropriate and verified

---

## Final Publishing Checklist

- [ ] All 7 workflow phases completed (including 4.5)
- [ ] All checklists passed
- [ ] Content reviewed for accuracy
- [ ] Links verified (internal + external)
- [ ] WordPress components properly formatted
- [ ] Component markers (`*Inside [Name]:*`) included
- [ ] HTML and shortcodes validated
- [ ] Ready for WordPress paste

---

# WORKFLOW SUMMARY

```
1. RESEARCH
   ↓
   [Research Output + Exit Criteria Met]
   ↓
2. TOC GENERATION
   ↓
   [TOC Approved + Checklist Passed]
   ↓
3. TESTDINO DOCUMENTATION REVIEW
   ↓
   [Facts Sheet Created + Checklist Passed]
   ↓
4. CONTENT WRITING
   ↓
   [Content Draft Complete + Checklist Passed]
   ↓
4.5. WORDPRESS COMPONENT FORMATTING
   ↓
   [All Components Applied + Markers Added]
   ↓
5. INTERNAL LINKING
   ↓
   [Links Added + Checklist Passed]
   ↓
6. FINAL QA
   ↓
   [All Checklists Passed]
   ↓
PUBLISH
```

---

# APPENDIX: QUICK REFERENCE URLS

**TestDino Official Documentation:**
- Primary docs: https://docs.testdino.com/
- NPM package: https://www.npmjs.com/package/@testdino/playwright
- Changelog: https://changelog.testdino.com/

**Internal Linking:**
- Sitemap: https://testdino.com/post-sitemap.xml

---

**END OF MASTER CONTENT PROTOCOL**
