# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a starter project for a React-based expense tracker app. It's part of a Claude Code course and **intentionally contains bugs, poor UI, and messy code** that are meant to be fixed throughout the course.

## Development Commands

```bash
# Install dependencies
npm install

# Start dev server (opens at http://localhost:5173)
npm run dev

# Build for production
npm run build

# Run linter
npm run lint

# Preview production build
npm run preview
```

## Architecture

**Component structure**: `src/App.jsx` is the root and owns the `transactions` array, `categories` list, and an `addTransaction` callback. UI is split into three child components under `src/components/`:

- `Summary.jsx` — receives `transactions` and computes `totalIncome`, `totalExpenses`, and `balance` internally.
- `TransactionForm.jsx` — owns its own form state (`description`, `amount`, `type`, `category`) and calls the `onAdd` prop when submitted. Coerces `amount` to `Number` before handing it to the parent.
- `TransactionList.jsx` — owns its own filter state (`filterType`, `filterCategory`) and renders the filtered transactions table. Receives `transactions` and `categories` as props.

**State management**: Basic React `useState` hooks. State is colocated with the component that uses it; only shared state (`transactions`) lives in `App`. No persistence — transactions reset on page reload.

**Data shape**: `transactions` is an array of `{ id, description, amount (number), type, category, date }`. Amounts are stored as numbers, not strings.

**Known issues by design**:
- Line 10 in `App.jsx`: Transaction #4 has `type: "expense"` but `category: "salary"` (likely should be income)
- No delete/edit functionality for transactions
- No data persistence (transactions reset on page reload)

## Tech Stack

- React 19.2.0 (with StrictMode enabled)
- Vite 7.2.4 for build tooling
- ESLint with React Hooks and React Refresh plugins
- No routing, state management, or UI libraries
