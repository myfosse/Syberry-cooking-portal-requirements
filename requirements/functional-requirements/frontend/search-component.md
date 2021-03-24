## Search Component

The system shall allow a user to search the recipes by Title and Ingredients. <br>

**This task must comply with the following requirements:** <br>

  - The component should be placed on the page follow this mockup: [https://o0m7mq.axshare.com/#id=096u8u&p=1_5_dashboard&g=1](https://o0m7mq.axshare.com/#id=096u8u&p=1_5_dashboard&g=1);
  - The search results should be paged (10 results per page).  

#### Technical details

1. Implement the GET `/recipes` endpoint to accept search query: `GET /recipes?query=someword`.