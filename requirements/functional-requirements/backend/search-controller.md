## Search Controller

**This task must comply with the following requirements:** <br>

#### Search

  - The search will be implemented using the MySQL `LIKE` operator;
  - For each entity, a search config must be created that describes which fields should be searched for;
  - One entity can have several configs for searching;
  - Search should add additional filtering to existing ones;
  - It should be possible to search by fields of related entities;
  - Update the GET `/recipes` endpoint to accept search query: `GET /recipes?query=someword`;
  - The search results should be paged (10 results per page).  

#### Filtering Entities

  - The filtering request must be passed in a query and be in the following format: <br>
  `?field[condition]=value&field2[condition]=value2&field2[condition2]=value3&...`

  Available conditions:
  ```
  class Condition
  {
    public const EQUAL = 'eq';
    public const NOT_EQUAL = 'neq';
    public const IS_NULL = 'is_null';
    public const NOT_NULL = 'not_null';
    public const GREATER_THAN = 'gt';
    public const GREATER_THAN_OR_EQUAL_TO = 'gte';
    public const LESS_THAN = 'lt';
    public const LESS_THAN_OR_EQUAL_TO = 'lte';
    public const IN = 'in';
    public const NOT_IN = 'not_in';
    public const LIKE = 'like';
    public const STARTS_WITH = 'sw';
  }
  ```

  First of all necessary to extract all available fields for filtering from the query and then configure the query builder.

