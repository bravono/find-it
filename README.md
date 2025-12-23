# FindIt: Solo Dev Project Blueprint (SRD)

## 1. Project Overview

* **Name:** FindIt
* **Mission:** A lifestyle "Super-App" for NYSC, students, and job seekers to manage housing, income, and community needs.
* **Modules:** Flat Rentals, Flatmate Finder, Item Marketplace, Pay-to-Stay, and Chore Board.

## 2. Technical Stack (The "Solo-Friendly" Choice)

* **Frontend (Mobile):** React Native (with Expo for fast iterations).
* **Frontend (Web):** Next.js (hosted on Vercel) for the Landing Page & Admin Dash.
* **Backend:** Node.js (Express) on a Vercel/Render server.
* **Database:** PostgreSQL (via Supabase — handles Auth & Storage out of the box).
* **Payments:** Paystack (Webhooks for Escrow).

---


## 3. The "Trust & Verification" Strategy

Since automated APIs cost money, we will use a **Hybrid Identity Flow**:

1. **Tier 1 (Free):** Users verify their **Email/Phone** and link a **Bank Account** (using Paystack’s free "Resolve Account" API to confirm their real name).
2. **Tier 2 (Manual):** Users upload a photo of their **NYSC/Student ID**. You approve these via your Next.js Admin Dashboard (Total cost: **₦0**).
3. **Trust Score:** Every successful chore completion or rental stay adds `+10` points. Fraud/Reports deduct points.

---

## 5. Core User Flow (The Escrow Path)

*This is the most complex logic you will code. Use this flow:*

1. **Post:** User A posts a chore (₦2,000).
2. **Commit:** User B accepts. User A "Funds" the chore via Paystack.
3. **Hold:** Your backend receives the Paystack webhook and marks the Escrow record as `FUNDS_HELD`.
4. **Complete:** User B finishes and clicks "Done." User A confirms.
5. **Payout:** Your system triggers a **Paystack Transfer** to User B (minus a small platform fee).

---

## 5. Implementation Roadmap (Phase 1: The MVP)

1. **Week 1-2:** Set up Supabase (Auth + DB) and build the **Marketplace UI**.
2. **Week 3:** Integrate **Paystack** for simple item purchases.
3. **Week 4:** Build the **Flatmate Profile** (lifestyle tags and filtering).
4. **Week 5:** Launch "Alpha" to a small group of NYSC members for feedback.

---
