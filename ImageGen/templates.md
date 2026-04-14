# Advanced Templates & Examples

This file contains additional code templates and real-world examples for the imagegen skill.

---

## Hero Image Templates

### Template: Diagonal Split with Arrow

Creates a dynamic diagonal split with an arrow suggesting transformation.

```python
from PIL import Image, ImageDraw, ImageFont
import math

W, H = 1600, 900

# Colors
OLD_COLOR = "#4A5568"   # slate gray
NEW_COLOR = "#38B2AC"   # teal
BG_COLOR = "#1A202C"    # dark blue-gray
ACCENT = "#F6E05E"      # gold accent

img = Image.new("RGB", (W, H), color=BG_COLOR)
draw = ImageDraw.Draw(img)

# Diagonal split - polygon for old side
old_poly = [(0, 0), (W * 0.6, 0), (W * 0.4, H), (0, H)]
draw.polygon(old_poly, fill=OLD_COLOR)

# New side is the remaining area (background shows through)
new_poly = [(W * 0.6, 0), (W, 0), (W, H), (W * 0.4, H)]
draw.polygon(new_poly, fill=NEW_COLOR)

# Arrow in the center
arrow_x = W // 2
arrow_y = H // 2
arrow_size = 80
# Arrow body
draw.rectangle([arrow_x - 60, arrow_y - 15, arrow_x + 30, arrow_y + 15], fill=ACCENT)
# Arrow head
draw.polygon([
    (arrow_x + 30, arrow_y - 40),
    (arrow_x + 90, arrow_y),
    (arrow_x + 30, arrow_y + 40)
], fill=ACCENT)

# Labels
try:
    label_font = ImageFont.truetype("/usr/share/fonts/truetype/dejavu/DejaVuSans-Bold.ttf", 36)
    title_font = ImageFont.truetype("/usr/share/fonts/truetype/dejavu/DejaVuSans-Bold.ttf", 64)
except:
    label_font = ImageFont.load_default()
    title_font = ImageFont.load_default()

draw.text((100, H//2 - 20), "BEFORE", font=label_font, fill="#FFFFFF")
draw.text((W - 250, H//2 - 20), "AFTER", font=label_font, fill="#FFFFFF")

# Title at bottom
title = "Digital → AI Transformation"
bbox = draw.textbbox((0, 0), title, font=title_font)
text_w = bbox[2] - bbox[0]
draw.text(((W - text_w) // 2, H - 120), title, font=title_font, fill="#FFFFFF")

img.save("/mnt/user-data/outputs/hero-diagonal.png", "PNG")
```

### Template: Gradient Transition

Creates a smooth gradient representing evolution/transformation.

```python
from PIL import Image, ImageDraw, ImageFont
import colorsys

W, H = 1600, 900

img = Image.new("RGB", (W, H))
draw = ImageDraw.Draw(img)

# Gradient from old (left) to new (right)
old_rgb = (74, 85, 104)    # muted slate
new_rgb = (0, 212, 255)    # electric cyan

for x in range(W):
    ratio = x / W
    r = int(old_rgb[0] + (new_rgb[0] - old_rgb[0]) * ratio)
    g = int(old_rgb[1] + (new_rgb[1] - old_rgb[1]) * ratio)
    b = int(old_rgb[2] + (new_rgb[2] - old_rgb[2]) * ratio)
    draw.line([(x, 0), (x, H)], fill=(r, g, b))

# Overlay text
try:
    title_font = ImageFont.truetype("/usr/share/fonts/truetype/dejavu/DejaVuSans-Bold.ttf", 72)
    sub_font = ImageFont.truetype("/usr/share/fonts/truetype/dejavu/DejaVuSans.ttf", 28)
except:
    title_font = ImageFont.load_default()
    sub_font = ImageFont.load_default()

# Title with shadow for readability
title = "Context Is The Multiplier"
bbox = draw.textbbox((0, 0), title, font=title_font)
text_w = bbox[2] - bbox[0]
x_pos = (W - text_w) // 2
y_pos = H // 2 - 40

# Shadow
draw.text((x_pos + 3, y_pos + 3), title, font=title_font, fill="#000000")
# Main text
draw.text((x_pos, y_pos), title, font=title_font, fill="#FFFFFF")

# Subtitle
subtitle = "From AI prompts to human teams"
bbox2 = draw.textbbox((0, 0), subtitle, font=sub_font)
sub_w = bbox2[2] - bbox2[0]
draw.text(((W - sub_w) // 2, y_pos + 90), subtitle, font=sub_font, fill="#FFFFFF")

img.save("/mnt/user-data/outputs/hero-gradient.png", "PNG")
```

### Template: Two Circles (Venn-style)

For posts about convergence or overlap between concepts.

