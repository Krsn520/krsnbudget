# Budget Tracker

A personal finance tracker that runs entirely in your browser. No accounts, no servers — all data is saved locally on your device.

---

## Getting Started

Open `index.html` in any modern browser. On your first visit, a short setup walkthrough will guide you through creating a category, a matching rule, and your first transaction. You can skip any step and come back to it later.

---

## Core Concepts

**Categories & Subcategories** — Every transaction belongs to a category (e.g. *Utilities*) and a subcategory (e.g. *Phone Bill*). You define these yourself in the Edit tab.

**Transaction Types** — Each transaction is classified as one of:
- **Expense** — reduces your balance (stored as a negative amount)
- **Income** — increases your balance (stored as a positive amount)
- **Not Reported** — excluded from all totals and charts (useful for transfers, adjustments, etc.)

---

## Adding Transactions

Click **+ Add** to open the transaction form. Fill in the type, description, amount, date, category, and an optional note. The app will warn you if a duplicate entry is detected (same description, amount, and date).

---

## Importing Bank Statements

Click **↑ Import** to import a `.xlsx`, `.xls`, or `.csv` file exported from your bank.

1. **Select your account type** — Chequing, Savings, or Credit Card. Credit card imports treat all charges as expenses automatically.
2. **Map your columns** — The app attempts to auto-detect which columns contain the date, amount, and description. You can override any of these using the dropdowns.
3. **Set the data start row** — If your file has a header row, the app detects this automatically. Adjust if needed.
4. **Review the preview** — A colour-coded spreadsheet preview shows exactly which rows and columns will be imported.
5. **Import** — Duplicate transactions (matched by date, amount, and description) are silently skipped. Any transactions that don't match an existing rule are sent to the **Unmatched Review** queue.

### Unmatched Review

After import, unmatched transactions appear one at a time for manual categorisation. For each one you can assign a category and subcategory, optionally save a rule so the same description is auto-categorised on future imports, and choose whether to remember that rule for similar patterns.

---

## Description Rules

Rules automatically categorise transactions based on their description. Go to **⚙ Edit → Description Rules** to manage them.

Each rule has:
- **Pattern** — a plain-text or regex string matched against the transaction description (case-insensitive)
- **Category / Subcategory** — where to file matching transactions
- **Type** — Auto (income if positive, expense if negative), Force Income, Force Expense, or Not Reported

Rules are tested in order — the first match wins. Drag the handle on the left of any rule to reorder them.

### Re-Run Rules

The **▶ Re-run Rules** button (in the Description Rules card header) applies your current rules retroactively to any transaction still categorised as *Not Assigned*. Useful after adding new rules to clean up previously unmatched imports.

### Creating a Rule from a Transaction

In any transaction list, click the **✦** button on a row to open a rule-creation dialog pre-filled with that transaction's description. Pattern suggestions (broad, medium, exact) are offered automatically.

---

## Editing & Deleting Transactions

Click any transaction row to open the edit modal. You can change the description, amount, date, type, category, subcategory, and note. To delete, use the **Delete** button inside the edit modal, or the **×** button directly on the row.

Deleting a transaction shows a brief **Undo** toast at the bottom of the screen. Click it within a few seconds to restore the transaction.

---

## Transactions Tab

The main transaction list with filtering and search:

- **Type filter** — show All, Expenses, Income, or Not Reported
- **Search** — filters by description, category, or note
- **Amount range** — filter by minimum and/or maximum absolute amount
- **Pagination** — transactions are paginated; navigate with the arrow buttons or page number pills

The header stats bar shows total income, total expenses, and net balance for the filtered view.

---

## Monthly View

Navigate month-by-month using the arrow buttons or the month/year dropdowns.

- **Stat cards** — transaction count, average expense, savings rate, and budget utilisation for the selected month
- **Income vs Expenses bar chart** — a 12-month rolling chart showing income and expenses side by side
- **Expenses by Category pie chart** — breakdown of spending by category for the month
- **Income by Category pie chart** — breakdown of income sources for the month
- **Expense Breakdown** — a detailed bar-chart breakdown by category and subcategory, with budget targets shown where set
- **Monthly transaction list** — all transactions for the selected month, sorted by date

---

## Categories & Subcategories

Go to **⚙ Edit → Categories & Subcategories** to manage your taxonomy.

- **Add** new entries using the form at the bottom — set a category, subcategory, type, and optional monthly budget
- **Edit** any entry inline by clicking on it
- **Reorder** entries by dragging the grip handle on the left
- **Delete** individual entries with the × button, or remove an entire category group at once with the × next to the category header
- When deleting a category that has transactions, you'll be prompted to reassign those transactions to a different category
- **↺ Reset to defaults** restores the built-in category set (with a confirmation prompt)

---

## Backup & Restore

In the app footer:

- **↓ CSV** — exports all transactions as a `.csv` file for use in Excel or other tools
- **↓ Backup** — exports a full `.json` backup including transactions, categories, and rules
- **↑ Restore** — imports a `.json` backup file, merging or replacing your current data (with a confirmation prompt)

---

## Data Storage

All data is saved in your browser's `localStorage` — it stays on your device and is never sent anywhere. Each browser and device has its own independent copy. Clearing your browser's site data will erase your tracker data, so use **↓ Backup** regularly to keep a copy.

---
