#### Objective

### LEARN RUBY ON RAILS

## Broadway

Broadway wants to build a Rails app for their home page. <u>Here’s an image of what it will look like</u>.<br>
Looking at the <u>request/response cycle</u>,
we need three parts to build this Rails app - a route, a controller, and a view.
To preview your app at any point:

1. In the terminal, type `rails server`
2. In the browser, visit `http://localhost:4001`

If you get stuck during this project or would like to see an experienced developer work through it,
click **“Get Unstuck“** to see a **project walkthrough video**.

#### Tasks

## Mark the tasks as complete by checking them off

1. Create a new Rails app named `broadway`.

   ```ruby
    cd broadway
   ```

   The `cd` command is a command line command used to switch into a folder.
   If you are new to the command line, we recommend you do our Command Line course.

2. After you create the new app, switch to its folder. In the terminal, type:
   $ cd broadway
   The `cd` command is a command line command used to switch into a folder.
   If you are new to the command line, we recommend you do our Command Line course.

3. Install the gems in the **Gemfile**.

4. Generate a controller named **Pages**.

5. In the Pages controller (`app/controllers/pages_controller.rb`), make an empty action named `home` for the Home page.

6. In the routes file (`config/routes.rb`), map the request for the URL `/pages/home` to Pages controller’s `home` action.

7. In the root directory of the project,
   we’ve provided the base HTML (`home-copy.html.erb`) and CSS (`pages-copy.css.scss`) for this project.
   Look at the bottom of your file navigator to locate them.
   In your Rails project, create `app/views/pages/home.html.erb`.
   Then, copy and paste the contents of the root `home-copy.html.erb` into your newly-created file.
   Then, similarly, create `app/assets/stylesheets/pages.css.scss`.
   Afterward, copy and paste the contents of the root `pages-copy.css.scss` into this new file as well.

8. Start a Rails server to preview the app in the browser. In the terminal, type:

   ```ruby
    rails server
   ```

   This command starts a Rails server listening on port 4001.
   Then visit `http://localhost:4001/pages/home` to see your app in the browser.

9. Currently, nothing happens if the user visits the base URL of our site (`http://localhost:4001`).
   To fix this, let’s replace our `/pages/home` route so that the user is routed to our home page when visiting the root of the site!
   In the routes file (`config/routes.rb`), set the `home` action as the app’s default page.
   To do this, replace the route you created in step 6 with:

   ```ruby
   root 'pages#home'
   ```

   This route tells Rails to map requests for the URL / to the Pages controller’s home action.

10. Now view the result by visiting `http://localhost:4001/`.
    If you need to restart the Rails server:
    1. In the terminal, press `Ctrl`+`C` to shut down the server.
    2. Then type `rails server` to restart the server.
