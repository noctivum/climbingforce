# Contributing to Noctivum Climbing App

First of all, welcome! Thank you for taking the time to contribute to the project.

Whether you are fixing a bug, proposing a new user story, refactoring an architectural enabler, or tweaking design tokens, please take a moment to read this guide to ensure a smooth and consistent workflow.

---

## 1. Ground Rules & Mindset

- **User Value First:** Every user-facing feature starts with a clear User Story following the INVEST principle and testable Gherkin acceptance criteria.
- **Architectural Runway:** Structural changes must be documented via Architectural Decision Records (ADRs) under `/docs/adr/`.
- **Quality is Non-Negotiable:** Every pull request requires passing automated tests and adherence to clean code principles.

---

## 2. Getting Started (Fork & Branch Workflow)

1. **Fork the Repository:** Create your own fork under your GitHub account.
2. **Clone your Fork locally:**
   ```bash
   git clone https://github.com/<your-username>/climbing-app.git
   cd climbing-app
   ```
3. **Set Up Remote Upstream:**
   ```bash
   git remote add upstream https://github.com/noctivum/climbing-app.git
   ```
4. **Create a Feature Branch:** Always branch off `main`:
   ```bash
   git checkout -b <branch-type>/<short-description>
   ```

### Branch Naming Conventions
Use descriptive, lower-case branch names prefixed by their purpose:

| Prefix | Usage / Context | Example |
| :--- | :--- | :--- |
| `feat/` | New user-facing story / feature | `feat/hangboard-timer` |
| `fix/` | Bug fix resolving an existing issue | `fix/offline-sync-retry` |
| `enabler/` | Architecture, refactoring, infra | `enabler/sqlite-persistence` |
| `docs/` | Documentation, ADR updates, guides | `docs/adr-0003-auth-flow` |
| `design/` | Noctivum design system & tokens | `design/dark-mode-palette` |

---

## 3. Commit Message Guidelines (Conventional Commits)

We strictly follow the [Conventional Commits](https://www.conventionalcommits.org/) standard. This allows automated changelog generation and maintains a crystal-clear Git history.

### Format
```text
<type>(<optional scope>): <imperative subject summary>

[optional detailed body explaining WHY, not WHAT]

[optional issue reference, e.g. Closes #42]
```

### Allowed Types
* `feat`: A new feature or User Story implementation
* `fix`: A bug fix
* `refactor`: Code change that neither fixes a bug nor adds a feature
* `test`: Adding or correcting tests
* `docs`: Documentation only changes
* `style`: Changes that do not affect code logic (formatting, white-space)
* `chore`: Maintenance tasks, dependency updates, CI/CD tweaks

### Good Examples
* `feat(tracking): persist completed workout sets in indexeddb`
* `fix(timer): prevent countdown freeze when app is backgrounded`
* `refactor(domain): decouple workout entity from persistence models`

---

## 4. Design System & Aesthetics (Noctivum Guidelines)

If your changes involve UI components:
* **No Hardcoded Hex Colors or Magic Numbers:** Always import tokens from `/src/theme/tokens`.
* **Theme Consistency:** UI must adhere to the Noctivum dark aesthetic and meet WCAG 2.1 AA contrast requirements.
* **Component Primitives:** Re-use existing primitives (`Button`, `Card`, `Badge`) before introducing custom elements.

---

## 5. Submitting a Pull Request (PR)

1. **Sync with Upstream:** Ensure your branch is rebased onto the latest `upstream/main`:
   ```bash
   git fetch upstream
   git rebase upstream/main
   ```
2. **Run Quality Checks:**
   ```bash
   npm run lint        # Code style & typing verification
   npm test            # All unit & integration tests must pass
   ```
3. **Open the Pull Request:**
   * Push your branch to your fork: `git push origin <branch-type>/<description>`.
   * Open a PR against `noctivum/climbing-app` (`base: main`).
4. **Complete the PR Template:**
   * Link the relevant Issue (`Closes #123`).
   * Tick off the checkboxes in the Quality & Compliance checklist (Tests, Self-Review, GDPR, Noctivum Style Guide).
5. **Code Review:** Address feedback or suggestions promptly. Once CI is green and the review is approved, your branch will be squash-merged.

---

## 6. Filing Issues & Proposing Stories

Before writing code for non-trivial changes, please open an Issue using one of our GitHub Issue Forms:
* **User Story:** For new end-user features.
* **Enabler Story:** For infrastructure, performance, or architectural spikes.
* **Bug Report:** For unexpected behavior with clear reproduction steps.

Thank you for helping craft clean, resilient software!
