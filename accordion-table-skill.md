---
name: accordion-comparison-table
description: Generates WordPress-ready accordion comparison table HTML by populating a proven, working template with new content from a markdown file. Use this skill whenever the user asks to create, build, generate, or update a comparison table, feature table, competitor table, or any table with collapsible/accordion sections for a blog post or WordPress page. Do NOT attempt to write comparison table HTML from scratch — always use this skill's template. Trigger even if the user simply pastes markdown data and says "make a comparison table" or "turn this into a table for the blog."
---

# Accordion Comparison Table

Generates WordPress Classic Editor-ready accordion comparison table HTML. The goal is **content replacement only** — the template's structure, CSS classes, inline styles, and accordion logic must never be altered.

## Step 1 — Read the template

Always begin by reading the reference template:

```
assets/template.html
```

Load its full content into context. This is the single source of truth for all class names, row types, icon paths, and HTML structure. Never reconstruct HTML from memory.

## Step 2 — Parse the markdown input

The user will provide a `.md` file or paste markdown text. Extract:

1. **Column headers** — the product/tool names (first row after `|` separator, skipping the label column)
2. **Logo URLs** — if provided (look for a `Logo` row or a comment above the headers like `<!-- logos: url1, url2 -->`)
3. **Always-visible rows** — top-level rows with no category parent (e.g. Pricing, Best for, Ease of use)
4. **Category sections** — marked with `##` headings or a `[CATEGORY]` prefix in the markdown
5. **Sub-feature rows** — rows that belong under a category section (they appear after a `##` heading or `[CATEGORY]` line)
6. **CTA row** — the final button row; look for a `CTA` section or `[CTA]` marker; extract button labels and URLs per column

### Expected markdown format

```markdown
## Columns
| | ProductA | ProductB | ProductC | ProductD | ProductE |
| Logo | https://... | https://... | https://... | https://... | https://... |

## Always-visible rows
| Pricing (starts at) | $39/mo | $49/mo | Free | $99/mo | $29/mo |
| Best for | Use case A | Use case B | Use case C | Use case D | Use case E |
| Ease of use | ★★★★★ | ★★★★½ | ★★★★ | ★★★ | ★★★★ |

## Category: Getting Started
| Onboarding Time | Quick | Moderate | Quick | Slow | Quick |
| Setup Complexity | Simple | Medium | Medium | Complex | Simple |

## Category: Features
| Feature X | ✓ | ✓ | ✗ | ~ | ✗ |
| Feature Y | ✓ | ~ | ✓ | ✓ | ~ |

## CTA
| | Try for FREE / https://app.example.com | Learn More / https://... | Learn More / https://... | Learn More / https://... | Learn More / https://... |
```

If the user's markdown uses a different layout, adapt flexibly. The key thing is identifying: headers, always-visible rows, category+sub rows, and the CTA row.

## Step 3 — Map cell values to HTML

### Icon-only cells

When a cell contains only a symbol with no additional text, render the icon alone:

| Markdown value | HTML output |
|---|---|
| `✅` or `✓` or `yes` | `<img decoding="async" src="https://testdino.com/wp-content/uploads/2025/10/Green_check.svg" alt="Check" class="mx-auto ">` |
| `❌` or `✗` or `no` | `<img decoding="async" src="https://testdino.com/wp-content/uploads/2025/10/wrong-mark.svg" alt="Cross" class="mx-auto ">` |
| `⚠️` or `~` or `partial` | `<img decoding="async" src="https://testdino.com/wp-content/uploads/2025/10/Tringle.svg" alt="Alert" class="mx-auto ">` |
| `★★★★★` / `5` stars | `<img decoding="async" src="https://testdino.com/wp-content/uploads/2025/10/5-Star.svg" alt="TestDino 5 Star" class="mx-auto">` |
| `★★★★½` / `4.5` stars | `<img decoding="async" src="https://testdino.com/wp-content/uploads/2025/10/4.5-Star.svg" alt="TestDino 4.5 Star" class="mx-auto">` |
| `★★★★` / `4` stars | `<img decoding="async" src="https://testdino.com/wp-content/uploads/2025/10/4-Star.svg" alt="TestDino 4 Star" class="mx-auto">` |
| `★★★½` / `3.5` stars | `<img decoding="async" src="https://testdino.com/wp-content/uploads/2025/10/3.5-Star.svg" alt="TestDino 3.5 Star" class="mx-auto">` |
| `★★★` / `3` stars | `<img decoding="async" src="https://testdino.com/wp-content/uploads/2025/10/3-Star.svg" alt="TestDino 3 Star" class="mx-auto">` |
| Plain text only | Text inside the `<td>` — no img tag |

