# Development Workflow

This document describes how we build, test, and ship software at Blue Car Rental. It is written for everyone on the team, regardless of technical background.

---

## Branch Strategy

We use two branches. Think of them as two environments: one for work-in-progress and one for what our customers actually use.

### `test` -- The Development Branch

This is where all day-to-day work happens. Code is written, tested, and iterated on here. It is safe to experiment -- nothing on `test` affects the live application.

### `main` -- The Production Branch

What is on `main` is what is live and deployed. This branch represents exactly what our customers see and use. Changes only reach `main` after they have been reviewed and approved.

---

## Workflow

Follow these steps to get your work from development to production.

### 1. Do Your Work on `test`

Write your code and make your changes on the `test` branch. You can also create a feature branch off of `test` if you prefer to work in isolation, then merge it back into `test` when you are done.

### 2. Open a Pull Request from `test` to `main`

When your changes on `test` are working correctly and ready for production, open a Pull Request (PR) targeting `main`. In the PR description, explain what the changes do and why they are being made.

### 3. Review and Approval

The development manager, Gudmundur (gudmundur@bluecarrental.is), reviews the Pull Request. He will check the changes for correctness, security, and overall quality. If anything needs to be fixed, he will leave comments on the PR.

### 4. Merge and Deploy

Once the PR is approved, it gets merged into `main`. The application automatically deploys from `main`, so your changes will be live shortly after the merge.

---

## Rules

These rules are enforced at the repository level. They are not optional.

- **No direct pushes to `main`.** All changes to `main` must go through a Pull Request. No exceptions.
- **PRs to `main` require at least one approval.** A Pull Request cannot be merged until it has been reviewed and approved.
- **The development manager is the gatekeeper.** Gudmundur is responsible for approving changes before they reach production.
- **Force pushes to `main` are blocked.** You cannot rewrite the history of the production branch.
- **`main` cannot be deleted.** The production branch is permanently protected.

---

## Our Philosophy

Code is cheap now. Anyone on the team can build something with AI, and if those solutions benefit the company, that is fantastic. We encourage it.

But what our customers see must work. Every time.

The ability to write code quickly does not remove the need for careful judgment about what goes live. A broken feature, a security gap, or a bad deploy costs more than the time it takes to review a Pull Request. Our job is not to slow things down -- it is to make sure we ship with confidence.

## Why the Review Gate Exists

The review gate is how we balance speed with safety. Before anything reaches production, it must pass through a human review. When Gudmundur reviews a Pull Request, he is checking for:

- **Does it work?** The change should do what it claims to do.
- **Is it safe?** No vulnerabilities, no exposed secrets, no data leaks.
- **Does it break anything?** The most important question. What our users rely on today must keep working tomorrow.
- **Is it understandable?** If no one can read it six months from now, it becomes a liability.

This single approval step is the line between "work in progress" and "live in production." It protects our customers and it protects the business.

Take the review process seriously. Write clear PR descriptions. Respond to feedback promptly. Build fast, but ship safely.
