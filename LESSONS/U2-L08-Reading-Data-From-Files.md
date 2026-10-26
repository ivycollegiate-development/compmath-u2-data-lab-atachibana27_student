# U2 L08 — Reading Data From Files

**LO:** load a CSV file with `csv.DictReader`, handle real-world quirks (comment lines, blank rows), and convert string values to numbers for computation.

**Estimated time:** 85 minutes.

---

## PART 0 — SETUP (10 min)

First command, always:

```bash
pwd
cd ~
git pull
```

Then open your data-lab repo and pull anything new:

```bash
cd ~/compmath-u2-data-lab
git pull
```

---

## PART 1 — THE COMMENT-LINE TRAP (15 min)

Open `data/u2_student_performance_data.csv` and look at the first few lines:

```bash
head -6 data/u2_student_performance_data.csv
```

You will see:
- Line 1: a `#` comment explaining the dataset
- Line 2: a blank line
- Line 3: the real header row

If you pass this file directly to `csv.DictReader`, the comment line becomes your header, and every column name is wrong. The fix is to filter the lines **before** they reach the reader:

```python
with open("data/u2_student_performance_data.csv", newline="") as f:
    lines = [ln for ln in f if ln.strip() and not ln.startswith("#")]
    reader = csv.DictReader(lines)
    rows = list(reader)
```

**In your notes:** why does `ln.strip()` remove the blank line? What would `ln.startswith("#")` catch?

---

## PART 2 — STRINGS ARE NOT NUMBERS (20 min)

Every value from `csv.DictReader` is a **string**. You must convert before doing math:

```python
math_scores = [float(r["Math Score"]) for r in rows]
print(f"Mean: {statistics.mean(math_scores):.1f}")
print(f"Median: {statistics.median(math_scores):.1f}")
```

**Key insight:** `"85" > "90"` is `True` in string comparison (lexicographic), but `85 > 90` is `False` numerically. Always convert.

---
