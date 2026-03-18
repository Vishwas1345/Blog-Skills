---
name: component-formatter
description: Assign WordPress component markers to plain blog content WITHOUT changing any words. Strictly preserves all original content - only adds headings tags and component wrappers (code_light for multi-line code, faq_item for FAQs). Never modifies, rewrites, or removes any text.
---

# CONTENT TO COMPONENT FORMATTER

## Purpose
Assign component markers to plain blog content. **STRICTLY PRESERVES all original content** – does not change, rewrite, or remove a single word. Only converts headings to HTML tags and wraps appropriate content in component markers.

---

## 🚨 CRITICAL RULES – READ CAREFULLY

### 🛑 ABSOLUTE CONTENT PRESERVATION (NON-NEGOTIABLE)

**You are a FORMATTER, not a writer. Your ONLY job is to assign components.**

- ❌ **DO NOT** change a single word of the original content
- ❌ **DO NOT** rewrite, rephrase, or improve any sentence
- ❌ **DO NOT** add new content, examples, or explanations
- ❌ **DO NOT** remove any word, sentence, or paragraph
- ❌ **DO NOT** fix grammar, spelling, or punctuation
- ❌ **DO NOT** summarize or shorten any content
- ❌ **DO NOT** expand or elaborate on any content
- ❌ **DO NOT** rearrange paragraphs or sections
- ❌ **DO NOT** move content from one place to another
- ❌ **DO NOT** change the order of sentences or words

**✅ You ONLY:**
1. Convert headings to `<h2>` and `<h3>` HTML tags
2. Assign component markers (code_light, faq_item, tables, CTA)
3. Keep EVERY SINGLE WORD exactly as provided
4. Keep the EXACT SAME ORDER of all content

**If the input says "teh" instead of "the" – keep it as "teh".**
**If a sentence is awkward – keep it awkward.**
**If the flow seems wrong – keep it exactly as provided.**
**Your job is ONLY to wrap content in components, nothing else.**

---

### Code Light Rules (STRICT)

**ONLY use `[code_light]` for ACTUAL CODE:**
- ✅ Multi-line commands (npm install, terminal commands)
- ✅ Programming syntax (functions, variables, config files)
- ✅ Code blocks with multiple lines
- ✅ JSON, YAML, or configuration snippets

**NEVER use `[code_light]` for:**
- ❌ Single words like `npm`, `playwright`, `API`, `before.all()` , `playwright.config.ts`, `to.be.visible()`
- ❌ Inline mentions of tool names or keywords
- ❌ Short phrases that aren't executable code
- ❌ File names mentioned in text (like "open config.js")

**Example – WRONG:**
```
Use the [code_light]npm[/code_light] package manager.
```

**Example – CORRECT:**
```
Use the npm package manager.

Inside Code Light: [code_light]

npm install playwright

[/code_light]
```

**🚨 CODE CONTEXT RULE (CRITICAL):** Every `[code_light]` block MUST be preceded by a **practical file name** (e.g., `playwright.config.ts`, `auth-setup.ts`) or a suitable heading that indicates where the code is executed. **NEVER** use generic names or actions (like "Code Snippet" or "Updating Logic") as the primary identifier. If it's a test snippet, always provide a spec file name (e.g., `login.spec.ts`). If the original content lacks this context, you MUST identify the correct file name and add it as a bold label or small heading immediately before the code light.

---

### 🚨 Inline Code Wrapping (CRITICAL)

**When code appears WITHIN a sentence, wrap it with `[ct]` shortcode:**

**Use `[ct]` for:**
- ✅ Single command words in sentences: `npm`, `npx`, `git`
- ✅ File paths/names in text: `playwright.config.ts`, `.github/workflows/playwright.yml`
- ✅ Function names in text: `before.all()`, `to.be.visible()`
- ✅ Keywords/parameters in text: `when: always`, `parallel`, `trace: 'on'`
- ✅ **Table Cells:** Any code-like words, file names, or commands within table cells MUST be wrapped with `[ct]`
- ✅ Short code snippets within sentences

