# 📊 DYDX Sales Report Generator

![Python](https://img.shields.io/badge/Python-3.x-3776AB?logo=python&logoColor=white)
![Tkinter](https://img.shields.io/badge/GUI-Tkinter-2b5b84)
![SQLite](https://img.shields.io/badge/database-SQLite-003B57?logo=sqlite&logoColor=white)
![Matplotlib](https://img.shields.io/badge/charts-Matplotlib-11557c)

> A desktop sales-reporting tool for small businesses. Enter or import item sales, get **total sales, profit/deficit and ROI** worked out instantly, chart the results, and keep every report in a **SQLite** database for later.

## ✨ Features

**📝 Report builder**
- Data-entry form for item code, name, selling price, quantity and unit cost.
- Each row is calculated automatically: total sales, total cost and **profit/deficit**, shown in Malaysian Ringgit (`RM`).
- Live summary panel with **Total Sales**, **Total Profit/Deficit** and **ROI** = profit ÷ cost × 100%.
- **Search**, **modify** and **delete** items, or clear the whole table.
- **Bulk import from a text file**, with checks on every line (field count, numeric quantity, price format) and clear error messages.

**📈 Visualisation**
- **Generate Graph** plots profit/deficit for each item, with a zero line so loss-making items stand out at once.

**🗄️ Persistence & history**
- **Save Report** stores the salesperson, date, totals and every line item in SQLite.
- The **History** screen lists past reports. You can open one, delete it, or **transfer** its data back into the editor to reuse it.
- Your unsaved work is kept when you close the app and restored next time.

**🔐 Access**
- Login screen in front of the main menu. Demo login: `admin` / `123`.

## 🗃️ Database design

```text
reports                      report_entries                  temp_table
───────────────────          ────────────────────────        ─────────────────────
id (PK)                 ┌──< report_id (FK)                  unsaved working data
sales_person            │    item_code, item_name            (restored on start-up)
report_date             │    selling_price, quantity
total_sales_amount      │    total, cost
total_profit_deficit    │    profit_deficit
roi                ─────┘
```

## 🚀 Getting started

```bash
git clone https://github.com/kfahchai-netizen/DYDX-Sales-Report-Generator.git
cd DYDX-Sales-Report-Generator
pip install matplotlib
python sign_menu.py
```

Sign in with **admin / 123**, then click **Generate Report**.

### Import format

Use one item per line: `code,name,selling price,quantity,unit cost`. There's a sample in `load_data_from_txt_file_sample.txt`:

```text
001,Pen,RM 2.00,50,RM 1.00
```

## 📁 Project structure

```
├── sign_menu.py   # ▶ Entry point: login, main menu, report history window
├── table.py       # Report editor: data entry, search, import, summary, save
├── database.py    # SQLite schema and CRUD helpers
├── graph.py       # Matplotlib profit/deficit chart
├── utils.py       # Price formatting, profit calculation, date validation
└── sales_report.db
```

## 📚 Key concepts

CRUD operations · Relational database design (one-to-many) · Input validation · Separating data, logic and UI layers · Data visualisation · Desktop GUI development

---

<sub>Made by **Kean Fah Chai** · Swinburne University of Technology Sarawak</sub>
