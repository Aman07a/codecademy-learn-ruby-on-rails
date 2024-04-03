#### Learn

### SAVING DATA

## Model

**5 min**

Great! You created a new Rails app named MessengerApp.

Looking at [this diagram of the request/response cycle](https://www.codecademy.com/articles/request-response-cycle-dynamic),
we need four parts to build a Rails app - a model, a route, a controller, and a view.

Let’s start here by creating a model.

#### Instructions

1. In the terminal, generate a new model named `Message`

   ```ruby
   rails generate model Message
   ```

2. In the code editor, open the migration file in **db/migrate/** for the messages table. <br>
   The name of the migration file starts with the timestamp of when it was created. <br>
   Inside the change method, add this line as line 4:

   ```ruby
   t.text :content
   ```

   Now hit **Run** to test your code!

3. Then in the terminal, run

   ```ruby
   bundle exec rake db:migrate
   ```

4. Finally, run

   ```ruby
   bundle exec rake db:seed
   ```

   Press **Next** to see an explanation of what we just did!