```python
from PIL import Image, ImageDraw, ImageFont

W, H = 1600, 900

BG_COLOR = "#0F172A"     # deep navy
CIRCLE1 = "#EF4444"      # red (concept A)
CIRCLE2 = "#3B82F6"      # blue (concept B)
OVERLAP = "#8B5CF6"      # purple (synthesis)

img = Image.new("RGB", (W, H), color=BG_COLOR)
draw = ImageDraw.Draw(img)

# Two overlapping circles
circle_r = 280
c1_center = (W//2 - 140, H//2)
c2_center = (W//2 + 140, H//2)

# Draw with transparency simulation using multiple layers
# First circle
draw.ellipse([c1_center[0] - circle_r, c1_center[1] - circle_r,
              c1_center[0] + circle_r, c1_center[1] + circle_r], 
             fill=CIRCLE1, outline=None)

# Second circle (we'll blend manually)
draw.ellipse([c2_center[0] - circle_r, c2_center[1] - circle_r,
              c2_center[0] + circle_r, c2_center[1] + circle_r], 
             fill=CIRCLE2, outline=None)

# Labels
try:
    label_font = ImageFont.truetype("/usr/share/fonts/truetype/dejavu/DejaVuSans-Bold.ttf", 32)
    title_font = ImageFont.truetype("/usr/share/fonts/truetype/dejavu/DejaVuSans-Bold.ttf", 56)
except:
    label_font = ImageFont.load_default()
    title_font = ImageFont.load_default()

draw.text((c1_center[0] - 100, c1_center[1] - 20), "HUMANS", font=label_font, fill="#FFFFFF")
draw.text((c2_center[0] - 20, c2_center[1] - 20), "AI", font=label_font, fill="#FFFFFF")

# Title
title = "The Context Connection"
bbox = draw.textbbox((0, 0), title, font=title_font)
text_w = bbox[2] - bbox[0]
draw.text(((W - text_w) // 2, H - 100), title, font=title_font, fill="#FFFFFF")

img.save("/mnt/user-data/outputs/hero-venn.png", "PNG")
```

---

## Data Visualization Templates

### Template: Grouped Bar Chart

For comparing multiple metrics across two groups.

```python
import matplotlib.pyplot as plt
import numpy as np

# Data
metrics = ['Merge Rate', 'CI Success', 'Review Comments']
core_values = [85.8, 51.2, 3.6]
peripheral_values = [77.8, 43.1, 2.0]

x = np.arange(len(metrics))
width = 0.35

fig, ax = plt.subplots(figsize=(12, 7))
fig.patch.set_facecolor('#F8F9FA')
ax.set_facecolor('#F8F9FA')

bars1 = ax.bar(x - width/2, core_values, width, label='Core Developers', color='#00D4FF')
bars2 = ax.bar(x + width/2, peripheral_values, width, label='Peripheral Developers', color='#3D4F5F')

# Labels on bars
def add_labels(bars):
    for bar in bars:
        height = bar.get_height()
        ax.annotate(f'{height}',
                    xy=(bar.get_x() + bar.get_width() / 2, height),
                    xytext=(0, 3),
                    textcoords="offset points",
                    ha='center', va='bottom', fontsize=11, fontweight='bold')

add_labels(bars1)
add_labels(bars2)

ax.set_ylabel('Value', fontsize=12)
ax.set_title('Agent Collaboration Patterns by Developer Type', fontsize=16, fontweight='bold', pad=20)
ax.set_xticks(x)
ax.set_xticklabels(metrics, fontsize=11)
ax.legend(loc='upper right')
ax.spines['top'].set_visible(False)
ax.spines['right'].set_visible(False)

fig.text(0.99, 0.01, 'Source: GitHub Agentic PR Study (2024)', ha='right', fontsize=8, color='#666666')

plt.tight_layout()
plt.savefig('/mnt/user-data/outputs/data-grouped-bar.png', dpi=150, bbox_inches='tight')
```

### Template: Stacked Horizontal Bar (Category Breakdown)

For showing distribution across categories.

```python
import matplotlib.pyplot as plt
import numpy as np

# Data: PR purposes by developer type
categories = ['Bug Fix', 'Feature', 'Docs', 'Testing', 'Other']
core_pct = [22, 25, 28, 18, 7]
peripheral_pct = [26, 27, 20, 15, 12]

fig, ax = plt.subplots(figsize=(12, 5))
fig.patch.set_facecolor('#F8F9FA')
ax.set_facecolor('#F8F9FA')

y = np.array([0, 1])
height = 0.5

# Colors
colors = ['#EF4444', '#F59E0B', '#10B981', '#3B82F6', '#8B5CF6']

# Stacked bars
for i, (cat, c_val, p_val) in enumerate(zip(categories, core_pct, peripheral_pct)):
    left_core = sum(core_pct[:i])
    left_peripheral = sum(peripheral_pct[:i])
    ax.barh(1, c_val, height, left=left_core, color=colors[i], label=cat if i == 0 else "")
    ax.barh(0, p_val, height, left=left_peripheral, color=colors[i])

ax.set_yticks([0, 1])
ax.set_yticklabels(['Peripheral', 'Core'], fontsize=12)
ax.set_xlabel('Percentage of PRs', fontsize=12)
ax.set_title('Purpose of Agentic PRs by Developer Type', fontsize=16, fontweight='bold', pad=20)

# Legend
handles = [plt.Rectangle((0,0),1,1, color=c) for c in colors]
ax.legend(handles, categories, loc='upper right', bbox_to_anchor=(1.15, 1))

ax.spines['top'].set_visible(False)
ax.spines['right'].set_visible(False)

plt.tight_layout()
plt.savefig('/mnt/user-data/outputs/data-stacked-bar.png', dpi=150, bbox_inches='tight')
```

