## Password Reset Endpoint

**This task must comply with the following requirements:** <br>

1. The system should provide two routes: <br>

    - `PUT /api/v1/password/reset` - send an email with a reset password link;
    - `PUT /api/v1/password/create` - restore a user password.

2. The 'reset' route: <br>

    Request:
    ```
    {
      "email": "mail@mail.com"
    }
    ```

    - Upon request, a unique code should be generated to reset the password;
    - Then need to send an email with a link to the password reset page;
    - The link must include the password reset code.
   
3. The 'create' route: <br>

    Request:
    ```
    {
      "code": "***",
      "email": "mail@mail.com",
      "password": "*****",
      "passwordConfirmation": "*****"
    }
    ```

    where is **code** is the password reset code;

4. In case of a successful password reset, a token should be returned to the user.