### Icon + text cells (IMPORTANT)

When a cell starts with a symbol followed by descriptive text (e.g. `✅ Via JUnit XML`, `⚠️ CLI upload + config`, `❌ Docker Compose setup`), render **both** the icon image AND the text together inside the same `<td>`, separated by a space:

```html
<td class="px-2 py-[18px] md:p-4 text-center border-b border-r border-[#F5F5F5] font-geist font-normal text-[14px] md:text-[16px] leading-[24px]"><img decoding="async" src="https://testdino.com/wp-content/uploads/2025/10/Green_check.svg" alt="Check" class="mx-auto " /> Works well</td>
```

The three icon URLs to use:
- Green check: `https://testdino.com/wp-content/uploads/2025/10/Green_check.svg`
- Triangle alert: `https://testdino.com/wp-content/uploads/2025/10/Tringle.svg`
- Red cross: `https://testdino.com/wp-content/uploads/2025/10/wrong-mark.svg`

**The rule:** always lead with the `<img />` tag, then a space, then the descriptive text. Never drop the icon when text is present, and never drop the text when an icon is present. Both must appear together.

## Step 4 — Handle variable column counts

The template uses 6 columns (1 label + 5 data). If the new table has a different number of data columns (N), adjust:

- `<thead>` `<th>` count: 1 label `<th>` + N data `<th>` tags
- Every `<tr>` `<td>` count: 1 label `<td>` + N data `<td>` tags
- Every `category-row` `<td colspan="...">`: set colspan to N+1
- Every `button-row` `<td>` count: 1 label `<td>` + N data `<td>` tags

Column width percentages for the label `<th>`:
- 3 data cols: label = `w-[20%] md:w-[20%]`, each data col = `w-[20%] md:w-[26.6%]`
- 4 data cols: label = `w-[20%] md:w-[16%]`, each data col = `w-[20%] md:w-[21%]`
- 5 data cols (default): label = `w-[20%] md:w-[14%]`, each data col = `w-[20%] md:w-[17.2%]`
- 6 data cols: label = `w-[20%] md:w-[12%]`, each data col = `w-[20%] md:w-[14.6%]`

## Step 5 — Build the HTML

Follow this exact row structure from the template. Do NOT deviate from class names, inline styles, or attributes.

### Header row (`<thead>`)

For each data column, the `<th>` block is:
```html
<th class="p-2 md:p-4 text-center font-geist text-sm md:text-lg font-bold border-b border-r border-[#E5E5E5] w-[20%] md:w-[17.2%]">
  <img decoding="async" class="mx-auto w-[49px]" src="LOGO_URL" alt="TOOL_NAME logo">
  <div class="mt-[12px] text-center font-[600] text-[16px] leading-normal">TOOL_NAME</div>
</th>
```
If no logo URL is provided, omit the `<img>` tag and render only the `<div>` with the name.

### Always-visible rows

Use `class="table-row"` and `style="display: table-row;"`. Label cell uses the label TD class. Data cells use the data TD class. These rows appear **before** the first category accordion block.

Label TD class:
```
class="lg:px-[20px] p-2 pl-[20px] md:p-4 text-start border-b border-r border-[#F5F5F5] font-geist font-[500] text-[14px] md:text-[16px]"
```

Data TD class:
```
class="px-2 py-[18px] md:p-4 text-center border-b border-r border-[#F5F5F5] font-geist font-normal text-[14px] md:text-[16px] leading-[24px]"
```

### Category accordion structure

Each category section is a pair: one **hidden duplicate** (always-open version, `class="category-row bg-[#FCFCFC] hidden"`) followed by the **toggle version** (`class="category-row bg-[#FCFCFC] toggle-icon"`). Copy both exactly from the template, only replacing the category name text. Then follow with the sub-feature rows (`class="sub-feature table-row"` with `style="display: none;"`).

