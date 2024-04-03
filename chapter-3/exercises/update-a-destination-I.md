#### Learn

### ASSOCIATIONS I

## Update a destination I

21 min
Great! The app now displays a specific destination.

Let’s continue by adding actions to update a destination’s name and description. <br>
Looking at the seven standard Rails actions, we need to use the `edit` and `update` actions to do this. <br>
Let’s set them up now.

## Instructions

1. First in the routes file (`config/routes.rb`), add these routes:

   ```ruby
    get '/destinations/:id/edit', to: 'destinations#edit', as: :edit_destination
    patch '/destinations/:id', to: 'destinations#update'
   ```

2. Then in the Destinations controller below the `show` action, add an `edit` action:

   ```ruby
    def edit
        @destination = Destination.find(params[:id])
    end
   ```

3. Below the `edit` action, add a private method named `destination_params`:

   ```ruby
    private
    def destination_params
        params.require(:destination).permit(:name, :description)
    end
   ```

4. Between the `edit` action and the private method, add an `update` action:

   ```ruby
   def update
       @destination = Destination.find(params[:id])
       if @destination.update(destination_params)
           redirect_to(action: 'show', id: @destination.id)
       else
           render 'edit'
       end
   end
   ```

5. In **app/views/destinations/edit.html.erb** inside `<div class="container">...</div>`,<br>
   use `form_for` to create a form with the fields of the `@destination` object.

   Look back at [this exercise on creating a form with fields]() for an example on how to use `form_for`.

6. Finally in **app/views/destinations/show.html.erb**, <br>
   use `link_to` to create a link to the destination’s edit path:

   - Use “Edit” for the link text
   - By giving the `edit` route a name of “edit_destination”, <br>
     Rails automatically creates a helper method named `edit_destination_path`. <br>
     Use it to generate a URL to a specific destination’s edit path.

7. Visit `http://localhost:4001/tags/1` in the browser and click on a destination. <br>
   Then click the Edit button to edit the destination’s name and description.
