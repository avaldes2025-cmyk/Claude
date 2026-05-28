# UI/UX Pro Max - Design Intelligence

This is a comprehensive design reference guide for web and mobile applications. It contains 50+ styles, 161 color palettes, 57 font pairings, 161 product types, 99 UX guidelines, and 25 chart types across 10 technology stacks (React, Next.js, Vue, Svelte, SwiftUI, React Native, Flutter, Tailwind, shadcn/ui, HTML/CSS).

## When to Use This Skill

Apply this skill when tasks involve UI structure, visual design decisions, interaction patterns, or user experience quality control. It is **required** for:
- Designing new pages or refactoring UI components
- Choosing color schemes, typography, spacing, or layout systems
- Reviewing UI code for accessibility and visual consistency
- Implementing navigation, animations, or responsive behavior

Skip this skill for pure backend logic, API design, performance optimization unrelated to interfaces, or infrastructure work.

## Rule Categories (Priority 1–10)

### 1. Accessibility
- Contrast ratio minimum 4.5:1 (WCAG AA), 7:1 for small text
- All interactive elements must have descriptive `aria-label` or visible label
- Keyboard navigation: logical tab order, visible focus rings (never `outline: none`)
- Images need meaningful alt text; decorative images use `alt=""`
- Use semantic HTML (`<button>`, `<nav>`, `<main>`, `<section>`)

### 2. Touch & Interaction
- Minimum touch target: 44×44px (iOS HIG and Material Design standard)
- Minimum 8px spacing between adjacent touch targets
- Provide visual and/or haptic feedback within 100ms of interaction
- Avoid hover-only interactions — ensure tap/click equivalents exist
- Loading states must be visible for any action >300ms

### 3. Performance
- Optimize images: use WebP/AVIF, lazy-load below-the-fold assets
- Cumulative Layout Shift (CLS) < 0.1 — reserve space for dynamic content
- Largest Contentful Paint (LCP) < 2.5s target
- First Contentful Paint (FCP) < 1.8s target
- Avoid layout thrash — batch DOM reads/writes

### 4. Style Selection
- Match UI style to product type (e.g., glassmorphism for fintech, minimalism for productivity)
- Maintain consistent style language across all screens — don't mix brutalism with neumorphism
- Use SVG icons, not emoji, for UI iconography
- Limit decorative elements — every visual element should serve communication
- Reference established design systems (Material, Fluent, HIG) before inventing patterns

### 5. Layout & Responsive Design
- Mobile-first approach: design for 375px width as baseline
- Never allow horizontal scroll on mobile (except intentional carousels)
- Configure `<meta name="viewport" content="width=device-width, initial-scale=1">`
- Use CSS Grid for 2D layouts, Flexbox for 1D alignment
- Breakpoints: 375px (mobile), 768px (tablet), 1024px (laptop), 1440px (desktop)
- Avoid fixed pixel heights that prevent content from expanding

### 6. Typography & Color
- Base font size: 16px minimum for body text
- Line height: 1.5 for body, 1.2–1.3 for headings
- Type scale: use a modular scale (1.25 or 1.333 ratio)
- Use semantic color tokens, not raw hex values in component code
- Limit palette to 1–2 primary, 1 accent, and neutral shades
- Ensure text on colored backgrounds meets contrast requirements
- Never rely on color alone to convey meaning — pair with icon or label

### 7. Animation & Motion
- Duration: 150–300ms for micro-interactions, 300–500ms for page transitions
- Use `transform` and `opacity` only — avoid animating layout properties
- Respect `prefers-reduced-motion` media query
- Animations should be purposeful, not decorative
- Easing: ease-out for elements entering, ease-in for elements leaving

### 8. Forms & Feedback
- Always use visible labels — never rely on placeholder text as the label
- Show inline error messages directly below the offending field
- Use progressive disclosure — show advanced options only when needed
- Validate on blur, not on each keystroke
- Success/error states must use both color and icon/text
- Disabled buttons should explain why they are disabled (tooltip or helper text)

### 9. Navigation Patterns
- Bottom navigation bar: maximum 5 items
- Back navigation must behave predictably — never trap users
- Support deep linking for all primary views
- Active state must be clearly distinguishable from inactive
- Mobile nav: hamburger menu acceptable for >5 secondary items
- Breadcrumbs for content hierarchies deeper than 3 levels

