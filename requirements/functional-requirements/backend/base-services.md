## Base Services

#### Service

  Each CRUD service must implement the `CrudService` interface:
  ```
  interface CrudService
  {
    /**
     * Get page of filtered entities
     * @param array $filter - Filter from request
     * @param PaginationParams $paging
     * @param string|null $search - Search string from request
     * @return Page
     */
    public function search(array $filter, PaginationParams $paging, ?string $search = null): Page;

    /**
     * Get all entities list by filter and search
     * @param array $filter - Filter from request
     * @param string|null $search - Search string from request
     * @return array - Serialized entity list
     */
    public function viewAll(array $filter = [], ?string $search = null): array;

    /**
     * Save entity in database
     * @param array $createData - Data from request
     * @return array - Serialized entity
     */
    public function create(array $createData): array;

    /**
     * Retrieve entity by id and return serialized data
     * @param int $entityId
     * @return array - Serialized entity
     */
    public function show(int $entityId): array;

    /**
     * Retrieve entity by id and update
     * @param int $entityId
     * @param array $editData - Data from request
     * @return array - Serialized entity
     */
    public function update(int $entityId, array $editData): array;

    /**
     * Delete entity by id
     * @param int $entityId
     */
    public function delete(int $entityId): void;
  }
  ```

#### Export Service

CRUD services with CSV export must implement the `CrudExportService` interface:
  ```
  interface CrudExportService extends CrudService
  {
    /**
     * Generate csv string by filter and search
     * @param array $filter - Filter from request
     * @param string|null $search - Search string from request
     * @return string
     */
    public function exportToCsv(array $filter = [], ?string $search = null): string;
  }
  ```

#### Serializer

Entity serializers must implement the Serializer interface. All entities must be serialized using a serializer. The abstract serializer must have the following method:
  ```
  public function serializeForList (object $entity, array $options = []): array;
  ```

  which calls serialize by default, but can be overridden.

  ```
  interface Serializer
  {
    /**
     * Serialize one entity
     * @param object $entity
     * @param array $options - Serialization options
     * @return array
     */
    public function serialize(object $entity, array $options = []): array;

    /**
     * Serialize entity list
     * @param array $entities
     * @param array $options - Serialization options
     * @return array
     */
    public function serializeList(array $entities, array $options = []): array;
  }
  ```

#### Pagination Params

A class for getting pagination parameters from a request must implement the `PaginationParams` interface:

  ```
  interface PaginationParams
  {
    /**
     * Get offset from request
     * @return int
     */
    public function getOffset(): int;

    /**
     * Set offset from request
     * @param int $offset
     */
    public function setOffset(int $offset): void;

    /**
     * Get limit from request
     * @return int
     */
    public function getLimit(): int;

    /**
     * Set limit from request
     * @param int $limit
     */
    public function setLimit(int $limit): void;

    /**
     * Get sort by from request
     * @return string|null
     */
    public function getSortBy(): ?string;

    /**
     * Set sort by from request
     * @param string|null $sortBy
     */
    public function setSortBy(?string $sortBy): void;

    /**
     * Get sort order from request
     * @return string|null
     */
    public function getSortOrder(): ?string;

    /**
     * Set sort order from request
     * @param string|null $sortOrder
     */
    public function setSortOrder(?string $sortOrder): void;
  }
  ```

#### Page

The pagination result should implement the `Page` interface:

  ```
  interface Page extends JsonSerializable
  {
    /**
     * Get serialized entity list
     * @return array
     */
    public function getItems(): array;

    /**
     * Set serialized entity list
     * @param array $items
     */
    public function setItems(array $items): void;

    /**
     * Get the total number of filtered items
     * @return int
     */
    public function getTotal(): int;

    /**
     * Set the total number of filtered items
     * @param int $total
     */
    public function setTotal(int $total): void;

    /**
     * Get current page offset
     * @return int
     */
    public function getOffset(): int;

    /**
     * Set current page offset
     * @param int $offset
     */
    public function setOffset(int $offset): void;

    /**
     * Get current page limit
     * @return int
     */
    public function getLimit(): int;

    /**
     * Set current page limit
     * @param int $limit
     */
    public function setLimit(int $limit): void;
  }
  ```