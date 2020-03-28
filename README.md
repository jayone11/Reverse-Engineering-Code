# Unit 14 Sequelize Homework: Reverse Engineering Code

# Server.js file 
- Require necessary npm packages
- Require passport configuration
- Set up port and require models for syncing
- Create and Express app and configuring middleware needed for authentication
- Use sessions to keep track of our user’s login status
- Require routes
- Sync the database and log a message to the user upon success

# Config directory
- Contains the middleware directory
- isAuthenticated.js
- This is middleware for restricting routes a user is not allowed to visit if not logged in
- If the user is logged in, continue with the request to the restricted route
- If the user isn't logged in, redirect them to the login page

# Routes directory 
- Contains api-routes.js file
- Requiring our models and passport as we've configured it
- Using the passport.authenticate middleware with our local strategy. If the user has valid login credentials, send them to the members page. Otherwise the user will be sent an error
- Route for signing up a user. The user's password is automatically hashed and stored securely thanks to how we configured our Sequelize User Model. If the user is created successfully, proceed to log the user in, otherwise send back an error
- Route for logging user out
- Route for getting some data about our user to be used client side
- If the user is not logged in, send back an empty object
- Otherwise (Else) send back the user's email and id sending back a password, even a hashed password, isn't a good idea

# Contains html-routes.js file
- Requiring path to so we can use relative routes to our HTML files
- Requiring our custom middleware for checking if a user is logged in
- If the user already has an account send them to the members page
- If the user already has an account send them to the members page
- Here we've add our isAuthenticated middleware to this route. If a user who is not logged in tries to access this route they will be redirected to the signup page

# Public directory
- Contains js directory
# Login.js file
- Getting references to our form and inputs
- When the form is submitted, we validate there's an email and password entered
- If we have an email and password we run the loginUser function and clear the form
- loginUser does a post to our "api/login" route and if successful, redirects us the the members page
- If there's an error, log the error
# Members.js file
- This file just does a GET request to figure out which user is logged in and updates the HTML on the page
# Signup.js file
- Getting references to our form and input
- When the signup button is clicked, we validate the email and password are not blank
- If we have an email and password, run the signUpUser function
- Does a post to the signup route. If successful, we are redirected to the members page
- Otherwise we log any errors
- If there's an error, handle it by throwing up a bootstrap alert

# Contains stylesheets directory
- Style.css for styling
- Contains login.html file
- Contains members.html file
- Contains signup.html file

# Models directory
- Contains index.js file
- Contains user.js file
