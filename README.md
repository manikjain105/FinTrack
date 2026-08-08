# FinTrack

> A local-first personal finance application designed to make expense tracking simple, fast, and insightful.

---

## Overview

FinTrack helps users manage their personal finances through an intuitive interface for tracking transactions, setting budgets, analyzing spending patterns, and generating financial reports.

The application is designed around a **local-first** philosophy, ensuring users retain ownership of their financial data while benefiting from a responsive and reliable experience.

---

## Features

* 📊 Interactive financial dashboard
* 💳 Transaction management
* 🎯 Monthly and category budgets
* 📈 Spending analytics
* 📄 Financial reports
* 🔍 Search and filtering
* 📥 Import transactions
* 📤 Export reports
* ⚡ Natural-language transaction entry
* 🔒 Local-first data storage

---

## Technology Stack

| Layer           | Technology         |
| --------------- | ------------------ |
| Frontend        | React + TypeScript |
| Styling         | Tailwind CSS       |
| Build Tool      | Vite               |
| Charts          | Recharts           |
| Backend         | Python             |
| API             | FastAPI            |
| Database        | SQLite             |
| ORM             | SQLAlchemy         |
| Validation      | Pydantic           |
| Package Manager | npm + pip          |
| Hosting         | Vercel (frontend)  |

---

## Project Structure

```text
FinTrack/
├── handbook/
├── frontend/
├── backend/
├── database/
├── tests/
└── docs/
```

The complete project specification is maintained in the `handbook/` directory.

---

## Handbook

The handbook is the single source of truth for the project.

It contains:

* Foundation
* Design System
* Product Specifications
* Engineering Documentation

All implementation should follow the guidance defined in the handbook.

---

## Getting Started

### Prerequisites

* Node.js
* Python
* Git

### Installation

```bash
git clone <repository-url>
cd FinTrack
```

Frontend:

```bash
cd frontend
npm install
```

Backend:

```bash
cd backend
pip install -r requirements.txt
```

Run the application using the project-specific development commands.

---

## Development Principles

When contributing:

* Follow the handbook.
* Keep changes small and focused.
* Maintain consistency with the Design System.
* Update documentation when behavior changes.
* Add tests for significant functionality.

---

## Roadmap

Version 1 focuses on:

* Transaction management
* Budget tracking
* Analytics
* Reports
* Local-first storage

Future versions may introduce:

* Cloud synchronization
* Recurring transactions
* Mobile support
* Investment tracking
* AI-assisted insights

---

## Contributing

See `CONTRIBUTING.md` for contribution guidelines.

---

## License

This project is licensed under the terms described in `LICENSE`.

---

## Acknowledgements

FinTrack is built with open-source technologies and guided by the documentation contained in the project handbook.

The handbook serves as the blueprint for the application's design, product behavior, and engineering decisions.

---

## Run FinTrack

FinTrack is local-first: transactions, budgets, and preferences are stored in
the browser. It supports transaction management, category and monthly budgets,
analytics, CSV import, and CSV report export.

```bash
npm install
npm run dev
```

Create a production bundle with:

```bash
npm run build
npm run preview
```

The included `vercel.json` deploys the `dist/` folder on Vercel after connecting
this repository to a Vercel project.
