## Recipes CRUD

**The implementation of this CRUD must comply with the base principes described in the following sections:** <br>

  - [Base Services](base-services.md);
  - [Base Controllers](base-controllers.md).

**This task must comply with the following requirements:** <br>

**1. Implement Products CRUD** <br>

  - Resource URL: `/api/v1/product`
  - Create the Product table in the database;
  - The model must contain the following fields:
    - `id` - the product identifier;    
    - `name` - the product name;    
    - `photoid` - foreign key to File (see [Image Upload Endpoint](image-upload-endpoint.md));

**2. Implement the required models** <br>

  - Implement the Recipe model in the database by the following scheme:
    - id
    - title
    - owner_id (foreign key to User)
  - Implement the File model by the following scheme:
    - id
    - external_id (the field is aimed to store the unique identifier in 3rd party service where files are stored)
  - Implement the RecipeFile model by the following scheme:
    - id
    - file_id (foreign key to File)
    - recipe_id (foreign key to Recipe)
    - is_main (Boolean, default: false) - the field is aimed to show whether the photo is main or not
  - Implement the RecipeCharacteristicGroup model by the following scheme:
    - id
    - name
  - Implement the RecipeCharacteristic model by the following scheme:
    - id
    - group_id (foreign key to RecipeCharacteristicGroup)
    - recipe_id (foreign key to Recipe)
    - value
  - Implement the SavedRecipe model by the following scheme:
    - id
    - saved_by_user_id (foreign key to User)
    - recipe_id (foreign key to Recipe)

**Note:** _RecipeCharacteristicGroup is a fixed group of characteristics that we should predefine (as we don't have functionality for adding groups). Thus, we have two groups: Serving time and Nutrition facts. It's a necessity to prepare a fixture to predefine these groups._

**3. Implement Recipes CRUD** <br>

  - Resource URL: `/api/v1/recipes`;  
  - Database table for CRUD: `recipes`;
  - The model must contain the following fields:
    - `id` - the unique recipe identifier;
    - `name` - the recipe name;
    - `description` - the 'how to cook' description;    
    - `serving_time` - text information about the estimated serving time;
    - `nutrition_facts` - showing what nutrients are in the food;
    - `tags` - the comma-separated list of tags;
  - Implement `GET /api/v1/recipes/:id`
    ```json
    {
      "id": 1,
      "mainPhoto": "https://link-to.photo",
      "name": "Cool recipe",
      "description": "<ol><li>First step</li><li>Second step</li></ol>"
    }
    ```
    _Note: The null value if the "mainPhoto" field is empty._
  - Implement a characteristic creating: `POST /api/v1/recipes/:id/characteristics` <br>
    Request: <br>
    ```json
    {
      "groupId": 1,
      "value": "5 mins"
    }
    ```
  - Implement a characteristic deletion: `DEELTE /api/v1/recipes/:recipeId/characteristics/:characteristicId`, where the request and response body are empty.
  - Implement `GET /api/v1/recipes/:id/characteristics`
    ```json
    {
      "сookingTime": ["5 mins"],
      "nutritionFacts": ["222 calories", "6.6 g fat"],
    }
    ```  
    The response format is as follows: the key in JSON is the group, and the value is the list of characteristics for the recipe.
  - Implement `POST /api/v1/users/me/saved-recipes` which should create an entry in the SavedRecipe table:
    ```json
    {
      "recipeId": 2
    }
    ```
  - Implement the `GET /users/me/recipes?pagenum=1` endpoint to get all recipes owned by the current user: <br>
    Response: <br>
    ```
    {
      "items": [
      {
        "id": 1,
        "mainPhoto": "https://link-to.photo", // null if empty
        "title": "Cool recipe",
        "servingTime": "5 mins",
        "ingredientsCount": 4, // 0 until the Ingredients model is not implemented
        },
        {
          "id": 2,
          "mainPhoto": "https://link-to.photo", // null if empty
          "title": "Cool recipe",
          "servingTime": "5 mins",
          "ingredientsCount": 4, // 0 until the Ingredients model is not implemented
        }
        ],
        "pageNumber": 1,
        "totalItems": 23
      }
    ```
  - Implement the `GET /users/me/saved-recipes?pagenum=1` endpoint for getting all recipes saved by current user. The response is just like the above. Lists should have a common controller for handling pagination (and sorting and filtering in the future). Page size should be 10 items per page.  

**4. Implement Ingredient model and required endpoints** <br>

  - The model must contain the following fields:
    - `id` - the unique ingredient identifier;
    - `recipe_id` - foreign key to Recipe;
    - `product_id` - foreign key to Product;
    - `count` - nullable, not numeric but string value to allow values like `1/2 cup` or `5 large`;
  - Implement `GET /api/v1/recipes/:id/ingredients`
    ```json
    [
        {
          "value": "1/2 cup whole milk",
          "photo": "https://link_to_photo",
          "count": 1
        }, {
          "value": "1 tsp olive oil",
          "photo": "https://link_to_photo",
          "count": 2
        }, {
          "value": "salt",
          "photo": "https://link_to_photo",
          "count": 4
        }
    ]
    ```
  - Update `ingredientsCount` fields in responses for lists requests;
  - Implement an ingredient creation: `POST /api/v1/recipes/:id/ingredients`:
    
    Request:
    ```json
    {
      "productId": 1,
      "count": 4
    }
    ```

    Response:
    ```json
    {
      "productId": 1,
      "recipeId": 2,
      "count": 4
    }
    ```
  - Implement an ingredient deletion: `DELETE /api/v1/recipes/:recipeId/ingredients/:ingredientId`, where the request and response body are empty.

**Note:** <br>

  - The field names mentioned above can be changed if necessary;  
  - Any required additional fields can also be added;
  - Any required related tables can also be added.