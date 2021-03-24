## Sign-Up Page

**This task must comply with the following requirements:** <br>

  - The system shall allow a guest to sign up for an account using the Sign-Up form;
  - Once the sign-up process is complete, the user shall get the User role and the system shall navigate him to the Dashboard page;
  - The form must contain the following fields:
    - **Username** – Text input – Required – Latin alphabet, a hyphen, space, comma, period, max length: 60, min. length: 2;
    - **Email** – Text input – Required – Email format, unique across the system;
    - **Password** – Text input – Required – Password format; At least 8 characters, must contain 2 letters (at least 1 uppercase and one lowercase), numbers, and special characters. The maximum password length is 64 symbols; Cannot be the same as the username;
    - **Confirm Password** – Text input – Required – Must match "Password".

#### Technical details

1. Fields validation should be implemented both on the backend and frontend sides;
2. Implement the `POST /v1/sign-up` endpoint (see the [Sign-Up Endpoint](requirements/functional-requirements/backend/sign-up-endpoint.md) section for more details):
    ```json
    {
      "username": "",
      "email": "",
      "password": ""
    }
    ```
        
    **200 - OK** <br>
    Response:
    ```
    {
      "token": "",
      "user": {
         ...user data,
       }
    }
    ```

    **400 - Bad Request** - if the validation of the values is failed <br>
    Response:
    ```json
    {
      "errors": {
        "username": "Error text",
        "password": "Error text"
      }
    }
    ```