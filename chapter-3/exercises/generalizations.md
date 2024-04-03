#### Learn

### ASSOCIATIONS I

## Generalizations

**<1 min**

Congratulations! You built an travel app that uses a database to store two kinds of data. <br>
What can we generalize so far?

- We connected a Tag to its Destinations using associations. <br>
  In this case, a tag `has_many` destinations, and a destination `belongs_to` one tag.
- The `has_many` / `belongs_to` pair can be used to model other one-to-many relationships, which occur frequently.
- Rails provides [seven standard controller actions](https://www.codecademy.com/articles/standard-controller-actions)
  can be used to do common things such as display and change data
