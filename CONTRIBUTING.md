# Contributing to LST Yield Explorer

Thanks for your interest in contributing! This guide will help you get started.

## How to Contribute

### Reporting Bugs

1. Check [existing issues](https://github.com/lucascbacasp/lst-yield-dashboard/issues) to avoid duplicates
2. Open a new issue with:
   - Clear title describing the bug
   - Steps to reproduce
   - Expected vs actual behavior
   - Browser and OS information
   - Screenshots if applicable

### Suggesting Features

Open an issue with the `enhancement` label describing:
- The problem you're trying to solve
- Your proposed solution
- Any alternatives you've considered

### Submitting Changes

1. Fork the repository
2. Create a feature branch from `main`:
   ```bash
   git checkout -b feature/your-feature-name
   ```
3. Make your changes
4. Test locally by opening `index.html` in a browser
5. Commit with a clear message:
   ```bash
   git commit -m "Add: brief description of what you added"
   ```
6. Push and open a Pull Request

## Code Style

### HTML
- Use semantic HTML5 elements
- Keep accessibility in mind (`aria-*` attributes where needed)
- Indent with 2 spaces

### CSS
- Use CSS custom properties (variables) defined in `:root` for colors and spacing
- Follow BEM-like naming: `.block-element` with descriptive class names
- Mobile-first responsive design using media queries
- No `!important` unless absolutely necessary

### JavaScript
- ES6+ syntax (const/let, arrow functions, template literals)
- Descriptive function and variable names
- Comment non-obvious logic
- Keep the render pipeline simple and readable

## Commit Message Convention

```
Type: Short description

Longer explanation if needed.
```

Types:
- `Add` — New feature or file
- `Fix` — Bug fix
- `Update` — Enhancement to existing feature
- `Refactor` — Code restructuring without behavior change
- `Docs` — Documentation changes
- `Style` — CSS/formatting changes (no logic change)

## Development Setup

```bash
git clone https://github.com/lucascbacasp/lst-yield-dashboard.git
cd lst-yield-dashboard
open index.html
# or
npx serve -s . -l 3000
```

No build tools required — edit and refresh.

## Questions?

Open an issue or reach out via the repository discussions tab.
