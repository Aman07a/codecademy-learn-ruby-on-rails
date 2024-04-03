# Routes Format

### Use the format:

```ruby
get '<URL>', to: '<Controller>#<Action>'
```

### Example for `routes.rb`:

```ruby
Rails.application.routes.draw do
  # Define your application routes per the DSL in https://guides.rubyonrails.org/routing.html

  # Defines the root path route ("/")
  # root "articles#index"

  # Defines the root path route ("/")
  root 'pages#home'

  # Add a new route for the about page
  get "about" => "pages#about"
end
```
