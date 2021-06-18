# sb_35-03-10_Lunch.ly_ReservationsAppExercise


## Technology Stack
- **Front-end**: Server-side templated application
- **Back-end**: Node.js, Express, and Postgres.


## Assignment Details

Lunch.ly is an Express application that demonstrates the use of a class for the database functions and separation of concerns -- routes only consist of logic for the rendering of the html templages. All database functions exist within classes in separate modules -- one with the `Customer` class and a second with the `Reservation` class.

Assignment involved implementing some changes and adding missing logic.

**Parts 1 - 4** involved envirnoment setup, code review, review of static methods, and an introduction to `Nunjucks`, an implementation of the Jinja2 language in JavaScript. 

**Part 5: Full Names** 
Implement a fullName function to join the first name and last name. Use the full name in the templates instead of `{{ firstName }} {{lastName}}`.

`this.fullName = createFullName();` was added to constructor and function `createFullName` concatenates this.firstName and this.lastName. The customer_detail.html, custoemr_edit_form.html, and customer_list.html templates were all updated to use `{{ customer.fullName }}` instead of `{{ firstName }} {{ lastName }}`.

**Part 6: Saving Reservations** 
Implement a `.save()` method in the `Reservation` class similar to the `.save()` method in the `Customer` class. The method was implemented, but only to save / insert a reservation. Existing logic in the application existed only for adding a reservation (without the save).

**Part 7: Add Search Functionality** 
Implement a search for a customer by name. The navbar was updated to include a search form with a search field and a search button. The `/search` post route was added to handle the ui apsects of the search and a search method was added to the `Customer` class. Initial iteration utilized `LIKE` in the SQL query with additional JavaScript and SQL commands to change firstName, lastName and the search string to lowercase. `ILIKE` was discovered while researching the proper full-text search (not implemented) and the existing seach method was updated by using `ILIKE` and removing all the lowercase-related variable changes.

The `customer_list.html` was enhanced to include a message to indicate the number of customers returned. The message was helpful for the cases where no customers were found for the specified search.

**Part 8: Best Customers** 
Implement a way to show the 10 best customers / 10 customers with the most reservations. The `/best` get route was created and the `.best10()` method was created in the `Customer` class. The only enhancements added to support the top 10 customers was to add a `nbrOfRes` field to the `Customer` class constructor with a default value of 0. `nbrOfRes` field is updated only through the `.best10()` method. 

The `customer_list.html` was expanded to add (# of reservations) at the end of the customer's name, only when (# of reservations) is a non-zero value / only when best customers route is selected.

The navbar was enhanced to change `Customers` to a dropdown with `All Customers` and `Best Customers` as options.

**Getters & Setters** and **Other fun things!** 
Reviewed the material. Nothing really jumped out as oooh I gotta do that. The proper full-text search was interesting, but a fuzzy name search would have caught my attention more! 

