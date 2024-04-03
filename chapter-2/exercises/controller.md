##### Learn

### SAVING DATA

## Controller

**14 min**

What did we just do?

1.  The `rails generate model` command created a new model named Message. In doing so, Rails created two files:

    - a model file in **app/models/message.rb**. The model represents a table in the database.

    - a migration file in **db/migrate/**. Migrations are a way to update the database.

2.  Open the migration file in **db/migrate/**. The migration file contains a few things:

    - The `change` method tells Rails what change to make to the database. <br>
      Here it uses the `create_table` method to create a new table in the database for storing messages.
    - Inside `create_table`, we added `t.text :content`. <br>
      This will create a text column called content in the messages tables.
    - The final line `t.timestamps` is a Rails command <br>
      that creates two more columns in the messages table called `created_at` and `updated_at`. <br>
      These columns are automatically set when a message is created and updated.

3.  The `bundle exec rake db:migrat`e command updates the database with the new messages data model. <br>
    With this command, we instruct the bundler to execute (`exec`) a rake task, in this case, `migrate`, on the database (`db`).

4.  Finally the `bundle exec rake db:seed` command seeds the database with sample data from db/seeds.rb.

#### Instructions

1.  Now that we have a model, let’s move on to the second and third parts of the request/response cycle <br>
    and create a controller and a route.

    In the terminal, generate a controller named `Messages`.

    ```bash
    rails generate controller Messages
    ```

2.  In the code editor, open the Messages controller file which is located at: <br>
    **app/controllers/messages_controller.rb**

    Then, inside of the `MessagesController` class, add the line:

    ```ruby
    skip_before_action :verify_authenticity_token
    ```

    This will allow us to create messages later without providing an authenticity token
    since we do not need this example project to be secure.

    Press **Run** to test your code.

3.  In the routes file, create a route that maps the URL `/messages` to the Messages controller’s `index` action.

    Make sure to use the format:

    ```ruby
    get '<url>', to: '<controller>#<action>'
    ```

4.  Back in the Messages controller (**app/controllers/messages_controller.rb**), add an `index` action:

    ```ruby
    def index
        @messages = Message.all
    end
    ```
