## Base Controllers

Each controller method must call the service method. Controllers shouldn't have any logic.

#### CRUD Controller

In the constructor of the CRUD controller, there must be a dependency injection for the corresponding CRUD service. The `entityName` is the plural name of the entity. For instance: `users`.

Endpoints:

  - `GET /api/v1/{entityName}` - get a page of entities;
  - `POST /api/v1/{entityName}/` - create an entity;
  - `GET /api/v1/{entityName}/{id}` - get an entity by id;
  - `PUT /api/v1/{entityName}/{id}` - update an entity by id;
  - `DELETE /api/v1/{entityName}/{id}` - delete an entity by id.

#### CRUD Export Controller

Must extends CRUD controller.

Additional endpoints:

  - `GET /api/v1/{entityName}/export` - return a file stream response. Generate a CSV-file by the filter.

#### Multiple Update (deprecated)

Additional endpoints:

  - `PUT /api/v1/{entityName}` - multiple update.

  Request format:
  ```
  {
    "entityId1": "Entity Object 1",
    "entityId2": "Entity Object 2"
  }
  ```

  When updating, need to get all entities by entity ids. Then update all data in entities from entity objects and save.
