#### Learn

### SAVING DATA

## Create messages I

**21 min**

Nice work! The app now displays a list of all messages in the database. How does this work?

The file **index.html.erb** is a web template.
Web templates are HTML [files](https://www.codecademy.com/resources/docs/ruby/files) that contain [variables](https://www.codecademy.com/resources/docs/ruby/variables) and control flow statements.
Rather than write the same HTML over and over again for each message,
we can use web templates to loop through and display data from the database.

In this case:

1. `<% @messages.each do |message| %>` iterates through each message in `@messages` array.
   We created `@messages` in the Messages controller’s index action.

2. For each message, we use `<%= message.content %>` and `<%= message.created_at %>` to display its content and the time when it was created.
   The default web templating language in Rails is embedded Ruby, or ERB.

Instructions

1. So far we’ve been loading messages from the database and displaying them in the view.<br>
   How can we create new messages and save them to the database? <br>
   Looking at the [seven standard Rails actions](http://www.codecademy.com/articles/standard-controller-actions), we need to use the `new` and `create` actions. <br>
   Let’s set them up now.

   In the routes file, create another route that maps `messages/new` requests to the Message controller’s new action.

2. Then in the Messages controller below the index action, add the new action:

   ```ruby
   def new
       @message = Message.new
   end
   ```

3. In the routes file, add this route to map requests to the Message controller’s `create` action:

   ```ruby
   post 'messages', to: 'messages#create'
   ```

4. Then in the Messages controller below the `new` action, add a private method named `message_params`. Type:

   ```ruby
   private
    def message_params
        params.require(:message).permit(:content)
    end
   ```

5. Between the `new` action and the private method, add the `create` action. Type:

   ```ruby
   def create
    @message = Message.new(message_params)
    if @message.save
        redirect_to '/messages'
    else
        render 'new'
    end
   end
   ```

6. Next, in **app/views/messages/new.html.erb** under line 11, type in the contents as you see here:

   ```ruby
   <%= form_for(@message) do |f| %>
    <div class="field">
        <%= f.label :message %><br>
        <%= f.text_area :content %>
    </div>
    <div class="actions">
        <%= f.submit "Create" %>
    </div>
   <% end %>
   ```

7. Finally in **app/views/messages/index.html.erb** below the `<% @messages.each do |message| %>...<% end %>` block, add

   ```ruby
   <%= link_to 'New Message', "messages/new" %>
   ```

8. Visit `http://localhost:4001/messages` in the browser. Click on New Message to add a message of your own.

   Once your done, click Run to pass this step.
