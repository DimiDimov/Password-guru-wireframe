# Password-guru-wireframe
Password Guru is a library that makes it simple to make a secure website. 

                                               CHECKING PASSWORDS
Simply download the source code from github, add it into your website file system and begin using the resources.

All of the resources will be provided using calls to javascript methods.

EXAMPLE:
Lets say that you are using JQuery to extract your HTML inputs to use in your javascript.
You would grab the username and password with lines of code like this:

  var username = $("#username").val();
  
  var password = $("#password").val();
 
From this point you will need to verify the strength of your users password to prevent their information being stolen
You can simply call the Password Guru function check strength

  var strengthResult = PassGuruCheck(username, password);
  
The strengthResult that is returned will be a String that is either pass or the error that describes why the password was not successful. Possible errors include:
"PasswordTooCommon"
"PasswordVariationOfUsername"
and others...


                                                 SECURE PASSWORD STORAGE
When storing passwords in your database you will want to use a secure hashing algorithm that is salted then hashed.
We have implemented this for you, to use it just download the golang code and import it into your project.

To store a new user simply call the golang register method from your javascript like this:

function register(username, password){
    $.post("/register", {username: $("#username").val(), password: $("#password").val()
    });


From this point you will need to store the salted hash and salt into your database.
To do this, go into the register.go where near the top of the code you will see two variables:


var hashedPass string
var salt int

you will want to store both of these in your database. An example of this is shown here:

import (

   // this is Go's built-in sql library
   "database/sql"
)

var (

   // this is the pointer to the database we will be working with
   // this is a "global" variable (sorta kinda, but you can use it as such)
   db *sql.DB
)

func main() {
    // here we want to open a connection to the database using an environemnt variable.
    // This isn't the best technique, but it is the simplest one for heroku
    db, errd = sql.Open("postgres", os.Getenv("DATABASE_URL"))
}


                                                       Another header
more info
more info
more info
more info
more info
more info
more info
more info
more info
