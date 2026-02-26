---
name: confluence-to-wordpress-html
description: Convert raw Confluence blog content into production-ready WordPress HTML with proper shortcodes, syntax highlighting (Geist Mono), and styling. Use when migrating Confluence content to WordPress or formatting blog posts with code blocks, CTAs, FAQs, and structured components.
---

# CONFLUENCE TO WORDPRESS HTML CONVERSION PROTOCOL

## Purpose
This protocol guides AI to convert raw Confluence blog content into production-ready WordPress HTML with proper shortcodes, styling, and structure.

---

## 🚨 CRITICAL RULES

1. **Input:** Raw Confluence blog content (plain text with headings, paragraphs, code blocks, image references)
2. **Output:** Fully formatted WordPress HTML ready for direct paste into WordPress editor
3. **NO markdown output** – Only HTML and WordPress shortcodes
4. **Preserve all content** – Do not remove or rewrite content, only format it
5. **NO custom classes or CSS** – Only use standard HTML tags (`<p>`, `<ul>`, `<li>`, `<table>`, `<h2>`, `<h3>`) with no classes
6. **ONLY allowed styling:**
   - Image box-shadow: `style="box-shadow: 0px 0px 12px rgba(0, 0, 0, 0.1);"`
   - Syntax highlighting in code blocks: inline `style` attributes with colors and Geist Mono font
   - Standard link classes (from examples below)
7. **Where a line break occurs, do NOT add `<p>` tag** – empty lines should remain empty, not wrapped in paragraph tags

---

## HEADING CONVERSION

### Confluence to WordPress Heading Mapping

| Confluence Format | WordPress Output | Notes |
|-------------------|------------------|-------|
| First major heading (Blog Title) | `<h1>` with data attributes | Primary heading, bold wrapped |
| Section headings | `<h2>` with `id` attribute | Appears in TOC sidebar |
| Subsection headings | `<h3>` with `id` attribute | Sub-level heading |
| Minor headings | `<h4>` with `id` attribute | Rare, use sparingly |

### Heading Structure Examples

**H1 (Blog Title):**
```html
<h1 data-local-id="xxx" data-renderer-start-pos="1" id="Blog-Title"><b>Blog Title</b></h1>
```

**H2 (Section Heading):**
```html
<h2 data-local-id="xxx" data-renderer-start-pos="XXX" id="Section-Heading">Section Heading</h2>
```

**H3 (Subsection Heading):**
```html
<h3 data-local-id="xxx" data-renderer-start-pos="XXX" id="Subsection-Heading">Subsection Heading</h3>
```

**ID Format:** Replace spaces with hyphens, remove special characters, preserve capitalization.

---

## TEXT FORMATTING CONVERSION

### Basic Text Elements

| Confluence | WordPress HTML |
|------------|----------------|
| **Bold text** | `<strong>Bold text</strong>` |
| *Italic text* | `<em>Italic text</em>` |
| Regular paragraph | `<p>Paragraph text</p>` |
| Line break | `<br>` (use sparingly) |

### Inline Code (Two Formats)

#### 1. Standard Inline Code (for Confluence content)
Confluence inline code (backticks or monospace) converts to simple `<code>` tag with specific class:

```html
<code class="_ca0qyh40 _u5f3m5ip _n3tdyh40 _19bvm5ip _2rkofajl _11c819w5 _1reo1wug _18m91wug _1dqoglyw _1e0c1nu9 _bfhk187e _16d9qvcn _syazi7uo _vwz41kw7 _1i4q1hna _o5721jtm" data-renderer-mark="true">code text</code>
```

**Examples:**
- `.zip` → `<code class="_ca0qyh40 _u5f3m5ip _n3tdyh40 _19bvm5ip _2rkofajl _11c819w5 _1reo1wug _18m91wug _1dqoglyw _1e0c1nu9 _bfhk187e _16d9qvcn _syazi7uo _vwz41kw7 _1i4q1hna _o5721jtm" data-renderer-mark="true">.zip</code>`
- `playwright.config.ts` → `<code class="_ca0qyh40 _u5f3m5ip _n3tdyh40 _19bvm5ip _2rkofajl _11c819w5 _1reo1wug _18m91wug _1dqoglyw _1e0c1nu9 _bfhk187e _16d9qvcn _syazi7uo _vwz41kw7 _1i4q1hna _o5721jtm" data-renderer-mark="true">playwright.config.ts</code>`
- `trace: 'on'` → `<code class="_ca0qyh40 _u5f3m5ip _n3tdyh40 _19bvm5ip _2rkofajl _11c819w5 _1reo1wug _18m91wug _1dqoglyw _1e0c1nu9 _bfhk187e _16d9qvcn _syazi7uo _vwz41kw7 _1i4q1hna _o5721jtm" data-renderer-mark="true">trace: 'on'</code>`

#### 2. `[ct]` Shortcode Inline Code (for Component Formatter content)
When content uses `[ct]code[/ct]` shortcode, convert to styled `<span>` tag with **context-aware styling**:

**🚨 CRITICAL:** The `[ct]` shortcode is used specifically for inline code within sentences from the component formatter. The styling changes based on context (default, Tip, or Note).

**Default Styling (outside Tip/Note blocks):**
```html
<span class="text-[#0B0C0E] ff-geist-mono bg-[#E9E9E9] rounded-[4px] font-[500]" style="padding-left: 5px;padding-right: 5px;font-size: 15px;">code text</span>
```

**Inside Note Notice Block:**
```html
<span class="text-[#065F46] ff-geist-mono bg-[#FDFFFE] rounded-[4px] font-[500]" style="padding-left: 5px;padding-right: 5px;font-size: 15px;">code text</span>
```
- Background: `bg-[#FDFFFE]` (off-white)
- Text color: `text-[#065F46]` (dark green, matches Note text color)

**Inside Tip Notice Block:**
```html
<span class="text-[#713F12] ff-geist-mono bg-[#FFFFFF] rounded-[4px] font-[500]" style="padding-left: 5px;padding-right: 5px;font-size: 15px;">code text</span>
```
- Background: `bg-[#FFFFFF]` (white)
- Text color: `text-[#713F12]` (dark brown, matches Tip text color)

