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

**Single-component app**: All logic lives in `src/App.jsx` - there are no separate components, utilities, or state management libraries. This monolithic structure is intentional for the starter.

**State management**: Uses basic React `useState` hooks. Transaction data is stored in component state (not persisted).

**Known issues by design**:
- Line 27-31 in `App.jsx`: `totalIncome` and `totalExpenses` calculations sum `t.amount` without parsing to number (amounts are stored as strings)
- Line 9 in `App.jsx`: Transaction #4 has `type: "expense"` but `category: "salary"` (likely should be income)
- No delete/edit functionality for transactions
- No data persistence (transactions reset on page reload)

## Tech Stack

- React 19.2.0 (with StrictMode enabled)
- Vite 7.2.4 for build tooling
- ESLint with React Hooks and React Refresh plugins
- No routing, state management, or UI libraries