**Format:**
```
[ct]code text[/ct]
```

**Examples:**
- Without it, someone has to manually run [ct]npx playwright test[/ct] before every merge
- The workflow file lives at [ct].github/workflows/playwright.yml[/ct]
- Set [ct]when: always[/ct] on artifacts in GitLab CI
- The [ct]parallel[/ct] keyword makes Playwright sharding dead simple
- Open the [ct]playwright.config.ts[/ct] file and add trace configuration
- Use the [ct]expect()[/ct] function to validate API responses

**🚨 IMPORTANT:**
- Use `[ct]` for inline code mentions WITHIN sentences
- Use `[code_light]` for multi-line code blocks
- `[ct]` can appear inside Tip and Note blocks - the HTML skill will apply context-aware styling (different background and text colors for Tips vs Notes)
- Do NOT nest `[ct]` inside other components (except Tip/Note blocks)

---

### Input/Output Rules

1. **Input:** Plain blog content (text with headings, paragraphs, code, lists)
2. **Output:** EXACT same content with HTML headings and component markers
3. **Convert headings** to `<h2>` and `<h3>` HTML tags
4. **Preserve ALL original text** – Every word must remain unchanged

### 🚨 Component Rules:

**ALWAYS add these components:**
- ✅ `[code_light]` – Required for ALL code snippets
- ✅ `[faq_item]` – Required for ALL FAQ questions
- ✅ `[tips_banner]` – Required when content contains "TL;DR" (see TL;DR Detection Rules below)
- ✅ `[tip]` – Required when content contains tip patterns (see Tip Detection Rules below)
- ✅ `[note]` – Required when content contains "NOTE:" or "Note:" (see Note Detection Rules below)

**NEVER add these components unless user explicitly requests:**
- ❌ `[info_banner]` – Only if user explicitly requests
- ❌ `[notice_block]` – Only if user explicitly requests
- ❌ `[tip_block]` – Only if user explicitly requests
- ❌ `[quote_block]` – Only if user explicitly requests
- ❌ `[cta_regular]` – Only if user explicitly requests or CTA = Yes

---

### 🚨 Tip Detection Rules (AUTOMATIC)

**When to add `[tip]` marker:**
Automatically detect and wrap tips when content contains these patterns:
- ✅ Starts with "TIP:" or "Tip:"
- ✅ Starts with "PRO TIP:" or "Pro tip:"
- ✅ Starts with "BEST PRACTICE:" or "Best practice:"
- ✅ Starts with "REMEMBER:" or "Remember:" (important reminder)

**Format:**
```
Inside Tip: [tip]
TIP: Your tip content here.
[/tip]
```

**Examples:**
```
Inside Tip: [tip]
TIP: Start with your most visited pages. Your homepage, login page, and primary user flow cover the highest-impact surface area.
[/tip]
```

```
Inside Tip: [tip]
PRO TIP: Use .exclude() sparingly and only for elements you genuinely can't control (third-party embeds, for example).
[/tip]
```

**🚨 IMPORTANT:**
- The tip marker `[tip]` is REQUIRED whenever you detect a tip pattern
- Keep the "TIP:" prefix in the content - don't remove it
- Wrap the entire tip paragraph, including the TIP: prefix
- This is NOT optional - tips must always be marked
- **Inline Code inside Tips**: If inline code inside a notice block for tip conversion (`[ct]`) is present, it MUST have `#FFFFFF` background (`bg-[#FFFFFF]`) and `#713F12` text color (`text-[#713F12]`).

---

### 🚨 Note Detection Rules (AUTOMATIC)

**When to add `[note]` marker:**
Automatically detect and wrap notes when content contains these patterns:
- ✅ Starts with "NOTE:" or "Note:"
- ✅ Starts with "IMPORTANT:" or "Important:"
- ✅ Starts with "PREREQUISITE:" or "Prerequisite:"

**Format:**
```
Inside Note: [note]
NOTE: Your note content here.
[/note]
```

