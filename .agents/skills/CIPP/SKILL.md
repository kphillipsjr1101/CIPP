```markdown
# CIPP Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill teaches you how to contribute to the CIPP codebase, a Next.js application written in JavaScript. You'll learn the project's coding conventions, how to add or update standards and alerts, develop Exchange user management features, and create or enhance shared React components. The guide includes step-by-step workflow instructions, code examples, and recommended commands for common tasks.

## Coding Conventions

### File Naming
- Use **PascalCase** for component and page files.
  - Example: `CippApiResults.jsx`, `CippMailboxPermissionsDialog.jsx`

### Import Style
- Use **relative imports** for modules and components.
  ```javascript
  import CippApiResults from '../CippComponents/CippApiResults';
  ```

### Export Style
- Use **default exports** for components and modules.
  ```javascript
  export default function CippApiResults(props) {
    // component code
  }
  ```

### Commit Patterns
- Commits often use the `feat` prefix, but are otherwise freeform.
- Average commit message length: ~40 characters.

## Workflows

### Add or Update Standard
**Trigger:** When you want to define or modify an organizational standard (policy/configuration) for tenants.  
**Command:** `/add-standard`

1. Edit or append an entry in `src/data/standards.json`.
2. Optionally, update related documentation or PowerShell equivalents within the same file.

**Example:**
```json
{
  "name": "MaxMailboxSize",
  "description": "Sets the maximum mailbox size for users.",
  "value": "50GB",
  "powershell": "Set-Mailbox -Identity <User> -ProhibitSendReceiveQuota 50GB"
}
```

---

### Add or Update Alert
**Trigger:** When you want to introduce a new alert or update alert logic/thresholds for tenant monitoring.  
**Command:** `/add-alert`

1. Edit or append an entry in `src/data/alerts.json`.
2. Update `src/pages/tenant/administration/alert-configuration/alert.jsx` to reflect the new or changed alert.

**Example:**
```json
{
  "id": "mailbox-quota",
  "name": "Mailbox Quota Exceeded",
  "threshold": 95,
  "description": "Alert when mailbox usage exceeds 95%."
}
```
```javascript
// In alert.jsx
import alerts from '../../../../data/alerts.json';
// Render new alert in configuration UI
```

---

### Feature Development: Exchange User Page
**Trigger:** When you want to add or improve Exchange user management features (mailbox permissions, alias management, forwarding, calendar permissions, etc.).  
**Command:** `/update-exchange-user-feature`

1. Update or refactor `src/pages/identity/administration/users/user/exchange.jsx`.
2. Add or modify supporting components in `src/components/CippFormPages/` or `src/components/CippComponents/`.
3. Optionally, split dialogs into separate components for modularity.

**Example:**
```javascript
// In exchange.jsx
import CippAliasDialog from '../../../components/CippComponents/CippAliasDialog';
// Use <CippAliasDialog /> in the Exchange user page
```

---

### Add or Update Shared Component
**Trigger:** When you want to introduce reusable UI logic or improve shared component functionality.  
**Command:** `/add-shared-component`

1. Create or update a component in `src/components/CippComponents/`.
2. Integrate or update usage in relevant pages or other components (e.g., `src/components/CippComponents/CippApiResults.jsx`, `src/pages/_app.js`).

**Example:**
```javascript
// src/components/CippComponents/CippDocsLookup.jsx
export default function CippDocsLookup(props) {
  // component code
}
```
```javascript
// Usage in a page
import CippDocsLookup from '../../components/CippComponents/CippDocsLookup';
```

## Testing Patterns

- **Test Framework:** Unknown (not detected in analysis)
- **Test File Pattern:** Files end with `.test.ts`
  - Example: `SomeComponent.test.ts`
- **Location:** Typically alongside the component or in a `__tests__` directory.

## Commands

| Command                    | Purpose                                                        |
|----------------------------|----------------------------------------------------------------|
| /add-standard              | Add or update an organizational standard                       |
| /add-alert                 | Add or modify an alert definition for tenant monitoring        |
| /update-exchange-user-feature | Implement or enhance Exchange user management features         |
| /add-shared-component      | Create or update a shared React component                      |
```
