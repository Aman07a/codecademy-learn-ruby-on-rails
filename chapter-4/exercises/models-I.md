#### Learn

### ASSOCIATIONS II

## Models I

**6 min**

Looking at the request/response cycle, we need four parts to build the movie app: models, controllers, routes, and views.

Let’s begin by creating the models.

## Instructions

1. Generate a model named `Movie`.

   ```ruby
   rails generate model Movie
   ```

2. Generate another model named `Actor`.

   ```ruby
   rails generate model Actor
   ```

3. Generate a third model named `Part`.

   ```ruby
   rails generate model Part
   ```

4. In **app/models/movie.rb**, inside the Movie class add the following associations:

   ```ruby
   class Movie < ApplicationRecord
    has_many :parts
    has_many :actors, through: :parts
   end
   ```

Press **Run** to test your code!

5. In **app/models/actor.rb**, add the following associations:

   ```ruby
   class Actor < ApplicationRecord
    has_many :parts
    has_many :movies, through: :parts
   end
   ```

   Press **Run** to test your code!

6. In **app/models/part.rb**, add the following associations:

   ```ruby
   class Part < ApplicationRecord
    belongs_to :movie
    belongs_to :actor
   end
   ```

   Press **Run** to test your code then press Next to learn about what we just added!
