```markdown
# CIPP Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you how to contribute to the CIPP codebase, a Next.js application written in JavaScript. You'll learn the project's coding conventions, file organization, and the main workflows for adding standards, alerts, Exchange user features, and new UI components. This guide includes step-by-step instructions, code examples, and suggested commands to streamline your development process.

## Coding Conventions

- **File Naming:**  
  Use PascalCase for component and page files.  
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
  - Prefix feature commits with `feat`
  - Commit messages are freeform, ~40 characters on average  
  _Example:_  
  ```
  feat: add mailbox forwarding dialog
  ```

## Workflows

### Add or Update Standard
**Trigger:** When you want to introduce a new compliance/configuration standard or modify an existing one (e.g., mailbox recipient limits, guest access, disabling accounts).  
**Command:** `/add-standard`

1. Edit `src/data/standards.json` to add or update the relevant standard entry.
2. Optionally, update related documentation or PowerShell command equivalents within the standard entry.

_Example:_
```json
{
  "name": "Mailbox Recipient Limit",
  "description": "Sets the maximum number of recipients per mailbox.",
  "powershell": "Set-Mailbox -RecipientLimits 500"
}
```

---

### Add or Update Alert
**Trigger:** When you want to introduce a new alert or modify an existing alert for tenant monitoring (e.g., TERRL alert).  
**Command:** `/add-alert`

1. Edit `src/data/alerts.json` to add or update the alert entry.
2. Update `src/pages/tenant/administration/alert-configuration/alert.jsx` to handle the new or updated alert in the UI.

_Example:_
```json
{
  "id": "TERRL",
  "description": "Tenant External Relay Limit Alert",
  "enabled": true
}
```
```javascript
// In alert.jsx
import alerts from '../../../data/alerts.json';
// ...handle new alert logic
```

---

### Exchange User Page Enhancement
**Trigger:** When you want to add, fix, or refactor Exchange-related user management features (e.g., mailbox permissions, alias management, forwarding, calendar permissions).  
**Command:** `/update-exchange-user-page`

1. Edit `src/pages/identity/administration/users/user/exchange.jsx` to implement the new feature or fix.
2. Optionally, update or create related dialog/component files in:
   - `src/components/CippComponents/`
   - `src/components/CippFormPages/`

_Example:_
```javascript
// Add new alias dialog integration
import CippAliasDialog from '../../../components/CippComponents/CippAliasDialog';

// ...in component render
<CippAliasDialog open={showAliasDialog} onClose={handleClose} />
```

---

### Add or Update Component with Integration
**Trigger:** When you want to introduce a new UI component (e.g., documentation lookup, dialog) and integrate it into an existing workflow.  
**Command:** `/add-component`

1. Create new component file(s) in `src/components/`.
2. Edit the relevant existing component or page to import and use the new component.

_Example:_
```javascript
// src/components/CippComponents/CippDocsLookup.jsx
const CippDocsLookup = () => { /* ... */ };
export default CippDocsLookup;

// Integrate into a page
import CippDocsLookup from '../../components/CippComponents/CippDocsLookup';

<CippDocsLookup />
```

## Testing Patterns

- **Test Framework:** Unknown (not detected in analysis)
- **Test File Pattern:**  
  Test files use the `.test.ts` suffix and are likely colocated with the code they test or in a `__tests__` directory.

_Example:_
```
src/components/CippComponents/CippAliasDialog.test.ts
```

## Commands

| Command                  | Purpose                                                        |
|--------------------------|----------------------------------------------------------------|
| /add-standard            | Add or update a compliance/configuration standard              |
| /add-alert               | Add or update an alert configuration for tenant monitoring     |
| /update-exchange-user-page | Enhance, fix, or refactor Exchange user management features   |
| /add-component           | Add a new UI component and integrate it into the application   |
```
