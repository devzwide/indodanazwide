# 🕷️ indodanazwide

<div align="center">
  <img src="https://media.giphy.com/media/v1.Y2lkPTc5MGI3NjExcm55NzloNWQ4bWJhdHNxcmt4bG5ldmZvaWIya2ZwYWliY3Y5ZW44aCZlcD12MV9naWZzX3NlYXJjaCZjdD1n/InVMYKXqkyuCGoZeQe/giphy.gif" alt="Animated header" width="100%">
</div>

This repository is a minimal React + TypeScript + Vite starter with sensible defaults and a modern CI that builds, tests, uploads artifacts, and creates releases.

**Highlights**
- Vite + React 19 + TypeScript
- ESLint linting
- CI that detects relevant changes, builds, and publishes release artifacts

## Quick start

Prerequisites: Node.js (18+ preferred) and npm.

Install dependencies:

```bash
npm ci
```

Run development server with HMR:

```bash
npm run dev
```

Build for production:

```bash
npm run build
```

Preview the production build locally:

```bash
npm run preview
```

## Project scripts

- `dev`: start Vite dev server
- `build`: typecheck and build (`tsc -b && vite build`)
- `lint`: run ESLint
- `preview`: preview the built app

See `package.json` for exact scripts and versions.

## Linting & Testing

Run the linter:

```bash
npm run lint
```

If you add tests, use `npm test`. The CI will run `npm test --if-present`.

## CI, Artifacts & Releases

This repo includes a GitHub Actions workflow at [.github/workflows/ci.yml](.github/workflows/ci.yml#L1-L400) that:
- detects changes relevant to the app (files under `src/`, `public/`, and key config files)
- runs lint, tests (if present), and builds the app
- uploads the `dist/` build as an artifact
- on tag pushes it creates a GitHub Release and uploads the `dist.zip` asset

The workflow will attempt to publish to GitHub Packages (npm) only if `package.json` has `private: false`. By default this template is private, so automated publish is skipped until you opt in.

## Publishing to GitHub Packages (manual)

To publish an npm package to GitHub Packages from CI you can:

1. Ensure `package.json` has `name` and `version`, and `private: false`.
2. Add a repository field and consider a scoped package name (e.g., `@OWNER/package`).
3. For manual local publishing, create an `.npmrc` with a personal access token (or use `npm login`):

```ini
//npm.pkg.github.com/:_authToken=PERSONAL_ACCESS_TOKEN
```

4. Run:

```bash
npm publish --registry https://npm.pkg.github.com/
```

Note: CI publish in the workflow uses `GITHUB_TOKEN` (provided by Actions) when permitted.

## Contributing

Contributions are welcome. Suggested steps:

1. Fork the repo and create a branch for your change.
2. Add tests and run `npm ci && npm run lint && npm test`.
3. Open a pull request targeting `dev`.

## License

This project is licensed under the MIT License — see [LICENSE](LICENSE) for details.

---

If you'd like, I can also:
- add a basic test runner (Vitest) and a sample test file
- add a `.npmrc.example` and instructions to enable automated publishes
- add badges (CI/status) to the top of this README