**Examples (Default):**
- `[ct]npx playwright test[/ct]` → `<span class="text-[#0B0C0E] ff-geist-mono bg-[#E9E9E9] rounded-[4px] font-[500]" style="padding-left: 5px;padding-right: 5px;font-size: 15px;">npx playwright test</span>`
- `[ct].github/workflows/playwright.yml[/ct]` → `<span class="text-[#0B0C0E] ff-geist-mono bg-[#E9E9E9] rounded-[4px] font-[500]" style="padding-left: 5px;padding-right: 5px;font-size: 15px;">.github/workflows/playwright.yml</span>`
- `[ct]when: always[/ct]` → `<span class="text-[#0B0C0E] ff-geist-mono bg-[#E9E9E9] rounded-[4px] font-[500]" style="padding-left: 5px;padding-right: 5px;font-size: 15px;">when: always</span>`
- `[ct]parallel[/ct]` → `<span class="text-[#0B0C0E] ff-geist-mono bg-[#E9E9E9] rounded-[4px] font-[500]" style="padding-left: 5px;padding-right: 5px;font-size: 15px;">parallel</span>`

**When to use which:**
- Use `<code>` tag for Confluence-sourced inline code
- Use `<span>` tag for `[ct]` shortcode from component formatter
- **Apply context-aware styling** when `[ct]` appears inside Tip or Note notice blocks

---

## CODE BLOCK CONVERSION

**🚨 CRITICAL: All code blocks MUST be fully syntax highlighted with colors - see SYNTAX HIGHLIGHTING RULES below.**

### Standard Code Block
Wrap all multi-line code in `[code_panel]` shortcode with syntax-highlighted `<pre><code>`:

```html
[code_panel title="filename.ext"]
<pre><code>// code here with full syntax highlighting in colored <span> tags</code></pre>
[/code_panel]
```

### Code Panel Title Guidelines

| Code Type | Title Example |
|-----------|---------------|
| Terminal/CLI commands | `terminal` |
| TypeScript config | `playwright.config.ts` |
| JavaScript file | `example.spec.js` |
| YAML/GitHub Actions | `.github/workflows/test.yml` |
| JSON config | `mcp.json` |
| Generic code | `code` |

### 🚨 SYNTAX HIGHLIGHTING RULES (CRITICAL)

**🚨 MANDATORY: All code inside `[code_panel]` MUST be fully syntax highlighted with colors.**

**This means:**
- Every single token (keyword, function, string, variable, punctuation, comment, number) gets its own colored `<span>` tag
- NO plain text allowed inside `<pre><code>` - everything must be wrapped in `<span>` with color styling
- Make the code visually colorful and readable like a modern code editor
- Use the exact color scheme and font specified below

#### Base Style for ALL Spans
Every `<span>` must include:
```css
font-family: 'Geist Mono'; font-weight: 300;
```

#### Color Reference

| Token Type | Color | Hex Code | Examples |
|------------|-------|----------|----------|
| **Keywords** | Blue | `#569CD6` | `import`, `export`, `const`, `let`, `var`, `await`, `async`, `function`, `return`, `if`, `else`, `for`, `default`, `from`, `true`, `false` |
| **Functions/Methods** | Yellow | `#DCDCAA` | `defineConfig()`, `launch()`, `test()`, `expect()`, `console.log()` |
| **Strings** | Orange | `#CE9178` | `'text'`, `"text"`, `` `template` `` |
| **Properties/Variables** | Purple | `#B392F0` | `trace`, `use`, `timeout`, `baseURL`, object keys |
| **Punctuation/Operators** | White | `#FFFFFF` | `{`, `}`, `(`, `)`, `[`, `]`, `:`, `;`, `,`, `=`, `=>`, `.` |
| **Comments** | Green | `#6D9957` | `// comment`, `/* comment */` |
| **Numbers** | Red | `#F27280` | `100`, `3000`, `0` |

#### Spacing & Line Breaks
- **Spaces:** Use `&nbsp;` for all spaces inside `<pre><code>`
- **Line breaks:** Use `<br>` at the end of each line
- **Indentation:** Use multiple `&nbsp;` for indentation (2 spaces = `&nbsp;&nbsp;`)

#### Structure Rules
1. Wrap entire code in `<pre><code>...</code></pre>`
2. Each token gets its own `<span>` with color and font styles
3. All spans should be inline (no actual newlines in the HTML source)
4. Use `<br>` to create visual line breaks
5. Use `&nbsp;` for all spacing

#### Complete Example

**Input Code:**
```javascript
import { defineConfig } from '@playwright/test';
export default defineConfig({
  use: {
    trace: 'on',
  },
});
```

**Output HTML (all on one logical line, `<br>` for line breaks):**
```html
[code_panel title="playwright.config.ts"]
<pre><code><span style="color: #569CD6; font-family: 'Geist Mono'; font-weight: 300;">import</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">&nbsp;{&nbsp;</span><span style="color: #DCDCAA; font-family: 'Geist Mono'; font-weight: 300;">defineConfig</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">&nbsp;}&nbsp;</span><span style="color: #569CD6; font-family: 'Geist Mono'; font-weight: 300;">from</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">&nbsp;</span><span style="color: #CE9178; font-family: 'Geist Mono'; font-weight: 300;">'@playwright/test'</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">;</span><br><span style="color: #569CD6; font-family: 'Geist Mono'; font-weight: 300;">export</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">&nbsp;</span><span style="color: #569CD6; font-family: 'Geist Mono'; font-weight: 300;">default</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">&nbsp;</span><span style="color: #DCDCAA; font-family: 'Geist Mono'; font-weight: 300;">defineConfig</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">({</span><br><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">&nbsp;&nbsp;</span><span style="color: #B392F0; font-family: 'Geist Mono'; font-weight: 300;">use</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">:&nbsp;{</span><br><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #B392F0; font-family: 'Geist Mono'; font-weight: 300;">trace</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">:&nbsp;</span><span style="color: #CE9178; font-family: 'Geist Mono'; font-weight: 300;">'on'</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">,</span><br><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">&nbsp;&nbsp;},</span><br><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">});</span></code></pre>
[/code_panel]
```

