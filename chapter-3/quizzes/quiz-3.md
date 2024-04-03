## Quiz 3

1. How can you say one model contains a lot of other model elements, like a List with many Tasks?

   ```ruby
   class List < ApplicationRecord
    ________________
   end
   ```

   ***

   - `has_many :tasks`
   - `:contains_many @tasks`
   - `@list = Tasks.all`
   - `List contains_many Tasks`

   Correct:

   - `has_many :tasks`

2. How does a Task model know about the List model in the Task model’s migration table?

   ```ruby
   class CreateTasks < ActiveRecord::Migration
    def change
        create_table :tasks do |t|
        t.string :name
        t.string :image
        t.string :description
        ________________
        t.timestamps
    end
   end
   ```

   ***

   - `t.references :list`
   - `t.longs_to :list`
   - `t.string :list`
   - `t.association :list`

   Correct:

   - `t.references :list`

3. What is the purpose of the as: tag for the provided Rails route?

   ```ruby
   get '/destinations/:id', to: 'destinations#show', as: :destination
   ```

   ***

   - It defines **:destination** as an alias for all actions in the destinations controller
   - It allows the route to redirect to multiple locations.
   - It forms a named route which allows the **#show** action from the **destinations** controller to be used elsewhere
   - It enables the route to access both **get** and **post** requests simultaneously

   Correct:

   - It forms a named route which allows the **#show** action from the **destinations** controller to be used elsewhere

4. What is the correct syntax to list the titles of all the tags in the Tag controller?

   ```erb
    <div class="cards row">
      ______________________
      <div class="card col-xs-4">
        <h2><%= t.title %></h2>
        <%= link_to "Learn more", tag_path(t) %>
      </div>
      <% end %>
    </div>
   ```

   ***

   - `@tags.each do |t|`
   - `for |tag| in @tags do |t|`
   - `<% for |tag| in @tags do |t| %>`
   - `<% @tags.each do |t| %>`

   Correct:

   - `<% @tags.each do |t| %>`

5. What is the reciprocal relationship to :has_many?

   - `child_of`
   - `belongs_to`
   - `part_of`
   - `contains_many`

   Correct:

   - `belongs_to`

6. Put these steps in order for the actions a Rails app takes when its data is being edited:

   1. The browser makes a HTTP GET request for the URL /tags/1/edit.
   2. The edit action finds the tag with id 1, stores it in @tag, and passes it on to the view app/views/tags/edit.html.erb.
   3. In the view, form_for creates a form with the fields of the @tags object.
   4. The Rails router maps this URL to the Tags controller's edit action.

   ***

   - `1, 2, 4, 3`
   - `3, 1, 2, 4`
   - `3, 1, 4, 2`
   - `1, 4, 2, 3`

   Correct:

   - `1, 4, 2, 3`

7. What is the correct syntax to build a list of all Tags?

   ```ruby
   class TagsController < ApplicationController
    def index
      _____________
    end
   end
   ```

   ***

   - `@tags = Tags.find(params[:id])`
   - `Tag.all`
   - `@tags = Tags.all`
   - `@tags = Tag.all`

   Correct:

   - `@tags = Tag.all`

8. Is it possible to create a route between two controllers like a Task and List controller set?

   - Yes, one-way post requests (ie. post a task to a list) will work
   - No, routes have to stay within their own controllers
   - No, any connection between Tasks and Lists has to come from the controllers
   - Yes, any Task can link to any List action in the routes file

   Correct:

   - Yes, any Task can link to any List action in the routes file

9. Which of these apps would require more than two models with associations between them?

   - A social thread app that posts messages into a stream
   - A grocery app that adds different foods to a shopping list
   - A resume app that allows users to build their own CV
   - A movie app that lets users look up actors/directors in their favorite movies

   Correct:

   - A movie app that lets users look up actors/directors in their favorite movies

10. Which of these relationships is a correct representation of has_many and belongs_to?

    - Store and Products
    - Book and Magazine
    - Person and Name
    - Task and Description

    Correct:

    - ?
