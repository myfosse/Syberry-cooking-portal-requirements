## Category Page

The system shall allow a user to see all recipes owned by the user and saved recipes on the Category page. In the context of this task, it is necessary to implement the Settings Page (UI and business logic). <br>

**This task must comply with the following requirements:** <br>

  - The screen appearance by this mockup: [https://o0m7mq.axshare.com/#id=4n236i&p=1_6_category_page&g=1](https://o0m7mq.axshare.com/#id=4n236i&p=1_6_category_page&g=1);  
  - Each list item should contain:
    - Recipe preview image;
    - Recipe title;
    - Serving time;
    - Ingredients count.

#### Technical details

1. Implement the required endpoints from the [Recipes CRUD](requirements/functional-requirements/backend/recipes-crud.md) to get or save the current recipe data.

2. Items count shall be retrieved from the `GET /users/me/recipes` and `GET /users/me/saved-recipes` responses, so you should get the first page of the lists right after a page load.

3. Implement a common list component that will be able to get a list and handle loading more items.