#### Terminal Commands Example

**Input:**
```bash
npm init playwright@latest
```

**Output:**
```html
[code_panel title="terminal"]
<pre><code><span style="color: #DCDCAA; font-family: 'Geist Mono'; font-weight: 300;">npm</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">&nbsp;</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">init</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">&nbsp;</span><span style="color: #CE9178; font-family: 'Geist Mono'; font-weight: 300;">playwright@latest</span></code></pre>
[/code_panel]
```

#### Code with Comments Example

**Input:**
```javascript
// Configure trace settings
const config = {
  trace: 'on', // Enable tracing
};
```

**Output:**
```html
[code_panel title="config.js"]
<pre><code><span style="color: #6D9957; font-family: 'Geist Mono'; font-weight: 300;">//&nbsp;Configure&nbsp;trace&nbsp;settings</span><br><span style="color: #569CD6; font-family: 'Geist Mono'; font-weight: 300;">const</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">&nbsp;</span><span style="color: #B392F0; font-family: 'Geist Mono'; font-weight: 300;">config</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">&nbsp;=&nbsp;{</span><br><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">&nbsp;&nbsp;</span><span style="color: #B392F0; font-family: 'Geist Mono'; font-weight: 300;">trace</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">:&nbsp;</span><span style="color: #CE9178; font-family: 'Geist Mono'; font-weight: 300;">'on'</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">,&nbsp;</span><span style="color: #6D9957; font-family: 'Geist Mono'; font-weight: 300;">//&nbsp;Enable&nbsp;tracing</span><br><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">};</span></code></pre>
[/code_panel]
```

---

## LINK CONVERSION

### External Links
```html
<a title="URL" href="URL" class="_ymio1r31 _ypr0glyw _zcxs1o36 _mizu1v1w _1ah3dkaa _ra3xnqa1 _128mdkaa _1cvmnqa1 _4davt94y _4bfu1r31 _1hms8stv _ajmmnqa1 _vchhusvi _kqswh2mm _ect4ttxp _syaz13af _1a3b1r31 _4fpr8stv _5goinqa1 _f8pj13af _9oik1r31 _1bnxglyw _jf4cnqa1 _30l313af _1nrm1r31 _c2waglyw _1iohnqa1 _9h8h12zz _10531ra0 _1ien1ra0 _n0fx1ra0 _1vhv17z1">Link Text</a>
```

### Internal TestDino Links
Same format as external links but with TestDino URLs:
```html
<a title="https://testdino.com/blog/debug-playwright-tests/" href="https://testdino.com/blog/debug-playwright-tests/" class="_ymio1r31 _ypr0glyw _zcxs1o36 _mizu1v1w _1ah3dkaa _ra3xnqa1 _128mdkaa _1cvmnqa1 _4davt94y _4bfu1r31 _1hms8stv _ajmmnqa1 _vchhusvi _kqswh2mm _ect4ttxp _syaz13af _1a3b1r31 _4fpr8stv _5goinqa1 _f8pj13af _9oik1r31 _1bnxglyw _jf4cnqa1 _30l313af _1nrm1r31 _c2waglyw _1iohnqa1 _9h8h12zz _10531ra0 _1ien1ra0 _n0fx1ra0 _1vhv17z1">debugging</a>
```

### Bold Link Text
Wrap `<strong>` inside the anchor:
```html
<a href="URL" class="..."><strong>Link Text</strong></a>
```

---

## IMAGE CONVERSION

### Standard Image Format
```html
<img style="box-shadow: 0px 0px 12px rgba(0, 0, 0, 0.1);" src="IMAGE_URL" alt="Alt Text" width="WIDTH" height="HEIGHT" class="size-full wp-image-XXXX" />
```

### Image Container Structure (Simplified - NO wrapper divs)
```html
<img style="box-shadow: 0px 0px 12px rgba(0, 0, 0, 0.1);" src="https://testdino.com/wp-content/uploads/2026/02/image-name.png" alt="Image description" width="2157" height="1201" class="size-full wp-image-XXXX" />
```

**🚨 CRITICAL:** Only use the `box-shadow` style on images. Do NOT add wrapper `<div>` containers unless explicitly shown in reference examples. Keep it simple - just the `<img>` tag with box-shadow.

### Image Placement Rules
- Place images AFTER the paragraph that references them
- Add blank line before and after image container
- Use descriptive alt text based on image filename or context
- Maintain original image dimensions when available

---

## LIST CONVERSION

### Unordered Lists
```html
<ul class="ak-ul" data-local-id="xxx" data-indent-level="1">
    <li>
<p data-renderer-start-pos="XXX" data-local-id="xxx">List item one</p>
</li>
    <li>
<p data-renderer-start-pos="XXX" data-local-id="xxx">List item two</p>
</li>
    <li>
<p data-renderer-start-pos="XXX" data-local-id="xxx">List item three</p>
</li>
</ul>
```

**Note:** Each list item content is wrapped in `<p>` tags with data attributes

### Ordered Lists
```html
<ol>
    <li>First step</li>
    <li>Second step</li>
    <li>Third step</li>
</ol>
```

### Nested Lists
```html
<ul>
    <li>Parent item
        <ul>
            <li>Child item</li>
        </ul>
    </li>
</ul>
```

---

## WORDPRESS SHORTCODE COMPONENTS

### When to Add Components (AI Decision)

The AI should analyze content and add appropriate components:

| Content Pattern | Component to Add |
|-----------------|------------------|
| Key feature list or summary | `[info_banner]` |
| Warning, caution, prerequisite | `[notice_block]` |
| Pro tip, best practice | `[tip_block]` |
| Code snippet | `[code_panel]` |
| FAQ question/answer | `[faq_item]` |
| Call-to-action text | `[cta_regular]` |
| Impactful quote/statement | `[quote_block]` |

### Tips Banner (Recommended for Quick Summaries)
**Use when:** Providing quick summaries, key points, or important callouts

```html
[tips_banner title="Quick pick" icon="" bg="#DBEAFE" border="#BFDBFE" color="#1E3A8A"]
<ul>
    <li><strong>Option 1</strong> is best when...</li>
    <li><strong>Option 2</strong> is best when...</li>
</ul>
[/tips_banner]
```

