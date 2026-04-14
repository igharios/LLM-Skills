---
name: imagegen
description: >
  Generate publication-ready images for blog posts and LinkedIn content. Produces two image types:
  (1) Hero/thumbnail images for posts comparing "old way vs new way" transitions, paradigm shifts,
  or multi-sided arguments — using bold, conceptual visuals with strong typography.
  (2) Data visualization images that illustrate specific research findings, statistics, or comparisons
  within articles. Use this skill whenever the user asks to "create an image for my blog", "make a
  hero image", "thumbnail for my post", "LinkedIn banner", "visualize this data point", "create a
  chart for my article", "make an image showing the comparison", or references their blog/LinkedIn
  content and needs visuals. Also trigger when the user shares a blog draft and asks for images,
  or when they mention "old way vs new way", "transition", "transformation", or "before/after" visuals.
---

# Blog & LinkedIn Image Generator

Creates two categories of images for content marketing:

1. **Hero Images** — Bold, conceptual thumbnails for posts about transitions, comparisons, or paradigm shifts
2. **Data Images** — Clean visualizations of statistics, research findings, and comparative data

All images are generated via Python (Pillow/Matplotlib) and saved as PNG files.

---

## Image Type Detection

Determine which image type the user needs:

| User Request | Image Type |
|--------------|------------|
| "hero image", "thumbnail", "main image", "header image", "cover image" | Hero |
| "LinkedIn post image", "blog banner", "featured image" | Hero |
| "old way vs new way", "transition", "before/after", "comparison of approaches" | Hero |
| "visualize this data", "chart for my article", "show the statistics" | Data |
| "illustrate this finding", "graph this comparison", "data point image" | Data |
| Post draft with research citations/statistics embedded | Both (Hero + Data) |

If unclear, ask the user: "Should I create a hero image (conceptual, for the thumbnail) or a data visualization (showing specific numbers/comparisons)?"

---

## Hero Images (Transition/Comparison Thumbnails)

### Purpose
Hero images represent the core argument of a post — typically a **paradigm shift** or **comparison between approaches**. They are conceptual and metaphorical, not literal illustrations.

### Design Philosophy

The hero image should visually encode the **tension** or **transition** in the post:

- **Two-sided comparisons**: Split compositions, contrasting colors, opposing shapes
- **Evolution/transformation**: Gradient transitions, metamorphosis imagery, before→after flow
- **Multi-perspective arguments**: Radial layouts, interconnected nodes, layered perspectives

### Visual Style Guide

| Element | Specification |
|---------|---------------|
| **Dimensions** | 1600×900px (Substack/blog) or 1200×628px (LinkedIn) |
| **Typography** | Bold, condensed sans-serif; title ≤10 words |
| **Color Palette** | 2-4 colors max; use contrast to encode the comparison |
| **Composition** | Asymmetric balance; visual weight on the "new way" side |
| **Background** | Solid, gradient, or geometric — never busy |

### Color Coding for Transitions

| Transition Type | "Old Way" Colors | "New Way" Colors |
|-----------------|------------------|------------------|
| Tech/AI transformation | Gray, muted blue | Electric blue, cyan, violet |
| Process improvement | Warm brown, amber | Cool teal, green |
| Mindset shift | Heavy black, charcoal | Light gold, white |
| Digital vs analog | Sepia, paper tones | Neon, digital blue |

### Composition Patterns

**Pattern 1: Split Screen**
```
┌─────────────┬─────────────┐
│             │             │
│  OLD WAY    │  NEW WAY    │
│  (muted)    │  (vibrant)  │
│             │             │
└─────────────┴─────────────┘
         TITLE OVERLAY
```

**Pattern 2: Transition Flow**
```
┌─────────────────────────────┐
│  ████ ──────────────▶ ████  │
│  OLD        →         NEW   │
│                             │
│       TITLE CENTERED        │
└─────────────────────────────┘
```

**Pattern 3: Convergence (Multi-sided)**
```
┌─────────────────────────────┐
│      ████     ████          │
│         \   /               │
│          ███  ← SYNTHESIS   │
│         /   \               │
│      ████     ████          │
│         TITLE               │
└─────────────────────────────┘
```

### Python Generation Template (Hero)

