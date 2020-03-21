

Sequelize Homework: Reverse Engineering Code

./middleware/isAuthenticated.js
The purpose of the .js file is to provide a module which is being called between API call and the callback function.
-If the user entry is valid, it directs to the next step which is a callback in the function which gives the user access to the homepage. 
-If the user entry is not valid it redirects to the login page. 

./passport.js
This .js file requires an npm passport package which is authentication middleware. And it is using the LocalStrategy of the passport. 
The function takes the email and password as a parameter and firstly searches the email in the MongoDB "Users" collection. 
-If the email does not exist then it returns an "Incorrect email" message.
-If the email exists it checks the password, if the password does not match with the saved db entry then it returns an "Incorrect password" message.
-If the email and the password matches with one of the entries in the DB collection, then it returns the valid user. 

./public/js/index.js
This file has been generated with the sequelize CLI and collects all the models from the models directory and associates them if needed.

./public/js/user.js
The purpose of this .js file is to create a "Users" collection in MongoDB and define email and password in it.
This .js file requires npm package bcryptjs to hash the password so the user password will be encrypted and stored in the database safely.
Also this model contains:
- password encryption which hashes the user entered password before storing into the database.
- password validator which takes the user entered password and compares it with the encrypted password in the database.

./public/js/login.js
This file is to listen to the submit button in the login page, and gets the email and password value from the input boxes then validates those values are not empty.
 Then it calls api post method and passes the user entered email and the password. 
 Then if the user is authenticated and no error was thrown, it directs the user to the homepage. 
 

./public/member.js
This file gets the authenticated user data and displays the user email in the home page.

./public/signup.html
This html file allows the new users to sign up and also there is a link to direct the existing users to the login page. 

login.html
This html file allows the existing users to login and also there is a link to direct the new users to signup page. 

./public/member.html
This html page is a Welcome page which opens after the user logs in. And also there is a logout link for the users to logout.

./public/stylesheets/style.css
This html page is a Welcome page which opens after the user logs in. And also there is a logout link for the users to logout.

routes/api-routes.js
This .js file contains all the following api routes:
- /api/login - this post method uses the passport authentication where we defined in the ./passport.js with the LocalStrategy.  
   If the user entered valid login credentials, it sends the user to the Welcome page. Otherwise the user will be sent an error.
- /api/signup -  This is for signing up the new user. The user's password is automatically hashed and stored securely.
  If the user is created successfully, it directs the user to the login page. 
- /logout - This route is for logging the user out and redirects the user to the signup page. 
- /api/user_data - This route is for getting email and id of a user. 

./routes/html-routes.js
This .js file contains following routes:
- / - this get method directs the user to the members page if the user is logged in. If not it redirects the user to the signup page.
- /login - this get method directs the user to the members page if the user is logged in. If not it redirects the user to the login page.
- /members -  This get method contains the isAuthenticated middleware. if the user is authenticated then it takes the user to the members/Welcome page, otherwise it takes the user to the signup page.  



