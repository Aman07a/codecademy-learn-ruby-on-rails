#### Objective

### LEARN RUBY ON RAILS

## Bass Music

Bass wants a Rails app for their music streaming service. <br>
Albums are displayed on the main page. <br>
Clicking on an album takes users to a page where they can see an album’s track listing.

Here’s what we’ll need to build this app:

- The first piece of data we need to store is an album. <br>
  An album contains a cover, title, and artist. <br>
  This means we’ll need an Album model to store this data.
- The second piece of data we need to store is a track. <br>
  A track contains a song’s name and duration. <br>
  This means we’ll need a Track model to store this data.
- We can connect an album to its tracks using a `has_many` / `belongs_to` association. <br>

To preview your app at any point:

- In the terminal, type `rails server`
- In the browser, visit `http://localhost:4001`

If you get stuck during this project or would like to see an experienced developer work through it, <br>
click “**Get Unstuck**“ to see a **project walkthrough video**.

## Setup

1. Create a new Rails app named `bass-music`.

   ```ruby
   rails new bass-music
   ```

2. After you create the new app, switch to its folder. In the terminal, type:

   ```bash
   cd bass-music
   ```

3. Install the gems in the **Gemfile**.

   ```ruby
   bundle install
   ```

4. In the root directory of the project, we’ve provided the base HTML and CSS, files for this project. <br>
   Look at the bottom of your file navigator to locate them. <br>
   Let’s put their contents in the correct place in your project. <br>

   In your Rails project, create **app/views/albums/index.html.erb** and copy and paste the contents of the root **index-copy.html.erb** into that file. <br>
   Create **app/views/albums/show.html.erb** and copy and paste the contents of the root **show-copy.html.erb** into that file.

   Then, similarly, create **app/assets/stylesheets/albums.css** and copy the contents of the root **albums-copy.css** into it.

## Add models and associations

5. Generate a model named Album.

   ```ruby
   rails generate model Album
   ```

6. Generate a model named Track

   ```ruby
   rails generate model Track
   ```

7. Associate the Album model with the Track model using the `has_many` and `belongs_to` methods.

   ```ruby
   class Album < ApplicationRecord
    has_many :tracks
   end
   ```

   ```ruby
   class Track < ApplicationRecord
    belongs_to :album
   end
   ```

8. Open up the migration file in **db/migrate/** for the `albums` table, and add the following columns:

   - a string column called cover
   - a string column called title
   - a string column called artist

   ```ruby
   class CreateAlbums < ActiveRecord::Migration[7.1]
    def change
        create_table :albums do |t|
        t.string :cover
        t.string :title
        t.string :artist
        t.timestamps
        end
    end
   end
   ```

9. Open the migration file in **db/migrate** for the `tracks` table, and add the following columns:

   - a string column called name
   - a string column called minutes
   - a references column to the Album model

   The references column is needed because the Track model has a `belongs_to` association with the Album model.

   ```ruby
   class CreateTracks < ActiveRecord::Migration[7.1]
    def change
        create_table :tracks do |t|
        t.string :name
        t.string :minutes
        t.references :album, null: false, foreign_key: true
        t.timestamps
        end
    end
   end
   ```

10. Run a migration to update the database with the Album model and Track model.

    ```ruby
    bundle exec rake db:migrate
    ```

11. We’ve prepared a few items to seed the database with albums and tracks in **seeds-copy.rb** at the root of the project. <br>
    Copy copy the content of this file and replace **db/seeds.rb**.

    Then, if you want, you can also add your own data inside **db/seeds.rb**:

    - Create one or two more Album records. <br>
      Feel free to use your favorite albums. <br>
    - Create Track records associated with each album.

12. Run `bundle exec rake db:seed` to seed the database with the data in **db/seeds.rb**.

    ```ruby
    bundle exec rake db:seed
    ```

## Add a controller and routes

13. Generate a controller named Albums.

    ```ruby
    rails generate controller Albums
    ```

14. In the routes file, add the `resource` route for the Albums controller.

    ```ruby
    resources :albums
    ```

15. Run the `rails routes` command in the terminal to view all of the new URLs that the resource route created.

    Take a look at the Rails [seven standard controller actions](https://www.codecademy.com/articles/standard-controller-actions). <br>
    Which actions from the `rails routes` command do we need for displaying a list of all albums and for displaying a specific album?

    We will create those in the next section!

    ```ruby
    rails routes
    ```

## Add controller actions and views

16. We’ve prepared a layout file for the project called **application-copy.html.erb** at the project’s root directory. <br>
    Copy this HTML and replace the contents of **app/views/layouts/application.html.erb**

17. In the Albums controller, make an action named index that retrieves all albums from the database, and saves it into a variable named `@albums`.

18. In the view **app/views/albums/index.html.erb**, loop through each element in `@albums` and display an album’s details.

19. In the routes file, set the `index` action as the root route.
    View the result by running your project.

20. Start a Rails server to preview the app in the browser. <br>
    In the terminal, type: <br>

    ```ruby
    rails server
    ```

    This command starts a Rails server listening on port 4001. <br>
    Then visit `http://localhost:4001` to see your app in the browser.

21. In the Albums controller, make an action named `show`. <br>
    Retrieve a single album, and save it in `@album`. <br>
    Then retrieve all of its tracks, and save them in `@tracks`.

22. Finish the view **app/views/albums/show.html.erb**. <br>
    First display an album’s details again. Then, loop through each track and display its information.

23. Reload the webpage and click on an album cover to see its tracks. <br>
    If you need to restart the Rails server, in the terminal, first press **Ctrl+C** to shut down the server. <br>
    Then type `rails server` to restart it.