```python
from PIL import Image, ImageDraw, ImageFont
import os

# Dimensions
W, H = 1600, 900  # or 1200, 628 for LinkedIn

# Color palette (example: AI transformation)
OLD_COLOR = "#3D4F5F"  # muted slate
NEW_COLOR = "#00D4FF"  # electric cyan
BG_COLOR = "#1A1A2E"   # deep navy
TEXT_COLOR = "#FFFFFF"

img = Image.new("RGB", (W, H), color=BG_COLOR)
draw = ImageDraw.Draw(img)

# --- Split composition ---
# Left side (old way) - muted rectangle
draw.rectangle([0, 0, W//2 - 20, H], fill=OLD_COLOR)

# Right side (new way) - vibrant rectangle  
draw.rectangle([W//2 + 20, 0, W, H], fill=NEW_COLOR)

# Center divider with gradient effect
for i in range(40):
    alpha = int(255 * (1 - abs(i - 20) / 20))
    draw.line([(W//2 - 20 + i, 0), (W//2 - 20 + i, H)], fill=BG_COLOR)

# --- Typography ---
# Load font (adjust path as needed)
try:
    title_font = ImageFont.truetype("/usr/share/fonts/truetype/dejavu/DejaVuSans-Bold.ttf", 72)
    subtitle_font = ImageFont.truetype("/usr/share/fonts/truetype/dejavu/DejaVuSans.ttf", 32)
except:
    title_font = ImageFont.load_default()
    subtitle_font = ImageFont.load_default()

# Title text
title = "OLD WAY → NEW WAY"
bbox = draw.textbbox((0, 0), title, font=title_font)
text_w = bbox[2] - bbox[0]
draw.text(((W - text_w) // 2, H - 150), title, font=title_font, fill=TEXT_COLOR)

# Byline
byline = "senzostack.com"
draw.text((W - 200, H - 50), byline, font=subtitle_font, fill="#888888")

img.save("/mnt/user-data/outputs/hero.png", "PNG")
print("Hero image saved to /mnt/user-data/outputs/hero.png")
```

---

## Data Images (Research Visualizations)

### Purpose
Data images illustrate **specific findings** within an article — statistics, comparisons, survey results, or research data. They make abstract numbers tangible.

### When to Use
- Article cites a specific percentage or statistic
- Comparing metrics between two groups (e.g., "core vs peripheral developers")
- Showing distribution or breakdown of categories
- Illustrating trends over time

### Visual Style Guide

