#### Learn

### ASSOCIATIONS II

## Movies I

**10 min**

Nice work! Let’s review what we did:

1. We added columns to the movies table and actors table
2. We used the `t.belongs_to` methods in the parts table to add foreign keys, setting up the many-to-many relationship.
3. Finally we ran the migrations to update the database, and seeded the database with the data in **db/seeds.rb**

## Instructions

1. Now that the models are set up, <br>
   let’s move on to the rest of the request/response cycle and create the routes, controllers, and views.

   Generate a controller named Movies.

   ```ruby
   rails generate controller Movies
   ```

2. In the routes file, create a new route that maps the URL /movies to the Movies controller’s `index` action.

   ```ruby
   get "/movies", to: "movies#index"
   ```

3. Then in the Movies controller, add the index action to display a list of all movies. <br>
   To do this, fetch all movies from the database and store them in variable `@movies`.

   ```ruby
   class MoviesController < ApplicationController
    def index
        @movies = Movie.all
    end
   end
   ```

4. In **app/views/movies/index.html.erb** inside `<div class="main">` iterate through each movie in `@movies` <br>
   and display the image, title, release year, and plot.

5. Visit `http://localhost:4001/movies` in the browser.

   Then press **Run** to pass this step.
