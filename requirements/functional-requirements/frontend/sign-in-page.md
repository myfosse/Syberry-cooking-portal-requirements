## Sign-In Page

**This task must comply with the following requirements:** <br>

  - The system shall allow unauthenticated users to sign in via the Login page via the following form submission: <br>
    Form fields: <br>
      **Username** – Text input – Required – Latin alphabet, a hyphen, space, comma, period, max length: 60, min. length: 2; <br>
      **Password** – Text input – Required – Password format; max length: 60; <br>
  - Once the user authenticated, the system shall navigate him to the [Dashboard page](homepage.md). In case this user has administrative permissions, the system shall navigate him to the [Administrative Dashboard page](requirements/functional-requirements/admin/administrative-dashboard.md);
  - If an unauthenticated user tries to access any page of the system besides public pages, the system shall redirect him to the Sign-In page;
  - The page shall contain an option that allows restoring access to the system if a user forgets a password.

#### Technical details

1. Implement `POST /v1/sign-in` endpoint (see the [Sign-In Endpoint](requirements/functional-requirements/backend/sign-in-endpoint.md) section for more details):

    Request:
    ```
    {
      "username": "",
      "password": "",
      "rememberMe": true|false
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
    
2. Tokens and user data should be stored in browser local storage using `redux-persist` package. Store structure:
    ```
    {
      "auth": {
        "token": "",
      },
      "user": {
        "username": ""
      }
    }
    ```

3. Every protected request should have an `Authorization` header: `Token: {token}`