**Color Presets:**
- Blue (info/definitions): `bg="#DBEAFE" border="#BFDBFE" color="#1E3A8A"` - **Use for definitions**
- Green (success): `bg="#F0FDF4" border="#BBF7D0" color="#166534"`
- Purple (feature): `bg="#FDF4FF" border="#F5D0FE" color="#86198F"`
- Yellow (TL;DR): `bg="#FEFCE8" border="#FDE68A" color="#713F12"` - **Use for TL;DR only**

### 🚨 Definition Conversion (AUTOMATIC - FROM COMPONENT FORMATTER)

**When component formatter outputs `[tips_banner]` with "What is X?" title, keep it as-is with BLUE theme:**

**🚨 CRITICAL FORMAT - DO NOT MODIFY:**
```html
[tips_banner title="What is Term Name?" icon="" bg="#DBEAFE" border="#BFDBFE" color="#1E3A8A"]Definition content here.[/tips_banner]
```

**🚨 STRICT RULES:**
- **ALWAYS** keep `title="What is X?"` exactly as provided (question format)
- **ALWAYS** keep `icon=""` (empty string)
- **ALWAYS** use BLUE theme colors: `bg="#DBEAFE" border="#BFDBFE" color="#1E3A8A"`
- **DO NOT** convert to any other component
- **DO NOT** change the blue color scheme
- Content inside should be plain text (no special formatting needed)

**Examples:**

**Input from component formatter:**
```
[tips_banner title="What is Playwright MCP?" icon="" bg="#DBEAFE" border="#BFDBFE" color="#1E3A8A"]Playwright MCP (Model Context Protocol) is an MCP server maintained by Microsoft that exposes Playwright's browser automation as a set of callable tools.[/tips_banner]
```

**Output (keep as-is):**
```html
[tips_banner title="What is Playwright MCP?" icon="" bg="#DBEAFE" border="#BFDBFE" color="#1E3A8A"]Playwright MCP (Model Context Protocol) is an MCP server maintained by Microsoft that exposes Playwright's browser automation as a set of callable tools.[/tips_banner]
```

**Another Example:**
```html
[tips_banner title="What is a Webhook?" icon="" bg="#DBEAFE" border="#BFDBFE" color="#1E3A8A"]A webhook is like a doorbell for your app – when something happens on another service, it automatically notifies your application.[/tips_banner]
```

**🚨 IMPORTANT - THREE TYPES OF tips_banner:**
1. **Definitions** (Blue): `title="What is X?"` with `bg="#DBEAFE" border="#BFDBFE" color="#1E3A8A"`
2. **TL;DR** (Yellow): `title="TL;DR"` with `bg="#FEFCE8" border="#FDE68A" color="#713F12"`
3. **Quick Summaries** (Blue): Other titles like "Quick pick" with blue theme

### 🚨 TL;DR Conversion (AUTOMATIC - FROM COMPONENT FORMATTER)

**When component formatter outputs `[tips_banner]` with "TL;DR" title, keep it as-is:**

**🚨 CRITICAL FORMAT - DO NOT MODIFY:**
```html
[tips_banner title="TL;DR" icon="" bg="#FEFCE8" border="#FDE68A" color="#713F12"]
Content here (can be bullet points or paragraphs)
[/tips_banner]
```

**🚨 STRICT RULES:**
- **ALWAYS** keep `title="TL;DR"` exactly as provided
- **ALWAYS** keep `icon=""` (empty string)
- **ALWAYS** use exact colors: `bg="#FEFCE8" border="#FDE68A" color="#713F12"`
- **DO NOT** convert to `[notice_block]` or any other component
- **DO NOT** change the yellow color scheme
- Content inside can contain `<ul>`, `<li>`, `<p>`, or plain text

**Examples:**

**Input from component formatter:**
```
[tips_banner title="TL;DR" icon="" bg="#FEFCE8" border="#FDE68A" color="#713F12"]
- Playwright Trace Viewer shows test execution timeline
- Enable with trace: 'on-first-retry'
- Access traces locally or stream to TestDino
[/tips_banner]
```

**Output (keep as-is, just format content to HTML):**
```html
[tips_banner title="TL;DR" icon="" bg="#FEFCE8" border="#FDE68A" color="#713F12"]
<ul>
    <li>Playwright Trace Viewer shows test execution timeline</li>
    <li>Enable with trace: 'on-first-retry'</li>
    <li>Access traces locally or stream to TestDino</li>
</ul>
[/tips_banner]
```

**Another example (paragraph format):**
```html
[tips_banner title="TL;DR" icon="" bg="#FEFCE8" border="#FDE68A" color="#713F12"]
Use visual regression testing to catch UI bugs automatically. Start with critical user flows and run tests in CI.
[/tips_banner]
```

**🚨 IMPORTANT:**
- TL;DR always uses yellow theme (`#FEFCE8`, `#FDE68A`, `#713F12`)
- This is the ONLY use case for yellow-themed tips_banner
- Never change the title from "TL;DR" to anything else
- Keep the shortcode structure intact - only format inner content to HTML

### Info Banner
**Use when:** Summarizing key points, highlighting important features

```html
[info_banner title="Banner Title" icon="https://testdino.com/wp-content/uploads/2026/01/fluent_info-sparkle-48-filled-3.svg" bg="#DBEAFE" border="#BFDBFE" color="#1E3A8A"]Content here[/info_banner]
```

**Color Presets:**
- Blue (info): `bg="#DBEAFE" border="#BFDBFE" color="#1E3A8A"`
- Green (success): `bg="#F0FDF4" border="#BBF7D0" color="#166534"`
- Purple (feature): `bg="#FDF4FF" border="#F5D0FE" color="#86198F"`

### Notice Block
**Use when:** Warnings, important cautions, prerequisites

```html
[notice_block bg="#FEF3C7" border="#FCD34D" color="#92400E" icon="https://testdino.com/wp-content/uploads/2026/01/fi_768818.svg"]Warning content[/notice_block]
```

**Color Presets:**
- Warning (amber): `bg="#FEF3C7" border="#FCD34D" color="#92400E"`
- Info (blue): `bg="#F0F6FF" border="#C8DEFD" color="#032759"`
- Danger (red): `bg="#FEF2F2" border="#FECACA" color="#991B1B"`

