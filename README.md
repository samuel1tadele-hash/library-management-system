# Library Management System (LMS)

A web-based library circulation platform with **real SQL, database triggers, transactional integrity, and automated business rules** — running entirely in the browser.

**[View live demo →](https://samuel1tadele-hash.github.io/library-management-system/)**

---

## What it does

LMS is a complete circulation desk application for a small-to-medium library:

- **Dashboard** — circulation stats, overdue alerts, most-borrowed titles, recent activity
- **Circulation** — issue and return books with real-time rule enforcement
- **Catalog** — full book management with search and category filters
- **Members** — member registration, borrowing history, fines tracking
- **Loans** — complete loan history with filters for active, overdue, and returned
- **Reservations** — FIFO queue for books with all copies on loan
- **Reports** — overdue report, popular titles, member activity, and a live SQL console
- **Role-based access** — admin, librarian, and viewer roles with distinct permissions

---

## Why SQL.js?

Most library management side projects use an array of JavaScript objects and call it a "database." That doesn't demonstrate any real database engineering.

This project uses **[SQL.js](https://sql.js.org/)** — SQLite compiled to WebAssembly — which means **the exact same SQL you'd write against MySQL or PostgreSQL runs here**, in the browser. The schema uses:

- **Five normalized tables** with foreign keys and `CHECK` constraints
- **Two SQLite triggers** that maintain inventory counts automatically
- **Transactions** (`BEGIN` / `COMMIT` / `ROLLBACK`) for every circulation operation
- **Date arithmetic in SQL** — `julianday()` — for overdue and fine calculations
- **Aggregate queries** with `GROUP BY`, `HAVING`, and conditional `SUM`

The entire database persists to `localStorage` as a SQLite binary file, so data survives page reloads.

---

## Tech stack

| Layer | Technology |
|---|---|
| Markup + Styling | HTML5, Tailwind CSS |
| Logic | Vanilla JavaScript (ES2020+) |
| Database | SQLite via SQL.js (WebAssembly) |
| Auth | SHA-256 hashing via Web Crypto API |
| Persistence | Browser localStorage (SQLite binary) |

No build step. No npm. No framework. Open `index.html` and it works.

---

