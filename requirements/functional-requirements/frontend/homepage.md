## Homepage

In the context of this task, it is necessary to implement the Homepage (UI and business logic). <br>

**This task must comply with the following requirements:** <br>

  - The screen appearance by this mockup: [https://o0m7mq.axshare.com/#id=096u8u&p=1_5_dashboard&g=1](https://o0m7mq.axshare.com/#id=096u8u&p=1_5_dashboard&g=1);
  - The page should include the following elements:
    - User information (name, number of followers, number of likes, number of published recipes, number of saved recipes, number of users that this user is subscribed to);
    - Links to pages of the user profile and settings;
    - Search component;
    - Logout component;
    - Recipe feed widget that contains several of the most popular recipes of the day;
    - Widget with most active users today;
    - Notification component that displays the number of unread notifications and allows you to go to the notification page;
    - Widget with users that have the largest number of followers.

#### Technical details

1. Implement `GET /recipes?pagenum=N` endpoint for getting a paged list of all recipes (see the [Recipes CRUD](requirements/functional-requirements/backend/recipes-crud.md) section for more details):
```
   {
       items: [
           {
               "id": 1,
               "mainPhoto": "https://link-to.photo", // null if empty
               "title": "Cool recipe",
               "description": "Description of the recipe",
               "servingTime": "5 mins",
               "ingredientsCount": 4, // 0 - until Ingredients model is not implemented
               "owner": {
                       "username": "Default user"
               },
               "createdAt": "2020-09-04T20:43:26Z" // UTC Date
           },
           {
               "id": 2,
               "mainPhoto": "https://link-to.photo", // null if empty
               "title": "Cool recipe",
               "description": "Description of the recipe",
               "servingTime": "5 mins",
               "ingredientsCount": 4, // 0 - until Ingredients model is not implemented
               "owner": {
                       "username": "Default user"
               },
               "createdAt": "2020-09-04T20:43:26Z" // UTC Date
           },
       ],
       pageNumber: 1,
       totalItems: 23,
   }
```

2. Implement the required endpoints from the [User CRUD](requirements/functional-requirements/backend/user-crud.md) to get the current user data;

**Note:** _Don't forget to update the responses of owned and saved recipe lists to support the consistency of the API._