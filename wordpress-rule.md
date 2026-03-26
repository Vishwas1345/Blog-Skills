---
name: wordpress-publishing-rules
description: Declarative rule book defining the exact standard of a correct, ready-to-publish WordPress blog post. Every rule states what a correct post IS — not instructions on how to create one. Use as the authoritative spec for all AI agents working on WordPress posts.
---

# WORDPRESS PUBLISHING RULE BOOK

## Purpose

This document defines what a correct, ready-to-publish WordPress blog post looks like. Every statement is a standard — not a guide. A post that violates any rule here is not ready to publish.

---

## 🚨 GOLDEN RULES (Absolute — Zero Tolerance)

1. The post body contains **no `<h1>` tag**. The WordPress Title field is the H1.
2. Heading hierarchy in the body is strictly `<h2>` → `<h3>` → `<h4>`. No level is skipped.
3. Every multi-line code block is inside a `[code_light]` shortcode. Naked `<pre>` or `<code>` outside a shortcode does not exist.
4. The post body is HTML and WordPress shortcodes only. No markdown.
5. Every image has `box-shadow: 0px 0px 12px rgba(0, 0, 0, 0.1);` applied.
6. No `<p></p>` or `<p> </p>` tags exist anywhere in the body.

---

## SECTION 1 — POST SETTINGS

### 1.1 Title

- The post title lives in the **WordPress Title field**, not in the body.
- Title length is **60 characters maximum**.
- The title matches the `Meta Title` from the content plan exactly.

### 1.2 URL Slug

- The slug is all lowercase, words separated by hyphens, no trailing slash.
- Stop words (`a`, `the`, `is`, `and`) are absent unless part of a brand name.
- Slug length is **5–7 meaningful words maximum**.
- ✅ `/playwright-test-automation-guide`
- ❌ `/how-to-use-playwright-for-test-automation-in-2025`

### 1.3 Category

- Exactly **one primary category** is assigned.
- The category is never "Uncategorized".
- If no specific category is determined, **"Playwright"** is selected. It is the default fallback category — not "Uncategorized".

### 1.4 Tags

- **3–7 tags** are present, matching secondary keywords from the content plan.
- Tags are lowercase and hyphenated (e.g., `test-automation`, `playwright`, `ci-cd`).
- No tag duplicates the category name.

### 1.5 Author

- The correct author is selected on the post.

### 1.6 New Design
- The **"New Design"** field on the post is set to **Yes**. This is mandatory on every post without exception.

---

## SECTION 2 — SEO SETTINGS


| Field                | Standard                                                                    |
| -------------------- | --------------------------------------------------------------------------- |
| **Focus Keyword**    | The primary keyword from the content plan                                   |
| **SEO Title**        | 55–65 characters. Format: `Primary Keyword — Brand Name`                    |
| **Meta Description** | 150–160 characters. Primary keyword appears naturally. No keyword stuffing. |
| **Canonical URL**    | Empty, unless the post is a duplicate or translation                        |
| **Schema Type**      | `Article` for blog posts. `FAQ Page` for primarily FAQ-structured posts.    |


---

## SECTION 3 — FEATURED IMAGE

- A featured image is always set. No post publishes without one.
- Dimensions: **minimum 1200 × 630 px**.
- Format: `.webp` is the standard. `.jpg` is acceptable. `.png` is not used for photos.
- File size: **200 KB maximum**.
- Alt text describes the image content with the primary keyword used naturally. Max 125 characters.
- File name is lowercase, hyphenated, and descriptive (e.g., `playwright-test-dashboard.webp`).
- **If no featured image is available or selected**, one of the **4 oldest images** in the media library is used. One is picked at random from those 4. No post goes without a featured image under any circumstance.

---

## SECTION 4 — HEADING STRUCTURE

- **H1** exists only as the WordPress Title field. The post body has zero H1 tags.
- **H2** marks major sections. Every H2 has a meaningful `id` attribute.
- **H3** marks subsections under an H2. No H3 appears before its parent H2.
- **H4** is rare, used only for items nested under an H3.
- The order `<h2>` → `<h4>` without an intervening `<h3>` does not exist.

