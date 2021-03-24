## Authentication Manager

This manager responds to everything issues related to the authentication process of a user. It works the following way: <br>

  - The server generates a token that certifies the user identity and sends it to the client;
  - The client will send the token back to the server for every subsequent request, so the server knows the request comes from a particular identity;
  - The system should add authentication implicitly to every API-request.