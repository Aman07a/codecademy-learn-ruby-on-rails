#### Learn

### ASSOCIATIONS I

## Models I

**5 min**

Great! According to the request/response cycle, we need four parts to build the travel app: `models`, `controllers`, `routes`, and `views`.

Let’s begin by creating the models.

## Instructions

1. Generate a model named `Tag`.

   ```ruby
   rails generate model Tag
   ```

2. Generate another model named `Destination`.

   ```ruby
   rails generate model Destination
   ```

3. In **app/models/tag.rb** create a new `has_many` association, like this:

   ```ruby
   class Tag < ApplicationRecord
    has_many :destinations
   end
   ```

   Press **Run** to test your code!

   You may see a `PendingMigrationError` in the browser. That’s ok! We will fix it in the next exercise.

4. In **app/models/destination.rb**, add a `belongs_to` association:

   ```ruby
   belongs_to :tag
   ```

   Press **Run** to test your code and hit **Next** to learn about what we just added!
