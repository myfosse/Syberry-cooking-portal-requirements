## API-manager

API-manager should provide sending and receiving HTTPS-requests to/from the back-end. The API-manager should have the following characteristics: <br>

  - data exchange with the back-end by client pull technology;
  - synchronous requests;
  - HTTPS protocol.

The API-manager should comply with the following requirements: <br>

  - Error responses should process based on HTTP status codes;
  - Timeouts and invalid responses should process and return as errors to a parent class;
  - Timeouts and invalid responses should be logged.