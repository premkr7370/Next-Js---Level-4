# Ultimate Next.js - Level 4

A TypeScript and Next.js practice project from the Ultimate Next.js. This level focuses on React fundamentals, form handling, component props, global TypeScript types, and the Next.js App Router.

> **Project status:** Educational starter project. The current form UI is in progress and does not yet contain submission or input-processing logic.

## Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Technology Stack](#technology-stack)
- [Project Structure](#project-structure)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Available Scripts](#available-scripts)
- [Application Behavior](#application-behavior)
- [TypeScript Exercises](#typescript-exercises)
- [Styling](#styling)
- [Development Notes](#development-notes)
- [Production Build](#production-build)
- [Troubleshooting](#troubleshooting)
- [Deployment](#deployment)
- [License](#license)

## Overview

This project demonstrates a small Next.js 15 application built with React 19 and TypeScript 5. It includes:

- A client-rendered React page
- A controlled-page structure for form experiments
- Reusable component prop definitions
- Global custom TypeScript declarations
- Tailwind CSS 4 integration
- Next.js font optimization with Geist
- Strict TypeScript checking
- ESLint configuration for Next.js

The repository is primarily intended for learning and should be expanded by implementing the form and exercise code.

## Features

### Implemented

- Next.js App Router setup
- React Client Component usage
- Form and input event handlers
- Reusable `Button` component skeleton
- Strict TypeScript configuration
- TypeScript path alias for the `src` directory
- Global custom type declarations
- Geist Sans and Geist Mono font loading
- Tailwind CSS 4 and basic CSS variables
- Development and production Next.js scripts

### In Progress

- Form submission behavior
- Input value state management
- Button action behavior
- Full tutorial page UI
- Final lesson-specific feature implementation

## Technology Stack

| Technology | Purpose |
| --- | --- |
| Next.js 15.5.4 | React framework and App Router |
| React 19.1.0 | Component-based UI |
| React DOM 19.1.0 | Browser rendering |
| TypeScript 5 | Static type checking |
| Tailwind CSS 4 | Utility-first styling |
| ESLint 9 | Code quality checks |
| Turbopack | Fast development and build tooling |

## Project Structure

```text
.
├── public/
│   ├── file.svg
│   ├── globe.svg
│   ├── next.svg
│   ├── vercel.svg
│   └── window.svg
├── src/
│   ├── app/
│   │   ├── favicon.ico
│   │   ├── globals.css
│   │   ├── layout.tsx
│   │   └── page.tsx
│   ├── Button.tsx
│   ├── tutorial.ts
│   └── types.d.ts
├── .gitignore
├── eslint.config.mjs
├── next.config.ts
├── package-lock.json
├── package.json
├── postcss.config.mjs
└── tsconfig.json
```

### Important Files

- `src/app/page.tsx` - Main page component. It contains a form and empty/in-progress event handlers.
- `src/app/layout.tsx` - Root layout, global CSS import, metadata, and Geist font setup.
- `src/app/globals.css` - Tailwind import, color variables, dark-mode colors, and global body styles.
- `src/Button.tsx` - Example reusable component with typed `data` and `action` props.
- `src/tutorial.ts` - Commented TypeScript learning examples for types, interfaces, unions, intersections, and inference.
- `src/types.d.ts` - Global custom type declarations.
- `next.config.ts` - Next.js project configuration.
- `tsconfig.json` - Strict TypeScript and `@/*` path alias configuration.

## Prerequisites

Install the following before running the project:

- [Node.js](https://nodejs.org/) 18.18 or later
- npm, yarn, pnpm, or Bun

npm is used in this README because `package-lock.json` is included.

## Getting Started

1. Open a terminal in the project directory.

2. Install dependencies:

   ```bash
   npm install
   ```

3. Start the development server:

   ```bash
   npm run dev
   ```

4. Open [http://localhost:3000](http://localhost:3000) in your browser.

The Next.js development server automatically reloads the page when source files change.

## Available Scripts

| Command | Description |
| --- | --- |
| `npm run dev` | Starts the Next.js development server with Turbopack |
| `npm run build` | Creates an optimized production build with Turbopack |
| `npm run start` | Runs the previously created production build |
| `npm run lint` | Runs ESLint across the project |

To use another package manager:

```bash
yarn dev
pnpm dev
bun dev
```

## Application Behavior

The main page is a client component because it uses React hooks and DOM event handlers.

Current form setup:

```tsx
<form onSubmit={handleSubmit}>
  <input type="text" ref={input} onChange={handleChange} />
  <button>click</button>
</form>
```

`handleSubmit` currently prevents the browser from performing the default form submission. `handleChange` is ready to receive input changes but does not yet process or store a value.

A possible next implementation would:

1. Add a state value or read the input through `useRef`.
2. Update state in `handleChange`.
3. Validate or transform the value in `handleSubmit`.
4. Display the result or call an API.

Example component prop pattern:

```tsx
type ButtonProps = {
  data: string
  action: () => void
}
```

The `Button` component currently renders a placeholder and can be extended with `data` and `action`.

## TypeScript Exercises

`src/tutorial.ts` contains commented examples of:

- Type inference
- Type annotations
- Union types
- Literal types
- Object types
- Interfaces
- Optional properties
- Function types
- Type intersections
- Interface extension

`src/types.d.ts` declares a few types globally:

```ts
type ayush = number | string

type user = {
  name: "string"
}
```

Global declarations are useful for course exercises, but application-specific types can become harder to maintain as a project grows. Prefer exported types or interfaces in dedicated modules for larger applications.

## Styling

The project uses Tailwind CSS 4 through its PostCSS plugin:

```css
@import "tailwindcss";
```

The global stylesheet defines:

- A light background and foreground pair
- Tailwind theme variables
- Automatic dark-mode values using `prefers-color-scheme`
- A simple global body font and colors

The path alias `@/*` maps to `src/*`, allowing imports such as:

```tsx
import Button from "@/Button"
```

## Development Notes

- Use `npm run lint` before committing changes.
- Add user-facing metadata in `src/app/layout.tsx` when finalizing the application.
- Keep event handlers inside a client component when they use browser APIs or React hooks.
- Reuse page-level components from `src/Button.tsx` or create new components as the UI grows.
- Place shared TypeScript types in `src/types.d.ts` or a dedicated `src/types/` directory.
- Avoid committing generated `.next`, build output, environment files, or dependency folders.

## Production Build

Create and run an optimized build:

```bash
npm run build
npm run start
```

The production server normally starts on port `3000`.

You can specify another port:

```bash
npm run start -- -p 3001
```

## Troubleshooting

### Port 3000 is already in use

```bash
npm run dev -- -p 3001
```

### Dependencies do not install correctly

Remove the local dependency folder and reinstall:

```bash
rm -rf node_modules
npm install
```

On Windows PowerShell, use:

```powershell
Remove-Item -Recurse -Force node_modules
npm install
```

### TypeScript reports module or alias issues

- Confirm the import uses `@/` for files inside `src`.
- Confirm the file exists and has the correct extension.
- Restart the TypeScript server or development server after major configuration changes.

### The page does not refresh

Stop the development server, then start it again:

```bash
npm run dev
```

## Deployment

This is a standard Next.js application and can be deployed to:

- [Vercel](https://vercel.com/)
- Netlify
- A Node.js server
- A container platform

Before deployment:

```bash
npm run lint
npm run build
```

For Vercel, import the repository and keep the framework preset set to Next.js.

## License

No license has been specified for this project. Add a license file if this repository will be distributed publicly or reused by others.
