#### Learn

### ASSOCIATIONS I

## Update a destination II

**1 min**

Nicely done! You can now update a destination’s name and description. How does it work?

When you visit `http://localhost:4001/destinations/1/edit` to edit a destination, it triggers the first turn of the request/response cycle:

1. The browser makes a HTTP GET request for the URL `/destinations/1/edit`.
2. The Rails router maps this URL to the Destinations controller’s `edit` action. <br>
   The `edit` action finds the destination with id 1, stores it in @destination, <br>
   and passes it on to the view **app/views/destinations/edit.html.erb**.
3. In the view, `form_for` creates a form with the fields of the `@destinations` object.

Then when you fill out the form and submit it, it triggers the second turn of the request/response cycle:

1. The browser sends the data to the Rails app via an HTTP POST request to the URL `/destinations/update`.
2. This time, the Rails router maps this URL to the update action.
3. The update uses the destination_params method to safely collect data from the form. <br>
   It finds the destination in the database, updates its attributes, and redirects to the destination’s `show` page.

## Instructions

Click **Next** to continue.