**Hidden duplicate `<tr>`** (the first category `<tr>` per section — always present, never remove):
```html
<tr class="category-row bg-[#FCFCFC] hidden">
  <td colspan="COLSPAN" class="p-2 md:p-4 font-geist font-semibold text-[18px] md:text-base border-b border-[#F0F0F1] relative">CATEGORY NAME <img decoding="async" src="https://testdino.com/wp-content/themes/Testdino/Testdino%20Landing%20Page%20Images/Testdino%20vs%20ReportPortal/dropdownsvg.svg" alt="▼" class="toggle-icon absolute right-2 md:right-4 top-[30%] transform -translate-y-1/2 w-4 h-4 md:w-6 md:h-6 cursor-pointer transition-transform duration-300" style="transform: rotate(180deg);" role="button" aria-expanded="true" tabindex="0"></td>
</tr>
```

**Toggle `<tr>`** (the clickable accordion header):
```html
<tr class="category-row bg-[#FCFCFC] toggle-icon" role="button" aria-expanded="false" tabindex="0">
  <td colspan="COLSPAN" class="p-2 md:p-4 font-geist font-semibold text-[18px] md:text-base border-b border-[#F0F0F1] relative">CATEGORY NAME <img decoding="async" src="https://testdino.com/wp-content/themes/Testdino/Testdino%20Landing%20Page%20Images/Testdino%20vs%20ReportPortal/dropdownsvg.svg" alt="▼" class=" absolute right-2 md:right-4 top-[30%] transform -translate-y-1/2 w-4 h-4 md:w-6 md:h-6 cursor-pointer transition-transform duration-300" style="transform: rotate(0deg);"></td>
</tr>
```

**Sub-feature rows** (hidden by default, toggled by accordion):
```html
<tr class="sub-feature table-row" style="display: none;">
  <td class="lg:px-[20px] p-2 pl-[20px] md:p-4 text-start border-b border-r border-[#F5F5F5] font-geist font-[500] text-[14px] md:text-[16px]">ROW LABEL</td>
  <!-- data cells -->
</tr>
```

### CTA button row

Always the last row. First column is blank. Column 1 (your product) gets the primary black button. Columns 2–N get the outlined "Learn More" button.

Primary button:
```html
<a href="CTA_URL" target="_blank" type="button" class="p-[11px] inline-block font-[500] rounded-[6px] text-[14px] lg:text-[14px] bg-[#171717] text-white hover:text-white hover:bg-gray-500" rel="noopener">CTA_LABEL</a>
```

Secondary button:
```html
<a href="CTA_URL" target="_blank" type="button" class="p-[11px] inline-block font-[500] rounded-[6px] text-[14px] lg:text-[14px] bg-transparent text-[#171717] border border-[#171717] hover:text-white hover:bg-black" rel="noopener">CTA_LABEL</a>
```

The CTA row `<tr>` uses `class="category-row bg-[#FCFCFC] button-row"`. CTA `<td>` uses `class="p-2 md:px-[12px] md:py-[11px] text-center border-b border-r border-[#F5F5F5] font-geist font-normal text-[14px]"` for col 1 and `class="p-2 md:px-[12px] md:py-[24px] text-center border-b border-r border-[#F5F5F5] font-geist font-normal text-[14px]"` for cols 2–N.

## Step 6 — Output

Output the complete HTML as a single code block, ready to paste into WordPress Classic Editor > Code view.

Do NOT:
- Add `<script>` tags (the accordion JS lives in the theme)
- Add `<style>` tags (all styling comes from Tailwind/theme classes)
- Change any class names, even ones that look redundant
- Remove the hidden duplicate category row — it is required for the accordion's initial state
- Invent new class names or inline styles not present in the template

If the user hasn't provided logo URLs, omit the `<img>` in the header and only render the name `<div>`. Ask if they'd like to add logos later.

If the user's markdown has ambiguous cell values (e.g. "Limited", "Partial", "Beta"), use `~` / Tringle (alert/partial) as the default icon, and mention the assumption so they can correct it.