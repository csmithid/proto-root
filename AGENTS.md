# AGENTS.md — Prototype Stack Guide

## Stack

| Layer         | Tool                          |
|---------------|-------------------------------|
| Framework     | Next.js (App Router)          |
| UI            | shadcn/ui + Tailwind CSS      |
| State         | Zustand (simple), XState (complex flows) |
| 3D            | React Three Fiber + Three.js  |
| Animation     | React Spring                  |
| Testing       | Jest + React Testing Library  |
| Runtime       | Bun                           |

## Key Patterns

### State Management
- **Zustand** for UI state, toggles, selections, and any flat/shared state.
  Create stores in `lib/stores/`. One store per domain (e.g. `use-viewer-store.ts`).
- **XState** for multi-step flows, stateful processes, or anything with defined transitions.
  Define machines in `lib/machines/`. Use `@xstate/react` hooks to consume them.
- Don't mix: if something is a simple flag, use Zustand. If it has states and transitions, use XState.

### 3D Scenes
- R3F components go in `components/canvas/`.
- Keep `<Canvas>` in a single wrapper component — don't scatter them.
- Heavy geometry or loaders go in `lib/three/`.
- Use `drei` helpers when needed (install as-needed: `bun add @react-three/drei`).

### Animation
- Use `@react-spring/web` for DOM animations (opacity, transforms, layout).
- For R3F animations, use `@react-spring/three` (install as-needed: `bun add @react-spring/three`).
- Prefer `useSpring` and `useTransition` over CSS transitions for coordinated motion.

### File Structure
```
app/              → Pages and routes (App Router)
components/
  ui/             → shadcn components (auto-managed)
  canvas/         → R3F / 3D components
  [feature]/      → Feature-specific components
lib/
  stores/         → Zustand stores
  machines/       → XState machines
  three/          → Three.js utilities, loaders, geometries
  utils.ts        → General helpers
*.test.ts(x)      → Co-located unit/component tests
```

### Testing
- Run tests: `bun test` (maps to `jest`)
- Watch mode: `bun test:watch`
- Coverage: `bun test:coverage`
- Test files: co-locate with source as `*.test.ts` / `*.test.tsx`, or place in `__tests__/`.
- Use **React Testing Library** for component tests — query by role/label, not by class or implementation detail.
- Use **jest.fn()** for mocking callbacks; use `jest.mock('module')` for module mocks.

**Component test example:**
```tsx
import { render, screen } from '@testing-library/react'
import userEvent from '@testing-library/user-event'
import { MyButton } from './my-button'

test('calls onClick when clicked', async () => {
  const user = userEvent.setup()
  const onClick = jest.fn()
  render(<MyButton onClick={onClick}>Click me</MyButton>)
  await user.click(screen.getByRole('button', { name: /click me/i }))
  expect(onClick).toHaveBeenCalledTimes(1)
})
```

**Store test example (Zustand):**
```ts
import { act } from '@testing-library/react'
import { useMyStore } from '@/lib/stores/use-my-store'

beforeEach(() => useMyStore.setState(useMyStore.getInitialState()))

test('increments count', () => {
  act(() => useMyStore.getState().increment())
  expect(useMyStore.getState().count).toBe(1)
})
```

- This is a prototype — don't over-test. Focus tests on logic in `lib/` and critical UI interactions. Skip tests for pure layout components.

### Conventions
- This is a prototype — bias toward speed over abstraction.
- Co-locate related code. Don't over-organize.
- shadcn components are in `components/ui/` — add new ones with `bunx --bun shadcn@latest add <component>`.
- All package management uses `bun`, not npm/yarn/pnpm.
