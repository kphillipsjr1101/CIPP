```markdown
# CIPP Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you how to contribute to the CIPP codebase, a Next.js application written in JavaScript. You'll learn the project's coding conventions, how to add or update compliance standards and alerts, enhance Exchange user settings, and create reusable React components. The guide also covers commit patterns, file organization, and how to run or write tests.

## Coding Conventions

- **File Naming:** Use PascalCase for component and page files.
  - Example: `CippAliasDialog.jsx`, `CippExchangeSettingsForm.jsx`

- **Import Style:** Use relative imports for modules within the project.
  ```js
  import CippAliasDialog from '../CippComponents/CippAliasDialog';
  ```

- **Export Style:** Use default exports for components and modules.
  ```js
  export default function CippAliasDialog(props) { ... }
  ```

- **Commit Messages:**
  - Prefix with `feat` for new features.
  - Freeform otherwise.
  - Average length: ~40 characters.
  - Example: `feat: add mailbox permissions dialog`

## Workflows

### Add or Update Standard
**Trigger:** When you want to introduce or modify a compliance standard (e.g., mailbox limits, guest access, disabling accounts).  
**Command:** `/add-standard`

1. Edit or append a new entry to `src/data/standards.json`.
   ```json
   [
     {
       "id": "mailboxLimit",
       "name": "Mailbox Size Limit",
       "value": "50GB"
     }
   ]
   ```
2. Optionally update related documentation or UI to reflect the new standard.

---

### Add or Update Alert
**Trigger:** When you want to introduce a new alert or modify an existing alert for tenant monitoring.  
**Command:** `/add-alert`

1. Edit `src/data/alerts.json` to add or update an alert definition.
   ```json
   [
     {
       "id": "guestLogin",
       "description": "Alert on guest user login"
     }
   ]
   ```
2. Update `src/pages/tenant/administration/alert-configuration/alert.jsx` to handle new alert logic or UI.
   ```js
   import alerts from '../../../data/alerts.json';
   // Add logic to display or process the new alert
   ```

---

### Exchange User Settings Enhancement
**Trigger:** When you want to add or improve Exchange-related user management features.  
**Command:** `/enhance-exchange-user-settings`

1. Update or refactor `src/pages/identity/administration/users/user/exchange.jsx` with new logic or UI.
2. Update or create supporting components in `src/components/CippFormPages/` or `src/components/CippComponents/` as needed (e.g., dialogs, forms).
   ```js
   import CippAliasDialog from '../../../CippComponents/CippAliasDialog';
   ```
3. Test and iterate on the new functionality.

---

### Add or Update Component with Related Usage
**Trigger:** When you want to introduce a new UI feature or refactor logic into a reusable component.  
**Command:** `/add-component`

1. Create a new component file in `src/components/` (e.g., `CippDocsLookup.jsx`).
   ```js
   export default function CippDocsLookup(props) { ... }
   ```
2. Update one or more files to use the new component (e.g., `CippApiResults.jsx`).
   ```js
   import CippDocsLookup from './CippDocsLookup';
   ```
3. Test integration and adjust as needed.

## Testing Patterns

- **Test Framework:** Unknown (not detected).
- **Test File Pattern:** Test files use the `.test.ts` extension and are likely colocated with the code they test.
  - Example: `CippAliasDialog.test.ts`
- **How to Write Tests:** Follow the pattern of existing `.test.ts` files for structure and assertions.

## Commands

| Command                             | Purpose                                                        |
|--------------------------------------|----------------------------------------------------------------|
| /add-standard                       | Add or update a compliance standard                            |
| /add-alert                          | Add or update an alert configuration                           |
| /enhance-exchange-user-settings     | Enhance or refactor Exchange user settings features            |
| /add-component                      | Add a new reusable component and integrate it into the UI      |
```