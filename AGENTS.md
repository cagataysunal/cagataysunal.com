# AGENTS.md - Agentic Coding Guidelines

This document provides guidance for agents operating in this repository.

## Project Overview

This is an Astro-based personal blog/portfolio website built with the official Astro blog starter template. The site features MDX support, sitemap generation, and RSS feeds.

## Commands

### Development

```bash
npm run dev          # Start local dev server at localhost:4321
npm run preview     # Preview production build locally
```

### Build

```bash
npm run build       # Build production site to ./dist/
```

### Formatting & Linting

```bash
npx prettier --write .           # Format all files
npx prettier --check .          # Check formatting without modifying
```

The project uses Prettier with `prettier-plugin-astro` for `.astro` files. A pre-commit hook (husky + lint-staged) automatically formats staged files.

### Type Checking

```bash
npm run astro -- check         # Run Astro's built-in type checking
```

### Testing

No test framework is currently configured. If tests are added in the future, typical commands would be:

```bash
npm test              # Run all tests
npm test -- --run     # Run tests once (for Vitest)
npm test <filepath>   # Run a specific test file
```

## Code Style Guidelines

### General Principles

- Keep code minimal and readable
- Use semantic HTML elements
- Follow Astro's default patterns

### File Organization

- `src/pages/` - Route-based pages (file-based routing)
- `src/layouts/` - Reusable page layouts
- `src/components/` - Reusable components
- `src/content/` - Content collections (MDX/Markdown)

### Astro Components (.astro files)

**Frontmatter (YAML fence):**

- Place all JavaScript/TypeScript logic in the frontmatter fence at the top
- Use `const` for component props with default values
- Keep logic concise; extract complex logic to separate utility files if needed

**Template:**

- Use 2-space indentation
- Use self-closing tags for void elements (`<meta />`, not `<meta>`)
- Wrap attributes in quotes: `<meta name="description" content={description} />`

**Styles:**

- Embed `<style>` tags within the component
- Use CSS custom properties for theming
- Keep styles scoped to the component (Astro does this automatically)
- Use modern CSS features (flexbox, grid, custom properties)

### TypeScript

- Enable strict mode when possible
- Use JSDoc comments with `@ts-check` for type inference in `.js` files
- Prefer explicit types for function parameters and return values

### CSS

- Use system font stacks for cross-platform consistency:
  ```css
  font-family:
    ui-sans-serif,
    system-ui,
    -apple-system,
    Segoe UI,
    Roboto,
    Ubuntu,
    Cantarell,
    Noto Sans,
    Arial;
  ```
- Use dark color scheme by default (this is a personal site)
- Use rgba with low opacity for subtle borders/backgrounds

### Imports

- Use relative imports for local modules
- Order imports logically (standard library → external → local)
- Keep import paths clean: `../layouts/BaseLayout` not `./layouts/BaseLayout.astro`

### Naming Conventions

- Files: kebab-case (`base-layout.astro`, `about-page.ts`)
- Components: PascalCase (`BaseLayout.astro`, `Header.astro`)
- Variables/functions: camelCase
- Constants: SCREAMING_SNAKE_CASE

### Error Handling

- Let errors propagate naturally in Astro components
- Use try/catch for async operations that might fail gracefully
- Provide meaningful error messages

### Markdown/MDX Content

- Use frontmatter for metadata (title, description, date, tags)
- Keep frontmatter keys lowercase
- Use descriptive slugs for blog posts

## Adding New Features

### Adding a New Page

1. Create `.astro` file in `src/pages/`
2. Import and use an existing layout
3. Add navigation link if needed

### Adding a Blog Post

1. Create `.md` or `.mdx` file in `src/content/blog/`
2. Add required frontmatter (title, description, pubDate)
3. Run `npm run build` to verify

### Adding Dependencies

```bash
npm run astro -- add <integration>  # Use Astro CLI for official integrations
npm install <package>              # For other packages
```

## Editor Setup

Recommended VS Code extensions:

- Astro (official extension)
- Prettier - Code formatter
- ESLint (optional, for advanced linting)

## Additional Resources

- [Astro Documentation](https://docs.astro.build)
- [Astro Content Collections](https://docs.astro.build/en/guides/content-collections/)
- [Prettier Astro Plugin](https://github.com/withastro/prettier-plugin-astro)
