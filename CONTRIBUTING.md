# Contributing to FindIt

First off, thank you for considering contributing to FindIt! Whether you're fixing a bug, adding a new "tenant" module, or improving documentation, your help is welcome.

## 1. Our Vision

FindIt is a modular "Super-App" designed to solve the relocation and lifestyle challenges of youth. We use a **Multi-Tenant Architecture** where each major service (Rentals, Marketplace, Chores, etc.) is treated as its own business unit within a shared infrastructure.

## 2. Project Structure (Monorepo)

We use **Turborepo** to manage our apps and packages. Understanding this layout is key to a successful PR:

* **`apps/mobile`**: The React Native (Expo) application.
* **`apps/web`**: The Next.js landing page and user marketplace.
* **`apps/admin`**: Internal dashboard for manual ID verification and moderation.
* **`packages/ui`**: Shared UI components (ShadUI for web, shared tokens for mobile).
* **`packages/validators`**: Shared Zod schemas used by both frontend and backend.
* **`packages/database`**: Prisma/Supabase configuration and migrations.

## 3. Getting Started

To get the project running locally, you need [Node.js](https://nodejs.org/) and [pnpm](https://pnpm.io/) installed.

1. **Fork & Clone:** Fork the repository and clone it to your machine.
2. **Install Dependencies:**
```bash
pnpm install

```


3. **Setup Environment:** Copy `.env.example` in each app folder to `.env` and fill in your Supabase/Paystack test keys.
4. **Run Development Mode:**
```bash
pnpm dev

```


*This will start the mobile bundler, web dev server, and backend simultaneously using Turbo.*

## 4. Development Workflow

### Branching Policy

Please create a branch from `main` using the following naming convention:

* `feat/your-feature-name` (for new features)
* `fix/bug-description` (for bug fixes)
* `docs/what-you-updated` (for documentation)

### Conventional Commits

We use **Husky** to enforce high-quality commits. Your commit messages should follow the [Conventional Commits](https://www.conventionalcommits.org/) format:

* `feat(marketplace): add price filtering to item list`
* `fix(auth): resolve login loop on mobile`

### Pre-commit Hooks

When you attempt to `git commit`, Husky will automatically:

1. **Lint** your code.
2. **Format** your code via Prettier.
3. **Run Tests** relevant to the files you changed.
*If any of these fail, the commit will be rejected.*

## 5. Adding New "Tenants"

If you are adding a new business module (e.g., "Laundry Service"):

1. Add a new folder in `apps/` or a new module in the shared backend logic.
2. Register the new feature in our **Feature Flag** system (PostHog).
3. Update the `@findit/validators` package if new data schemas are required.

## 6. Pull Request Process

1. Ensure your code passes all linting and tests locally.
2. Link your PR to an existing **Issue**.
3. Include screenshots or a screen recording for UI changes (especially for the React Native app).
4. The core maintainer will review your PR within 48-72 hours.

---

### Pro-Tip for Contributors:

If you want to contribute but don't know where to start, look for issues labeled **`good first issue`**. These are usually small UI fixes or documentation updates meant to help you get familiar with the monorepo setup.

