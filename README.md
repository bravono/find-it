# FindIt: Open-Source Lifestyle Super-App

## 1. Project Vision

**FindIt** is a community-driven lifestyle hub designed for high-mobility youth (NYSC, students, job seekers). It streamlines housing, micro-earning, and peer-to-peer commerce into a single, modular ecosystem.

## 2. Architecture: The "Modular Monolith"

To keep the project scalable for multiple contributors, we use a **Monorepo** structure. This ensures that a fix in the "Identity" package instantly updates both the Mobile and Web apps.

### The Stack

* **Monorepo:** [Turborepo](https://turbo.build/)
* **Mobile:** React Native + Expo + NativeWind
* **Web & Admin:** Next.js + Shadcn/UI
* **Backend & DB:** Node.js + PostgreSQL (Supabase)
* **Verification:** Hybrid (Manual + Paystack Identity API)

---

## 3. Multi-Tenant Business Logic

We treat each core feature as an isolated "Business Tenant." This allows developers to contribute to specific modules independently:

* 🏠 **Rentals Tenant:** Long-term housing and flatmate matching.
* 🛒 **Marketplace Tenant:** P2P used item sales.
* 🛠️ **Chore Tenant:** Task-based gig economy and escrow payments.
* 🛌 **Stay Tenant:** Short-term "pay-to-sleep" accommodations.

---

## 4. Contributor Guardrails (DX)

To maintain code quality as the team grows, we enforce strict standards via **Husky**:

* **Pre-commit:** Runs `Lint-Staged` and `Prettier` to ensure consistent formatting.
* **Type Safety:** Shared `Zod` schemas in `@findit/validators` ensure that data is validated the same way on the Mobile app and the Backend.
* **Feature Flags:** We use **PostHog** for "Dark Launches." New features can be merged into `main` but remain hidden behind a flag until they are fully tested.

---

## 5. Security & Trust (The Escrow Flow)

Trust is our core product. For the **Chore** and **Stay** modules, we use a custom Escrow logic:

1. **Fund:** User A pays (Funds are held via Paystack sub-accounts).
2. **Verify:** User B completes the task.
3. **Release:** Upon mutual confirmation, funds are transferred to User B.
4. **Identity:** Users earn "Verified" badges by linking bank accounts or uploading ID for manual admin approval.

---

## 6. Getting Started (For Contributors)

1. **Clone the repo**
2. **Install dependencies:** `pnpm install`
3. **Environment Setup:** Copy `.env.example` to `.env` in the `web`, `mobile`, and `api` apps.
4. **Run Dev:** `turbo dev` (This starts the Mobile bundler, Web dev server, and Backend simultaneously).

---

### What's next?

> 📖 **Want to contribute?** Please read our [CONTRIBUTING.md](./CONTRIBUTING.md) to get started with our Monorepo and development workflow.

