## API Introduction

### API Reference

The API is organized around REST. Our API has resource-oriented URLs, uses requests with JSON arguments and JSON responses, and uses standard HTTP response codes, authentication, and verbs. <br>

### Authentication

The API uses tokens to authenticate requests. All API requests must be made over HTTPS. Calls made over plain HTTP will fail. API requests without authentication will also fail. <br>

### Requests

  - For all GET and DELETE requests, parameters must be passed in the query string;
  - For all POST and PUT requests, data must be passed in the body of the request in JSON format. The controller should receive an array of data from JSON in the request body;
  - The file uploading request must be POST. Content-Type must be multipart/form-data. The file must be passed in the request body.

### Responses

  - All response must be in the JSON format;
  - A request for a list of entities must return a JSON array;
  - The entity page request should return a JSON page object;
  - Request to get one entity, create and update entity should return JSON entity object;
  - Delete requests must have an empty response body.

### Errors

The API uses conventional HTTP response codes to indicate the success or failure of an API request. In general: Codes in the 2xx range indicate success. Codes in the 4xx range indicate an error that failed given the information provided (for instance, a required parameter was omitted, etc.). Codes in the 5xx range indicate an error with the server. <br>

##### HTTP Status Code Summary
**200 - OK**<br>	_Everything worked as expected._ <br><br>
**400 - Bad Request**<br>	_The request was unacceptable, often due to missing a required parameter._ <br><br>
**401 - Unauthorized**<br>	_No valid token provided._ <br><br>
**402 - Request Failed**<br>	_The parameters were valid but the request failed._ <br><br>
**403 - Forbidden**<br>	_The client doesn't have permission to perform the request._ <br><br>
**404 - Not Found**<br>	_The requested resource doesn't exist._ <br><br>
**409 - Conflict**<br>	_The request conflicts with another request._ <br><br>
**429 - Too Many Requests**<br>	_Too many requests hit the API too quickly._ <br><br>
**500, 502, 503, 504 - Server Errors**<br>	_Something went wrong on the server end._ <br><br>

### Versioning

A versioning strategy allows clients to continue using the existing REST API and migrate their applications to the newer API when they are ready. For the system will use the versioning through URI Path. For example, `https://www.cme.com/api/v1/specificApiMethod` <br>

### Date format

All dates in the API use UTC and are strings in the ISO 8601 "[combined date and time representation](https://en.wikipedia.org/wiki/ISO_8601#Combined_date_and_time_representations)" format: _2020-04-15T15:50:38Z._ <br>
