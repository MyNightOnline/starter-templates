# Project Setup: Vite + React (TS) + Tailwind CSS + React Router + Lucide React

Follow these steps to initialize the project.

## Prerequisites
- Runtime: Bun (or your preferred runtime, e.g., Node.js / pnpm / yarn)

## 1. Initialize Vite Project
```bash
bun create vite . --template react-ts
```

## 2. Install Dependencies
```bash
bun add react-router tailwindcss @tailwindcss/vite lucide-react
```

## 3. Setup Tailwind CSS

### 3.1 Configure Vite Plugin
Add the `@tailwindcss/vite` plugin to your `vite.config.ts`:

```typescript
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react'
import tailwindcss from '@tailwindcss/vite'

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [
    react(),
    tailwindcss(),
  ],
})
```

### 3.2 Remove Default Files
Remove the following files:
- `src/App.css`
- `src/App.tsx`

### 3.3 Configure Global CSS
Update `src/index.css` to contain only the Tailwind import:

```css
@import "tailwindcss";
```

## 4. Setup Main Entry Point
Update `src/main.tsx` to set up the RouterProvider:

```tsx
import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'
import './index.css'
import { RouterProvider } from "react-router";
import router from './router';

createRoot(document.getElementById('root')!).render(
  <StrictMode>
    <RouterProvider router={router} />
  </StrictMode>,
)
```

## 5. Create Router Configuration
Create a new file `src/router/index.tsx` with the following content:

```tsx
import { createBrowserRouter } from "react-router";

const router = createBrowserRouter([
  {
    path: "/",
    element: <div className="p-4 text-2xl font-bold flex gap-2 items-center">Hello World</div>,
  },
]);

export default router;
```
