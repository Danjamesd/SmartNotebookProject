---
banner: "![[IMG-20251006-WA0018.jpg]]"
banner_x: 0.5
---
```python
import matplotlib.pyplot as plt
import matplotlib.patches as mpatches
import matplotlib.style as style
style.use('seaborn-v0_8')

# Define months and phases
months = [f"Month {i}" for i in range(1, 13)]
phases = {
    "Foundations": (0, 3),
    "Core Skills": (3, 6),
    "Integration": (6, 9),
    "Production Prep": (9, 12)
}

# Skill development timelines (start, end)
skills = {
    "Math": (0, 6),
    "Machine Learning": (1, 11),
    "Computer Vision": (4, 9),
    "Embedded Systems": (2, 11),
    "Electronics": (1, 11),
    "App Development": (8, 12)
}

colors = {
    "Math": "#1f77b4",
    "Machine Learning": "#ff7f0e",
    "Computer Vision": "#2ca02c",
    "Embedded Systems": "#d62728",
    "Electronics": "#9467bd",
    "App Development": "#8c564b"
}

fig, ax = plt.subplots(figsize=(14, 6))

# Draw phase background blocks
for phase, (start, end) in phases.items():
    ax.axvspan(start, end, color='lightgrey', alpha=0.3)
    ax.text((start + end) / 2 - 0.5, len(skills) + 0.5, phase, fontsize=12, weight='bold', ha='center')

# Plot skill bars
for i, (skill, (start, end)) in enumerate(skills.items()):
    ax.barh(i, end - start, left=start, color=colors[skill], edgecolor='black')

# Formatting
ax.set_yticks(range(len(skills)))
ax.set_yticklabels(list(skills.keys()), fontsize=11)
ax.set_xticks(range(12))
ax.set_xticklabels(months, rotation=45, fontsize=10)
ax.set_xlim(0, 12)
ax.set_title("12-Month Smart Pen Development Timeline", fontsize=14, weight='bold')
ax.grid(axis='x', linestyle='--', alpha=0.5)

# Legend
patches = [mpatches.Patch(color=color, label=skill) for skill, color in colors.items()]
ax.legend(handles=patches, bbox_to_anchor=(1.05, 1), loc='upper left')

plt.tight_layout()
plt.savefig("/mnt/data/smart_pen_gantt_timeline.png")
plt.close()```

[1]: [[Session plan]]
[^2]: [[Gnatt Timeline + code]]
[^3]: [[12 month Timeline]]
[^4]: [[Skills Needed]]



#ml