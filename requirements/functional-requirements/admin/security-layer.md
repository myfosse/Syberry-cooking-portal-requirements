## Security Layer

**This task must comply with the following requirements:** <br>

1. Security: <br>

  - Security should determine whether a role has the right to access permission. Each Secured Entity must implement the AuthorizationContext interface:
  ```
  interface AuthorizationContext
  {
  	/**
  	* Return an entity id
  	* @return int
  	*/
  	public function getId(): int;

  	/**
  	* Return a constant of class EntityName
  	* @return string
  	*/
  	public function getEntityName(): string;
  }
  ```
  - The `EntityName` class must contain the constants of the entity names to which the access rights apply;
  - The class determines whether a role has access to permission and must implement the following interface:
  ```
  interface AuthorizationManagerInterface
  {
  	/**
  	* Checks if the user has permission to entity
  	* @param int $entityId
  	* @param string $entityName
  	* @param string $permission
  	* @return bool
  	*/
  	public function isGranted(int $entityId, string $entityName, string $permission): bool;
  }
  ```
  The IsGranted method description:
    - It gets a list of user roles for the entity of checking;
    - It checks whether the roles have permission.

2. Model Description: <br>

  - Permission must have the next fields:
    - roleId - the role id;
    - entityName - the constant of the EntityName class;
    - permission - global permission name.

  - RoleAssignment must have the next fields:
    - userId - A user that has a current assignment.
    - roleId - The current user role.