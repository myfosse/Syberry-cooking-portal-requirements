## Sign-Up Endpoint

**This task must comply with the following requirements:** <br>

1. Use User CRUD and User Settings CRUD to storing the user's sign up data in the database. <br>

2. Username and Email should be unique. <br>
  
3. Fields validation should be implemented both on backend and frontend. <br>

4. Implement the `POST /api/v1/sign-up` endpoint:
    ```
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
    **400 - Bad Request** - if the validation of the values is faileЗd <br>
    Response:
    ```
    {
      "errors": {
        "username": "Error text",
        "password": "Error text"
      }
    }
    ```