### 10. Charts & Data Visualization
- Use accessible color palettes (avoid red/green alone — add pattern or label)
- Always include a legend when using multiple data series
- Tooltips on hover/tap for precise values
- Axes must be labeled with units
- Empty states for charts must be meaningful, not just blank
- Support keyboard navigation for interactive charts

## How to Use

**Step 1 — Analyze:** Identify the product type, target audience, style keywords, and technology stack before making any design decisions.

**Step 2 — Design System:** Generate or define your core design tokens first: colors, typography scale, spacing scale, border radii, shadow levels.

**Step 3 — Component Design:** Apply stack-specific patterns (React hooks for state, SwiftUI modifiers, Flutter widgets) aligned with your design tokens.

**Step 4 — Review Checklist:** Before delivery, verify all items in the Pre-Delivery Checklist below.

## Stack-Specific Guidelines

### React / Next.js
- Use CSS Modules or Tailwind for scoped styles — avoid global class name collisions
- Memoize expensive renders with `React.memo`, `useMemo`, `useCallback`
- Server Components for static/data-fetching, Client Components for interactivity
- Image optimization: use `next/image` with `priority` for above-the-fold images

### Vue / Nuxt.js
- Use `<script setup>` syntax for cleaner composition API code
- Leverage `useLazyLoad` for deferred image loading
- Transition components with named transitions for page changes

### Tailwind CSS
- Use the `@layer` directive to organize custom utilities
- Extend theme tokens in `tailwind.config.js` rather than using arbitrary values
- Prefer `clsx` or `cn()` utility for conditional class composition

### shadcn/ui
- Always use the design system's built-in variant props before overriding
- Extend components by wrapping, not modifying source
- Use `cn()` for merging Tailwind classes in custom variants

### SwiftUI
- Follow iOS Human Interface Guidelines for spacing and typography
- Use `@Environment` for system values like color scheme and dynamic type
- Minimum touch target via `.frame(minWidth: 44, minHeight: 44)`

### React Native
- Use `StyleSheet.create()` for performance-optimized style objects
- Platform-specific code via `Platform.select()` or `.ios.tsx` / `.android.tsx` files
- Handle safe area insets with `react-native-safe-area-context`

### Flutter
- Use `ThemeData` for consistent design tokens across the app
- Prefer `const` constructors for stateless widgets to reduce rebuilds
- Material 3 tokens over hard-coded values

## Pre-Delivery Checklist

- [ ] All icons are SVG, not emoji
- [ ] Interactive elements have `:focus-visible` styles
- [ ] All contrast ratios verified (use a contrast checker tool)
- [ ] No horizontal scroll on 375px viewport
- [ ] All images have alt text
- [ ] Form labels are visible and associated correctly
- [ ] `prefers-reduced-motion` handled for animated elements
- [ ] Light mode and dark mode tested independently
- [ ] Touch targets ≥ 44×44px
- [ ] Empty states defined for all data-driven UI sections
- [ ] Loading states defined for all async operations
- [ ] Error states defined for all user-facing operations

## Quick Reference

### Common Color Token Names
```
--color-primary         Brand primary action
--color-primary-hover   Hover/active variant
--color-surface         Card/panel background
--color-surface-raised  Elevated surface (modal, popover)
--color-border          Default border
--color-text            Primary body text
--color-text-secondary  Muted/secondary text
--color-text-disabled   Disabled text
--color-error           Error states
--color-success         Success states
--color-warning         Warning states
```

### Type Scale (1.25 ratio)
```
xs:   12px / 0.75rem
sm:   14px / 0.875rem
base: 16px / 1rem
lg:   20px / 1.25rem
xl:   24px / 1.5rem
2xl:  32px / 2rem
3xl:  40px / 2.5rem
4xl:  48px / 3rem
```

### Spacing Scale (4px base)
```
1:  4px    5: 20px   9:  36px
2:  8px    6: 24px   10: 40px
3: 12px    7: 28px   12: 48px
4: 16px    8: 32px   16: 64px
```