**Examples:**
```
Inside Note: [note]
NOTE: Make sure to install dependencies before running tests.
[/note]
```

```
Inside Note: [note]
PREREQUISITE: You need Node.js 18+ and npm installed on your system.
[/note]
```

**🚨 IMPORTANT - DO NOT CONFUSE TIPS AND NOTES:**
- The note marker `[note]` is REQUIRED whenever you detect a note pattern
- Keep the "NOTE:" prefix in the content - don't remove it
- Wrap the entire note paragraph, including the NOTE: prefix
- This is NOT optional - notes must always be marked

**🚨 CRITICAL DIFFERENCE BETWEEN TIPS AND NOTES:**
- **TIPS** (`[tip]`): Yellow theme with sparkle icon in HTML
  - HTML: `[notice_block bg="#FEFCE8" border="#FDE68A" color="#713F12" icon="...fluent_info-sparkle-48-filled.svg"]`
  - Inline code `[ct]` inside tips MUST use `bg-[#FFFFFF]` and `text-[#713F12]`
- **NOTES** (`[note]`): Green theme with NO icon in HTML
  - HTML: `[notice_block bg="#E1FFF0" border="#A7F3D0" color="#065F46" icon=""]`

**When to use which:**
- Use `[tip]` for: TIP:, PRO TIP:, BEST PRACTICE:, REMEMBER:
- Use `[note]` for: NOTE:, IMPORTANT:, PREREQUISITE:

---

### 🚨 TL;DR Detection Rules (AUTOMATIC - USES TIPS_BANNER)

**When to add `[tips_banner]` marker:**
Automatically detect and wrap TL;DR content when it contains:
- ✅ Starts with "TL;DR" or "TL;DR:" or "TLDR" or "TLDR:"
- ✅ Contains quick summary or key takeaways at the start of blog

**🚨 CRITICAL FORMAT - USE EXACTLY THIS:**
```
[tips_banner title="TL;DR" icon="" bg="#FEFCE8" border="#FDE68A" color="#713F12"]Content[/tips_banner]
```

**Format Rules:**
- **ALWAYS** use `title="TL;DR"` (exactly as shown)
- **ALWAYS** use `icon=""` (empty string)
- **ALWAYS** use `bg="#FEFCE8"` (light yellow background)
- **ALWAYS** use `border="#FDE68A"` (yellow border)
- **ALWAYS** use `color="#713F12"` (dark brown text)
- **DO NOT** use `[tip]` or `[notice_block]` for TL;DR - only `[tips_banner]`

**Examples:**
```
[tips_banner title="TL;DR" icon="" bg="#FEFCE8" border="#FDE68A" color="#713F12"]
- Playwright Trace Viewer shows test execution timeline and DOM snapshots
- Enable with trace: 'on-first-retry' in playwright.config.ts
- Access traces locally or stream to TestDino for CI debugging
[/tips_banner]
```

```
[tips_banner title="TL;DR" icon="" bg="#FEFCE8" border="#FDE68A" color="#713F12"]
Use visual regression testing to catch UI bugs automatically. Start with critical user flows, exclude dynamic elements, and run tests in CI.
[/tips_banner]
```

**🚨 IMPORTANT:**
- TL;DR uses `[tips_banner]` shortcode, NOT `[tip]` or `[notice_block]`
- Always use the EXACT color values provided above
- Keep the content exactly as written - no modifications
- The title must be "TL;DR" (not "Summary" or anything else)

---

### 💡 Definition Blocks (OPTIONAL – Use Sparingly)

**Purpose:** Help non-technical readers understand complex technical terms.

**When to add:**
- ✅ ONLY for terms that a non-technical person would NOT understand
- ✅ Technical jargon, acronyms, or concepts that need explanation
- ✅ Use your judgment – NOT every blog needs definitions

**Strict Limits:**
- 🚨 **MAXIMUM 2 definition blocks per blog** – No more than 2
- 🚨 Do NOT add definitions for common terms (API, URL, database, etc.)
- 🚨 Do NOT add definitions if the blog is already beginner-friendly

