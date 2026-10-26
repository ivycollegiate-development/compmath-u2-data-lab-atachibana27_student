# U2 L10 — Scatter Plots and Relationships

**LO:** create scatter plots to explore relationships between two numeric variables; interpret direction, form, and strength; articulate why correlation ≠ causation.

**Estimated time:** 85 minutes.

---

## PART 0 — SETUP (5 min)

```bash
cd ~/compmath-u2-data-lab
git pull
```

---

## PART 1 — SCATTER PLOT BASICS (15 min)

A scatter plot shows the relationship between **two numeric columns**. Each point = one row.

```python
import csv
import matplotlib.pyplot as plt

with open("data/u2_student_performance_data.csv", newline="") as f:
    lines = [ln for ln in f if ln.strip() and not ln.startswith("#")]
    reader = csv.DictReader(lines)
    rows = list(reader)

study = [float(r["Hours Studied Per Week"]) for r in rows]
gpa = [float(r["Overall GPA"]) for r in rows]

plt.figure()
plt.scatter(study, gpa, s=10, alpha=0.4, color="steelblue")
plt.title("Study Hours vs GPA — Positive Association")
plt.xlabel("Hours Studied Per Week")
plt.ylabel("Overall GPA")
plt.grid(True, alpha=0.3)
plt.savefig("scatter_study_gpa.png", dpi=150, bbox_inches="tight")
```

**Run it and open the image.** What do you see?

---

## PART 2 — VOCABULARY: DIRECTION, FORM, STRENGTH (15 min)

In your notes, define each using your scatter plot:

| Term | Definition | Your Plot |
|------|------------|-----------|
| **Direction** | Positive (↗), Negative (↘), or None (flat fuzz) | |
| **Form** | Linear, curved, clustered, or no pattern | |
| **Strength** | Tight cloud = strong; diffuse = weak | |

**Key rule:** Scatter plots only show **association**, not causation.

---
