<div align="center">

# 🎓 EduFinder

**Explore India's top 100 NIRF-ranked universities, their courses, and indicative annual fees — all in one place.**

`Flask` · `Jinja2` · `Supabase (PostgreSQL)` · `Python`

</div>

---

## 📌 Overview

EduFinder is a web application that helps students discover and compare Indian universities.
Instead of hopping across dozens of websites and PDFs, a student can search, filter and sort
**100 top NIRF-ranked universities**, browse the **courses** each one offers, and see
**indicative annual fees** — from a single, clean interface.

- 🔎 **Search** by university name, city, state, or course
- 🗺️ **Filter** by any of 22 states
- 💰 **Budget slider** to cap results by annual fee
- ↕️ **Sort** by NIRF rank, rating, or fees (low→high / high→low)
- 📄 **Detail page** per university with a visual fee-comparison for every course

---

## 🖥️ Tech stack

| Layer | Technology | Role |
|-------|-----------|------|
| Frontend | HTML + Jinja2 + CSS | Server-rendered responsive card UI |
| Backend | Python + Flask | Routing, search / filter / sort, fee formatting |
| Data | Supabase (PostgreSQL) | `universities` ⋈ `courses` via foreign key |

No JavaScript framework required — all logic lives in Python.

---

## 📂 Project structure

```
edufinder/
├── app.py              # Flask backend — routes + search/filter/sort logic
├── data.py             # 100 universities + 493 courses (indicative fees)
├── static/
│   ├── logo.svg        # header logo (book + search lens)
│   └── icon.svg        # favicon / app icon
└── templates/
    ├── index.html      # home: search, state filter, fee slider, sort, cards
    └── university.html # detail page: courses + fee-comparison bars
```

---

## 🚀 Getting started

```bash
# 1. install the one dependency
pip install flask

# 2. run the app
python app.py

# 3. open in your browser
http://localhost:5000
```

That's it — the dataset ships inside `data.py`, so no database setup is needed to demo.

---

## 🗃️ Data notes

- **Rankings:** NIRF 2025 for the top 10; NIRF 2024 for ranks 11–100.
- **Fees:** shown figures are **indicative annual fees** (General category) for
  representative flagship courses — **not** an exhaustive list of every degree, and
  **not** official quotes. Always verify exact, current fees on each university's
  official website before applying.
- **Coverage:** 100 universities · 493 courses · 22 states · 61 cities.

---

## 🔌 Connecting to Supabase (later)

The app reads from `UNIVERSITIES` in `data.py`. To go live, replace that import with a
query result from your PostgreSQL/Supabase instance, keeping the same shape:

```python
# each university object:
{
  "id": 1,
  "name": "Indian Institute of Science, Bangalore",
  "location": "Bengaluru",
  "state": "Karnataka",
  "rating": 4.9,
  "nirf_rank": 1,
  "courses": [
    {"course_name": "B.Tech (Mathematics & Computing)", "annual_fee": 230000},
    ...
  ]
}
```

A single SQL `LEFT JOIN` between `universities` and `courses`, aggregated into a JSON
array per university, produces exactly this structure.

---

## 🛣️ Roadmap

- [x] MVP: 100 universities, search / filter / sort, detail pages
- [ ] Verified, category-wise fees with official-source links
- [ ] Side-by-side comparison & shortlists
- [ ] Student reviews, cut-offs & admission deadlines

---

## 👤 Author

**Manthan** — B.Tech, Sharda University

<div align="center">

*EduFinder — find your university.*

</div>
