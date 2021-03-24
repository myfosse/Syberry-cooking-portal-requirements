## Sign-In Endpoint

**This task must comply with the following requirements:** <br>

1. It is a necessity to create the authorization model in the database by the following scheme: <br>

    - user_id (foreign key to User)
    - token (VARCHAR)
    - remember_me (Boolean, default: false)

    Authentication should be implemented as follows: <br>

     - During Authentication, the user must have an access token.
     - The access token must have a lifetime.
     - On every request, the token's lifetime must be updated.
     - The user should be able to use several sessions with different tokens.
     - The token lifetime must be set in environment variables.
     - The token must be passed in the request headers: Token: {token}

2. Implement the `POST /api/v1/sign-in` endpoint: <br>

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
   
3. Every protected request should have an `Authorization` header: `Token: {token}`

4. Access token should expire every 60 minutes.

5. If `remember_me = true`, the access token will expire after 2 weeks.