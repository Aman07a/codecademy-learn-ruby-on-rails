## Quiz 4

1. In which file is the has_many association listed for a Movie controller?

   ```ruby
   app/model/movie.rb
   ```

   ```ruby
   app/db/associations.erb
   ```

   ```ruby
   app/controller/application_controller.rb
   ```

   ```ruby
   app/helpers/application_helper.rb
   ```

   Correct:

   ```ruby
   app/model/movie.rb
   ```

2. What is the difference between one-to-many and many-to-many data associations in Rails?

   ```ruby
   There is no difference.
   ```

   ```ruby
   One-to-many describes a data model with two Controllers; many-to-many describes a model with three or more controllers.
   ```

   ```ruby
   Many-to-many allows Controllers to share model variables inside methods (ie @list = Tasks.all); one-to-many does not.
   ```

   ```ruby
   One-to-many only allows one-way has_many associations; many-to-many allows has_many for both data models involved.
   ```

   Correct:

   ```ruby
   One-to-many only allows one-way has_many associations; many-to-many allows has_many for both data models involved.
   ```

3. What is the correct way to say in Ruby that an actor has many parts, and many movies through those parts?

   ```ruby
   class Actor < ApplicationRecord
    ____________________
   end
   ```

   ***

   ```ruby
   has_many :movies
   ```

   ```ruby
   has_many :movies, through: :movies
   ```

   ```ruby
   has_many :movies, through: :parts
   ```

   ```ruby
   belongs_to :movies, through: :parts
   ```

   Correct:

   ```ruby
   has_many :movies, through: :parts
   ```

4. After adding strings to data tables and including foreign keys between models, what console command needs to be run to cement the associations?

   ```ruby
   rails routes
   ```

   ```ruby
   rails generate associates
   ```

   ```ruby
   bundle exec rake db:seed
   ```

   ```ruby
   bundle exec rake db:migrate
   ```

   Correct:

   ```ruby
   bundle exec rake db:migrate
   ```

5. Which of these pairings would require a has-many/has-many association?

   ```ruby
   Car and Wheel
   ```

   ```ruby
   Class and Student
   ```

   ```ruby
   Channel and TV Show
   ```

   ```ruby
   Year and Date
   ```

   Correct:

   ```ruby
   Class and Student
   ```

6. In the Movies controller, what is the best way to show all actors associated with the movie?

   ```ruby
   def show
    ________________
   end
   ```

   ***

   ```ruby
   @movies = @actor.Movies.all
   ```

   ```ruby
   @movies = @actor.movies
   ```

   ```ruby
   @actors = @movie.actors
   ```

   ```ruby
   @movies = Movie.all
   ```

   Correct:

   ```ruby
   @actors = @movie.actors
   ```

7. Which of these pairings would NOT require a has-many/has-many association?

   ```ruby
   Textbook and Author
   ```

   ```ruby
   Article and Source
   ```

   ```ruby
   Store and Product
   ```

   ```ruby
   Book and Page
   ```

   Correct:

   ```ruby
   Book and Page
   ```

8. Which action in Actors controller would automatically generate the helper method actor_path when given the name ‘actor’?

   ```ruby
   def create
   ```

   ```ruby
   def index
   ```

   ```ruby
   def edit
   ```

   ```ruby
   def show
   ```

   Correct:

   ```ruby
   def show
   ```
