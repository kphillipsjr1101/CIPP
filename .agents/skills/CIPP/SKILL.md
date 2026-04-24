```markdown
# CIPP Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill teaches you how to contribute to the CIPP codebase, a Next.js application written in JavaScript. You'll learn the project's coding conventions, how to add or update standards and alerts, enhance Exchange user management features, and introduce new React components with proper integration. The guide also covers typical commit patterns, testing file structure, and provides ready-to-use commands for common workflows.

## Coding Conventions

- **File Naming:**  
  Use PascalCase for file names, especially for React components.  
  _Example:_  
  ```
  src/components/CippComponents/CippAliasDialog.jsx
  ```

- **Import Style:**  
  Use relative imports for modules and components.  
  _Example:_  
  ```javascript
  import CippAliasDialog from '../../CippComponents/CippAliasDialog';
  ```

- **Export Style:**  
  Use default exports for components and modules.  
  _Example:_  
  ```javascript
  export default CippAliasDialog;
  ```

- **Commit Patterns:**  
  - Prefix with `feat` for features (e.g., `feat: add mailbox limits`)
  - Messages are short (~40 characters)
  - Freeform for other types

## Workflows

### Add or Update Standard
**Trigger:** When you need to introduce or modify a standard (e.g., mailbox limits, guest access, resource mailbox behavior).  
**Command:** `/add-standard`

1. Edit `src/data/standards.json` to add or update the relevant standard entry.
2. Optionally update or create related documentation or PowerShell command references.

_Example:_  
```json
[
  {
    "name": "MailboxLimit",
    "description": "Maximum mailbox size in GB",
    "value": 50
  }
]
```

---

### Add or Update Alert
**Trigger:** When you want to introduce or update an alert configuration (e.g., monitor recipient rate limits).  
**Command:** `/add-alert`

1. Edit `src/data/alerts.json` to add or update the alert definition.
2. Update `src/pages/tenant/administration/alert-configuration/alert.jsx` to handle new alert logic or UI.
3. Optionally update `cspell.json` if new terminology is introduced.

_Example:_  
```json
[
  {
    "id": "TERRL",
    "description": "Recipient rate limit exceeded",
    "enabled": true
  }
]
```

---

### Enhance Exchange User Page
**Trigger:** When you want to add, improve, or fix Exchange mailbox/user management features (aliases, permissions, forwarding, etc.).  
**Command:** `/update-exchange-user-page`

1. Edit `src/pages/identity/administration/users/user/exchange.jsx` to implement or update the feature.
2. If new dialogs/components are needed, create or update files in `src/components/CippComponents/` (e.g., `CippAliasDialog.jsx`, `CippMailboxPermissionsDialog.jsx`).
3. Optionally update `src/components/CippFormPages/CippExchangeSettingsForm.jsx` for form logic.

_Example (adding a dialog):_  
```javascript
import CippAliasDialog from '../../../components/CippComponents/CippAliasDialog';

// ...inside component render
<CippAliasDialog
  open={isDialogOpen}
  onClose={handleClose}
  user={user}
/>
```

---

### Add or Update Component with Related Usage
**Trigger:** When you want to introduce a new UI component and immediately use it in the app.  
**Command:** `/add-component`

1. Create a new component file in `src/components/` (e.g., `CippDocsLookup.jsx`, `CippApiDialog.jsx`).
2. Edit one or more files to use the new component (e.g., `CippApiResults.jsx`, `exchange.jsx`).

_Example:_  
```javascript
// src/components/CippComponents/CippDocsLookup.jsx
const CippDocsLookup = ({ docId }) => (
  <div>Documentation for {docId}</div>
);
export default CippDocsLookup;

// Usage in another component
import CippDocsLookup from './CippDocsLookup';

<CippDocsLookup docId="mailbox-limits" />
```

## Testing Patterns

- **Test File Pattern:**  
  Test files use the `.test.ts` extension and are colocated with or near the code under test.  
  _Example:_  
  ```
  src/components/CippComponents/CippAliasDialog.test.ts
  ```

- **Testing Framework:**  
  Not explicitly detected; refer to project documentation or package.json for specifics.

## Commands

| Command                   | Purpose                                                        |
|---------------------------|----------------------------------------------------------------|
| /add-standard             | Add or update a compliance or feature standard                 |
| /add-alert                | Add or update an alert configuration                           |
| /update-exchange-user-page| Enhance or fix Exchange user management features               |
| /add-component            | Add a new React component and integrate it into the application|
```