**🚨 Format (uses tips_banner with BLUE theme):**
```
[tips_banner title="What is Term Name?" icon="" bg="#DBEAFE" border="#BFDBFE" color="#1E3A8A"]Brief, simple definition that a non-technical person can understand.[/tips_banner]
```

**🚨 CRITICAL FORMAT RULES:**
- Use `[tips_banner]` shortcode (NOT `[tip_block]`)
- Title must be a question: `title="What is Term Name?"`
- Use BLUE theme colors: `bg="#DBEAFE" border="#BFDBFE" color="#1E3A8A"`
- Icon must be empty: `icon=""`
- Content goes between opening and closing tags

**Examples:**

```
[tips_banner title="What is Playwright MCP?" icon="" bg="#DBEAFE" border="#BFDBFE" color="#1E3A8A"]Playwright MCP (Model Context Protocol) is an MCP server maintained by Microsoft that exposes Playwright's browser automation as a set of callable tools. It uses the MCP standard introduced by Anthropic, which lets AI models interact with external tools in a structured way.[/tips_banner]
```

```
[tips_banner title="What is a Webhook?" icon="" bg="#DBEAFE" border="#BFDBFE" color="#1E3A8A"]A webhook is like a doorbell for your app – when something happens on another service, it automatically notifies your application.[/tips_banner]
```

```
[tips_banner title="What is CI/CD?" icon="" bg="#DBEAFE" border="#BFDBFE" color="#1E3A8A"]CI/CD (Continuous Integration/Continuous Deployment) is an automated process that tests and deploys code changes to production whenever developers push updates.[/tips_banner]
```

**Remember:**
- This is OPTIONAL – many blogs won't need any definitions
- Keep definitions SHORT and in simple language
- Place the definition near where the term first appears
- Title should always be "What is X?" format

---

## HEADING CONVERSION

### Rules

| Main title / Section headings | `<h2>Heading Text</h2>` |
| Subsections | `<h3>Subsection Text</h3>` |

**🚨 STRICT HIERARCHY:** Headings MUST follow a strict hierarchy (H2 > H3 > H4). Never skip a level (e.g., skip H2 and go straight to H3).

**🚨 NEVER use `<h1>`** – WordPress handles page title separately.

---

## REQUIRED COMPONENTS

### 1. Code Light (ONLY FOR MULTI-LINE CODE BLOCKS)

**Triggers:** Multi-line code blocks, terminal commands, configuration files

**Common code syntaxes to detect:**
- ✅ Test files (`.spec.js`, `.test.js`, `.spec.ts`, `.test.ts`)
- ✅ Test cases with describe/it blocks
- ✅ Playwright config files (`playwright.config.js`, `playwright.config.ts`)
- ✅ GitHub Actions workflow YAML files (`.yml`, `.yaml`)
- ✅ Package.json scripts
- ✅ TypeScript/JavaScript functions
- ✅ Configuration files (JSON, YAML, JS, TS)
- ✅ Any multi-line code syntax

**🚨 REMINDER:** Do NOT wrap single words, function names, or file names in code lights. Only wrap actual executable multi-line code.

**Format:**
```
Inside Code Light: [code_light]



npm init playwright@latest

[/code_light]
```

**🚨 CRITICAL:**
- Leave two blank lines after `[code_light]` opening tag
- The HTML skill will apply full syntax highlighting with colors to EVERY code token
- Every keyword, function, string, variable, punctuation, comment, and number will be wrapped in colored `<span>` tags
- Code will use Geist Mono font with weight 300
- Make sure to detect ANY multi-line code syntax, not just the examples above
- **Context Awareness:** Ensure the code block is preceded by a filename or suitable description.

---

### 2. Tip Marker (ALWAYS REQUIRED FOR TIPS)

**Triggers:** Content that starts with "TIP:", "PRO TIP:", "BEST PRACTICE:", "REMEMBER:"

**Format:**
```
Inside Tip: [tip]
TIP: Your tip content here.
[/tip]
```

