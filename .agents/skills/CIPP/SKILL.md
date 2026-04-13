```markdown
# CIPP Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you the key development patterns, coding conventions, and common workflows for contributing to the CIPP repository—a Next.js application written in JavaScript. You'll learn how to add or update standards and alerts, extend Exchange user management, integrate new React components, and merge feature branches, all while following the established code style and commit patterns.

## Coding Conventions

- **File Naming:**  
  Use PascalCase for files, especially components.  
  _Example:_  
  ```
  src/components/CippComponents/CippAliasDialog.jsx
  ```

- **Import Style:**  
  Use relative imports for modules within the project.  
  _Example:_  
  ```js
  import CippAliasDialog from '../../CippComponents/CippAliasDialog';
  ```

- **Export Style:**  
  Use default exports for components and modules.  
  _Example:_  
  ```js
  export default CippAliasDialog;
  ```

- **Commit Messages:**  
  - Prefix with `feat` for new features (optional, not enforced).
  - Freeform otherwise.
  - Keep messages concise (~40 characters).

## Workflows

### Add or Update Standard
**Trigger:** When you need to define or update a compliance or operational standard for the tenant.  
**Command:** `/add-standard`

1. Edit `src/data/standards.json` to add or update the relevant standard entry.
2. Optionally, update related documentation or PowerShell command references within the same JSON.

_Example:_
```json
{
  "mailboxLimit": {
    "description": "Set mailbox size limit",
    "powershell": "Set-Mailbox -Identity ... -ProhibitSendQuota ..."
  }
}
```

---

### Add or Update Alert
**Trigger:** When you want to introduce a new alert or modify alert logic for tenant monitoring.  
**Command:** `/add-alert`

1. Edit `src/data/alerts.json` to add or update the alert definition.
2. Edit `src/pages/tenant/administration/alert-configuration/alert.jsx` to implement or update the alert's UI/configuration.

_Example:_
```json
{
  "highMailboxUsage": {
    "description": "Alert when mailbox usage exceeds threshold",
    "threshold": 90
  }
}
```
```js
// In alert.jsx
import alerts from '../../../../data/alerts.json';
// ...update logic to handle new alert
```

---

### Extend Exchange User Management
**Trigger:** When you need to add, refactor, or fix mailbox/alias/calendar/permissions management for a user.  
**Command:** `/update-exchange-user`

1. Edit `src/pages/identity/administration/users/user/exchange.jsx` to update Exchange user management logic or UI.
2. Edit or add supporting components in:
   - `src/components/CippFormPages/`
   - `src/components/CippComponents/`
   as needed.

_Example:_
```js
import CippAliasDialog from '../../../components/CippComponents/CippAliasDialog';
// ...use <CippAliasDialog /> in the Exchange user page
```

---

### Add or Update Component with Test or Usage
**Trigger:** When you want to introduce new UI functionality or refactor dialog/component logic.  
**Command:** `/add-component`

1. Create or edit a component in `src/components/`.
2. Edit a page in `src/pages/` to utilize the new or updated component.

_Example:_
```js
// src/components/CippComponents/CippNewDialog.jsx
const CippNewDialog = () => { /* ... */ };
export default CippNewDialog;

// src/pages/somePage.jsx
import CippNewDialog from '../../components/CippComponents/CippNewDialog';
// ...use <CippNewDialog />
```

---

### Merge Feature or Fix Branch
**Trigger:** When you want to integrate a completed feature or bugfix into the dev branch.  
**Command:** `/merge-branch`

1. Merge the branch via GitHub or CLI.
2. Resolve any conflicts and ensure all related files are included.

_Example CLI:_
```sh
git checkout dev
git merge feature/my-new-feature
# Resolve conflicts if any
git push origin dev
```

---

## Testing Patterns

- **Test File Pattern:**  
  Test files are named with the `.test.ts` suffix.
  _Example:_  
  ```
  src/components/CippComponents/CippAliasDialog.test.ts
  ```

- **Testing Framework:**  
  Not explicitly detected; refer to project documentation or existing test files for specifics.

## Commands

| Command           | Purpose                                                            |
|-------------------|--------------------------------------------------------------------|
| /add-standard     | Add or update a compliance or operational standard                 |
| /add-alert        | Add or update an alert definition and its configuration UI         |
| /update-exchange-user | Enhance or fix Exchange user management features               |
| /add-component    | Add a new React component and integrate it into a page/component   |
| /merge-branch     | Merge a feature or fix branch into the main development branch     |
```