### 🚨 Tip Conversion (AUTOMATIC - FROM COMPONENT FORMATTER)

**When component formatter outputs `[tip]...[/tip]`, convert to notice_block with tip styling:**

**Format:**
```html
[notice_block bg="#FEFCE8" border="#FDE68A" color="#713F12" icon="https://testdino.com/wp-content/uploads/2026/01/fluent_info-sparkle-48-filled.svg"]<strong>Tip:</strong> Tip content here.[/notice_block]
```

**🚨 CRITICAL STYLING:**
- Background: `bg="#FEFCE8"` (light yellow)
- Border: `border="#FDE68A"` (yellow)
- Text color: `color="#713F12"` (dark brown)
- Icon: `icon="https://testdino.com/wp-content/uploads/2026/01/fluent_info-sparkle-48-filled.svg"`
- **BOLD the prefix** using `<strong>` tag (e.g., `<strong>Tip:</strong>`)

**Examples:**

**Input from component formatter:**
```
Inside Tip: [tip]
TIP: Start with your most visited pages. Your homepage, login page, and primary user flow cover the highest-impact surface area.
[/tip]
```

**Output HTML:**
```html
[notice_block bg="#FEFCE8" border="#FDE68A" color="#713F12" icon="https://testdino.com/wp-content/uploads/2026/01/fluent_info-sparkle-48-filled.svg"]<strong>Tip:</strong> Start with your most visited pages. Your homepage, login page, and primary user flow cover the highest-impact surface area.[/notice_block]
```

**Another Example:**

**Input:**
```
Inside Tip: [tip]
PRO TIP: Use .exclude() sparingly and only for elements you genuinely can't control (third-party embeds, for example).
[/tip]
```

**Output:**
```html
[notice_block bg="#FEFCE8" border="#FDE68A" color="#713F12" icon="https://testdino.com/wp-content/uploads/2026/01/fluent_info-sparkle-48-filled.svg"]<strong>Pro Tip:</strong> Use .exclude() sparingly and only for elements you genuinely can't control (third-party embeds, for example).[/notice_block]
```

**Example with Inline Code `[ct]`:**

**Input:**
```
Inside Tip: [tip]
TIP: Tip content here. [ct]npx playwright test[/ct]
[/tip]
```

**Output:**
```html
[notice_block bg="#FEFCE8" border="#FDE68A" color="#713F12" icon="https://testdino.com/wp-content/uploads/2026/01/fluent_info-sparkle-48-filled.svg"]<strong>Tip:</strong> Tip content here. <span class="text-[#713F12] ff-geist-mono bg-[#FFFFFF] rounded-[4px] font-[500]" style="padding-left: 5px;padding-right: 5px;font-size: 15px;">npx playwright test</span>[/notice_block]
```

**🚨 CRITICAL FOR TIPS WITH INLINE CODE:**
- When `[ct]` appears inside Tip notice blocks, use `bg-[#FFFFFF]` (white) and `text-[#713F12]` (dark brown)
- This ensures the inline code stands out against the yellow Tip background

**🚨 IMPORTANT:**
- **BOLD the prefix** using `<strong>` tag (e.g., `<strong>Tip:</strong>`, `<strong>Pro Tip:</strong>`)
- Convert prefix to title case (TIP: → Tip:, PRO TIP: → Pro Tip:)
- Use EXACT color values provided above
- Use the specific icon URL for tips (fluent_info-sparkle-48-filled.svg)

### 🚨 Note Conversion (AUTOMATIC - FROM COMPONENT FORMATTER)

**When component formatter outputs `[note]...[/note]`, convert to notice_block with note styling:**

**Format:**
```html
[notice_block bg="#E1FFF0" border="#A7F3D0" color="#065F46" icon=""]<strong>Note:</strong> Note content here.[/notice_block]
```

**🚨 CRITICAL STYLING - GREEN THEME WITH NO ICON:**
- Background: `bg="#E1FFF0"` (light green)
- Border: `border="#A7F3D0"` (green)
- Text color: `color="#065F46"` (dark green)
- Icon: `icon=""` (empty string - NO ICON)

**🚨 DO NOT CONFUSE WITH TIPS:**
- **TIPS**: Yellow theme (`#FEFCE8`, `#FDE68A`, `#713F12`) with sparkle icon
- **NOTES**: Green theme (`#E1FFF0`, `#A7F3D0`, `#065F46`) with NO icon

**Examples:**

**Input from component formatter:**
```
Inside Note: [note]
NOTE: Make sure to install dependencies before running tests.
[/note]
```

**Output HTML:**
```html
[notice_block bg="#E1FFF0" border="#A7F3D0" color="#065F46" icon=""]<strong>Note:</strong> Make sure to install dependencies before running tests.[/notice_block]
```

**Another Example:**

**Input:**
```
Inside Note: [note]
PREREQUISITE: You need Node.js 18+ and npm installed on your system.
[/note]
```

**Output:**
```html
[notice_block bg="#E1FFF0" border="#A7F3D0" color="#065F46" icon=""]<strong>Prerequisite:</strong> You need Node.js 18+ and npm installed on your system.[/notice_block]
```

**Another Example:**

**Input:**
```
Inside Note: [note]
IMPORTANT: Always run tests before deploying to production.
[/note]
```

**Output:**
```html
[notice_block bg="#E1FFF0" border="#A7F3D0" color="#065F46" icon=""]<strong>Important:</strong> Always run tests before deploying to production.[/notice_block]
```

**Example with Inline Code `[ct]`:**

**Input:**
```
Inside Note: [note]
NOTE: Note content here. [ct]npx playwright test[/ct]
[/note]
```

**Output:**
```html
[notice_block bg="#E1FFF0" border="#A7F3D0" color="#065F46" icon=""]<strong>Note:</strong> Note content here. <span class="text-[#065F46] ff-geist-mono bg-[#FDFFFE] rounded-[4px] font-[500]" style="padding-left: 5px;padding-right: 5px;font-size: 15px;">npx playwright test</span>[/notice_block]
```

