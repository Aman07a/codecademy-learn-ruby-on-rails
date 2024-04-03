#### Learn

### ASSOCIATIONS I

## Models II

**9 min**

What did we just do?

We created two models named Tag and Destinations. <br>
Then, in the model [files](https://www.codecademy.com/resources/docs/ruby/files),
we used the methods `has_many` and `belongs_to` to define an association between Tag and Destination.

- `has_many :destinations` denotes that a single Tag can have multiple Destinations.
- `belongs_to :tag` denotes that each Destination belongs to a single Tag.

The `has_many / belongs_to` pair is frequently used to define one-to-many relationships. <br>
A few examples are:

- a Library has many Books; a Book belongs to a Library
- an Album has many Photos; a Photo belongs to an Album
- a Store has many Products; a Product belongs to a Store

## Instructions

1. Now that there’s an association between Tag and Destination, let’s add columns to the migration files.

   In the `<timestamp>\_create_tags` migration file located in **db/migrate/**,<br>
   we have a table definition generated for us. It should look like:

   ```ruby
   create_table :tags do |t|

    t.timestamps
   end
   ```

   Within this file, add two new columns to the table (`t`):

   - a `string` column called `title`
   - a `string` column called `image`

   Use the format of: `<table>.<type> :<name>`

   Then hit **Run** to test your code!

2. Next, in the migration file for the destinations table, add the following columns:

   - a `string` column called `name`
   - a `string` column called `image`
   - a `string` column called `description`
   - a `references` column called `tag`

   Now hit **Run** to test your code!

3. **Run** the migration command to update the database with the new Tag and Destination columns:

   ```ruby
   bundle exec rake db:migrate
   ```

4. Open up **db/seeds.rb**. We’ve added a few items here to seed the database with tags and destinations. <br>
   To populate the database with the data in **db/seeds.rb**, run:

   ```ruby
   bundle exec rake db:seed
   ```
