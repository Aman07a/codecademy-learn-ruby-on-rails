#### Learn

### ASSOCIATIONS II

## Many to Many

**3 min**

So far we’ve made an app that stores data using two models. <br>
We used the `has_many` / `belongs_to` association to model a one-to-many relationship between the data.

But not all data is one-to-many. <br>
For example, a movie has many actors in the cast, but each actor also has many movies she’s starred in.

To model this data, we need a <i>many-to-many relationship</i>. <br>
Let’s see how to do this by building a Rails app for a movie website.

## Instructions

1. Create a new app named `MovieApp`.

   ```ruby
   rails new MovieApp
   ```

2. In the terminal, use the cd MovieApp command to navigate to the project’s directory.

   ```bash
   cd MovieApp
   ```

3. Install the gems.

   ```ruby
   bundle install
   ```

4. Run the local server and visit `http://localhost:4001`.

   ```ruby
   rails server
   ```

Make sure to wait until the server finishes booting up in the terminal. <br>
Afterwards, refresh the workspace browser window.

You should see the Ruby logo on the page.
