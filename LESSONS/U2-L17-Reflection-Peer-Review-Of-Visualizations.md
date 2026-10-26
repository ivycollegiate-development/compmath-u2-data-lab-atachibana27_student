# U2 L17 — Reflection: Peer Review of Visualizations

**LO:** give and receive feedback on visualizations — clarity, honesty, impact; revise from feedback.

**Estimated time:** 85 minutes.

---

## PART 1 — WHAT MAKES A CHART GOOD? (15 min)

Before you score anyone, agree on the standard. In your notes, answer:

**What is the difference between a chart that is *unclear* and one that is *dishonest*?**

**Expected:** Unclear = the audience cannot figure out what the chart says (missing labels, confusing encoding, jargon). Dishonest = the chart *appears* clear but leads the audience to a wrong conclusion (truncated axis, hidden data gaps, selective highlighting). One is a mistake; the other is a lie.

**Name one way a chart can be technically correct but still mislead its audience — think about the three-audience exercise from U2 L14.**

**Expected (examples):** Truncating the y-axis to exaggerate a small trend; plotting two series on different y-axes without labeling it; showing a 3-day spike as "the trend" while hiding 60 days of flat data; using area encoding for 1D data.

**We will use three scoring dimensions all day, each 1–5:**

| Dimension | 5 means... |
| --- | --- |
| **Clarity** | I understood the chart with no explanation: title, labels, legend all do their job. The audience never has to guess. |
| **Honesty** | The chart says exactly what the data says — no dropped context, no inflated axes, no hidden gaps. Y-axis starts at 0 (or states why not). Missing data is acknowledged. |
| **Impact** | The one thing the audience should notice jumps out immediately. The chart has a *point*, not just data. |

**Write these definitions in your notes** — you will reference them for every score.

---

## PART 2 — STRUCTURED SWAP (30 min)

Get your partner's repo link (their GitHub URL from yesterday's PR). Clone or read it on github.com, then review **all three** required charts.

**For each chart, fill out the feedback form in your notes:**

```
Chart: [timeline / weekday / histogram] (circle one)
Clarity: 1 2 3 4 5 — because: ________________________________________
Honesty: 1 2 3 4 5 — because: ________________________________________
Impact:  1 2 3 4 5 — because: ________________________________________
One suggestion — specific and actionable:
______________________________________________________________________________
```

**Examples of specific suggestions:**
- "Add `bbox_to_anchor=(1.05, 1), loc='upper left'` to move legend outside plot area"
- "Add `plt.tight_layout()` to prevent label clipping"
- "Y-axis on bar chart starts at 42 — must start at 0 or explain why"
- "Histogram uses 100 bins — too noisy; try 20"

**Rules of review:**
- Be specific. "Make it better" is not feedback.
- Reference the three dimensions by name.
- If you cannot read a label, that is a clarity score of 1.

Then swap roles. You will each give and receive a full review.

---
