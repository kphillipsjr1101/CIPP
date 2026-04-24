```markdown
# CIPP Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you how to contribute to the CIPP codebase, a Next.js application written in JavaScript. You'll learn the project's coding conventions, how to add or update standards and alerts, develop new features, refactor key pages, and merge branches following established workflows. The guide includes code examples, step-by-step instructions, and suggested slash commands for common tasks.

## Coding Conventions

**File Naming**
- Use PascalCase for component and page files.
  - Example: `UserManagement.jsx`, `AlertConfiguration.jsx`

**Import Style**
- Use relative imports for local modules.
  ```js
  import UserCard from '../components/UserCard';
  ```

**Export Style**
- Use default exports for components and modules.
  ```js
  // Good
  export default function UserCard() { ... }

  // Not used
  // export { UserCard };
  ```

**Commit Messages**
- Freeform, often prefixed with `feat`.
- Average length: ~40 characters.
  - Example: `feat: add new alert for mailbox quota`

## Workflows

### Add or Update Standard
**Trigger:** When introducing a new organizational standard or modifying an existing one.  
**Command:** `/add-standard`

1. Edit or add an entry in `src/data/standards.json`.
   ```json
   [
     {
       "id": "passwordPolicy",
       "title": "Password Policy",
       "description": "Minimum 12 characters, must include a symbol."
     }
   ]
   ```
2. Optionally update related documentation or PowerShell equivalents.

---

### Add or Update Alert
**Trigger:** When introducing a new alert or updating alert logic for tenant administration.  
**Command:** `/add-alert`

1. Edit or add an entry in `src/data/alerts.json`.
   ```json
   [
     {
       "id": "mailboxQuota",
       "name": "Mailbox Quota Exceeded",
       "description": "Alert when a user's mailbox exceeds quota."
     }
   ]
   ```
2. Update `src/pages/tenant/administration/alert-configuration/alert.jsx` to reflect the new or changed alert.
   ```js
   import alerts from '../../../../data/alerts.json';

   // Example usage in component
   alerts.map(alert => <AlertCard key={alert.id} {...alert} />);
   ```

---

### Feature Development with Shared Component and Page
**Trigger:** When adding a new UI feature or extending an existing one with significant logic/UI changes.  
**Command:** `/add-feature`

1. Create or update one or more components in `src/components/`.
   ```js
   // src/components/UserStats.jsx
   export default function UserStats({ stats }) { ... }
   ```
2. Integrate or update logic in a page under `src/pages/`.
   ```js
   // src/pages/dashboard.jsx
   import UserStats from '../components/UserStats';
   ```
3. Optionally refactor related files for better separation or reuse.

---

### Refactor or Enhance Exchange User Page
**Trigger:** When adding new Exchange-related functionality, fixing bugs, or improving UX for user mailbox management.  
**Command:** `/update-exchange-page`

1. Update `src/pages/identity/administration/users/user/exchange.jsx` with new logic or UI.
2. Optionally update or create related components in:
   - `src/components/CippFormPages/`
   - `src/components/CippComponents/`
3. Optionally split dialogs or logic into separate component files.
   ```js
   // src/components/CippFormPages/ExchangeMailboxDialog.jsx
   export default function ExchangeMailboxDialog(props) { ... }
   ```

---

### Merge Feature or Fix Branch
**Trigger:** When completing a feature or bugfix and merging it into the main development branch.  
**Command:** `/merge-branch`

1. Merge the branch or pull request.
2. Update multiple files across:
   - `src/components/*`
   - `src/data/*`
   - `src/pages/*`
3. Resolve any conflicts and ensure all tests pass.

---

## Testing Patterns

- **Test File Pattern:** Files end with `.test.ts`.
  - Example: `UserCard.test.ts`
- **Framework:** Unknown (not detected from repository analysis).
- **Typical Usage:**
  ```ts
  // UserCard.test.ts
  import { render } from '@testing-library/react';
  import UserCard from './UserCard';

  test('renders user name', () => {
    // test implementation
  });
  ```

## Commands

| Command            | Purpose                                                      |
|--------------------|--------------------------------------------------------------|
| /add-standard      | Add or update an organizational standard                     |
| /add-alert         | Add or update an alert definition                            |
| /add-feature       | Develop a new feature with shared components and page logic  |
| /update-exchange-page | Refactor or enhance the Exchange user management page     |
| /merge-branch      | Merge a feature or fix branch into the main development branch|
```
