#### Learn

### Getting Started

## Routes

**4 min**

Great! We created a new controller named Pages. How did we do this?

1. The `rails generate controller Pages` command generated a new controller named Pages.
   This created a file named **app/controllers/pages_controller.rb**.
2. Inside the new Pages controller, we added a method called `home`.
   Methods in Rails controllers are also referred to as controller actions,
   so here we added the `home` action to the Pages controller.

#### Instructions

Now that we have a controller, let’s move on to the second part of the request/response cycle and create a route.

In the code editor, open **config/routes.rb** and underneath line 1, type:

```ruby
get 'welcome', to: 'pages#home'
```

**routes.rb**

```ruby
Rails.application.routes.draw do
  get 'welcome', to: 'pages#home'

  # Define your application routes per the DSL in https://guides.rubyonrails.org/routing.html

  # Defines the root path route ("/")
  # root "articles#index"

end
```
