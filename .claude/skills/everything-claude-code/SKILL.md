```markdown
# everything-claude-code Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches the core development patterns, coding conventions, and collaborative workflows used in the `everything-claude-code` repository. The project is primarily JavaScript-based, with a focus on modular AI skills, agent definitions, and extensible installation targets. No major framework is used, and contributions are managed through well-defined, command-driven workflows.

## Coding Conventions

- **File Naming:**  
  Use `camelCase` for JavaScript files and directories.  
  *Example:*  
  ```
  scripts/lib/installTargets.js
  skills/textSummarizer/SKILL.md
  ```

- **Import Style:**  
  Use relative imports for modules.  
  *Example:*  
  ```js
  const installTarget = require('../lib/installTargets');
  ```

- **Export Style:**  
  Mixed: both CommonJS (`module.exports`) and ES module (`export`) styles may be found.  
  *Example (CommonJS):*  
  ```js
  module.exports = function doSomething() { ... };
  ```
  *Example (ESM):*  
  ```js
  export function doSomething() { ... }
  ```

- **Commit Messages:**  
  Use prefixes: `fix`, `feat`, `docs`, `chore`.  
  Keep messages concise (~58 characters on average).  
  *Example:*  
  ```
  feat: add install target for VSCode
  fix: correct path resolution in install script
  ```

## Workflows

### Add New Skill or Agent
**Trigger:** When introducing a new AI skill or agent  
**Command:** `/add-skill`

1. Create a new `SKILL.md` (for skills) or agent definition file in `skills/` or `agents/`.
2. Add supporting files (scripts, prompts, etc.) as needed.
3. Update `manifests/install-modules.json` to register the new skill/agent.
4. Update `AGENTS.md` and/or `README.md` to document the addition.
5. Optionally, add or update tests.

*Example directory structure:*
```
skills/textSummarizer/
  SKILL.md
  summarizer.js
```

---

### Add or Update Install Target
**Trigger:** When supporting a new IDE, plugin, or integration  
**Command:** `/add-install-target`

1. Add install/uninstall scripts (`install.js`, `install.sh`, etc.) under a dedicated directory (e.g., `.codebuddy/`).
2. Update `manifests/install-modules.json` to include the new target.
3. Update schemas:  
   - `schemas/ecc-install-config.schema.json`  
   - `schemas/install-modules.schema.json`
4. Add or update logic in `scripts/lib/install-targets/*.js`.
5. Update or add tests in `tests/lib/install-targets.test.js`.
6. Update documentation (`README.md`).

*Example:*
```
.codebuddy/vscode/install.js
.codebuddy/vscode/uninstall.sh
```

---

### Add or Update Command
**Trigger:** When introducing or enhancing a CLI command  
**Command:** `/add-command`

1. Create or update a markdown file in `commands/` (e.g., `commands/prp-commit.md`).
2. Optionally, update YAML frontmatter, documentation, or templates.
3. Address PR review feedback.
4. Update references in `plan.md` or `code-review.md` as needed.

*Example:*
```
commands/prp-commit.md
```

---

### Dependency Update via Dependabot or Manual
**Trigger:** When dependencies need updating for security, compatibility, or features  
**Command:** `/update-dependencies`

1. Update dependency versions in `package.json`, `yarn.lock`, `package-lock.json`, etc.
2. Regenerate lockfiles as needed.
3. Update `.github/workflows/*` if CI dependencies are involved.
4. Optionally, update `.github/dependabot.yml` for automation.

*Example:*
```json
// package.json
"dependencies": {
  "express": "^4.18.2"
}
```

---

### Refactor or Fix Hook or Script
**Trigger:** When fixing or refactoring a hook/script for CI, security, or reliability  
**Command:** `/fix-hook`

1. Edit `scripts/hooks/*.js`, `hooks/hooks.json`, or related shell scripts.
2. Update/add tests in `tests/hooks/` or `tests/scripts/`.
3. Update documentation if behavior changes.
4. Regenerate lockfiles if dependencies are changed.

*Example:*
```
scripts/hooks/precommit.js
tests/hooks/precommit.test.js
```

---

### Revert or Remove Feature
**Trigger:** When a feature, skill, or plugin needs to be removed or reverted  
**Command:** `/revert-feature`

1. Delete or revert the relevant `SKILL.md`, agent, or plugin files.
2. Update `manifests/install-modules.json` or other registries as needed.
3. Document the reason for removal in the commit message.

*Example:*
```
git rm skills/textSummarizer/SKILL.md
```

## Testing Patterns

- **Test File Pattern:**  
  All test files should be named with the `.test.js` suffix and placed alongside or within a `tests/` directory.  
  *Example:*  
  ```
  tests/lib/install-targets.test.js
  ```

- **Framework:**  
  No specific testing framework detected; use standard Node.js assertions or your preferred test runner.

- **Test Example:**  
  ```js
  // tests/lib/install-targets.test.js
  const assert = require('assert');
  const installTarget = require('../../scripts/lib/installTargets');

  describe('installTarget', () => {
    it('should install VSCode target', () => {
      assert(installTarget('vscode'));
    });
  });
  ```

## Commands

| Command              | Purpose                                                        |
|----------------------|----------------------------------------------------------------|
| /add-skill           | Add a new AI skill or agent                                    |
| /add-install-target  | Add or update an install target (IDE, plugin, integration)     |
| /add-command         | Add or update a CLI command                                    |
| /update-dependencies | Update dependencies or lockfiles                               |
| /fix-hook            | Refactor or fix a hook or script                               |
| /revert-feature      | Revert or remove a feature, skill, or plugin                   |
```
