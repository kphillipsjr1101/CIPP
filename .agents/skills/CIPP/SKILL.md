```markdown
# CIPP Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill provides a comprehensive guide to contributing to the CIPP codebase, a Next.js application written in JavaScript. It covers coding conventions, common workflows, and best practices for adding features, updating standards or alerts, and integrating new components. Whether you're updating compliance standards, enhancing Exchange user management, or merging feature branches, this guide will help you follow the project's established patterns for consistency and maintainability.

## Coding Conventions

**File Naming:**  
- Use PascalCase for component and page files.
  - Example: `CippExchangeSettingsForm.jsx`, `AlertConfiguration.jsx`

**Import Style:**  
- Use relative imports for modules and components.
  ```js
  import CippExchangeSettingsForm from '../../components/CippFormPages/CippExchangeSettingsForm';
  ```

**Export Style:**  
- Use default exports for components and modules.
  ```js
  // src/components/CippExchangeSettingsForm.jsx
  export default function CippExchangeSettingsForm(props) {
    // ...
  }
  ```

**Commit Messages:**  
- Use freeform messages, often with a `feat` prefix.
  - Example: `feat: add mailbox permissions dialog`
- Average commit message length: ~40 characters.

## Workflows

### Add or Update Standard
**Trigger:** When introducing or modifying a compliance or configuration standard (e.g., for tenants or mailboxes).  
**Command:** `/add-standard`

1. Edit or add an entry in `src/data/standards.json`.
2. Optionally update related documentation or PowerShell command references.

**Example:**
```json
// src/data/standards.json
[
  {
    "id": "mailbox-retention",
    "name": "Mailbox Retention Policy",
    "description": "Ensures mailboxes are retained for 30 days after deletion."
  }
]
```

---

### Add or Update Alert
**Trigger:** When adding a new alert or modifying an existing alert for tenant monitoring.  
**Command:** `/add-alert`

1. Edit or add an entry in `src/data/alerts.json`.
2. Update `src/pages/tenant/administration/alert-configuration/alert.jsx` to reflect the new or changed alert.

**Example:**
```json
// src/data/alerts.json
[
  {
    "id": "mailbox-quota",
    "name": "Mailbox Quota Exceeded",
    "severity": "high"
  }
]
```
```js
// src/pages/tenant/administration/alert-configuration/alert.jsx
import alerts from '../../../data/alerts.json';
// ...update UI to include new alert
```

---

### Exchange User Page Enhancement
**Trigger:** When adding, refactoring, or fixing Exchange-related user management features.  
**Command:** `/update-exchange-user-page`

1. Edit `src/pages/identity/administration/users/user/exchange.jsx` to add or update features.
2. Edit or create supporting components in `src/components/CippFormPages/` or `src/components/CippComponents/` as needed.
3. Test and refine the UI and logic.

**Example:**
```js
// src/pages/identity/administration/users/user/exchange.jsx
import CippExchangeSettingsForm from '../../../components/CippFormPages/CippExchangeSettingsForm';
// ...use new or updated form component
```

---

### Add or Update Component and Usage
**Trigger:** When introducing a reusable UI component and integrating it into the app.  
**Command:** `/add-component`

1. Create a new component file in `src/components/`.
2. Edit an existing page or component to use the new component.
3. Test the integration.

**Example:**
```js
// src/components/CippCustomButton.jsx
export default function CippCustomButton({ label, onClick }) {
  return <button onClick={onClick}>{label}</button>;
}

// src/pages/dashboard.jsx
import CippCustomButton from '../components/CippCustomButton';
```

---

### Merge Feature Branch
**Trigger:** When integrating a completed feature or fix into the main development line.  
**Command:** `/merge-feature`

1. Merge the feature branch via git.
2. Resolve any conflicts.
3. Update multiple files across `src/components/`, `src/data/`, and `src/pages/` as needed.

**Example:**
```sh
git checkout dev
git merge feature/my-new-feature
# Resolve conflicts if prompted
```

## Testing Patterns

- Test files use the `.test.ts` pattern (TypeScript test files).
- The specific testing framework is unknown, but tests are likely colocated with the code under test.
- Example file: `src/components/CippExchangeSettingsForm.test.ts`

## Commands

| Command             | Purpose                                                        |
|---------------------|----------------------------------------------------------------|
| /add-standard       | Add or update a compliance/configuration standard              |
| /add-alert          | Add or update an alert definition and its configuration UI     |
| /update-exchange-user-page | Enhance or fix Exchange user management features        |
| /add-component      | Add a new reusable component and integrate it                  |
| /merge-feature      | Merge a feature branch into the main development branch        |
```
