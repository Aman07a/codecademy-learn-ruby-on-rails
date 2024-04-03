#### Learn

### ASSOCIATIONS I

## Show a tag

**17 min**

Well done! The app now displays a list of tags from the database!

## Instructions

1. Let’s add another action to display a specific tag. <br>
   Looking at the [seven standard controller actions](http://www.codecademy.com/articles/standard-controller-actions),
   we need to use the `show` action. Let’s set it up now.

   First in the routes file, add this route:

   ```ruby
   get '/tags/:id', to: 'tags#show', as: :tag
   ```

   Here we use `as:` to name this route “tag”.

   Now press **Run** to test your code!

2. Then in the Tags controller, add the `show` action:

   ```ruby
   def show
    @tag = Tag.find(params[:id])
    @destinations = @tag.destinations
   end
   ```

3. In **app/views/tags/show.html.erb** inside the `<h2>` element, display a tag’s title.

   Then in `<div class="cards row">...</div>`, <br>
   iterate through each destination in the `@destinations` array and display its image, name, and description.

   Press **Run** to test your code!

4. Finally in **app/views/tags/index.html.erb** within the `<% @tags.each do |t| %>...<% end %>` block,
   add this link at the bottom of the `<div>:`

   ```ruby
   <%= link_to "Learn more", tag_path(t) %>
   ```

   By giving the route in step 1 the name “tag”, Rails automatically creates a helper method named `tag_path`. <br>
   We use `tag_path(t)` here to generate the URL to a specific tag’s path, for example `/tag/1`.

   Press **Run** to test your code!

5. Visit `http://localhost:4001/tags` in the browser. <br>
   Click on a ‘Learn more’ to see all destinations under that tag. <br>
   Make sure your server is still running with the command:

   ```ruby
   rails s
   ```

   Now press **Run** to test your code!