### Template: Simple Comparison Cards

For A vs B statistics displayed as visual cards.

```python
from PIL import Image, ImageDraw, ImageFont

W, H = 1200, 600

BG_COLOR = "#F8F9FA"
CARD_A = "#3D4F5F"
CARD_B = "#00D4FF"
TEXT_LIGHT = "#FFFFFF"
TEXT_DARK = "#1A202C"

img = Image.new("RGB", (W, H), color=BG_COLOR)
draw = ImageDraw.Draw(img)

# Card dimensions
card_w, card_h = 400, 300
margin = 100
y_pos = (H - card_h) // 2

# Card A (left)
x1 = margin
draw.rounded_rectangle([x1, y_pos, x1 + card_w, y_pos + card_h], radius=20, fill=CARD_A)

# Card B (right)  
x2 = W - margin - card_w
draw.rounded_rectangle([x2, y_pos, x2 + card_w, y_pos + card_h], radius=20, fill=CARD_B)

# VS badge in center
vs_x, vs_y = W // 2, H // 2
draw.ellipse([vs_x - 40, vs_y - 40, vs_x + 40, vs_y + 40], fill="#1A202C")

try:
    num_font = ImageFont.truetype("/usr/share/fonts/truetype/dejavu/DejaVuSans-Bold.ttf", 72)
    label_font = ImageFont.truetype("/usr/share/fonts/truetype/dejavu/DejaVuSans.ttf", 24)
    vs_font = ImageFont.truetype("/usr/share/fonts/truetype/dejavu/DejaVuSans-Bold.ttf", 28)
except:
    num_font = label_font = vs_font = ImageFont.load_default()

# Card A content
draw.text((x1 + 80, y_pos + 80), "11.2%", font=num_font, fill=TEXT_LIGHT)
draw.text((x1 + 60, y_pos + 180), "Core Dev CI Skip Rate", font=label_font, fill=TEXT_LIGHT)

# Card B content
draw.text((x2 + 80, y_pos + 80), "19.1%", font=num_font, fill=TEXT_DARK)
draw.text((x2 + 40, y_pos + 180), "Peripheral CI Skip Rate", font=label_font, fill=TEXT_DARK)

# VS text
draw.text((vs_x - 20, vs_y - 18), "VS", font=vs_font, fill=TEXT_LIGHT)

# Title
title_font = ImageFont.truetype("/usr/share/fonts/truetype/dejavu/DejaVuSans-Bold.ttf", 32)
title = "CI Check Discipline"
bbox = draw.textbbox((0, 0), title, font=title_font)
text_w = bbox[2] - bbox[0]
draw.text(((W - text_w) // 2, 30), title, font=title_font, fill=TEXT_DARK)

img.save("/mnt/user-data/outputs/data-comparison-cards.png", "PNG")
```

---

## Color Palette Reference

### Tech/AI Transformation
```python
PALETTE_AI = {
    "old": "#3D4F5F",      # muted slate
    "new": "#00D4FF",      # electric cyan
    "accent": "#8B5CF6",   # violet
    "bg_dark": "#1A1A2E",  # deep navy
    "bg_light": "#F8F9FA", # off-white
}
```

### Business/Strategy
```python
PALETTE_BUSINESS = {
    "old": "#78716C",      # warm gray
    "new": "#F59E0B",      # amber gold  
    "accent": "#10B981",   # emerald
    "bg_dark": "#292524",  # stone dark
    "bg_light": "#FFFBEB", # amber tint
}
```

### Process/Methodology
```python
PALETTE_PROCESS = {
    "old": "#6B7280",      # cool gray
    "new": "#14B8A6",      # teal
    "accent": "#F97316",   # orange
    "bg_dark": "#111827",  # gray-900
    "bg_light": "#F0FDFA", # teal tint
}
```

### Urgent/Provocative
```python
PALETTE_URGENT = {
    "old": "#1F2937",      # near black
    "new": "#EF4444",      # red
    "accent": "#FBBF24",   # yellow warning
    "bg_dark": "#0F0F0F",  # pure dark
    "bg_light": "#FEF2F2", # red tint
}
```

---

## Font Recommendations

System fonts available on most Linux systems:

```python
# Bold sans-serif (titles)
"/usr/share/fonts/truetype/dejavu/DejaVuSans-Bold.ttf"
"/usr/share/fonts/truetype/liberation/LiberationSans-Bold.ttf"

# Regular sans-serif (body/labels)
"/usr/share/fonts/truetype/dejavu/DejaVuSans.ttf"
"/usr/share/fonts/truetype/liberation/LiberationSans-Regular.ttf"

# Monospace (data/code)
"/usr/share/fonts/truetype/dejavu/DejaVuSansMono.ttf"
```

To check available fonts:
```bash
fc-list | grep -i truetype | head -20
```