### ID Format

- Spaces become hyphens. Capitalization is preserved. Special characters are removed.
- ✅ `id="How-to-Install"` `id="Key-Benefits"` `id="FAQ"`

### Heading HTML

```html
<h2 data-local-id="xxx" data-renderer-start-pos="100" id="Section-Name">Section Name</h2>
<h3 data-local-id="xxx" data-renderer-start-pos="200" id="Subsection-Name">Subsection Name</h3>
<h4 data-local-id="xxx" data-renderer-start-pos="300" id="Minor-Heading">Minor Heading</h4>
```

---

## SECTION 5 — CODE BLOCKS

### 5.1 Shortcode Structure

Every multi-line code block has this exact structure:

```
[code_light title="filename.ext"]
<pre><code>…syntax-highlighted spans…</code></pre>
[/code_light]
```

### 5.2 Title Attribute

- Every `[code_light]` block has a `title` attribute with a real, practical filename.
- Generic labels (`Code Snippet`, `Example`, `Action`) do not exist as titles.

### 5.2a Commented Filename at the Top of a Code Block

If the first line of a code block is a comment that contains a filename — such as `// playwright.config.ts`, `# config.yml`, or `/* auth.setup.ts */` — that comment **is** the filename. It is used as the `title` attribute of `[code_light]` and is **not** included inside `<pre><code>`. Including it inside the code would duplicate the title that already appears on the block header.

- ✅ Correct — filename taken from the comment, comment removed from code body:
```
[code_light title="playwright.config.ts"]
<pre><code>// actual code starts here…</code></pre>
[/code_light]
```
- ❌ Wrong — comment left inside the code, causing duplication:
```
[code_light title="playwright.config.ts"]
<pre><code>// playwright.config.ts
// actual code starts here…</code></pre>
[/code_light]
```


| Code Type           | Title                        |
| ------------------- | ---------------------------- |
| Terminal / CLI      | `terminal`                   |
| TypeScript config   | `playwright.config.ts`       |
| Test file           | `example.spec.ts`            |
| Setup file          | `auth.setup.ts`              |
| GitHub Actions YAML | `.github/workflows/test.yml` |
| JSON config         | `mcp.json`                   |


### 5.3 `<pre>` and `<code>` Tags

- `<pre>` and `<code>` are bare. No `style`, `class`, `id`, or `data-*` attributes on either tag.
- No `background-color` (including `#ffffff`) on `<pre>` or `<code>`.
- Syntax highlighting exists only on inner `<span>` elements.

### 5.4 Code Block Colors

→ The full color specification is in **Section 16**. Summary:


| Token                     | Color         |
| ------------------------- | ------------- |
| Keyword                   | `#cf222e`     |
| Function / method         | `#0550ae`     |
| String                    | `#0a3069`     |
| Variable / punctuation    | `#24292f`     |
| Comment                   | `#6e7781`     |
| Number / constant         | `#953800`     |
| Type / class name         | `#6639ba`     |
| **Terminal (all tokens)** | `**#000000`** |


### 5.5 Span Base Style

Every `<span>` in a code block carries:

```
font-family: 'Geist Mono'; font-weight: 300;
```

### 5.6 Token Spacing

Every token has a clear space between it and the next token, using  `` inside `<pre><code>`. Merged tokens (`constclient`, `awaitpage`) do not exist.

### 5.7 Indentation

Indentation is represented by  `` characters (2 spaces =   ``). Line breaks use `<br>`.

### 5.8 Label Before Code Block

Every `[code_light]` block is preceded immediately by a `<p><strong>filename.ext</strong></p>` or a heading that identifies the file.

---

## SECTION 6 — INLINE CODE

### 6.1 The Only Inline Code Format: `[ct]`

`**[ct]code[/ct]` is the one and only inline code format in this WordPress post.**

A standard `<code>` tag does not exist in a correct post. If any `<code>` tag is seen anywhere in the post body, it is wrong and must be replaced with the appropriate `[ct]` span (see 6.2).

### 6.2 `[ct]` Inline Code — Context Colors

