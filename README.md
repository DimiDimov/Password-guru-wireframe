# Password-guru-wireframe
Password Guru is a library that makes it simple to help your users make safe passwords. It provides quick feedback that helps them avoid frustration in the process of creating an account all while checking their passwords against attacks that real hackers use. 

                                               Using Password Guru
Simply download the source code from github, add it into your website file system and begin using the resources. There are 3 steps to using it. 


1.
Once the source code is in the files add in:
<script src="FrontEndPassStrengthCheck.js"></script>
in your html file for the create account page.

2.
From your main javascript that handles the create account page just call the method:
passguruReturnArray = guruStrengthTest(username, password);
and you will returned array will use our algorithms to determine a strength score value, a group of yes or no checks for the password (such as whether they password is long enough), as well as feedback you should give the user if they want to make their password stronger.

3. 
Use the array to provide feedback to users as they type. Use the example below to see how to do this.

EXAMPLE:
Lets say that you are using JQuery to extract your HTML inputs to use in your javascript.
You would grab the username and password with lines of code like this:

  var username = $("#username").val();
  var password = $("#password").val();
 
From this point you will need to verify the strength of your users password to prevent their information being stolen
You can simply call the Password Guru function check strength

  var strengthResult = guruStrengthTest(username, password);
  
The strengthResult array that is returned is in the form 
[
strength score (a score between 0-100 that determines how hard the password is to be cracked, a very secure password would be over 80,
A length boolean that is 1 if the password is over 8 characters and 0 if it is 8 or less,
A boolean that is 1 if and 0 if,
A boolean that is 1 if and 0 if,
A boolean that is 1 if and 0 if,
A boolean that is 1 if and 0 if,
A boolean that is 1 if and 0 if
]

From here you should parse the array and store it into variables like this

passguruReturnArray = guruStrengthTest(user1, pass1);
strengthScore = passguruReturnArray[0];
var lengthBool = passguruReturnArray[1];
var commonPassBool = passguruReturnArray[2];
var commonWordBool = passguruReturnArray[3];
var multipleCommonWordBool = passguruReturnArray[4];


you can then 

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