| Element | Specification |
|---------|---------------|
| **Dimensions** | 800×600px (in-article) or 1200×800px (full-width) |
| **Chart Types** | Bar (comparisons), Pie (distribution), Line (trends), Table (multi-variable) |
| **Colors** | Match the hero image palette; use contrast for compared groups |
| **Labels** | Always include axis labels, legend, and source citation |
| **Background** | White or very light gray (#F8F9FA) for readability |

### Chart Type Selection

| Data Type | Best Chart | Example |
|-----------|------------|---------|
| A vs B comparison | Horizontal bar | "Core: 85.8% vs Peripheral: 77.8%" |
| Category breakdown | Stacked bar or pie | "PR purposes by developer type" |
| Multiple metrics | Grouped bar | "CI check outcomes by group" |
| Trend over time | Line chart | "Adoption rate by quarter" |
| Multi-variable comparison | Table/heatmap | "Review comments by category" |

### Python Generation Template (Data - Bar Chart)

```python
import matplotlib.pyplot as plt
import matplotlib.patches as mpatches
import numpy as np

# Data
categories = ['Core Developers', 'Peripheral Developers']
values = [85.8, 77.8]
colors = ['#00D4FF', '#3D4F5F']  # Match hero palette

# Create figure
fig, ax = plt.subplots(figsize=(10, 6))
fig.patch.set_facecolor('#F8F9FA')
ax.set_facecolor('#F8F9FA')

# Horizontal bar chart
bars = ax.barh(categories, values, color=colors, height=0.5)

# Add value labels
for bar, val in zip(bars, values):
    ax.text(val + 1, bar.get_y() + bar.get_height()/2, f'{val}%', 
            va='center', fontsize=14, fontweight='bold')

# Styling
ax.set_xlim(0, 100)
ax.set_xlabel('Merge Rate (%)', fontsize=12)
ax.set_title('Agentic PR Merge Rates by Developer Type', fontsize=16, fontweight='bold', pad=20)
ax.spines['top'].set_visible(False)
ax.spines['right'].set_visible(False)

# Source citation
fig.text(0.99, 0.01, 'Source: University of Saskatchewan Study (2024)', 
         ha='right', fontsize=8, color='#666666')

plt.tight_layout()
plt.savefig('/mnt/user-data/outputs/data-chart.png', dpi=150, bbox_inches='tight')
print("Data chart saved to /mnt/user-data/outputs/data-chart.png")
```

### Python Generation Template (Data - Comparison Table)

```python
import matplotlib.pyplot as plt
import numpy as np

# Data for table
columns = ['Metric', 'Core Developers', 'Peripheral Developers']
data = [
    ['Median Agentic PRs', '2.0', '2.0'],
    ['Mean Agentic PRs', '3.73', '6.08'],
    ['Merge Rate', '85.8%', '77.8%'],
    ['Review Comments (median)', '3.6', '2.0'],
    ['CI Skip Rate', '11.2%', '19.1%'],
]

fig, ax = plt.subplots(figsize=(10, 4))
ax.axis('off')

# Create table
table = ax.table(
    cellText=data,
    colLabels=columns,
    cellLoc='center',
    loc='center',
    colColours=['#2C3E50', '#00D4FF', '#3D4F5F'],
    colWidths=[0.4, 0.3, 0.3]
)

# Style the table
table.auto_set_font_size(False)
table.set_fontsize(11)
table.scale(1.2, 1.8)

# Header row styling
for j in range(len(columns)):
    table[(0, j)].set_text_props(color='white', fontweight='bold')

plt.title('Developer Behavior with Coding Agents', fontsize=14, fontweight='bold', pad=20)
fig.text(0.99, 0.01, 'Source: University of Saskatchewan Study', ha='right', fontsize=8, color='#666666')

plt.savefig('/mnt/user-data/outputs/data-table.png', dpi=150, bbox_inches='tight', 
            facecolor='#F8F9FA', edgecolor='none')
print("Data table saved to /mnt/user-data/outputs/data-table.png")
```

---

## Workflow

### Step 1: Analyze the Content

Read the user's blog post or content brief. Identify:

1. **Core transition/comparison** — What is the "old way" vs "new way"? What paradigm shift is being argued?
2. **Key data points** — Are there specific statistics, percentages, or research findings that should be visualized?
3. **Tone** — Is this technical, business-focused, personal, or provocative?

### Step 2: Propose Image Plan

Present the user with a plan:

```
Based on your post about [TOPIC], I recommend:

**Hero Image (thumbnail/header):**
- Concept: [Describe the visual metaphor]
- Composition: [Split/Flow/Convergence]
- Color scheme: [Old way colors] → [New way colors]
- Title text: "[Condensed title, ≤10 words]"

**Data Images (optional):**
- Chart 1: [Description] — visualizes [statistic/finding]
- Chart 2: [Description] — visualizes [statistic/finding]

Should I proceed with this plan, or would you like adjustments?
```

### Step 3: Generate Images

1. Install dependencies if needed:
   ```bash
   pip install Pillow matplotlib --break-system-packages --quiet
   ```

2. Generate each image using the templates above, customized for the content

3. Save to `/mnt/user-data/outputs/`:
   - Hero: `hero.png` or `hero-[slug].png`
   - Data: `data-[description].png`

4. Call `present_files` to show the user the results

### Step 4: Iterate

Ask the user:
- "Does the hero image capture the transition you're describing?"
- "Are the data visualizations accurate to your findings?"
- "Any color/style adjustments?"

Regenerate as needed.

---

## Platform-Specific Dimensions

| Platform | Hero Image | Data Image |
|----------|------------|------------|
| Substack | 1600×900px | 800×600px |
| LinkedIn Post | 1200×628px | 1200×628px |
| LinkedIn Article | 1280×720px | 800×600px |
| Medium | 1400×788px | 800×600px |
| Blog (general) | 1600×900px | 800×600px |

Ask the user which platform they're targeting, or default to Substack dimensions.

---

## Edge Cases

- **No clear transition**: If the post isn't about a comparison, create a conceptual hero that captures the main theme using bold typography and abstract shapes
- **No data points**: Skip data images entirely; focus on a strong hero
- **Multiple comparisons**: Create one hero for the main thesis; offer additional data images for subsidiary comparisons
- **User provides specific data**: Use their exact numbers; never fabricate statistics
- **Color preference stated**: Override the default palette with user preferences

---

## Constraints

| Rule | Detail |
|------|--------|
| **No stock imagery** | All images generated via code, not sourced externally |
| **No copyrighted elements** | Don't recreate logos, brand assets, or copyrighted visuals |
| **Data accuracy** | Never invent statistics; use only data the user provides or verifies |
| **Readability first** | Text must be legible; never sacrifice clarity for aesthetics |
| **Always generate PNG** | Output as PNG for maximum compatibility |
| **Always present files** | Call `present_files` after generation so user can preview/download |