`[ct]code[/ct]` is a styled `<span>`. Its color depends on where it appears.
→ Full color specification in **Section 16.3**. Summary:


| Where `[ct]` appears          | Text color | Background |
| ----------------------------- | ---------- | ---------- |
| Body, lists, tables (default) | `#0B0C0E`  | `#E9E9E9`  |
| Inside `[note]` block         | `#065F46`  | `#FDFFFE`  |
| Inside `[tip]` block          | `#713F12`  | `#171717`  |


**Default:**

```html
<span class="text-[#0B0C0E] ff-geist-mono bg-[#E9E9E9] rounded-[4px] font-[500]" style="padding-left: 5px;padding-right: 5px;font-size: 15px;">code text</span>
```

**Inside `[note]`:**

```html
<span class="text-[#065F46] ff-geist-mono bg-[#FDFFFE] rounded-[4px] font-[500]" style="padding-left: 5px;padding-right: 5px;font-size: 15px;">code text</span>
```

**Inside `[tip]`:**

```html
<span class="text-[#713F12] ff-geist-mono bg-[#171717] rounded-[4px] font-[500]" style="padding-left: 5px;padding-right: 5px;font-size: 15px;">code text</span>
```

### 6.3 Table Cells

All code-like text inside `<td>` cells is wrapped in the Default styled `<span>` above. Plain-text code in table cells does not exist.

---

## SECTION 7 — IMAGES

### 7.1 Shadow

A global `<style>` tag is present **once** at the top of the post body:

```html
<style>
img { box-shadow: 0px 0px 12px rgba(0, 0, 0, 0.1); }
</style>
```

This applies the shadow to all images. Individual inline shadow styles on `<img>` tags do not exist.

### 7.2 Placement

Images appear **after** the paragraph that references them, never before.

### 7.3 Alt Text

Every `<img>` has descriptive alt text. Maximum 125 characters. Includes the primary keyword where contextually natural. Generic alt values (`"image"`, `"screenshot"`, `""`) do not exist.

### 7.4 HTML Format

```html
<img src="image-url.webp" alt="Descriptive alt text" width="1200" height="630" />
```

---

## SECTION 8 — LINKS

### 8.1 Internal Links

- Every internal link uses the long designated class string.
- Anchor text is descriptive and keyword-relevant. `"click here"` and `"read more"` do not exist as anchor text.
- A minimum of **2–3 internal links** are in every post.

### 8.2 External Links

- External links carry `target="_blank" rel="noopener noreferrer"`.
- All external links point to authoritative, relevant sources only.
- No links to direct competitors.

### 8.3 Link HTML

```html
<a title="URL" href="URL" class="_ymio1r31 _ypr0glyw _zcxs1o36 _mizu1v1w _1ah3dkaa _ra3xnqa1 _128mdkaa _1cvmnqa1 _4davt94y _4bfu1r31 _1hms8stv _ajmmnqa1 _vchhusvi _kqswh2mm _ect4ttxp _syaz13af _1a3b1r31 _4fpr8stv _5goinqa1 _f8pj13af _9oik1r31 _1bnxglyw _jf4cnqa1 _30l313af _1nrm1r31 _c2waglyw _1iohnqa1 _9h8h12zz _10531ra0 _1ien1ra0 _n0fx1ra0 _1vhv17z1">Link Text</a>
```

### 8.4 CTA Buttons

- Every post has at least **1 CTA** block.
- TestDino CTA buttons link to `https://app.testdino.com/`.
- The correct gradient background class is applied to all CTA buttons.

---

## SECTION 9 — NOTICE BLOCKS (Tip / Note)

```
[tip]
Content here. [ct] inline code uses the Tip color span.
[/tip]

[note]
Content here. [ct] inline code uses the Note color span.
[/note]
```

- Tip blocks contain best practices and pro suggestions.
- Note blocks contain warnings, important caveats, and required steps.
- Tip and Note styles are never mixed.

---

## SECTION 10 — TABLES

