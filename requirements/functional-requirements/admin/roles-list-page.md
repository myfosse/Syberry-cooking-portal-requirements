## Roles List Page

The system shall allow the administrator to see and edit the list of roles. In the context of this task, it is necessary to implement the Roles List Page (UI and business logic). <br>

**This task must comply with the following requirements:** <br>

  - The page should include the following elements:
    - List of roles;
    - The 'Edit' button. On pressing this button, the system shall navigate the administrator to the [Role Edit Page](role-edit-page.md);
  - The list of users must include the following columns:
    - Role title;    
    - Permissions of the current role.

#### Technical details

1. Implement the required endpoints from the [Roles CRUD](roles-management-endpoints.md) to get the current list items.