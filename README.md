# smnl-website project

Astro-based corporate website project for smnl-website, adapted from the **Modern Business / Green Energy Astro Template by Vilmos Bartalis**.

The original template is being repurposed for an international trading business. Website content, sections, imagery, branding, and styling are being progressively replaced with project-specific material.

---

## Technology Stack

- **Astro** `7.3.2`
- **Tailwind CSS** `3.4.18`
- **@astrojs/tailwind** `6.0.2` _(legacy integration; see Dependency Notes)_
- **TypeScript** `5.x`
- **Prettier** `3.9.6`
- **prettier-plugin-astro** `0.14.1`
- **Node.js** `20.11.0`
- **npm**
- **Git / GitHub**

---

## Original Template

This project started from an Astro business website template by **Vilmos Bartalis**.

The original template was designed around a green-energy business and included template-specific sections, content, imagery, and styling.

Those elements are being modified or replaced for the smnl-website project.

**Important:** Do not assume that existing template components, text, images, statistics, testimonials, or section names represent the current project.

---

## Project Structure

The main project directories are:

```text
/
├── public/
├── src/
│   ├── components/
│   │   ├── blocks/
│   │   ├── sections/
│   │   └── shared/
│   ├── layouts/
│   └── pages/
├── astro.config.mjs
├── tailwind.config.mjs
├── package.json
├── package-lock.json
└── README.md
```

Some directories and components originated from the starting template and are being progressively repurposed or replaced.

---

## Astro Configuration

The current `astro.config.mjs` uses:

```js
import { defineConfig } from "astro/config";
import tailwind from "@astrojs/tailwind";

export default defineConfig({
  integrations: [tailwind()],
  site: "https://energy-template.vbartalis.dev",
  output: "static",
  trailingSlash: "ignore",
});
```

### Important

The `site` value currently points to the original template/demo domain and **must be changed before production deployment**.

The project is currently configured for static output:

```js
output: "static";
```

The planned production host is Hostinger.

---

## Tailwind CSS

Tailwind is configured in:

```text
tailwind.config.mjs
```

The project currently uses Tailwind CSS 3.

The configuration contains custom:

- Colour scales
- Breakpoints
- Shadows
- Typography
- Font family

Current core colours include:

```text
Base:       #FFFFFF
Base Dark:  #0B1228
Primary:    #1F4AE0
Secondary:  #F87937
CTA:        #F87937
```

Use the existing Tailwind configuration when modifying the visual system.

---

## Development Setup

### Prerequisites

- Node.js 20.11.0
- npm
- Git
- Visual Studio Code

### Install dependencies

```bash
npm install
```

### Start development server

```bash
npm run dev
```

The local development site is normally available at:

```text
http://localhost:4321
```

### Production build

```bash
npm run build
```

The current build script runs:

```text
astro check
    ↓
astro build
```

### Preview production build

```bash
npm run preview
```

### Astro CLI

```bash
npm run astro
```

---

## Code Formatting

The project uses:

- Prettier
- `prettier-plugin-astro`

VS Code is configured to use the **Astro formatter**.

With format-on-save enabled:

```text
Ctrl + S
```

formats the current file automatically.

Manual formatting:

```text
Shift + Alt + F
```

### Formatter Configuration

The project currently does not require a `.prettierrc` file for the basic formatting setup.

If project-specific formatting rules are needed later, a Prettier configuration can be added.

---

## Astro File Conventions

Astro components normally contain frontmatter followed by markup:

```astro
---
/* JavaScript / TypeScript */
---

<!-- Astro markup -->
```

### Comments

Developer-only Astro comment:

```astro
<!---
  Developer note
--->
```

HTML/markup comment:

```astro
<!--
  Temporarily commented-out markup
-->
```

JavaScript/TypeScript comment in frontmatter:

```astro
---
// Comment
const value = "...";
---
```

Do not place `//` inside a JavaScript template literal and expect it to behave as a comment.

For example, this is **not** a valid way to comment out a Tailwind class:

```astro
class={`
  // content-center
`}
```

It becomes part of the generated string.

---

## Tailwind Class Troubleshooting

When a Tailwind class appears unnecessary or has no visible effect:

