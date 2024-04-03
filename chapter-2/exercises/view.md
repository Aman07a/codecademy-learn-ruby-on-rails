#### Learn

### SAVING DATA

## View

**1 min**

Nice work. We added a controller and a route to the Rails app.

Why does the Messages controller use an action named `index`? Check out the diagram in the browser. <br>
Rails provides seven standard controller actions for doing common operations with data. <br>
Here we want to display a list of all messages, so we used the `index` action.

Putting it all together:

1. When a user visits http://localhost:4001/messages, the routes file maps this request to the Messages controller’s `index` action.
2. The `index` action retrieves all messages from the database and stores them in the variable `@messages`. <br>

The `@messages` variable is passed on to the view. The view should display each message, so let’s set it up next.

#### Instructions

1. Open **app/views/messages/index.html.erb**. Under line 11, type the contents as you see here:

```ruby
<% @messages.each do |message| %>
  <div class="message">
    <p class="content"><%= message.content %></p>
    <p class="time"><%= message.created_at %></p>
  </div>
<% end %>
```

2. Start up the server and visit http://localhost:4001/messages in the browser, then press **Run**.