**Examples:**
```
Inside Tip: [tip]
TIP: Start with your most visited pages. Your homepage, login page, and primary user flow cover the highest-impact surface area. You can expand coverage later without restructuring anything.
[/tip]
```

```
Inside Tip: [tip]
PRO TIP: Use .exclude() sparingly and only for elements you genuinely can't control (third-party embeds, for example). Every exclusion is a blind spot.
[/tip]
```

**🚨 CRITICAL:**
- This is AUTOMATIC and REQUIRED - not optional
- Keep the "TIP:" prefix in the content
- Wrap the complete tip paragraph

---

### 3. Note Marker (ALWAYS REQUIRED FOR NOTES)

**Triggers:** Content that starts with "NOTE:", "IMPORTANT:", "PREREQUISITE:"

**Format:**
```
Inside Note: [note]
NOTE: Your note content here.
[/note]
```

**Examples:**
```
Inside Note: [note]
NOTE: Make sure to install dependencies before running tests.
[/note]
```

```
Inside Note: [note]
PREREQUISITE: You need Node.js 18+ and npm installed on your system.
[/note]
```

**🚨 CRITICAL:**
- This is AUTOMATIC and REQUIRED - not optional
- Keep the "NOTE:" prefix in the content
- Wrap the complete note paragraph
- Notes use the same colors as tips but a DIFFERENT icon (prerequisites icon)

---

### 4. FAQ Item (ALWAYS REQUIRED FOR FAQs)

**Triggers:** Questions with answers in FAQ section

**Format:**
```
Inside FAQ Item: [faq_item question="Question text here?"]answer="Answer text here. [/faq_item]
```

---

## OPTIONAL COMPONENTS (ONLY IF USER REQUESTS)

The following components should ONLY be added if the user explicitly requests them. Do NOT add them automatically based on content patterns.

### Tip Block (ONLY IF REQUESTED)

**Format:**
```
Inside Tip Block: [tip_block icon_name="lightbulb" color_name="blue" content="Your tip content here."] [/tip_block]
```

---

### Info Banner (ONLY IF REQUESTED)

**Format:**
```
Inside Info Banner: [info_banner icon_name="info" color_name="COLOR" content="Your content here."] [/info_banner]
```

**Color Options:**
- `"blue"` – Statistics, data, informational
- `"green"` – Success, positive outcomes
- `"purple"` – Features, capabilities
- `"amber"` – Highlights, important notes

---

### Notice Block (ONLY IF REQUESTED)

**Format:**
```
Inside Notice Block: [notice_block icon_name="warning" color_name="COLOR" content="Your notice content here."] [/notice_block]
```

**Color Options:**
- `"yellow"` – Warnings, cautions
- `"blue"` – Notes, information
- `"red"` – Danger, critical warnings

---

### CTA Regular (ONLY IF REQUESTED OR CTA = YES)

**Format:**
```
Inside CTA Regular: [cta_regular title="Title" description="Description" button_text="Button Text" button_link="URL"]
```

---

## PLACEMENT RULES

### Guidelines

1. **Introduction section:** NO components – plain paragraphs only
2. **Code snippets:** ALWAYS wrap with Code Light
3. **FAQ section:** ALWAYS use FAQ Items for all Q&As
4. **Tips/Warnings/Info:** Do NOT add unless user explicitly requests
5. **CTA:** Only if user requests or CTA = Yes

---

## EXAMPLE CONVERSION

### Input (Plain Content):

```
Playwright API Testing: Complete Guide with Examples

Testing APIs shouldn't mean switching between tools. You're already running Playwright for your UI tests, and here's the thing: Playwright handles API testing too.

What is Playwright API Testing?

Playwright API testing lets you send HTTP requests and validate responses without opening a browser.

Setting Up Playwright for API Testing

Getting started with Playwright API testing takes about five minutes.

Step 1 - Install Playwright

Open your terminal and run this command:

npm init playwright@latest

Store API tokens in environment variables, never commit them to your repository.

Note: Never commit authentication credentials to version control.

Always clean up test data after your tests run. Use afterEach hooks to delete resources.

FAQs

Can Playwright test GraphQL APIs?
Yes, Playwright can test GraphQL APIs. Send POST requests with your GraphQL query in the request body.

How do I test file uploads with Playwright API?
Use the multipart option in your POST request.
```

