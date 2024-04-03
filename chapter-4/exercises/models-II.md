#### Learn

### ASSOCIATIONS II

## Models II

**8 min**

What did we just do? Check out the diagram in the browser:

- We created three models - `Movie`, `Actor`, and `Part`.
- In the models, we used the `has_many :through` association to connect the `Movie` model to the `Actor` model through the `Part` model. <br>
  In this way, the `has_many :through` association [sets](https://www.codecademy.com/resources/docs/ruby/sets)
  up a many-to-many relationship between movies and actors.

## Instructions

1. Now that there’s an association between Movie and Actor, let’s continue and add columns to the migration files:

   Open the migration file in **db/migrate/** for the movies table, and add the following columns:

   - a `string` column called `title`
   - a `string` column called `image`
   - a `string` column called `release_year`
   - a `string` column called `plot`

   Then press **Run** to test your code!

   ```ruby
   class CreateMovies < ActiveRecord::Migration[7.1]
    def change
        create_table :movies do |t|
            t.string :title
            t.string :image
            t.string :release_year
            t.string :plot
            t.timestamps
        end
    end
   end
   ```

2. Next in the migration file for the actors table, and add the following columns:

   - a `string` column called `first_name`
   - a `string` column called `last_name`
   - a `string` column called `image`
   - a `string` column called `bio`

   Now press **Run** to test your code!

   ```ruby
   class CreateActors < ActiveRecord::Migration[7.1]
    def change
        create_table :actors do |t|
        t.string :first_name
        t.string :last_name
        t.string :image
        t.string :bio
        t.timestamps
        end
    end
   end
   ```

3. Then in the migration file for the parts table, add the following lines. <br>
   They add foreign keys that point to the movie and actor tables.

   ```ruby
   t.belongs_to :movie, index: true
   t.belongs_to :actor, index: true
   ```

   Press **Run** to test your code!

   ```ruby
   class CreateParts < ActiveRecord::Migration[7.1]
    def change
        create_table :parts do |t|
        t.belongs_to :movie, index: true
        t.belongs_to :actor, index: true
        t.timestamps
        end
    end
   end
   ```

4. Run the migration command to update the database with the three tables.

   ```ruby
   bundle exec rake db:migrate
   ```

5. Open up **db/seeds.rb**. <br>
   We’ve added a few items here to seed the database with movies and actors. <br>
   Run `bundle exec rake db:seed` to seed the database with the data in **db/seeds.rb**.

   ```ruby
   bundle exec rake db:seed
   ```