- Tables use standard `<table>`, `<thead>`, `<tbody>`, `<tr>`, `<th>`, `<td>`. No custom classes or CSS on table tags.
- Every table has a `<thead>` row.
- Every code-like value in a `<td>` is wrapped in the Default `[ct]` span (Section 6.2). Plain-text code in table cells does not exist.

---

## SECTION 11 — FAQ SECTION

- FAQs live under `<h2 id="FAQ">Frequently Asked Questions</h2>`.
- Every FAQ item uses the `[faq_item]` shortcode:

```
[faq_item question="What is X?"]
Answer text here.
[/faq_item]
```

- A minimum of **4 FAQ items** are present.
- Questions target long-tail queries from the content plan.
- Answers are 2–4 sentences (optimized for AEO / featured snippets).

---

## SECTION 12 — TEXT & CONTENT STANDARDS


| Element        | Standard                                                   |
| -------------- | ---------------------------------------------------------- |
| Paragraph      | Wrapped in `<p>` tags. No loose text exists in the body.   |
| Bold           | `<strong>` — `<b>` does not exist                          |
| Italic         | `<em>` — `<i>` does not exist                              |
| Line break     | `<br>` used sparingly. Separate paragraphs use `<p>` tags. |
| Spacing        | `<p></p>` and `<p> </p>` do not exist                      |
| Unordered list | `<ul>` with `<li>` items                                   |
| Ordered list   | `<ol>` with `<li>` items                                   |
| Markdown       | `#`, `*`*, `_`, backticks do not appear in the HTML editor |


---

## SECTION 13 — CONTENT LENGTH BENCHMARKS


| Post Type          | Minimum     | Target      |
| ------------------ | ----------- | ----------- |
| Tutorial / How-to  | 1,800 words | 2,500–3,500 |
| Comparison article | 1,500 words | 2,000–3,000 |
| Listicle           | 1,200 words | 1,800–2,500 |
| Concept explainer  | 1,000 words | 1,500–2,200 |
| FAQ-focused        | 800 words   | 1,200–2,000 |


---

## SECTION 14 — PRE-PUBLISH CHECKLIST

Every item is satisfied before the post is published or scheduled.

### Post Settings

- Title is in the WordPress Title field, not in the body
- Slug is lowercase, hyphenated, no trailing slash, 5–7 words max
- One primary category assigned, not "Uncategorized"
- 3–7 tags added
- Author is correct
- [ ] "New Design" field is set to **Yes**
- Featured image set (min 1200×630 px, max 200 KB, descriptive alt text) — if none, one of the 4 oldest media library images is used

### SEO

- Focus keyword set
- SEO title is 55–65 characters, includes primary keyword
- Meta description is 150–160 characters, includes primary keyword
- Schema type is `Article` or `FAQ Page`

### Body Structure

- No `<h1>` in the body
- Heading hierarchy `<h2>` → `<h3>` → `<h4>` with no skips
- All `<h2>` and `<h3>` tags have `id` attributes
- No `<p></p>` or `<p> </p>` tags

### Code & Inline

- All multi-line code is inside `[code_light title="..."]`
- Every `[code_light]` has a practical filename title
- `<pre>` and `<code>` are bare — no attributes
- Every token is in a colored `<span>` with Geist Mono
- No merged/sticky tokens
- No `<code>` tags exist anywhere in the body — only `[ct]` spans
- `[ct]` inline code uses the correct color span for its context (default / note / tip)
- All code-like text in table cells is wrapped in the Default `[ct]` span

### Images

- Global `<style>` shadow tag is at the top of the body
- All `<img>` tags have descriptive alt text
- All images appear after their referencing paragraph

### Links & CTAs

- Minimum 2–3 internal links with descriptive anchor text
- External links have `target="_blank" rel="noopener noreferrer"`
- At least 1 CTA linking to `https://app.testdino.com/`

### Content

- Minimum 4 `[faq_item]` blocks present
- Word count meets the minimum for the post type (Section 13)
- Content reads like a human wrote it — no robotic phrasing
- All TestDino claims are verified against official documentation

---

## SECTION 15 — PUBLISH SETTINGS


