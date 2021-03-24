## Users List Page

The system shall allow the administrator to see and edit the list of users. In the context of this task, it is necessary to implement the Users List Page (UI and business logic). <br>

**This task must comply with the following requirements:** <br>

  - The page should include the following elements:
    - List of users;
    - The 'Edit' button. On pressing this button, the system shall navigate the administrator to the [User Edit Page](user-edit-page.md);
  - The list of users must include the following columns:
    - Full name;
    - Email address;
    - State of the user account (locked or unlocked);
    - Role of the current user.

#### Technical details

1. Implement the required endpoints from the [User CRUD](requirements/functional-requirements/backend/user-crud.md) to get the current list items.