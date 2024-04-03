#### Learn

### ASSOCIATIONS I

## Show a destination

**22 min**

Nice job! The app displays all destinations that belong to a tag. How does this work?

When a user visits `http://localhost:4001/tags/1`, the route `get '/tags/:id', to: 'tags#show'` <br>
sends this request to the Tags controller’s show action with `{id: 1}` in `params`. <br>
The `@destinations = @tag.destinations` retrieves all the destinations that belong to the tag, and stores them in `@destinations`. <br>
The `has_many` / `belongs_to` association lets us query for destinations like this. <br>
The tag and its destinations are sent to the view to be displayed.

## Instructions

1. Let’s add functionality to see a destination.

   Generate a controller named Destinations.

   ```ruby
   rails generate controller Destinations
   ```

2. Now in the Destinations controller file, add the line:

   ```ruby
   skip_before_action :verify_authenticity_token
   ```

   inside of the `DestinationsController` class.

   This will allow us to edit the destinations later without providing an authenticity token
   since we do not need this example project to be secure.

3. Next, in the routes file, map `/destinations/:id `requests to the Destinations controller’s `show` action. <br>
   Use `as:` to name this route `:destination`.

   ```ruby
   get '/destinations/:id', to: 'destinations#show', as: :destination
   ```

   Press **Run** to test your code!

4. Then in the Destinations controller, set up the `show` action.
   Use params to find a destination by id, and save it in `@destination`

   ```ruby
    class DestinationsController < ApplicationController
        skip_before_action :verify_authenticity_token

        def show
            @destination = Destination.find(params[:id])
        end
    end
   ```

   Press **Run** to test your code!

5. Then in the view **app/views/destinations/show.html.erb**, display the destination’s image, name, and description.

   ```erb
    <h2><%= @destination.name %></h2>
    <img src="<%= @destination.image %>" alt="<%= @destination.name %> Image" width="200">
    <p><%= @destination.description %></p>
   ```

6. Now, navigate to the tags show view in **app/views/tags/show.html.erb** below a destination’s description,
   use `link_to` to add a link to that destination:

   - Use “See more” for the link text

   - By giving the `show` route a name of “destination”, <br>
     Rails automatically creates a helper method named `destination_path`. <br>
     Use `destination_path` to generate a URL to a specific destination’s path.

   ```erb
   <%= link_to "See more", destination_path(destination) %>
   ```

   Press **Run** to test your code!

7. Visit `http://localhost:4001/tags/1` in the browser. <br>
   Click on a destination to see its show page.

   Press **Run** to test your code!
