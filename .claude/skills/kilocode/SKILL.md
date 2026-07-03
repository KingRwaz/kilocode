```markdown
# kilocode Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you the core development patterns, coding conventions, and collaborative workflows used in the **kilocode** repository. The codebase is primarily TypeScript, built on the [Hono](https://hono.dev/) framework, and employs modern conventions for code organization, testing, and release management. You'll learn how to contribute features, fix bugs, manage tests, handle versioning, and work with TUI plugins using standardized processes.

---

## Coding Conventions

- **File Naming:**  
  Use **kebab-case** for all file names.
  > Example:  
  > `user-service.ts`, `api-handler.test.ts`

- **Import Style:**  
  Use **relative imports** for internal modules.
  > Example:  
  > ```ts
  > import { getUser } from './user-service';
  > ```

- **Export Style:**  
  Use **named exports** rather than default exports.
  > Example:  
  > ```ts
  > // user-service.ts
  > export function getUser(id: string) { ... }
  > ```

- **Commit Messages:**  
  Follow **conventional commit** format with these prefixes:  
  `chore`, `fix`, `test`, `feat`, `refactor`
  > Example:  
  > `feat: add user authentication middleware`

---

## Workflows

### Feature or Fix with Test and Changeset
**Trigger:** When adding a new feature or fixing a bug that should be tested and documented for release notes.  
**Command:** `/feature-with-test`

1. Edit or create implementation files in `packages/opencode/src/...`.
2. Add or update corresponding test files in `packages/opencode/test/...`.
3. Add a `.changeset/*.md` file describing the change.
4. Commit all changes with a conventional commit message.

> Example:
> ```
> feat: support multi-user sessions
> ```

---

### Feature or Fix with Test (No Changeset)
**Trigger:** When adding a new feature or fix that is internal or not user-facing (no release note needed).  
**Command:** `/feature-internal`

1. Edit or create implementation files in `packages/opencode/src/...`.
2. Add or update corresponding test files in `packages/opencode/test/...`.
3. Commit changes with a conventional commit message.

> Example:
> ```
> fix: correct edge case in token refresh logic
> ```

---

### Generate or Sync After Feature
**Trigger:** After adding a feature or fix, when generated files or test outputs need updating.  
**Command:** `/generate`

1. Run code generation or test update scripts.
2. Commit changes to generated files (e.g., `.gen.ts`, `.json`, updated test snapshots).
3. Ensure all generated/test files are up to date.

> Example:
> ```
> chore: update openapi.json and test snapshots
> ```

---

### Update Nix Node Modules Hashes
**Trigger:** After changing dependencies or `package.json`, to keep Nix builds reproducible.  
**Command:** `/update-nix-hashes`

1. Run the hash update script.
2. Commit changes to `nix/hashes.json`.

> Example:
> ```
> chore: update nix node_modules hashes
> ```

---

### Version Bump & Sync Release
**Trigger:** When preparing a new release and synchronizing package versions and lockfiles.  
**Command:** `/sync-versions`

1. Update version numbers in all relevant `package.json` files.
2. Update lockfiles (`bun.lock`, `package-lock.json`, etc.).
3. Commit all updated files.

> Example:
> ```
> chore: bump versions for v1.2.0 release
> ```

---

### TUI Plugin or Keymap Feature
**Trigger:** When adding or updating a TUI plugin or keymap functionality.  
**Command:** `/tui-plugin`

1. Edit or create TUI plugin/keymap files in `packages/opencode/src/cli/cmd/tui/...`.
2. Update or add config/schema/spec files as needed.
3. Add or update related tests in `packages/opencode/test/cli/tui/...`.
4. Optionally update documentation in `packages/web/src/content/docs/...`.

> Example:
> ```
> feat: add fuzzy search to TUI command palette
> ```

---

## Testing Patterns

- **Framework:** [Playwright](https://playwright.dev/)
- **Test File Pattern:** `*.test.ts` (e.g., `user-service.test.ts`)
- **Location:** All tests are placed under `packages/opencode/test/`
- **Test Example:**
  ```ts
  import { test, expect } from '@playwright/test';
  import { getUser } from '../src/user-service';

  test('getUser returns correct user', async () => {
    const user = await getUser('123');
    expect(user.id).toBe('123');
  });
  ```

---

## Commands

| Command            | Purpose                                                        |
|--------------------|----------------------------------------------------------------|
| /feature-with-test | Add a new feature or fix with tests and a changeset            |
| /feature-internal  | Add a new feature or fix with tests (no changeset)             |
| /generate          | Run code generation or sync generated/test files                |
| /update-nix-hashes | Update Nix node_modules hashes after dependency changes         |
| /sync-versions     | Synchronize package versions and lockfiles for a new release    |
| /tui-plugin        | Add or update a TUI plugin or keymap feature                   |
```