| Setting                | Standard                                                                                  |
| ---------------------- | ----------------------------------------------------------------------------------------- |
| Visibility             | Public                                                                                    |
| Publish date           | Scheduled minimum 24 h ahead unless urgent                                                |
| Comments               | Enabled                                                                                   |
| Pingbacks / Trackbacks | Disabled                                                                                  |
| Excerpt                | Manual excerpt, **18–22 words exactly**. Includes the primary keyword. No more, no fewer. |


---

## SECTION 16 — COLOR STANDARDS

This section is the single authoritative source for every color used in the blog. All other sections refer here.

---

### 16.1 Code Light Block — Token Colors (Code Files)

These are the token colors for all `[code_light]` blocks where the title is **not** `terminal`.


| Token                                   | Color     | What it covers                                                                                                                                                           |
| --------------------------------------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Keyword**                             | `#cf222e` | `import` `export` `const` `let` `var` `function` `return` `if` `else` `for` `while` `await` `async` `from` `default` `new` `delete` `typeof` `instanceof` `true` `false` |
| **Function / method**                   | `#0550ae` | Any callable followed by `()`: `defineConfig()` `test()` `expect()` `describe()` `beforeAll()` `afterAll()` `launch()` `goto()` `click()` `fill()` `console.log()`       |
| **String**                              | `#0a3069` | Everything inside quotes, including the quote characters: `'single'` `"double"` ``template``                                                                             |
| **Variable / identifier / punctuation** | `#24292f` | Variable names, property names, object keys, and ALL punctuation and operators: `{` `}` `(` `)` `[` `]` `:` `;` `,` `.` `=` `=>` `+` `-` `*` `/` `!` `|` `&`             |
| **Comment**                             | `#6e7781` | The entire comment including slashes: `// text` `/* text */`                                                                                                             |
| **Number / constant**                   | `#953800` | `0` `1` `100` `3000` `null` `undefined` `NaN` `Infinity`                                                                                                                 |
| **Type / class name**                   | `#6639ba` | TypeScript primitives and class names: `string` `number` `boolean` `void` `any` `unknown` `never` `Promise` `Array` `Page` `Browser` `Error`                             |


Every `<span>` carries the base style:

```
font-family: 'Geist Mono'; font-weight: 300;
```

Full span pattern:

```html
<span style="color: #HEXCOLOR; font-family: 'Geist Mono'; font-weight: 300;">token</span>
```

#### Working Example (Code File)

```html
[code_light title="playwright.config.ts"]
<pre><code><span style="color: #cf222e; font-family: 'Geist Mono'; font-weight: 300;">import</span> <span style="color: #24292f; font-family: 'Geist Mono'; font-weight: 300;">{ </span><span style="color: #0550ae; font-family: 'Geist Mono'; font-weight: 300;">defineConfig</span><span style="color: #24292f; font-family: 'Geist Mono'; font-weight: 300;"> } </span><span style="color: #cf222e; font-family: 'Geist Mono'; font-weight: 300;">from</span> <span style="color: #0a3069; font-family: 'Geist Mono'; font-weight: 300;">'@playwright/test'</span><span style="color: #24292f; font-family: 'Geist Mono'; font-weight: 300;">;</span><br><span style="color: #cf222e; font-family: 'Geist Mono'; font-weight: 300;">export</span> <span style="color: #cf222e; font-family: 'Geist Mono'; font-weight: 300;">default</span> <span style="color: #0550ae; font-family: 'Geist Mono'; font-weight: 300;">defineConfig</span><span style="color: #24292f; font-family: 'Geist Mono'; font-weight: 300;">({</span><br><span style="color: #24292f; font-family: 'Geist Mono'; font-weight: 300;">  use: {</span><br><span style="color: #24292f; font-family: 'Geist Mono'; font-weight: 300;">    trace: </span><span style="color: #0a3069; font-family: 'Geist Mono'; font-weight: 300;">'on'</span><span style="color: #24292f; font-family: 'Geist Mono'; font-weight: 300;">, </span><span style="color: #6e7781; font-family: 'Geist Mono'; font-weight: 300;">// Enable tracing</span><br><span style="color: #24292f; font-family: 'Geist Mono'; font-weight: 300;">  },</span><br><span style="color: #24292f; font-family: 'Geist Mono'; font-weight: 300;">});</span></code></pre>
[/code_light]
```

