## User Settings CRUD

**The implementation of this CRUD must comply with the base principes described in the following sections:** <br>

  - [Base Services](base-services.md);
  - [Base Controllers](base-controllers.md).

**This task must comply with the following requirements:** <br>

  - Resource URL: `/api/v1/user/settings`;
  - Database table for CRUD: `usersettings`;
  - The model must contain the following fields:
    - `user_id` - the unique user identifier;
    - `new_follower_notification` - the notification about a new follower;
    - `new_message_notification` - the notification about a new message;
    - `followers_can_see_recipes` - followers can see this user's recipes;
    - `followers_can_see_profiles` - followers can see profiles this user follows;
    - `password` - the user's password that must be saved in encrypted form; 
  - The field names mentioned above can be changed if necessary;
  - Any required additional fields can also be added;
  - Any required related tables can also be added.