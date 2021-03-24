## User Management Endpoints

**This task must comply with the following requirements:** <br>

1. It is a necessity to expand the [User CRUD](requirements/functional-requirements/backend/user-crud.md) in the following way: <br>

  - Database tables for the CRUD:
    - user;
    - role_assignment.

2. Implement the `POST /api/v1/user/{userId}/lock` endpoint: <br>

  - All existing user sessions must be terminated.
   
3. Implement the `POST /api/v1/user/{userId}/unlock` endpoint to unlock a user account. <br>