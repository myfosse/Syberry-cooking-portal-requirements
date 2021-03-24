## Roles Management

**This task must comply with the following requirements:** <br>

1. It is a necessity to create Roles CRUD in the following way: <br>

  - Resource URL: `/api/v1/roles`;
  - Database tables for the CRUD:
    - role;
    - permission.

2. The role must have at least one permission. <br>
   
3. The `user` and `administrator` roles must be pre-created in the system, and there must be a ban on their deletion. <br>

4. After removing the role: <br>

  - all users who had this role must be assigned the user role;
  - all users who are left without a role also must be assigned the user role.