```markdown
# CIPP Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill teaches you how to contribute to the CIPP codebase, a Next.js project written in JavaScript. You'll learn the project's coding conventions, file organization, and the main workflows for adding or updating standards, alerts, features, and shared dialog components. The guide includes practical code examples and suggested commands for common tasks.

## Coding Conventions

### File Naming
- Use **PascalCase** for component and page files.
  - Example: `CippExchangeSettingsForm.jsx`, `AlertConfiguration.jsx`

### Import Style
- Use **relative imports** for modules within the project.
  - Example:
    ```javascript
    import CippApiDialog from '../../components/CippComponents/CippApiDialog';
    ```

### Export Style
- Use **default exports** for components and modules.
  - Example:
    ```javascript
    export default function CippApiDialog(props) {
      // ...
    }
    ```

### Commit Messages
- Freeform style, often prefixed with `feat`.
- Average commit message length: ~40 characters.
  - Example: `feat: add Exchange settings form`

## Workflows

### Add or Update Standard
**Trigger:** When you want to introduce or modify a compliance or operational standard.  
**Command:** `/add-standard`

1. Edit or add an entry in `src/data/standards.json`.
2. Optionally update or create related UI components or documentation.

**Example:**
```json
// src/data/standards.json
[
  {
    "id": "password-policy",
    "description": "Minimum password length is 12 characters"
  }
]
```

---

### Add or Update Alert
**Trigger:** When you want to introduce a new alert or update alert logic.  
**Command:** `/add-alert`

1. Edit or add an entry in `src/data/alerts.json`.
2. Update `src/pages/tenant/administration/alert-configuration/alert.jsx` to reflect the new or updated alert.

**Example:**
```json
// src/data/alerts.json
[
  {
    "id": "mailbox-quota",
    "message": "Mailbox quota exceeded"
  }
]
```
```javascript
// src/pages/tenant/administration/alert-configuration/alert.jsx
import alerts from '../../../data/alerts.json';
// ...use alerts in UI
```

---

### Feature Development with Shared Component and Page
**Trigger:** When adding a feature that has both reusable logic and a user-facing page.  
**Command:** `/add-feature`

1. Update or create shared component(s) in `src/components/`.
2. Update or create the corresponding page in `src/pages/`.
3. Optionally refactor related dialogs or forms.

**Example:**
```javascript
// src/components/CippFormPages/CippExchangeSettingsForm.jsx
export default function CippExchangeSettingsForm(props) {
  // form logic
}

// src/pages/identity/administration/users/user/exchange.jsx
import CippExchangeSettingsForm from '../../../components/CippFormPages/CippExchangeSettingsForm';
// ...use form in page
```

---

### Add or Update Shared Dialog Component
**Trigger:** When modularizing dialog logic or adding new dialog-based features.  
**Command:** `/add-dialog`

1. Create or update dialog component(s) in `src/components/CippComponents/`.
2. Refactor page(s) to use the new dialog component(s).

**Example:**
```javascript
// src/components/CippComponents/CippApiDialog.jsx
export default function CippApiDialog({ open, onClose }) {
  // dialog logic
}

// src/pages/identity/administration/users/user/exchange.jsx
import CippApiDialog from '../../../components/CippComponents/CippApiDialog';
// ...use dialog in page
```

## Testing Patterns

- **Test Framework:** Unknown (not detected)
- **Test File Pattern:** Files end with `.test.ts`
  - Example: `UserManagement.test.ts`
- Tests are likely colocated with the code or in a `__tests__` directory.

## Commands

| Command        | Purpose                                                        |
|----------------|----------------------------------------------------------------|
| /add-standard  | Add or update a compliance or operational standard             |
| /add-alert     | Add or update an alert definition and its configuration UI     |
| /add-feature   | Implement a new feature with shared components and a page      |
| /add-dialog    | Create or refactor shared dialog components                    |
```
