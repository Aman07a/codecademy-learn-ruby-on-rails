#### Learn

### Getting Started

## Views

Estimated Time: 4 min

Well done! Now when a user visits `http://localhost:4001/welcome`, the route

```ruby
get 'welcome', to: 'pages#home'
```

will tell Rails to send this request to the Pages controller’s `home` action.

#### Instructions

1. Now that we have a controller and a route,
   let’s move on to the third part of the request/response cycle and create a view.

   Open **app/views/pages/home.html.erb**, and paste in the following HTML.
   Fill in your own name then hit the **Run** button.

   ```html
   <div class="main">
     <div class="container">
       <h1>Hello my name is __</h1>
       <p>I make Rails apps.</p>
     </div>
   </div>
   ```

   We’ve provided CSS in the file **app/assets/stylesheets/pages.css.scss**.

2. View your app by visiting `http://localhost:4001/welcome` in the browser.

   Press the **Run** button to test out your web app!
