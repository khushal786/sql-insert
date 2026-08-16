# Insert Trace

A single-file, zero-dependency web tool for working with SQL `INSERT` statements — in both directions.

Ever pasted a 50-column `INSERT` and lost track of which value belongs to which column? Or needed to hand-write an insert for a wide table and dreaded typing out every column name? Insert Trace solves both.

> Everything runs client-side in the browser. No data is sent anywhere — safe to paste real production rows into it.

---

## Features

**Trace mode — SQL → table**
- Paste any `INSERT INTO table (...) VALUES (...)` and see every column wired to its value, side by side
- Handles bulk inserts (multiple `VALUES` rows) and multiple statements in one paste
- Correctly parses quoted strings containing commas, nested function calls (`NOW()`, `CONCAT(a,b)`), and escaped quotes
- Flags column/value count mismatches so you can catch a stray comma before it bites you
- Color-coded by type (string, number, boolean, `NULL`, expression) for a fast visual scan
- Copy any single value, or the whole row as JSON

**Build mode — table → SQL**
- Import an existing sample `INSERT` to auto-populate all columns and starting values — no manually typing out 50 column names
- Free hand to edit any value, per column, with an explicit type selector (String / Number / Boolean / NULL / Raw-Expression)
- Add multiple rows for a bulk insert, or duplicate a row to tweak just a couple of fields
- **Dialect-aware output** — PostgreSQL, MySQL, SQL Server, and Oracle handle booleans, timestamps, and identifier quoting differently; pick your engine and the generated SQL adjusts automatically
- One-click "Open in Trace" to sanity-check the SQL you just built before running it

---

## Usage

1. Open `insert-trace.html` in any modern browser — no install, no server, no build step
2. **To trace an existing insert:** switch to *Trace SQL → table*, paste your statement, hit **Trace columns**
3. **To build a new insert:** switch to *Build table → SQL*
   - Paste a sample `INSERT` in the import box and hit **Import columns & values**, *or* add columns manually
   - Pick your database dialect
   - Edit values, add rows as needed
   - Hit **Generate INSERT** and copy the result

## Tech stack

Plain HTML, CSS, and vanilla JavaScript. No frameworks, no build tooling, no external runtime dependencies (only a Google Fonts import for typography). The whole app is one `.html` file, so it's trivially portable — clone it, open it, use it.

## Running it

```bash
git clone https://github.com/<your-username>/insert-trace.git
cd insert-trace
open insert-trace.html   # or just double-click the file
```

Or publish it for free via **GitHub Pages**: Settings → Pages → deploy from the `main` branch, and the tool is live at `https://<your-username>.github.io/insert-trace/`.

## Roadmap ideas

- [ ] Import columns from a pasted `CREATE TABLE` statement
- [ ] CSV / JSON import for bulk row building
- [ ] `UPDATE` statement tracing, not just `INSERT`
- [ ] Dark/light theme toggle

Contributions and issues welcome.

## License

MIT © Khushal
