### Objective

##### LEARN RUBY ON RAILS

## Innovation Cloud

Innovation Cloud want to create a Rails app to collect email signups. <br>
At the bottom of the page, when a user enters their email, the email is saved into a database.

Using the [request/response cycle](https://www.codecademy.com/articles/request-response-cycle-forms) as a guide,
here’s what we need to do for the Innovation Cloud app:

In the first turn of the request/response cycle, the signup form is displayed to the user. <br>
When the user fills in the form with an email and submits it, it triggers the second turn of the request/response cycle,
where the email data is saved into the database. <br>

To preview your app at any point:

1. In the terminal, type rails server
2. In the browser, visit http://localhost:4001

If you get stuck during this project or would like to see an experienced developer work through it, <br>
click “**Get Unstuck**“ to see a **project walkthrough video**.

### Tasks

## Setup

1. Create a new Rails app named `innovation-cloud`.

   ```ruby
   rails new innovation-cloud
   ```

2. After you create the new app, switch to its folder.

   ```bash
   cd innovation-cloud
   ```

3. Install the gems in **Gemfile**.

   ```bash
   bundle install
   ```

4. In the root directory of the project, we’ve provided the base HTML, CSS, and a Ruby controller file for this project. <br>
   Look at the bottom of your file navigator to locate them.

   In the next few steps, we’ll put their contents in the correct place.

   Within the file navigator, navigate to **app/views** and create the folder **signups**.<br>
   Within your new folder, **app/views/signups**, create a new file **new.html.erb**. <br>
   Copy and paste the contents of the root **new-copy.html.erb** into that file.

5. Next, navigate to **app/views** and create the folder pages. <br>
   Within your new folder, **app/views/pages**, create a new file **thanks.html.erb**. <br>
   Copy and paste the contents of the root **thanks-copy.html.erb** into your new file.

6. Then, navigate to **app/controllers** and create a **pages_controller.rb** file. <br>
   Copy the contents of the root **pages_controller-copy.rb** <br>
   and paste them into your new **app/controllers/pages_controller.rb** file.

7. Finally, navigate to **app/assets/stylesheets** and create the file pages.css. <br>
   Copy and paste the contents of the root pages-copy.css into your new **app/assets/stylesheets/pages.css** file.

## Add a model

8. Generate a model named `Signup`.

   ```ruby
   rails generate model Signup
   ```

9. Open the migration file in **db/migrate/**, and add a string column called email.

   ```ruby
   class CreateSignups < ActiveRecord::Migration[6.0]
       def change
           create_table :signups do |t|
           t.string :email
           t.timestamps
           end
       end
   end
   ```

10. Run a migration to update the database with the Signup model.

    ```ruby
    bundle exec rake db:migrate
    ```

## Add a controller and routes

11. Generate a controller named Signups.

    ```ruby
    rails generate controller Signups
    ```

12. Open the Signups controller file: **app/controllers/signups_controller**.

    Inside of the SignupsController class, paste the line:

    ```ruby
    skip_before_action :verify_authenticity_token
    ```

    This allows us to skip verification when submitting data in our test app.

13. In earlier steps, we created a controller named Pages in `app/controllers/pages_controller.rb` that has an action named `thanks`.

    In the routes file, map the request for the url /thanks to the Pages controller’s `thanks` action. We’ll use this route later.

    ```ruby
    get '/thanks', to: 'pages#thanks'
    ```

14. In the routes file, under the `thanks` route, add:

    ```ruby
    resources :signups
    ```

    This is called a resource route.
    It maps URLs to the Signups controller’s [seven standard actions](https://www.codecademy.com/articles/standard-controller-actions).

15. In the terminal, run:

    ```ruby
    bundle exec rails routes
    ```

    to view all of the new URLs that the resource route created. Resize the terminal component to see the routes.

    Which routes should we use? Looking back at the request/response cycle,
    we need a controller action to handle `GET` requests and another controller action to handle `POST` requests. <br>
    According to the output of `bundle exec rails routes`, we can use:

    - `signups#new` to handle `GET` requests by displaying the signup form.
    - `signups#create` to handle `POST` requests by saving an email to the database.

## Add controller actions and views

16. We’ll set up the `signups#new` controller action to handle `GET` requests.

    In the Signups controller, make an action named `new`.

    ```ruby
    def new
        @signup = Signup.new
    end
    ```

17. Inside **app/views/signups/new.html.erb** under line 37, create a form to gather email signups. <br>
    Use `form_for` to create a form with the fields of the `@signup` object. <br>
    [Adapt your code from this Rails exercise](https://www.codecademy.com/courses/learn-rails/lessons/one-model/exercises/one-model-create-messages-i).

18. In the routes file, set the new action as the root route.

    ```ruby
    root 'signups#new'
    ```

19. Start a Rails server to preview the app in the browser. In the terminal, type:

    ```ruby
    rails server
    ```

    This command starts a Rails server listening on port 4001. <br>
    Then visit `http://localhost:4001` to see your app in the browser.

20. Set up the `signups#create` controller action to handle `POST` requests.

    In the Signups controller, write a private method named `signup_params`:

    ```ruby
    private
    def signup_params
        params.require(:signup).permit(:email)
    end
    ```

    Strong parameters give us a safe way to collect data from a form and update the Signup model. <br>
    Here we require the model name signup and permit the column name email.

21. In the Signups controller, make an action named `create`. <br>
    Use `signup_params` to safely collect data from the form and update the database.

    After saving to the database, redirect to `thanks_url`. <br>
    If the signup wasn’t saved successfully, render the `new` template.
    [Adapt your code from this Rails exercise](https://www.codecademy.com/en/learn/learn-rails/topics/one-model/exercises/one-model-create-messages-i).

22. Restart the Rails server and view the result by visiting `http://localhost:4001/`.
    Type in an email address and submit the form.

    To restart a Rails server, in the terminal, first press `ctrl` + `c` to shut down the server.
    Then type `rails server` to restart it.

## Check the database

23. Confirm that your email saved to the database.
    The Rails console is a useful tool to interact with Rails apps.

    We’ll use it here to query the database.

    - In the terminal, open a new tab by clicking the plus (+) icon located to the left of the first tab.
    - Switch into your app’s folder by typing `cd innovation-cloud`.
    - Start the Rails console by running `rails console`.
    - When you enter the Rails console, retrieve all emails in the database by running the query `Signup.all`.
    - This query returns all emails in the database as an array. Your email should show up in the console output.
      To exit the Rails console at any point, use `ctrl` + `d`.

24. Sign up a few more emails through the app, and use the Rails console to check that they saved to the database.
