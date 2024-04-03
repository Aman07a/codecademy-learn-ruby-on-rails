#### Objective

### LEARN RUBY ON RAILS

## Threadly

Threadly wants to create a Rails app for their commenting service. <br>
When a user types a comment into the box and clicks the Post button, the comment is saved into a database.

Using the [request/response cycle](https://www.codecademy.com/articles/request-response-cycle-forms)
as a guide, here’s what we need to do for the Threadly app:

1. In the first turn of the request/response cycle, the list of all posts is displayed to the user.
2. When a user posts a comment, it triggers the second turn of the request/response cycle, where a new post is added to the database.

To preview your app at any point:

1. In the terminal, type `rails server`
2. In the browser, visit `http://localhost:4001`

If you get stuck during this project or would like to see an experienced developer work through it, <br>
click “**Get Unstuck**“ to see a **project walkthrough video**.

#### Tasks

## Setup

1. Create a new Rails app named `threadly`.

   ```ruby
   rails new threadly
   ```

2. After you create the new app, switch to its folder. In the terminal, type:

   ```bash
   cd threadly
   ```

3. Install the gems in **Gemfile**.

   ```ruby
   bundle install
   ```

4. In the root directory of the project, we’ve provided the base HTML and CSS, files for this project. <br>
   Look at the bottom of your file navigator to locate them. <br>
   Let’s put their contents in the correct place in your project.

   In your Rails project, create **app/views/posts/** folder. <br>
   Then, inside your folder, create a file, **app/views/posts/index.html.erb**, <br>
   and copy and paste the contents of the **root index-copy.html.erb** into that file.

   Then, similarly, create **app/assets/stylesheets/posts.css** and copy the contents of the root **posts-copy.css** into it.

## Add a model

5. Generate a model named **Post**.

   ```ruby
   rails generate model Post
   ```

6. Open the migration file in **db/migrate/**, and add a string column called `comment`.

   ```ruby
   t.string :comment
   ```

7. Run a migration to update the database with the Post model.

   ```ruby
   bundle exec rake db:migrate
   ```

## Add a controller and routes

8. Generate a controller named Posts.

   ```ruby
   rails generate controller Posts
   ```

9. In the Posts controller file, add

   ```ruby
   skip_before_action :verify_authenticity_token
   ```

   to the PostsController class to skip verification when submitting data in this example project.

10. In the routes file, add the resource route `resources :posts`.

11. Run the `bundle exec rails routes` command in the terminal to view all of the new URLs <br>
    that the resource route maps to the Posts controller’s seven standard actions. <br>
    Resize the terminal component to see the routes.

    Looking back at the request/response cycle, <br>
    we need a controller action to handle `GET` requests and another controller action to handle POST requests. <br>
    According to the output of bundle exec rake routes, we can use:

    - `posts#index` to handle `GET` requests by displaying all comments.
    - `posts#create` to handle `POST` requests by saving a new post to the database.

## Add controller actions and views

12. Let’s set up the `posts#index` controller action to handle `GET` requests:

    In the Posts controller, make an action named `index`:

    ```ruby
    def index
        @new_post = Post.new
        @all_posts = Post.order(created_at: :desc).all
    end
    ```

13. Next, we’ll use `@new_post` in the view to render a form.

    In **app/views/posts/index.html**, create a Rails form with the fields of the `@new_post` object to post comments.

14. Now let’s use `@all_posts` to render a list of all posts, sorted in descending order.

    In **app/views/posts/index.html**, replace the hardcoded`<ul>` element by using `@all_posts`:

    ```ruby
    <ul class="comments">
        <% @all_posts.each do |p| %>
        <li><%= p.comment %></li>
        <% end %>
    </ul>
    ```

    Here we loop through each element in `@all_posts` and display them in `<li>` elements.

15. In the routes file, set the `index` action as the root route.

16. Set up the `posts#create` controller action to handle POST requests:

    - In the Posts controller, write a private method named `post_params`. <br>
      Require the model name `post` and permit the column name `comment`. <br>

    - In the Posts controller, make an action named `create`.<br>
      Use `post_params` to create a new Post object.<br>
      After saving to the database, redirect to `root_path`.

17. Start a Rails server to preview the app in the browser.
    In the terminal, type:

    ```ruby
    rails server
    ```

    This command starts a Rails server listening on port 4001.
    Then visit `http://localhost:4001` to see your app in the browser.

    Try typing a comment and submitting the form!

    ```ruby
    private
    def post_params
        params.require(:post).permit(:comment)
    end
    ```

    ```ruby
    def create
        @new_post = Post.new(post_params)
        if @new_post.save
            redirect_to root_path
        end
    end
    ```

## Check the database

18. Check that your comment saved to the database using the Rails console.

    Open a new terminal tab by clicking the icon. <br>
    Navigate to your `threadly` folder using cd. <br>
    Then start the Rails console and retrieve all comments in the database using `Post.all`. <br>
    Your comment should show up in the results. <br>

19. Add more comments through the form, and use the Rails console to check that they saved to the database.