**🚨 CRITICAL FOR NOTES WITH INLINE CODE:**
- When `[ct]` appears inside Note notice blocks, use `bg-[#FDFFFE]` (off-white) and `text-[#065F46]` (dark green)
- This ensures the inline code stands out against the green Note background

**🚨 IMPORTANT:**
- **BOLD the prefix** using `<strong>` tag (e.g., `<strong>Note:</strong>`)
- Convert prefix to title case (NOTE: → Note:, IMPORTANT: → Important:)
- Use EXACT color values provided above (green theme)
- ALWAYS use `icon=""` (empty string - NO icon for notes)
- Notes use GREEN theme, Tips use YELLOW theme - completely different styling

### Tip Block (DEPRECATED - Use tips_banner instead)

**⚠️ NOTE:** For definitions and term explanations, use `[tips_banner]` with blue theme instead.

**Legacy format (rarely used):**
```html
[tip_block title="Tip Title" icon="https://testdino.com/wp-content/uploads/2026/01/fi_841743.svg"]Tip content[/tip_block]
```

**Preferred format for definitions:**
```html
[tips_banner title="What is Term?" icon="" bg="#DBEAFE" border="#BFDBFE" color="#1E3A8A"]Definition content[/tips_banner]
```

### CTA Regular (FROM COMPONENT FORMATTER)
**Use when:** Component formatter marks CTA content or Confluence contains call-to-action text

**🚨 CRITICAL STYLING - USE EXACT VALUES:**
- Background: `background="linear-gradient(90deg, #171717 0%, #4D4D4D 100%);"`
- Dino Image: `dragon_image="https://testdino.com/wp-content/uploads/2026/01/Group-626031.svg"`
- Button Link: `button_link="https://app.testdino.com/"`

**Format:**
```html
[cta_regular title="CTA Title" description="CTA description" button_text="Button Text" button_link="https://app.testdino.com/" background="linear-gradient(90deg, #171717 0%, #4D4D4D 100%);" dragon_image="https://testdino.com/wp-content/uploads/2026/01/Group-626031.svg"]
```

**Examples:**

**Input from Confluence:**
```
Ready to debug faster?
Stream your Playwright runs into TestDino for instant trace access.
Try TestDino Free
```

**Output HTML:**
```html
[cta_regular title="Ready to debug faster?" description="Stream your Playwright runs into TestDino for instant trace access." button_text="Try TestDino Free" button_link="https://app.testdino.com/" background="linear-gradient(90deg, #171717 0%, #4D4D4D 100%);" dragon_image="https://testdino.com/wp-content/uploads/2026/01/Group-626031.svg"]
```

**🚨 IMPORTANT:**
- Extract title, description, and button text from the Confluence content
- ALWAYS use `button_link="https://app.testdino.com/"` (default TestDino signup)
- ALWAYS use the gradient background and dino image URL provided above
- Do NOT change these values - they are standardized for all CTAs

### FAQ Item
**Use when:** Content has FAQ section with questions and answers

```html
[faq_item question="Question text?" open="Yes"]Answer text[/faq_item]
[faq_item question="Another question?" open="No"]Answer text[/faq_item]
```

- First FAQ: `open="Yes"` (expanded)
- All others: `open="No"` (collapsed)

---

## CTA DETECTION PATTERNS

The AI should identify CTA content in Confluence and convert to `[cta_regular]`:

### CTA Indicators in Confluence Content:
- Text like "Try TestDino", "Start now", "Get started"
- Promotional statements followed by button-like text
- Standalone lines with call-to-action language
- Section breaks followed by marketing copy

### 🚨 Standard CTA Values (ALWAYS USE THESE):
- **Background:** `background="linear-gradient(90deg, #171717 0%, #4D4D4D 100%);"`
- **Dino Image:** `dragon_image="https://testdino.com/wp-content/uploads/2026/01/Group-626031.svg"`
- **Button Link:** `button_link="https://app.testdino.com/"` (default for all CTAs)

### Example Conversion:

**Confluence Input:**
```
Tired of downloading trace files from CI?
Get instant trace access with AI failure classification.
Try TestDino
```

**WordPress Output:**
```html
[cta_regular title="Tired of downloading trace files from CI?" description="Get instant trace access with AI failure classification." button_text="Try TestDino" button_link="https://app.testdino.com/" background="linear-gradient(90deg, #171717 0%, #4D4D4D 100%);" dragon_image="https://testdino.com/wp-content/uploads/2026/01/Group-626031.svg"]
```

**🚨 CRITICAL:**
- Extract title, description, and button_text from Confluence content
- ALWAYS use the exact background gradient, dino image URL, and button link shown above
- These values are standardized and must NOT be changed

---

## PARAGRAPH STRUCTURE

### Standard Paragraph
```html
<p data-renderer-start-pos="XXX" data-local-id="XXXXX">Paragraph content here.</p>
```

- `data-renderer-start-pos`: Use incremental numbers (1, 245, 544, etc.)
- `data-local-id`: Generate unique alphanumeric IDs (e.g., "fc15075ffab1", "ee75abdaf031")

### 🚨 CRITICAL: When NOT to Add `<p>` Tags
**Do NOT wrap empty lines or line breaks in `<p>` tags.** Where a line is dropped/empty in the original content, leave it as whitespace or use `<br>` if needed for spacing. Adding unnecessary `<p>` tags causes improper WordPress output.

**Examples:**
- ❌ WRONG: `<p></p>` or `<p>&nbsp;</p>` for empty lines
- ✅ CORRECT: Just leave blank lines or use actual HTML whitespace

**Between shortcodes and content:** Do not add `<p>` tags between closing and opening shortcodes

### Paragraph with Links
```html
<p data-renderer-start-pos="245" data-local-id="4e73e6f3f191"><a title="URL" href="URL" class="...">Link text</a> continues with regular text.</p>
```

### Paragraph with Bold and Inline Code
```html
<p data-renderer-start-pos="1085" data-local-id="8bd1a068df1e"><strong data-renderer-mark="true">Bold text:</strong> Regular text with <code class="_ca0qyh40 _u5f3m5ip _n3tdyh40 _19bvm5ip _2rkofajl _11c819w5 _1reo1wug _18m91wug _1dqoglyw _1e0c1nu9 _bfhk187e _16d9qvcn _syazi7uo _vwz41kw7 _1i4q1hna _o5721jtm" data-renderer-mark="true">inline code</code> here.</p>
```

