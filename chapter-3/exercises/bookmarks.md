#### Objective

### LEARN RUBY ON RAILS

## Bookmarks

Bookmarks wants a Rails app for their best-seller list. <br>
Books are listed by rank on the main page. <br>
Clicking on a book takes users to a page where they can read editorial reviews.

To preview your app at any point:

1. In the terminal, type `rails server`
2. In the browser, visit `http://localhost:4001`

If you get stuck during this project or would like to see an experienced developer work through it, click “**Get Unstuck**“ to see a **project walkthrough video**.

## Setup

1. Create a new Rails app named `bookmarks`.

   ```ruby
   rails new bookmarks
   ```

2. After you create the new app, switch to its folder. In the terminal, type:

   ```bash
   cd bookmarks
   ```

3. Install the gems in the **Gemfile**.

   ```ruby
   bundle install
   ```

4. In the root directory of the project, we’ve provided the base HTML and CSS, files for this project. <br>
   Look at the bottom of your file navigator to locate them. Let’s put their contents in the correct place in your project.

   In your Rails project, create **app/views/books/index.html.erb** and copy and paste the contents of the root **index-copy.html.erb** into that file. <br>
   Create **app/views/books/show.html.erb** and copy and paste the contents of the root **show-copy.html.erb** into that file.

   Then, similarly, create **app/assets/stylesheets/books.css** and copy the contents of the root **books-copy.css** into it.

5. Open **app/views/layouts/application.html.erb** and add the following lines immediately following the `<title>` tag.

   ```html
   <link
     rel="stylesheet"
     href="http://content.codecademy.com/projects/bootstrap.min.css"
   />
   <link
     href="http://fonts.googleapis.com/css?family=Domine"
     rel="stylesheet"
     type="text/css"
   />
   <link
     href="http://fonts.googleapis.com/css?family=Merriweather:300italic,300"
     rel="stylesheet"
     type="text/css"
   />
   ```

6. Generate a model named Book.

   ```ruby
   rails generate model Book
   ```

7. Generate a model named Review.

   ```ruby
   rails generate model Review
   ```

8. Associate the Book model with the Review model using the `has_many` and `belongs_to` methods:

   - Open up `app/models/book.rb` and add the `has_many` method.
   - Open up `app/models/review.rb` and add the `belongs_to` method.

   ```ruby
   class Book < ApplicationRecord
    has_many :reviews
   end
   ```

   ```ruby
   class Review < ApplicationRecord
    belongs_to :book
   end
   ```

9. Open the migration file in **db/migrate/** for the books table, and add the following columns:

   - a string column called `title`
   - a string column called `author`
   - a string column called `description`
   - a string column called `publisher`
   - an integer column called `weeks_on_list`
   - an integer column called `rank_this_week`

   ```ruby
   class CreateBooks < ActiveRecord::Migration[6.0]
    def change
        create_table :books do |t|
        t.string :title
        t.string :author
        t.string :description
        t.string :publisher
        t.integer :weeks_on_list
        t.integer :rank_this_week
        t.timestamps
        end
    end
   end
   ```

10. Open the migration file in **db/migrate/** for the reviews table, and add the following columns:

    - a string column called `author`
    - a string column called `comment`
    - a references column to the Book model

    The references column is needed because the Review model has a `belongs_to` association with the Book model.

    ```ruby
    class CreateReviews < ActiveRecord::Migration[6.0]
        def change
            create_table :reviews do |t|
            t.string :author
            t.string :comment
            t.references :book, foreign_key: true
            t.timestamps
            end
        end
    end
    ```

11. Run a migration to update the database with the Book model and Review model.

    ```ruby
    rails db:migrate
    ```

12. We’ve prepared a few items in the **seeds-copy.rb** file located at the root directory of the project (outside of /bookmarks). <br>
    Prepare to seed the database with books and reviews by copying the contents of the file and replacing everything in **db/seeds.rb**.

    You can even create your own data in **db/seeds.rb**! Optionally consider:

    - Creating two more Book records. Feel free to use your favorite books.
    - Creating Review records associated with each book.

13. Run `bundle exec rake db:seed` to seed the database with the data in **db/seeds.rb**.

    ```ruby
    bundle exec rake db:seed
    ```

## Add a controller and routes 14.

14. Generate a controller named Books.

    ```ruby
    rails generate controller Books
    ```

15. In the routes file, add the resource route for the Books controller.

    ```ruby
    resources :books
    ```

16. Run the `rails routes` command in the terminal to view all of the new URLs that the resource route created.

    ```ruby
    rails routes
    ```

    Take a look at the Rails [seven standard controller actions](https://www.codecademy.com/articles/standard-controller-actions). <br>
    Think about which actions from the `rails routes` command, we need for displaying a list of all books and for displaying a specific book. <br>
    Then, we will create those in the next section!

    Add controller actions and views

    ```ruby
    rails generate controller
    ```

17. Now let’s set up the `books#index` controller action.

    In the Books controller, make an action named `index` that retrieves all books from the database,
    and saves it into a variable named `@books`.

    ```ruby
    class BooksController < ApplicationController
        def index
            @books = Book.all
        end
    end
    ```

18. Check out the view index.html.erb inside the app/views/books directory. <br>
    We use

    ```erb
    <% @books.each do |book| %>
    ```

    to loop through each element in @books.

    Finish the view to display a book’s details. <br>
    In each of the `<p>` elements, display the appropriate data from the book element.

    For example:

    ```erb
    <p class="title"> <%= book.title %> </p>
    ```

19. In the routes file, set the `index` action as the root route.

    ```ruby
    root 'books#index'
    ```

20. View the result by running your project.

    Start a Rails server to preview the app in the browser.
    In the terminal, type:

    ```ruby
    rails server
    ```

    This command starts a Rails server listening on port 4001.
    Visit `http://localhost:4001` to see your app in the browser.

21. In the Books controller, make an action named show:

    ```ruby
    def show
        @book = Book.find(params[:id])
        @reviews = @book.reviews
    end
    ```

    First we retrieve a single book, and save it in `@book`. <br>
    Then we retrieve all of its reviews, and save them in `@reviews`. <br>
    The `has_many` / `belongs_to` association lets us query for reviews like this.

22. Update the view **app/views/books/show.html.erb**.

    First, display a single book’s details in each of the provided `<p>` elements.

    For example:

    ```erb
    <p class="title"> <%= @book.title %> </p>
    ```

23. Let’s keep modifying **app/views/books/show.html.erb**!

    In the reviews loop later in the code, display the details of each review inside of the provided `<p>` elements.

    For example:

    ```erb
    <p class="author"> <%= review.author %> </p>
    ```

24. View the result by refreshing `http://localhost:4001/`.

    Click on a book’s **See all Editorial Reviews** link to see its reviews.

    If you need to restart the Rails server, first press **Ctrl+C** in the terminal to shut down the server. <br>
    Then type `rails server` to restart it.

    ```ruby
    rails server
    ```
