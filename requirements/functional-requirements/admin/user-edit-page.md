## User Edit Page

The system shall allow the administrator to edit the selected user. In the context of this task, it is necessary to implement the User Edit Page (UI and business logic). <br>

**This task must comply with the following requirements:** <br>

  - The page should include the following elements:
    - Editable field with the full username;
    - Editable field with the user email address;
    - The 'Delete' button. Confirmation of user deletion must be implemented;
    - A switch component that allows changing the state of the user account (locked or unlocked);
    - A drop-down list that allows selecting the user role.

#### Technical details

1. Implement the required endpoints from the [User CRUD](requirements/functional-requirements/backend/user-crud.md) and additional endpoints from the [User Management](user-management-endpoints.md).