1. Temporarily remove the class.
2. Check the page visually.
3. Use browser Developer Tools to inspect the element.
4. Compare the layout with and without the class.
5. Keep the class only if it contributes to the intended design.

Avoid accumulating unused or commented-out Tailwind classes.

---

## Dependency Notes

### Astro / Tailwind Integration Mismatch

The project currently has a known dependency compatibility issue:

```text
astro               7.3.2
@astrojs/tailwind    6.0.2
```

`@astrojs/tailwind@6.0.2` declares a peer dependency compatible with Astro 3, 4, or 5, while the project currently uses Astro 7.3.2.

This currently causes npm dependency-resolution problems such as `ERESOLVE` / `ELSPROBLEMS`.

### Important limitation

Do **not** use:

```bash
npm install --force
```

or:

```bash
npm install --legacy-peer-deps
```

as a permanent solution.

These options can bypass npm's dependency-resolution safeguards without actually resolving compatibility.

### Planned cleanup approach

Before changing Astro, Tailwind, or their integrations:

1. Make a Git commit of the working project.
2. Create a separate copy of the project without `node_modules`.
3. Test the dependency changes there.
4. Confirm that:
   - `npm install` succeeds normally
   - `npm run dev` works
   - `npm run build` works
   - Tailwind styles still work
   - Existing Astro components still render correctly
5. Only then apply confirmed changes to the main project.

Dependency modernization should be treated as a separate task from major website design work.

---

## Git Workflow

Check changes:

```bash
git status
```

Review differences:

```bash
git diff
```

Stage changes:

```bash
git add .
```

Commit:

```bash
git commit -m "Describe the change"
```

Push:

```bash
git push
```

For significant changes, make a Git commit before starting the next major task.

---

## Current Development Status

### Completed

- Astro project running locally
- Git repository connected
- Tailwind CSS customized
- Prettier installed
- Astro Prettier plugin installed
- VS Code Astro formatter selected
- Format on save working
- Manual formatting working with `Shift + Alt + F`
- Website template identified and being repurposed

### In Progress

- Replacing original template content
- Reworking website sections
- Refining layout and Tailwind classes
- Replacing template imagery
- Implementing branding
- Refining responsive behaviour

### Pending

- Resolve Astro / `@astrojs/tailwind` dependency mismatch
- Finalize production domain
- Update `site` in `astro.config.mjs`
- Complete SEO metadata
- Finalize favicon and branding
- Complete responsive QA
- Run final production build
- Deploy to Hostinger
- Complete production QA

---

## Production Checklist

```text
[ ] npm install succeeds without dependency-resolution errors
[ ] npm run build succeeds
[ ] No unexpected browser console errors
[ ] No broken images
[ ] No broken links
[ ] Responsive layouts tested
[ ] Navigation tested
[ ] Buttons and forms tested
[ ] Final domain configured
[ ] astro.config.mjs site value updated
[ ] Page title finalized
[ ] Meta description finalized
[ ] Canonical URL configured
[ ] Open Graph metadata configured
[ ] Favicon configured
[ ] Image alt text reviewed
[ ] 404 handling reviewed
[ ] Production build tested
[ ] Hostinger deployment tested
```

---

## Important Limitations

- This project is still being adapted from an existing template.
- Some component and directory names may still reflect the original template.
- Existing template content should not automatically be treated as current project content.
- The current `site` URL is still the original template/demo URL.
- The Astro / `@astrojs/tailwind` dependency mismatch remains unresolved.
- The final production domain has not yet been configured.
- Some website content and contact details are not yet finalized.
- Do not invent statistics, testimonials, certifications, customer names, or product specifications.
- Avoid large dependency changes without first creating a recoverable Git checkpoint.

---

## Deployment Target

Planned hosting:

```text
Hostinger
```

The final deployment configuration will be documented after it has been tested successfully.

---

## Repository

GitHub repository:

```text
https://github.com/andy-minn/smnl-website
```

---

## Maintenance

Update this README when there are significant changes to:

- Framework versions
- Dependencies
- Build commands
- Project structure
- Development workflow
- Deployment configuration
- Known limitations

Keep this README primarily focused on the **technical setup, project origin, development workflow, limitations, and maintenance requirements**.
