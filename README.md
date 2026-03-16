# Final-Project-1st-YR-2nd-Sem
[![Maintenance](https://img.shields.io/badge/Maintained%3F-Yes-green.svg)](https://GitHub.com/Naereen/StrapDown.js/graphs/commit-activity)
![Generic badge](https://img.shields.io/badge/Development%3f-Ongoing-green.svg)
![Developer](https://img.shields.io/badge/Developer-ChristianJude23-blue)
![Developer](https://img.shields.io/badge/Developer-owenlim225-blue)

### Project: Pera Ko – Money Tracker App

**Pera Ko** is a desktop expense tracker built with Python `tkinter` that helps users log daily incomes and expenses, visualize their cash flow, and maintain an up‑to‑date running balance. The app uses a local SQLite database to persist entries and provides a custom‑designed GUI generated from Figma via Tkinter Designer.

---

### Key Features

- **Daily expense & income logging**: Add transactions for the currently selected date, with a category (`Income` or `Expense`), name/description, and amount.
- **Per‑day view**: Navigate between days using previous/next date buttons and see only that day’s entries in the main table.
- **Automatic totals**:
  - **Expenses** and **Income** totals for the selected date.
  - **Overall balance** across all dates (total income minus total expenses) shown in the top bar.
- **Inline editing tools**:
  - Update or remove existing entries by ID through a dedicated edit window.
  - Clear **all** data (with confirmation) from the database when needed.
- **Built‑in utilities**:
  - **Calculator** (`Calculator` window) for quick arithmetic.
  - **Currency converter** (`CurrencyConverter` window) with predefined exchange rates.
- **Polished UI**:
  - Custom assets and layout from Figma (via Tkinter Designer).
  - Styled `ttk.Treeview` with color‑coded income (green) and expense (red) rows.
  - Loading screen and sidebar menu with project team, about, and exit options.

---

### Tech Stack

- **Language**: Python 3
- **GUI Framework**: `tkinter`, `ttk`
- **Database**: SQLite (file `finance.db` created beside the Python files)
- **Supporting Libraries**:
  - `Pillow` (`PIL`) for image handling in the “Project Team” window
  - `idlelib.tooltip.Hovertip` for button tooltips

---

### Project Structure (Core Files)

- `gui.py` – Main application:
  - `LoadingScreen` and `MyApp` classes
  - Main window layout, widgets, and event wiring
  - Integration with `function_list.py`, `db.py`, `calc.py`, and `currency_conv.py`
- `db.py` – Data layer:
  - Creates `finance.db` and `entries` table on first run
  - CRUD helpers: load entries, insert, update, delete single row, delete all, compute total balance
- `function_list.py` – Application logic for `MyApp`:
  - Add‑entry popup and validation
  - Date navigation and per‑day loading
  - Income/expense/total balance calculations and label updates
  - Edit/remove dialogs and handlers
- `calc.py` – Standalone calculator window (`Calculator` class).
- `currency_conv.py` – Standalone currency converter window (`CurrencyConverter` class) with hard‑coded exchange rates.

Backup versions of some modules are stored under `backup/` for reference.

---

### Data Model

The app uses a single SQLite table `entries`:

- `date` – `DATE`: user‑selected date (displayed as `Month DD, YYYY` in the UI)
- `id` – `INTEGER PRIMARY KEY`: unique row identifier (also used in edit/remove dialogs)
- `category` – `TEXT`: `"Income"` or `"Expense"`
- `name` – `TEXT`: short description of the entry
- `amount` – `REAL`: positive numeric value (sign is inferred from `category`)

Totals:

- **Per‑day** totals are computed in `function_list.py` and shown in the top bar.
- **Global balance** is computed in `db.total_amount()` as total income minus total expenses over all rows.

---

### How to Run the Project

- **Prerequisites**
  - Python 3 installed and on your PATH.
  - Recommended Python packages:
    - `Pillow`

- **Steps**
  - Clone or download this repository.
  - (Optional) Create and activate a virtual environment.
  - Install dependencies:
    - `pip install pillow`
  - Run the main GUI:
    - `python gui.py`

On first launch, `finance.db` will be created automatically in the project directory.

---

### Basic Usage

- **Adding a transaction**
  - Open the app (`gui.py`).
  - Ensure the correct date is shown (use `<` and `>` date buttons if needed).
  - Click the **Add** button on the right.
  - In the popup:
    - Choose `Income` or `Expense`.
    - Enter a name/description.
    - Enter an amount (numeric).
  - Click **Add** to save and refresh the table and totals.

- **Editing or removing a transaction**
  - Click the **Edit** button on the right.
  - In the options window, choose **Update** or **Remove**.
  - For **Update**:
    - Enter the `ID` for the current date, update the fields, and click **Update**.
  - For **Remove**:
    - Enter the `ID` and click **Remove**.

- **Clearing all data**
  - Open the sidebar menu (bottom‑left).
  - Click **Clear Data** and confirm. This deletes all rows from `entries`.

---

### Known Limitations / Notes

- Exchange rates in `currency_conv.py` are **hard‑coded** (as of May 10, 2024) and not updated dynamically.
- All data is stored locally in `finance.db`; there is no cloud sync or multi‑device support.
- Input validation is focused on basic numeric and text checks; there is no advanced error handling for corrupted databases.

---

### Snapshots

![image](https://github.com/owenlim225/Money-Tracker-App-1/assets/87555304/f00fb541-001b-4358-91fc-6ed9bda43e2f)

![image](https://github.com/owenlim225/Money-Tracker-App-1/assets/87555304/19d5e2e9-7610-4694-b582-e63db927386f)

![image](https://github.com/owenlim225/Money-Tracker-App-1/assets/87555304/dc30fcaa-f0af-4d90-a291-4a0c34d80fa8)

![image](https://github.com/owenlim225/Money-Tracker-App-1/assets/87555304/aff28859-2499-4098-9804-2428153c58ff)

![image](https://github.com/owenlim225/Money-Tracker-App-1/assets/87555304/2930e2d6-6c17-4c93-bbc2-dd4605e1cf64)

![image](https://github.com/owenlim225/Money-Tracker-App-1/assets/87555304/010a1330-86be-4123-9367-026689a56be8)

<img src="https://github.com/SAWARATSUKI/ServiceLogos/blob/main/Python/Python.png" alt="" width=300>
Ctto: https://github.com/ParthJadhav/Tkinter-Designer/blob/master/docs/instructions.md
