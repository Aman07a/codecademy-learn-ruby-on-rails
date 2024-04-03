#### Learn

#### ASSOCIATIONS II

#### Movies II

**15 min**

Well done! The movies show up on the page.

Let’s add another action to display a specific movie and its actors. <br>
Looking at the [seven standard controller actions](https://www.codecademy.com/articles/standard-controller-actions),
we need to use the `show` action to do this.

#### Instructions

1. In the routes file, add another route to send requests to URLs like `/movies/1` to the Movie controller’s `show` action. <br>
   Use `as:` to name this route “movie”.

2. Then in the Movies controller, add the `show` action to display a specific movie and its actors.

   - First use `Movie.find` to find the movie by its `id`.
   - Then retrieve all actors that belong to the movie, and store them in `@actors`.

3. In **app/view/movies/show.html.erb**

   - Inside `<div class="movie">...</div>`, create a new “info” div which displays the movie’s image, title, release year, and plot.
   - Below `<h2>Cast</h2>`, iterate through each actor and display the image, first name, last name, and bio.

4. Finally in `app/views/movies/index.html.erb` below a movie’s plot, use `link_to` to add a link to that movie:

   - Use “Learn more” for the link text
   - By giving the `show` route a name of “movie”, <br>
     Rails automatically creates a helper method named `movie_path`, so use it to generate a URL to a specific movie’s path

5. Visit `http://localhost:4001/movies` in the browser. <br>
   Click on a ‘Learn more’ to see a movie and its actors.

   Then press **Run** to pass this step.
