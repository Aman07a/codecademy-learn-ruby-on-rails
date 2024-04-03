#### Learn

### ASSOCIATIONS II

## Actors I

**17 min**

Great job! The app displays all actors that belong to a movie.<br>
The `has_many :through` association lets us easily query for all actors that belong to a movie.

## Instructions

1. Let’s add the ability to see all movies an actor has appeared in.

   Generate a controller named Actors.

   ```ruby
   rails generate controller Actors
   ```

2. In the routes file, add a route that maps the URL `/actors` to the Actors controller’s `index` action.

3. Then in the Actors controller, add the `index` action to display a list of all actors.

4. In **app/views/actors/index.html.erb**, iterate through each actor and display the image, first name, and last name.

5. Back in the routes file, add another route to send requests to URLs like `/actors/1` to the Actors controller’s show action. <br>
   Use `as:` to name this route `:actor`.

6. Then in the Actors controller, add the `show` action to display a specific actor and the filmography. <br>
   To do this, first find an actor by id. Then retrieve all movies that belong to the actor.

7. In **app/views/actors/show.html.erb**:

   Display the actor’s image, first name, last name, and bio.
   Then iterate through each movie and display its title, image, and release year.

8. Finally in **app/views/actors/index.html.erb** below an actor’s name, use `link_to` to add a link to that actor:

   - Use “Learn more” for the link text.
   - By giving the show route a name of “actor”, <br>
     Rails automatically creates a helper method named actor_path, so use it to generate a URL to a specific actor’s path

9. Visit `http://localhost:4001/movies` in the browser. <br
   Click on a movie to see its cast.

Then visit `http://localhost:4001/actors`. <br
Click on an actor to see what movies they have appeared in.

Press **Run** to test your code!
