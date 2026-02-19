# Proto-template

This is a prototype project built with React, Vite, TypeScript, and Tailwind CSS. It's used by a product designer to create interactive prototypes for work.

## Tech stack

- **Framework:** React + Vite + TypeScript
- **Styling:** Tailwind CSS v4
- **UI components:** shadcn/ui (available, not required — use when a standard component is needed)
- **Animation:** Motion (motion.dev) — import from `motion/react`
- **Icons:** Lucide React (default, but any icon source is fine if asked)
- **Config panels:** DialKit — floating control panel for tweaking UI values at runtime

## Commands

- `npm run dev` — start dev server
- `npm run build` — production build
- `npx shadcn@latest add <component>` — add a shadcn/ui component (e.g. button, dialog, card)

## Path alias

`@/` maps to `./src/` — use it for all imports (e.g. `@/lib/utils`, `@/components/ui/button`).

## Deployment

This project deploys to Vercel. Run `vercel` to deploy a preview, `vercel --prod` for production.

## Who you're working with

You're working with a product designer who knows basic HTML, CSS, and JS. They are not a developer. Keep explanations simple and avoid unnecessary jargon. When you need to explain something technical, use plain language and relate it to visual/design concepts they already understand.

## Your job

Build interactive prototypes that look and feel real. The designer will describe what they want — sometimes in words, sometimes with screenshots, sometimes through Figma (via MCP). Your output should be something they can show to stakeholders and get meaningful feedback on.

## How to work

### Do the simple thing first
- Build what was asked for. Don't add infrastructure, abstractions, or "nice to haves."
- If a component is used once, just write it inline. Don't create a separate file for it.
- If something can be done in 10 lines, don't architect it into 3 files.
- Use shadcn/ui when a standard component is needed (buttons, dialogs, inputs, cards). Build custom when the interaction is specific or unusual — which it often will be.

### Keep it flat
- Start in App.tsx. Only split into separate component files when things get genuinely hard to follow.
- Don't add routing unless the prototype has multiple distinct pages/screens. When it does, install react-router-dom and set it up.
- Don't add state management libraries. React's built-in useState and useContext are enough for prototypes.

### Motion and animation
- Use Motion (motion.dev) for animations. Import from `motion/react`.
- Every state change, transition, and interaction should feel smooth and intentional.
- Use appropriate easing — avoid linear timing for UI motion. Springs and ease-out curves feel more natural.
- Keep animations quick. Most UI transitions should be 150-300ms. Don't make people wait.

### Config menus (DialKit)
- When asked to add a config menu, control panel, or tweakable settings to a prototype, use DialKit.
- `DialRoot` is already mounted in main.tsx. Just use the `useDialKit` hook in any component:
  ```tsx
  import { useDialKit } from 'dialkit'

  const params = useDialKit('ComponentName', {
    blur: [24, 0, 100],    // [default, min, max] → slider
    color: '#ff5500',       // → color picker
    visible: true,          // → toggle
  })
  ```
- The hook returns a reactive object — use `params.blur`, `params.color`, etc. directly in your JSX/styles.

### Styling
- Use Tailwind classes directly. Don't create CSS files unless there's a specific reason.
- shadcn/ui's theme variables (defined in index.css) are available — use them for consistency when it makes sense, but each prototype can have its own look.
- The Inter font is loaded by default. Change it if the design calls for something else.

### Mock data
- When the prototype needs realistic content (names, avatars, product info), create a simple data array at the top of the file. Keep it co-located with the component that uses it.
- Use real-sounding names, real-looking numbers, and plausible content. Never use "Lorem ipsum", "John Doe", or "Test User" — these break the illusion.

### Images and assets
- Put static assets in the `public/` folder.
- For placeholder images, use picsum.photos or similar services.

## What not to do

- Don't over-engineer. This is a prototype, not a production app.
- Don't add error boundaries, loading skeletons, or error states unless specifically asked.
- Don't add TypeScript types or interfaces unless they genuinely help you write the code. Skip them for simple props.
- Don't refactor or reorganize existing code unless asked to.
- Don't add comments explaining obvious things. The code should be readable on its own.
- Don't install extra packages without being asked. Work with what's already in the project. If you truly need something new, mention it briefly before installing.

## Git

- Never add "Co-Authored-By" lines to commit messages.

## Naming

When creating a new prototype from this template, name it `proto-{name}` where `{name}` is a short descriptor. Ask the designer what to call it if unclear.
