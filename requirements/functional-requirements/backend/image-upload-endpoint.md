## Image Upload Endpoint

**This task must comply with the following requirements:** <br>

1. Implement `POST /api/v1/files` using Cloudinary Java SDK <br>

    Request:
    ```
    {
      "file": binary
    }
    ```

    Response:
    ```json
    {
      "id": 1,
      "path": "https://path_to_file",
    }
    ```
   
2. Update `GET /recipes/:id` response (see [Recipes CRUD](recipes-crud.md))
    ```
    {
      ... response fields
      "photos": [{ "id": 1, "path": "path_to_file" }, { "id": 2, "path": "path_to_file" }]
    }
    ```