### Output (Component-Specified Content):

```
<h2>Playwright API Testing: Complete Guide with Examples</h2>

Testing APIs shouldn't mean switching between tools. You're already running Playwright for your UI tests, and here's the thing: Playwright handles API testing too.

<h2>What is Playwright API Testing?</h2>

Playwright API testing lets you send HTTP requests and validate responses without opening a browser.

<h2>Setting Up Playwright for API Testing</h2>

Getting started with Playwright API testing takes about five minutes.

<h3>Step 1 - Install Playwright</h3>

Open your terminal and run this command:

Inside Code Light: [code_light]



npm init playwright@latest

[/code_light]

Store API tokens in environment variables, never commit them to your repository.

Never commit authentication credentials to version control.

Always clean up test data after your tests run. Use [ct]afterEach[/ct] hooks to delete resources.

<h2>FAQs</h2>

Inside FAQ Item: [faq_item question="Can Playwright test GraphQL APIs?"] Yes, Playwright can test GraphQL APIs. Send POST requests with your GraphQL query in the request body. [/faq_item]

Inside FAQ Item: [faq_item open="No" question="How do I test file uploads with Playwright API?"] Use the multipart option in your POST request. [/faq_item]
```

**Note:** The `[ct]afterEach[/ct]` wraps inline code within a sentence. This will be converted to a styled span in the HTML skill.

**Note:** Tips, notices, and info banners are NOT included unless the user explicitly requests them.

---

## VALIDATION CHECKLIST

Before finalizing output, verify:

**🛑 Content Preservation (MOST IMPORTANT):**
- [ ] Every single word from input exists in output UNCHANGED
- [ ] No words were added that weren't in the original
- [ ] No words were removed from the original
- [ ] No sentences were rewritten or rephrased
- [ ] Grammar/spelling mistakes from original are KEPT as-is
- [ ] Content flow/order is EXACTLY the same as input
- [ ] No paragraphs or sections were rearranged

**Code Light Usage:**
- [ ] Code lights ONLY wrap actual multi-line code/commands
- [ ] Single words (npm, API, etc.) are NOT wrapped in code lights
- [ ] Inline code within sentences is wrapped with `[ct]` shortcode
- [ ] `[ct]` is used for file paths, function names, commands, and keywords in text (including inside table cells)
- [ ] **Code Context:** Every code light is preceded by a file name or a suitable descriptive heading.

**Definition Blocks (if used):**
- [ ] Maximum 2 definition blocks in the entire blog
- [ ] Only for genuinely complex/technical terms
- [ ] Definitions are SHORT and in simple language

**Headings:**
- [ ] All main headings converted to `<h2>` tags
- [ ] All subsections converted to `<h3>` tags
- [ ] NO `<h1>` tags used
- [ ] **Strict Hierarchy:** Headings follow a strict H2 > H3 > H4 tag hierarchy with no jumping/skipping levels

**Required Components:**
- [ ] All multi-line code blocks wrapped with `Inside Code Light:` marker
- [ ] All tips (TIP:, PRO TIP:, etc.) wrapped with `Inside Tip:` marker
- [ ] All notes (NOTE:, IMPORTANT:, PREREQUISITE:) wrapped with `Inside Note:` marker
- [ ] All FAQs use `Inside FAQ Item:` format
- [ ] First FAQ has `open="Yes"`, others have `open="No"`

**Optional Components (ONLY if user requested):**
- [ ] Info banners – ONLY if user explicitly requested
- [ ] Notice blocks – ONLY if user explicitly requested
- [ ] Tip blocks – ONLY if user explicitly requested

**General:**
- [ ] No components in introduction section

---

**END OF COMPONENT FORMATTER SKILL**
