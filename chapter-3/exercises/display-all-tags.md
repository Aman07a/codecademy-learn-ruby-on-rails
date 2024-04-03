#### Learn

### ASSOCIATIONS I

## Display all tags

**13 min**

Nice work. What did we just do?

1. We added two string columns `title` and `image` to the tags table
2. We added three string columns `name`, `image`, and `description` to the destinations table
3. We also added the line `t.references :tag` to the destinations table. <br>
   This adds a foreign key pointing to the tags table. (Foreign keys are references to rows on other tables.)
4. Finally we ran the migration to update the database, and seeded the database with the data in **db/seeds.rb**.

## Instructions

1. Now that the models are set up, let’s move on to the rest of the request/response cycle and create a controller, a route, and a view.

   Generate a controller named `Tags`.

   ```ruby
   rails generate controller Tags
   ```

2. In the routes file, add a new route that maps requests to `/tags` to the Tags controller’s `index` action.

   Press **Run** to test your code!

3. Then in the Tags controller, add the `index` action to display a list of all tags. <br>
   To do this, fetch all tags from the database (`Tag.all`) and store them in variable `@tags`.

4. In **app/views/tags/index.html.erb** at line 19, iterate through each tag in the `@tags` array. <br>
   Then for each tag, display its title and image. <br>
   Notice that we’ve included some HTML template help in the multi-line comment from lines 12-18.

   We’ve already linked the CSS file to this view. <br>
   If you’re curious, you can find the CSS file at **app/assets/stylesheets/application.css**.

   Then press **Run** to test your code!

5. Visit `http://localhost:4001/tags` in the browser.

   Now press **Run** to test your code!
