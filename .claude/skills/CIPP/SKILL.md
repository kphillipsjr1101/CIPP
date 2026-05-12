```markdown
# CIPP Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you how to contribute to the CIPP codebase, a Next.js application written in JavaScript. You'll learn the project's coding conventions, file organization, and step-by-step workflows for common tasks such as adding standards, defining alerts, developing features, refactoring dialogs, and introducing shared components. The guide also covers testing patterns and provides handy commands for frequent operations.

## Coding Conventions

- **File Naming:**  
  Use **PascalCase** for component and page files.  
  _Example:_  
  ```
  src/components/CippFormPages/CippExchangeSettingsForm.jsx
  src/pages/identity/administration/users/user/exchange.jsx
  ```

- **Import Style:**  
  Use **relative imports** for modules within the project.  
  _Example:_  
  ```javascript
  import CippApiDialog from '../../CippComponents/CippApiDialog';
  ```

- **Export Style:**  
  Use **default exports** for components and modules.  
  _Example:_  
  ```javascript
  export default CippExchangeSettingsForm;
  ```

- **Commit Patterns:**  
  - Prefix with `feat` for new features.
  - Commit messages are freeform and average around 40 characters.

## Workflows

### Add or Update Standard
**Trigger:** When introducing or modifying a compliance/configuration standard (e.g., mailbox limits, guest access).  
**Command:** `/add-standard`

1. Edit or add an entry in `src/data/standards.json`.
2. Optionally, update related documentation or PowerShell commands within the standard entry.

_Example:_
```json
{
  "name": "MailboxLimit",
  "description": "Set mailbox size limit",
  "powershell": "Set-Mailbox -Identity ... -ProhibitSendQuota ..."
}
```

---

### Add or Update Alert
**Trigger:** When adding a new alert or changing alert logic/configuration for tenant monitoring.  
**Command:** `/add-alert`

1. Edit or add an entry in `src/data/alerts.json`.
2. Update `src/pages/tenant/administration/alert-configuration/alert.jsx` to reflect alert changes.

_Example:_
```json
{
  "id": "mailbox-over-quota",
  "description": "Mailbox is over quota",
  "severity": "high"
}
```
```javascript
// In alert.jsx
import alerts from '../../../data/alerts.json';
// ...update alert rendering logic as needed
```

---

### Feature Development with Shared Component and Page
**Trigger:** When adding or enhancing a feature that involves both backend logic (component) and UI (page) changes.  
**Command:** `/feature-dev`

1. Update or create a component in `src/components/` (e.g., `CippFormPages`, `CippCards`, `CippComponents`).
2. Update the corresponding page in `src/pages/` (e.g., `user/exchange.jsx`).
3. Test the integration between the component and the page.

_Example:_
```javascript
// src/components/CippFormPages/CippExchangeSettingsForm.jsx
export default function CippExchangeSettingsForm(props) {
  // component logic
}

// src/pages/identity/administration/users/user/exchange.jsx
import CippExchangeSettingsForm from '../../../components/CippFormPages/CippExchangeSettingsForm';
// ...use the component in the page
```

---

### Refactor or Enhance Dialogs for User Exchange
**Trigger:** When modularizing or extending dialog functionality for Exchange user management.  
**Command:** `/refactor-dialogs`

1. Create or update dialog components in `src/components/CippComponents/` (e.g., `CippAliasDialog`, `CippCalendarPermissionsDialog`, `CippMailboxPermissionsDialog`).
2. Update `src/pages/identity/administration/users/user/exchange.jsx` to use the new or refactored dialogs.

_Example:_
```javascript
// src/components/CippComponents/CippAliasDialog.jsx
export default function CippAliasDialog(props) {
  // dialog logic
}

// src/pages/identity/administration/users/user/exchange.jsx
import CippAliasDialog from '../../../components/CippComponents/CippAliasDialog';
// ...use the dialog in the page
```

---

### Add or Update Shared Component and Usage
**Trigger:** When introducing reusable UI logic and immediately applying it.  
**Command:** `/add-component`

1. Create a new component in `src/components/`.
2. Update one or more files to use the new component (e.g., `CippApiResults.jsx`, `CippApiDialog.jsx`).

_Example:_
```javascript
// src/components/CippComponents/CippDocsLookup.jsx
export default function CippDocsLookup(props) {
  // component logic
}

// src/components/CippComponents/CippApiDialog.jsx
import CippDocsLookup from './CippDocsLookup';
// ...integrate the new component
```

## Testing Patterns

- **Test File Pattern:**  
  Test files are named with the `.test.ts` suffix (e.g., `Component.test.ts`).
- **Testing Framework:**  
  The specific framework is unknown, but standard JavaScript/TypeScript testing conventions likely apply.

_Example:_
```typescript
// src/components/CippComponents/CippApiDialog.test.ts
describe('CippApiDialog', () => {
  it('renders without crashing', () => {
    // test implementation
  });
});
```

## Commands

| Command         | Purpose                                                        |
|-----------------|----------------------------------------------------------------|
| /add-standard   | Add or update a compliance/configuration standard              |
| /add-alert      | Add or modify an alert definition and its configuration UI     |
| /feature-dev    | Develop or enhance a feature with shared component and page    |
| /refactor-dialogs | Refactor or enhance dialog components for user Exchange      |
| /add-component  | Add a new shared component and integrate it into the codebase  |
```
