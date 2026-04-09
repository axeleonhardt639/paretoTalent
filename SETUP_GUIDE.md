# Setup Guide — Animated Hero Component

## Current State

The current project (`index.html`) is plain HTML. To use the animated React component, you need to bootstrap a React + TypeScript + Tailwind + shadcn project. Here's the complete path.

---

## Step 1 — Bootstrap the Project (shadcn CLI)

The fastest way is with Vite + shadcn:

```bash
# Create a new Vite + React + TypeScript project
npm create vite@latest my-app -- --template react-ts
cd my-app
npm install

# Install Tailwind CSS
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```

Then initialize shadcn:

```bash
npx shadcn@latest init
```

The CLI will ask:
- **Style:** Default
- **Base color:** Neutral (or your preference)
- **CSS variables:** Yes

This automatically sets up `tailwind.config.ts`, `globals.css`, `components.json`, and the `@/` path alias.

---

## Step 2 — Why `/components/ui` Matters

shadcn uses `/components/ui` as its **canonical component directory**. Every component added via `npx shadcn add <component>` lands there automatically. If you use a different path:

- The `@/components/ui/button` import in `animated-hero.tsx` will break
- The `components.json` config won't resolve components correctly
- Future `npx shadcn add` commands will put files in the wrong place

Always keep shadcn components in `/components/ui`.

---

## Step 3 — Copy the Component Files

The following files are already created in this folder and ready to copy into your new project:

| Source (this folder)           | Destination (new project)         |
|-------------------------------|-----------------------------------|
| `components/ui/animated-hero.tsx` | `src/components/ui/animated-hero.tsx` |
| `components/ui/button.tsx`        | `src/components/ui/button.tsx`        |
| `lib/utils.ts`                    | `src/lib/utils.ts`                    |
| `demo.tsx`                        | `src/demo.tsx` (or use in `App.tsx`)  |

---

## Step 4 — Install NPM Dependencies

```bash
npm install framer-motion lucide-react @radix-ui/react-slot class-variance-authority clsx tailwind-merge
```

| Package                   | Purpose                                      |
|--------------------------|----------------------------------------------|
| `framer-motion`          | Powers the animated word cycling in the hero |
| `lucide-react`           | Provides `MoveRight` and `PhoneCall` icons   |
| `@radix-ui/react-slot`   | Used by the Button component (`asChild` prop)|
| `class-variance-authority` | Manages button variant styles              |
| `clsx` + `tailwind-merge` | Powers the `cn()` utility in `lib/utils.ts` |

---

## Step 5 — Use the Component in Your App

In `src/App.tsx`:

```tsx
import { HeroDemo } from "./demo";

function App() {
  return (
    <main>
      <HeroDemo />
    </main>
  );
}

export default App;
```

---

## Step 6 — Configure the `@/` Path Alias

Make sure `tsconfig.json` and `vite.config.ts` both have the alias set up:

**tsconfig.json:**
```json
{
  "compilerOptions": {
    "baseUrl": ".",
    "paths": {
      "@/*": ["./src/*"]
    }
  }
}
```

**vite.config.ts:**
```ts
import path from "path"
import { defineConfig } from "vite"
import react from "@vitejs/plugin-react"

export default defineConfig({
  plugins: [react()],
  resolve: {
    alias: {
      "@": path.resolve(__dirname, "./src"),
    },
  },
})
```

Also install the Node types if needed:
```bash
npm install -D @types/node
```

---

## Step 7 — Run the Dev Server

```bash
npm run dev
```

Visit `http://localhost:5173` and the animated hero should be live.

---

## Questions Answered

**What props does this component take?**
None — `Hero` is self-contained. The animating titles are hardcoded in the component (`["amazing", "new", "wonderful", "beautiful", "smart"]`). You can customize them in `animated-hero.tsx`.

**State management?**
Only local `useState` — no external store needed.

**Required assets?**
Only icons from `lucide-react` (already installed). No image assets.

**Responsive behavior?**
Fully responsive via Tailwind. Text scales from `text-5xl` (mobile) to `text-7xl` (desktop). Buttons stack naturally on small screens.

**Best place to use this component?**
As the first section of any landing page — import `HeroDemo` in `App.tsx` or your root page component.
