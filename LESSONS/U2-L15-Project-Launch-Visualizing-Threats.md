# U2 L15 — Project Launch: Visualizing Threats

**LO:** launch the Unit 2 project — load the campus threat dataset, design a cleaning pipeline, and plan three required visualizations for a specific audience.

**Estimated time:** 85 minutes.

---

## PART 0 — SETUP (5 min)

```bash
cd ~/compmath-u2-data-lab
git pull
```

---

## PART 1 — MEET THE PROJECT DATA (15 min)

The Unit 2 project uses `u2_campus_threat_daily.csv` — 60 days of synthetic campus network threat data.

```bash
head -10 data/u2_campus_threat_daily.csv
```

Columns:
- `date` — YYYY-MM-DD
- `phishing_reports` — count of reported phishing emails
- `failed_logins` — count of failed login attempts
- `login_success_rate` — fraction (0.0–1.0)
- `malware_blocks` — count of blocked malware downloads
- `vpn_connections` — count of VPN sessions
- `wifi_devices` — count of unique WiFi clients

**In your notes:** Which columns are counts? Which is a rate? Which is a date?

---

## PART 2 — BUILD YOUR CLEANING PIPELINE (30 min)

Create `clean_threats.py` modeled on your `clean_data.py` from L11.

**Your pipeline must:**
1. Load the CSV (this one has NO comment lines — but verify)
2. Parse `date` strings into `datetime.date` objects (use `datetime.strptime`)
3. Apply sanity bounds:
   - Counts (`phishing_reports`, `failed_logins`, `malware_blocks`, `vpn_connections`, `wifi_devices`) ≥ 0
   - `login_success_rate`: 0.0–1.0
   - Dates: chronological, no duplicates, no gaps > 1 day
4. Track every dropped row with reason
5. Write to `data/u2_campus_threat_clean.csv`
6. Print audit summary: original/cleaned/dropped counts by reason

**Date parsing pattern:**

```python
from datetime import datetime

def parse_date(s):
    try:
        return datetime.strptime(s.strip(), "%Y-%m-%d").date()
    except (ValueError, AttributeError):
        return None
```

**Gap detection:**

```python
dates = [parse_date(r["date"]) for r in rows if parse_date(r["date"])]
dates.sort()
for i in range(1, len(dates)):
    if (dates[i] - dates[i-1]).days > 1:
        print(f"Gap: {dates[i-1]} to {dates[i]}")
```

---
