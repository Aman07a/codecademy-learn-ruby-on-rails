# Quiz 2

1. In the following migration table, fill in the blank to identify the datatype <br>
   that would be used for the body of an email message stored in the database.

   Hint: the message body will be longer than 255 characters.

   ```ruby
    def change
        create_table :messages do |t|
        t._____ :message_body
        t.timestamps
        end
    end
   ```

   - model
   - text
   - string
   - integer

   Correct: text

2. How would you add a route to a new message in the routes.rb file?

   - `get '/messages/new', to: 'messages#create'`
   - `get '/new/messages'`
   - `get '/messages/new', to: '#new'`
   - `get '/messages/new', to: 'messages#new'`

   Correct: `get '/messages/new', to: 'messages#new'`

3. How many standard controller actions does Rails provide?

   - 7
   - 4
   - 10
   - 1

   Correct: 7

4. What common controller action creates a list of a controller’s component parts, like a list of messages in Messages?

   - def index
   - def soft
   - def list
   - def all

   Correct: def index

5. The command `rails generate model` command creates which two types of files?

   - A controller file and a migration file
   - A model file and a controller file
   - A model file and a migration file
   - A controller file and a route file

   Correct: A model file and a migration file

6. What code will create a “New Message” button in the view once the Messages controller is up and running?

   - <%= link_to "messages/new" %>
   - <%= link_to "New Message", "messages/new" %>
   - <%= messages.create %>
   - <a href="<%= link_to "messages/new" %>">New Message</a>

   Correct: <%= link_to "New Message", "messages/new" %>

7. The Request/Response Cycle is

   - The amount of time it takes a Rails application to run the Rails server.
   - A pattern that traces the flow of a user’s request through a Rails application.
   - The amount of time it takes for a browser to load a Rails application.
   - Is an obselete technique used to develop Rails applications.

   Correct: A pattern that traces the flow of a user’s request through a Rails application.

8. What does the correct index method look like?

   ```ruby
   class MessagesController < ApplicationController
        def index
            _________________
        end
    end
   ```

   - @messages = Message.all
   - @message.all
   - @messages = list_of Messages
   - Messages.all

   Correct: @messages = Message.all

9. What does the command bundle exec rake db:migrate do?

   - Creates new routes based on data from a migration table.
   - Seeds the database with data from seeds.rb.
   - Updates the database schema with data from the migration table.
   - Seeds the database with new information from routes created by a new Controller.

   Correct: Updates the database schema with data from the migration table.

10. What are the standard Rails actions used in the controller?

    - index, new, alter, change
    - index_all, new, create_all, show, edit_all, update, and destroy_all
    - index, new, create, show, edit, update, and destroy.
    - list, create, declare, display, alter, change, and delete

    Correct: index, new, create, show, edit, update, and destroy.

11. What is ERB?

    - A ruby library used in Rails.
    - A way to create routes in Rails.
    - An alternative name for Model, Views and Controller (MVC).
    - A way to embed Ruby code in an HTML file in Rails.

    Correct: A way to embed Ruby code in an HTML file in Rails.
