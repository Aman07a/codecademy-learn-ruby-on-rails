#### Objective

### LEARN RUBY ON RAILS

## Bolt Network

Bolt Network wants to create a Rails app with a Home page and an About page.
[Here’s an image of what it will look like](https://static-assets.codecademy.com/Courses/learn-ruby-on-rails/Bolt-network/bolt-network-app.jpeg).

Using the [request/response cycle](https://www.codecademy.com/articles/request-response-cycle-static) as a guide, there are eight changes to be made.

To preview your app at any point:

1. In the terminal, type `rails server`
2. In the browser, visit `http://localhost:4001` or `http://127.0.0.1/:3000`

If you get stuck during this project or would like to see an experienced developer work through it,
click “**Get Unstuck**“ to see a **project walkthrough video**.

## Tasks

**Progress**: 4/10 complete

Mark the tasks as complete by checking them off.

1. Create a new Rails app named `bolt-network`.

   ```
   rails new bolt-network
   ```

2. After you create the new app, switch to its folder. In the terminal, type:

   ```
   cd bolt-network
   ```

3. Install the gems in the `Gemfile`.

   ```
   bundle install
   ```

4. In the root directory of the project, we’ve provided the base HTML (`home-copy.html.erb`) <br>
   and CSS (`pages-copy.css.scss`) for this project. Look at the bottom of your file navigator to locate them.

   In your Rails project, create a new directory and file for `app/views/pages/home.html.erb`. <br>
   Then, copy and paste the contents of the root `home-copy.html.erb` into your newly-created file.

   Then, similarly, create `app/assets/stylesheets/pages.css.scss` <br>
   and copy and paste the contents of the root `pages-copy.css.scss` into that new file.

5. Generate a controller named `Pages`. <br>
   In the Pages controller file (`app/controllers/pages_controller.rb`) create two empty actions. <br>
   One named `home` for the Home page and another named `about` for the About page.

6. In the routes file (`config/routes.rb`), first set the `home` action as the root route.

7. Next, create a new route to map the URL `/about` to the `about` action.

8. Start a Rails server to preview the app in the browser. In the terminal, type:

   ```
   rails server
   ```

   Then visit `http://localhost:4001` in the browser.

   Also, try visiting `http://localhost:4001/about` to ensure your route is set up correctly. <br>
   You’ll notice an error about a missing template but don’t worry, that’ll be resolved in the next few steps.

9. In the `app/views/pages/` directory, create a new view called `about.html.erb`. <br>
   Copy the HTML from `about-copy.html.erb` in the root directory (outside of the bolt-network directory) <br>
   and paste it inside `app/views/pages/about.html.erb`.

10. The layout file lets you build a base view that contains all the common elements of your site, such as CSS files, the header, and the footer. <br>
    The <%= yield %&> defines the portion of the layout that child templates (like home.html.erb and about.html.erb) can fill in.

    Now let’s up the layout file (`app/views/layouts/application.html.erb`): <br>
    In the <head> element below the <title>, add the CSS files for Bootstrap and the web font:

    ```html
    <link
      rel="stylesheet"
      href="https://content.codecademy.com/projects/bootstrap.min.css"
    />

    <link
      href="https://fonts.googleapis.com/css?family=Oxygen:300,400,700"
      rel="stylesheet"
      type="text/css"
    />
    ```

    Then in the browser, click the reload icon to refresh the page and preview your updated app.
