# U2 L09 — Reflection: What Makes Data Real?

**LO:** distinguish synthetic from real data; articulate a provenance statement for any dataset; practice the provenance checklist on the student performance dataset.

**Estimated time:** 70 minutes.

---

## PART 1 — OPENING QUESTION (10 min)

Before any code, answer in your notes:

**What is the difference between a dataset that describes real people and one that was generated to *look like* it describes real people?**

Write your answer. We will discuss. The distinction is not about file format — it is about **provenance**.

---

## PART 2 — THE STUDENT PERFORMANCE DATASET (20 min)

Open your data-lab repo and load the data:

```bash
cd ~/compmath-u2-data-lab
python3 -c "
import csv
with open('data/u2_student_performance_data.csv', newline='') as f:
    lines = [ln for ln in f if ln.strip() and not ln.startswith('#')]
    reader = csv.DictReader(lines)
    rows = list(reader)
print(f'Rows: {len(rows)}')
print(f'Columns: {reader.fieldnames}')
print(f'Sample row: {rows[0]}')
"
```

This dataset has **1,000 rows** of synthetic student records. It was generated with:
- **Seed:** 20261027
- **Library:** Python Faker
- **Columns:** Student_ID, Math Score, English Score, Science Score, Overall GPA, Hours Studied Per Week, Absence Rate, Extracurricular Activities, Parent Education Level

**In your notes:** What does "synthetic" mean here? Can you treat these correlations as real findings about students?

---