---

## SPECIAL CONTENT PATTERNS

### Feature Lists with Bold Labels
Confluence often has feature descriptions with bold labels:

**Confluence:**
```
Action Timeline - Every Playwright action with duration, status, and locator details.
DOM Snapshots - Complete page state before and after each action.
```

**WordPress:**
```html
<p data-renderer-start-pos="1146" data-local-id="21ad1b5dd8c6"><strong data-renderer-mark="true">Action Timeline</strong> - Every Playwright action with duration, status, and locator details.</p>
<p data-renderer-start-pos="1325" data-local-id="9bd22b81bd30"><strong data-renderer-mark="true">DOM Snapshots</strong> - Complete page state before and after each action.</p>
```

### Configuration Options
Confluence lists of config options:

**Confluence:**
```
trace: 'on' - Records traces for every test.
trace: 'off' - Disables tracing entirely.
```

**WordPress:**
```html
<p data-renderer-start-pos="6637" data-local-id="09e03b1142fd"><code class="_ca0qyh40 _u5f3m5ip _n3tdyh40 _19bvm5ip _2rkofajl _11c819w5 _1reo1wug _18m91wug _1dqoglyw _1e0c1nu9 _bfhk187e _16d9qvcn _syazi7uo _vwz41kw7 _1i4q1hna _o5721jtm" data-renderer-mark="true">trace: 'on'</code> - Records traces for every test.</p>
<p data-renderer-start-pos="6812" data-local-id="e4fc1a08d415"><code class="_ca0qyh40 _u5f3m5ip _n3tdyh40 _19bvm5ip _2rkofajl _11c819w5 _1reo1wug _18m91wug _1dqoglyw _1e0c1nu9 _bfhk187e _16d9qvcn _syazi7uo _vwz41kw7 _1i4q1hna _o5721jtm" data-renderer-mark="true">trace: 'off'</code> - Disables tracing entirely.</p>
```

---

## DOCUMENT WRAPPER STRUCTURE

Wrap entire output in container div:

```html
<div class="_19itglyw _vchhusvi _r06hglyw _1e0cj4ch" data-vc="view-page-main-content-container" data-testid="view-page-main-content-container">

<!-- All content here -->

</div>
```

---

## CONVERSION CHECKLIST

Before finalizing output, verify:

**Headings & Structure:**
- [ ] NO `<h1>` tags used
- [ ] Blog title and sections use `<h2>` with `id` attributes
- [ ] Subsections use `<h3>` with `id` attributes
- [ ] All paragraphs have `data-renderer-start-pos` and `data-local-id`
- [ ] Document wrapped in main container div

**Code Blocks (CRITICAL - MUST BE FULLY COLORIZED):**
- [ ] All code blocks wrapped in `[code_panel]` shortcode
- [ ] Code inside `<pre><code>...</code></pre>` tags
- [ ] 🚨 EVERY SINGLE TOKEN wrapped in `<span>` with color + `font-family: 'Geist Mono'; font-weight: 300;`
- [ ] 🚨 NO plain text in code - 100% of code must be in colored `<span>` tags
- [ ] Keywords use `#569CD6` (blue) - import, export, const, let, var, from, etc.
- [ ] Functions use `#DCDCAA` (yellow) - function names, method calls
- [ ] Strings use `#CE9178` (orange) - 'text', "text", `template`
- [ ] Properties/Variables use `#B392F0` (purple) - object keys, variable names
- [ ] Punctuation uses `#FFFFFF` (white) - {}, (), [], :, ;, ,, =, .
- [ ] Comments use `#6D9957` (green) - //, /* */
- [ ] Numbers use `#F27280` (red) - 100, 3000, etc.
- [ ] Spaces replaced with `&nbsp;`
- [ ] Line breaks use `<br>` tags
- [ ] All spans inline (no actual newlines in HTML source)

**Inline Code & Text:**
- [ ] Confluence inline code uses `<code>` tag with the standard class attribute
- [ ] `[ct]` shortcode converts to `<span>` with Geist Mono styling and `font-size: 15px`
- [ ] 🚨 `[ct]` uses context-aware styling:
  - [ ] Default (outside Tip/Note): `bg-[#E9E9E9]` and `text-[#0B0C0E]`
  - [ ] Inside Note notice blocks: `bg-[#FDFFFE]` and `text-[#065F46]`
  - [ ] Inside Tip notice blocks: `bg-[#FFFFFF]` and `text-[#713F12]`
- [ ] Bold text uses `<strong data-renderer-mark="true">`
- [ ] All links have full class attribute string
- [ ] NO custom classes or CSS added (only standard tags and example-based classes)

**Components:**
- [ ] CTAs converted to `[cta_regular]` shortcode
- [ ] FAQs converted to `[faq_item]` shortcodes
- [ ] Definitions kept as `[tips_banner]` with blue styling (title="What is X?", bg="#DBEAFE", border="#BFDBFE", color="#1E3A8A")
- [ ] TL;DR kept as `[tips_banner]` with yellow styling (title="TL;DR", bg="#FEFCE8", border="#FDE68A", color="#713F12")
- [ ] Tips (`[tip]`) converted to `[notice_block]` with yellow styling (bg="#FEFCE8", border="#FDE68A", color="#713F12", icon=sparkle)
- [ ] Notes (`[note]`) converted to `[notice_block]` with green styling (bg="#E1FFF0", border="#A7F3D0", color="#065F46", icon="")
- [ ] All images have box-shadow style and proper container structure

---

## EXAMPLE: COMPLETE CONVERSION

### Input (Confluence):
```
Why Playwright trace viewer essential for debugging tests

Test failures without context waste valuable development time. When your Playwright test breaks in CI, you get a generic "element not found" error.

Playwright Trace Viewer captures five critical data layers:

Action Timeline - Every Playwright action with duration and status.

Add trace configuration to playwright.config.ts:

import { defineConfig } from '@playwright/test';
export default defineConfig({
  use: {
    trace: 'on-first-retry',
  },
});
```

