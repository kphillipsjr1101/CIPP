```markdown
# CIPP Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill teaches you how to contribute effectively to the CIPP codebase, a Next.js application written in JavaScript. You'll learn the project's coding conventions, common workflows for updating standards, alerts, and Exchange user features, as well as how to add reusable components. The guide includes step-by-step instructions, code examples, and suggested commands for frequent tasks.

## Coding Conventions

### File Naming
- Use **PascalCase** for component and page files.
  - Example: `CippAliasDialog.jsx`, `CippExchangeSettingsForm.jsx`

### Imports
- Use **relative imports** for modules and components.
  ```javascript
  import CippAliasDialog from '../../CippComponents/CippAliasDialog';
  ```

### Exports
- Use **default exports** for components.
  ```javascript
  export default CippAliasDialog;
  ```

### Commit Messages
- Use the `feat` prefix for new features.
- Messages are freeform and concise (~40 characters).
  - Example: `feat: add mailbox permissions dialog`

## Workflows

### Add or Update a Standard
**Trigger:** When you want to introduce or modify a standard (e.g., mailbox limits, guest access, resource mailbox handling).
**Command:** `/add-standard`

1. Edit `src/data/standards.json` to add or update the standard entry.
   ```json
   {
     "name": "Mailbox Size Limit",
     "description": "Maximum mailbox size in GB",
     "value": 50
   }
   ```
2. Optionally update related documentation or PowerShell equivalents in the same file.

---

### Add or Update an Alert
**Trigger:** When you want to introduce a new alert or update alert configuration (e.g., for recipient rate limits).
**Command:** `/add-alert`

1. Edit `src/data/alerts.json` to add or update the alert.
   ```json
   {
     "id": "recipientRateLimit",
     "description": "Recipient rate limit exceeded",
     "threshold": 1000
   }
   ```
2. Update `src/pages/tenant/administration/alert-configuration/alert.jsx` to implement or reflect the alert in the UI.
   ```javascript
   import alerts from '../../../data/alerts.json';
   // Use the new or updated alert in the component logic
   ```

---

### Enhance Exchange User Page
**Trigger:** When you want to add, refactor, or fix Exchange-related user management features.
**Command:** `/update-exchange-user-page`

1. Edit `src/pages/identity/administration/users/user/exchange.jsx` to implement or fix features.
   ```javascript
   import CippMailboxPermissionsDialog from '../../../../../../components/CippComponents/CippMailboxPermissionsDialog';
   // Add or update logic for mailbox, alias, or permissions
   ```
2. Optionally update or create supporting components in:
   - `src/components/CippFormPages/CippExchangeSettingsForm.jsx`
   - `src/components/CippComponents/CippAliasDialog.jsx`
   - `src/components/CippComponents/CippCalendarPermissionsDialog.jsx`
   - `src/components/CippComponents/CippMailboxPermissionsDialog.jsx`

---

### Add or Update Component with Related Usage
**Trigger:** When you want to introduce a reusable UI component and immediately use it in the app.
**Command:** `/add-component`

1. Create or update a component in `src/components/` (e.g., `CippDocsLookup`, `CippApiDialog`).
   ```javascript
   // src/components/CippComponents/CippDocsLookup.jsx
   const CippDocsLookup = () => { /* ... */ };
   export default CippDocsLookup;
   ```
2. Edit one or more files that use or display this component, such as:
   - `src/components/CippComponents/CippApiResults.jsx`
   - `src/pages/_app.js`
   ```javascript
   import CippDocsLookup from './CippDocsLookup';
   // Use <CippDocsLookup /> in the render tree
   ```

## Testing Patterns

- **Test files** use the pattern `*.test.ts`.
- The specific testing framework is unknown, but tests are likely colocated with the code they test.
- Example test file: `src/components/CippComponents/CippAliasDialog.test.ts`

## Commands

| Command                  | Purpose                                                        |
|--------------------------|----------------------------------------------------------------|
| /add-standard            | Add or update a compliance/configuration standard              |
| /add-alert               | Add or update a tenant monitoring alert                        |
| /update-exchange-user-page| Enhance or fix Exchange user management features              |
| /add-component           | Add a reusable component and integrate it into the app         |
```
