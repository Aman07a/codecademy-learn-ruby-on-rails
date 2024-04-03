#### Objective

### LEARN RUBY ON RAILS

## Stories

Stories is making a landing page for their upcoming travel journal app. <br>
On the contact page when a user enters her contact information, it is saved into the app’s database.

To build this app, you’ll use:

- `HTML` and CSS for the front end
- `Rails` for the back end
- `Git` to manage your code
- `GitHub` to share your code with others

To preview your app at any point:

- In the terminal, type `rails server`
- In the browser, visit `http://localhost:4001`

If you get stuck during this project or would like to see an experienced developer work through it, <br>
click “**Get Unstuck**“ to see a **project walkthrough video**.

Setup

1. Create a new Rails app named stories.

   ```ruby
   rails new stories
   ```

2. After you create the new app, switch to its folder. <br>
   In the terminal, type:

   ```bash
   cd stories
   ```

3. Install the gems specified in the Gemfile.

   ```ruby
   bundle install
   ```

4. Generate a controller named Pages.

   ```ruby
   rails generate controller Pages
   ```

5. Set up the layout file (**app/views/layouts/application.html.erb**):

   - In the `<head>` below the `<title>`, add CSS for Bootstrap. <br>
     Follow the [instructions here](http://getbootstrap.com/getting-started/#download-cdn). <br>
     Use the latest compiled and minified CSS, and not the optional theme.

   - Add CSS for a [web font](http://www.google.com/fonts). <br>
     Browse web fonts here, and choose one to use in this app.

   - Make sure all CSS URLs start with `https`.

   - Move this line from the `<head>` and place it just before the `</body>` tag:

   ```ruby
   <%= javascript_include_tag 'application', 'data-turbolinks-track' => true %>
   ```

   This line includes all of your app’s JavaScript files, including jQuery, as new `<script>` elements. <br>
   By placing this line just before the `</body>` tag, <br>
   the page’s HTML will load first before the JavaScript applies to the HTML.

## Make a home page

6. In the Pages controller, make an action named `home`.

   ```ruby
   rails generate controller home
   ```

7. In the routes file, set the `home` action as the root route.

   ```ruby

   ```

8. Create a view named **app/views/pages/home.html.erb** and style it in **app/assets/stylesheets/pages.css**:

   - Add a main section with a heading and a ‘Learn more’ button. <br>
     Use your own image for the background image of the main section.
   - Add a supporting section with a subheading and tagline.
   - Add a secondary section with a background image. Use your own image.
   - Add a discover section with a subheading and a ‘Learn more’ button.
   - Add a footer.

   To use images, add URLs to images in HTML or CSS [as shown here](http://guides.rubyonrails.org/asset_pipeline.html#coding-links-to-assets).

9. Create a navigation menu that slides out from the left side. <br>
   Write your JavaScript code in **app/assets/javascripts/application.js**.

   Here is an [example](http://jsfiddle.net/fh6p4/) of a possible way to create this menu.

   Here are menu icons
   (![menu-black](https://content.codecademy.com/projects/z2d/stories/menu-black.svg),
   ![menu-white](https://content.codecademy.com/projects/z2d/stories/menu-white.svg)) and close icons
   (![close-black](https://content.codecademy.com/projects/z2d/stories/close-black.svg),
   ![close-white](https://content.codecademy.com/projects/z2d/stories/close-white.svg)).

10. Start a Rails server to preview the app in the browser. In the terminal, type:

    ```ruby
    rails server
    ```

    This command starts a Rails server listening on port 4001.
    View the result at `http://localhost:4001`.

## Make an about page

13. The about page has the same navigation menu and footer as the home page. <br>
    Instead of writing the same code twice, <br>
    refactor the navigation menu and footer from the home page and place them into **application.html.erb** <br>
    so that they are available to all pages in the app.

14. Make a new controller action and a new route for the about page.

15. Create a view for the about page and style it

    - Add a main section with a heading. <br>
      Use your own background image for the main section.
    - Add a supporting section with a subheading, tagline, and ‘Signup’ button.

16. In the navigation menu, use the `link_to` helper to generate links to the home page and about page.

17. In the home page, use `link_to` to generate both ‘Learn more’ links pointing to the about page.

18. Run the local server to view the result at `http://localhost:4001`.

19. Commit the changes using Git, and push up to GitHub.

## Make a contact page

21. Using the [request/response cycle](https://www.codecademy.com/articles/request-response-cycle-forms)
    as a guide, there are two things to handle:

    - In the first turn of the request/response cycle, the signup form is displayed to the user via a `GET` request.<br>
    - When the user fills out the form and submits it, it triggers the second turn of the request/response cycle, <br>
      where the user’s info is sent to the app via a `POST` request and saved into the database.<br>
      Generate a model named `Signup`.

22. Open the migration file and add a string column called `firstname` and a string column called `email`.

23. Run the migration to update the database.

24. Generate a controller named Signups.

25. In the routes file, add the resource route for the Signups controller.

26. Set up the Signups `new` action to handle `GET` requests by displaying the signup form:

    In the Signups controller, make an action named `new` that creates a new Signup object.

    Create a view named **app/views/signups/new.html.erb** and style it in **app/assets/stylesheets/signups.css**. <br>
    Add a heading, a form, and your own background image.

27. In the navigation menu, use `link_to` to generate links to the contact page.

28. In the about page, use `link_to` to generate the ‘Sign up’ links pointing to the contact page.

29. Run the local server to view the result at `http://localhost:4001`.

30. Set up the Signups `create` action to handle `POST` requests by saving user info to the database:

    In the Signups controller, write a private method named `signup_params`. <br>
    Require the model name `signup` and permit the columns `firstname` and `email`.

    Then make an action named `create`. <br>
    Use `signup_params` to create a new Signup object. <br>
    After saving to the database, redirect to the thanks page. <br>
    We’ll set this page up next.

## Make a thanks page

31. The thanks page is what users see after successfully submitting their name and email.

    In the Pages controller, make a new action and a new route for the thanks page.

32. Create a view for the thanks page and style it. <br>
    Add a thank you message and a background image.

## Check that signups save to the local database

33. View the app by starting a local web server.

34. In the contact page, type in your name and email address, and submit the form.

35. Check that your info saved to your local database. <br>
    Start the local Rails console and retrieve all signups in the database. <br>
    Your info should show up in the results.

## Check that signups save to the production database

36. Commit all your changes using Git, and push up to GitHub.

37. In the contact page, type in your name and email address, and submit the form.

38. Check that your info saved to the production database. <br>
    Start the production Rails console by running

    ```ruby
    rails console
    ```

    and retrieve all signups in the database. <br>
    Your info should show up in the results.