### Output (WordPress HTML):
```html
<h2 id="Why-Playwright-trace-viewer-essential-for-debugging-tests">Why Playwright trace viewer essential for debugging tests</h2>

<p data-renderer-start-pos="1" data-local-id="abc123">Test failures without context waste valuable development time. When your Playwright test breaks in CI, you get a generic "element not found" error.</p>

<p data-renderer-start-pos="150" data-local-id="def456"><strong data-renderer-mark="true">Playwright Trace Viewer captures five critical data layers:</strong></p>

<p data-renderer-start-pos="200" data-local-id="ghi789"><strong data-renderer-mark="true">Action Timeline</strong> - Every Playwright action with duration and status.</p>

<p data-renderer-start-pos="280" data-local-id="jkl012">Add trace configuration to <code class="_ca0qyh40 _u5f3m5ip _n3tdyh40 _19bvm5ip _2rkofajl _11c819w5 _1reo1wug _18m91wug _1dqoglyw _1e0c1nu9 _bfhk187e _16d9qvcn _syazi7uo _vwz41kw7 _1i4q1hna _o5721jtm" data-renderer-mark="true">playwright.config.ts</code>:</p>

[code_panel title="playwright.config.ts"]
<pre><code><span style="color: #569CD6; font-family: 'Geist Mono'; font-weight: 300;">import</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">&nbsp;{&nbsp;</span><span style="color: #DCDCAA; font-family: 'Geist Mono'; font-weight: 300;">defineConfig</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">&nbsp;}&nbsp;</span><span style="color: #569CD6; font-family: 'Geist Mono'; font-weight: 300;">from</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">&nbsp;</span><span style="color: #CE9178; font-family: 'Geist Mono'; font-weight: 300;">'@playwright/test'</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">;</span><br><span style="color: #569CD6; font-family: 'Geist Mono'; font-weight: 300;">export</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">&nbsp;</span><span style="color: #569CD6; font-family: 'Geist Mono'; font-weight: 300;">default</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">&nbsp;</span><span style="color: #DCDCAA; font-family: 'Geist Mono'; font-weight: 300;">defineConfig</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">({</span><br><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">&nbsp;&nbsp;</span><span style="color: #B392F0; font-family: 'Geist Mono'; font-weight: 300;">use</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">:&nbsp;{</span><br><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #B392F0; font-family: 'Geist Mono'; font-weight: 300;">trace</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">:&nbsp;</span><span style="color: #CE9178; font-family: 'Geist Mono'; font-weight: 300;">'on-first-retry'</span><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">,</span><br><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">&nbsp;&nbsp;},</span><br><span style="color: #FFFFFF; font-family: 'Geist Mono'; font-weight: 300;">});</span></code></pre>
[/code_panel]
```

---

## 🚨 CRITICAL RESTRICTIONS SUMMARY

**ABSOLUTELY NO:**
1. ❌ Custom classes (except the standard ones shown in examples: `ak-ul` for lists, long class string for links, `<code>` class)
2. ❌ Custom CSS or inline styles (except syntax highlighting in code blocks and image box-shadow)
3. ❌ Wrapper `<div>` containers for images
4. ❌ `<p>` tags for empty lines or dropped content
5. ❌ Changing/rewriting/rearranging ANY content
6. ❌ Adding extra spacing, margins, or padding styles

**ONLY ALLOWED:**
1. ✅ Standard HTML tags: `<p>`, `<ul>`, `<li>`, `<h1>`, `<h2>`, `<h3>`, `<h4>`, `<table>`, `<code>`, `<strong>`, `<em>`, `<a>`
2. ✅ Data attributes: `data-renderer-start-pos`, `data-local-id`, `data-renderer-mark`, `data-indent-level`
3. ✅ Standard classes from examples (link classes, `ak-ul`, code classes)
4. ✅ WordPress shortcodes: `[code_panel]`, `[tips_banner]`, `[info_banner]`, `[notice_block]`, `[tip_block]`, `[cta_regular]`, `[faq_item]`
5. ✅ Syntax highlighting in code blocks using inline `style` attributes with Geist Mono font and colors
6. ✅ Image box-shadow: `style="box-shadow: 0px 0px 12px rgba(0, 0, 0, 0.1);"`
7. ✅ `[tip]` markers automatically convert to `[notice_block]` with yellow theme and sparkle icon (bg="#FEFCE8")
8. ✅ `[note]` markers automatically convert to `[notice_block]` with green theme and NO icon (bg="#E1FFF0", icon="")
9. ✅ `[tips_banner]` with "TL;DR" title kept as-is with yellow theme (bg="#FEFCE8", border="#FDE68A", color="#713F12")
10. ✅ `[tips_banner]` with "What is X?" title kept as-is with blue theme (bg="#DBEAFE", border="#BFDBFE", color="#1E3A8A")

**HTML STRUCTURE RULES:**
- Use clean, minimal HTML structure
- Common text lines go in `<p>` tags with data attributes
- Lists use `<ul class="ak-ul">` with `<li>` containing `<p>` tags
- Code snippets use `[code_panel]` shortcode with syntax-highlighted `<pre><code>`
- Inline code from Confluence uses `<code>` tag with standard class attribute
- `[ct]` shortcode converts to `<span>` with Geist Mono styling (padding-left: 5px, padding-right: 5px, font-size: 15px)
- `[tips_banner]` with TL;DR title kept as-is with exact yellow theme colors
- Headings use `<h1>`, `<h2>`, `<h3>` with `id` and data attributes
- Links use full class attribute string from examples

---

## WORKFLOW

1. **Receive** Confluence blog content
2. **Analyze** structure (headings, code blocks, images, CTAs)
3. **Convert** each element using this protocol
4. **Apply** syntax highlighting to code blocks (ONLY place to use inline styles besides images)
5. **Add** WordPress shortcode components where appropriate
6. **Keep content structure exactly as provided** - NO rearranging or rewriting
7. **Use ONLY standard HTML tags** - NO custom classes or CSS
8. **Validate** against checklist
9. **Output** complete WordPress HTML

---

**END OF CONFLUENCE TO WORDPRESS HTML CONVERSION PROTOCOL**