---

### 16.2 Terminal Blocks — `title="terminal"`

**All tokens in a terminal block are `#000000`. Every single span.**

Terminals have no syntax theme. There are no keywords, strings, or types in a shell command. The entire block is black text.

- `#cf222e`, `#0550ae`, `#0a3069` and every other palette color do **not** appear in a terminal block.

#### Working Example (Terminal)

```html
[code_light title="terminal"]
<pre><code><span style="color: #000000; font-family: 'Geist Mono'; font-weight: 300;">npm</span> <span style="color: #000000; font-family: 'Geist Mono'; font-weight: 300;">init</span> <span style="color: #000000; font-family: 'Geist Mono'; font-weight: 300;">playwright@latest</span><br><span style="color: #000000; font-family: 'Geist Mono'; font-weight: 300;">npx</span> <span style="color: #000000; font-family: 'Geist Mono'; font-weight: 300;">playwright</span> <span style="color: #000000; font-family: 'Geist Mono'; font-weight: 300;">test</span> <span style="color: #000000; font-family: 'Geist Mono'; font-weight: 300;">--reporter=html</span></code></pre>
[/code_light]
```

---

### 16.3 `[ct]` Inline Code — Context Colors

Inline code spans have three color states. Which state applies depends solely on the block the `[ct]` sits inside.


| Context                       | Text color             | Background             | Why                                                                                            |
| ----------------------------- | ---------------------- | ---------------------- | ---------------------------------------------------------------------------------------------- |
| Default — body, lists, tables | `#0B0C0E` (near-black) | `#E9E9E9` (light gray) | High contrast on the white page background                                                     |
| Inside `[note]`               | `#065F46` (dark green) | `#FDFFFE` (off-white)  | Matches the Note block's green text; off-white prevents clash with the Note's green background |
| Inside `[tip]`                | `#713F12` (dark brown) | `#171717` (near-black) | Ensures contrast against the Tip block's yellow/amber background                               |


**Default span:**

```html
<span class="text-[#0B0C0E] ff-geist-mono bg-[#E9E9E9] rounded-[4px] font-[500]" style="padding-left: 5px;padding-right: 5px;font-size: 15px;">code text</span>
```

**Note span:**

```html
<span class="text-[#065F46] ff-geist-mono bg-[#FDFFFE] rounded-[4px] font-[500]" style="padding-left: 5px;padding-right: 5px;font-size: 15px;">code text</span>
```

**Tip span:**

```html
<span class="text-[#713F12] ff-geist-mono bg-[#171717] rounded-[4px] font-[500]" style="padding-left: 5px;padding-right: 5px;font-size: 15px;">code text</span>
```

Context detection rule:

- `[ct]` between `[note]` and `[/note]` → Note span.
- `[ct]` between `[tip]` and `[/tip]` → Tip span.
- `[ct]` anywhere else → Default span.

---

### 16.4 Complete Color Reference (One-Glance)


| Where              | Element                | Text / Token Color | Background |
| ------------------ | ---------------------- | ------------------ | ---------- |
| Code file block    | keyword                | `#cf222e`          | —          |
| Code file block    | function/method        | `#0550ae`          | —          |
| Code file block    | string                 | `#0a3069`          | —          |
| Code file block    | variable / punctuation | `#24292f`          | —          |
| Code file block    | comment                | `#6e7781`          | —          |
| Code file block    | number / constant      | `#953800`          | —          |
| Code file block    | type / class name      | `#6639ba`          | —          |
| Terminal block     | all tokens             | `#000000`          | —          |
| `[ct]` default     | inline span            | `#0B0C0E`          | `#E9E9E9`  |
| `[ct]` in `[note]` | inline span            | `#065F46`          | `#FDFFFE`  |
| `[ct]` in `[tip]`  | inline span            | `#713F12`          | `#171717`  |


---

**END OF WORDPRESS PUBLISHING RULE BOOK**