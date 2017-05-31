# Password-guru-wireframe
Password Guru is a library that makes it simple to help your users make safe passwords. It provides quick feedback that helps them avoid frustration in the process of creating an account all while checking their passwords against attacks that real hackers use. 

                                                       QUICK SETUP
To get Password guru set up to work on your site it just takes 3 easy steps to access the algorithms then a quick implementation.

                                                            1
Get the source code by either copy and pasting the **FrontEndPassStrengthCheck.js** or using git clone then dragging the file into your repository.


                                                            2
In your html include a reference to  FrontEndPassStrengthCheck.js like shown below.                                                 
**<script src="FrontEndPassStrengthCheck.js"></script>**

                                                            3
From your main javascript that handles the create account page just call the method guruStrengthTest and pass in the user's username and password as shown below:                                                                                                   
**passguruReturnArray = guruStrengthTest(username, password);**

you will be returned an array that was determined using our algorithms. 

                                                   EXAMPLE OF IMPLEMENTATION

Lets say that you are using JQuery to extract your HTML inputs to use in your javascript.
You would grab the username and password with lines of code like this:
**
  var username = $("#username").val();                                                                                    
  var password = $("#password").val();
**
From this point you will need to verify the strength of your users password to prevent their information being stolen
You can simply call the Password Guru function check strength                                                                          

**var strengthResult = guruStrengthTest(username, password);**
  
The strengthResult array that is returned is in the form                                                                          
[                                                                                                                                 
strength score (explaination below),                                                                                   
A boolean that is 1 if the password is over 8 characters and 0 if it is 8 or less,                                 
A boolean 1 if the password does not have a password from a common password list,                             
A boolean 1 if the password does not have a word from a common word list,                                                     
A boolean 1 if the password is not made of two or more common words,                                                              
A boolean 1 if the password does not contain more than 3 of the same letter in a row,                                             
A string recommendation that can be displayed to show to the user of how to make a stronger password                                    
]                                                                          

From here you should parse the array and store it into variables like this                                        
**passguruReturnArray = guruStrengthTest(username, password);**                                                                         
**strengthScore = passguruReturnArray[0];**                                                                                     
**var lengthBool = passguruReturnArray[1];**                                                                             
**var commonPassBool = passguruReturnArray[2];**                                                                                
**var commonWordBool = passguruReturnArray[3];**                                                                                   
**var multipleCommonWordBool = passguruReturnArray[4];**                                                         
**var threeLettersInARowBool = passguruReturnArray[5];**                                                             
**var recommendationString = = passguruReturnArray[6];**                                     

you can then use these values to easily provide feedback to users, here is an example of some javascript that does this:


                                                 


                                                  DESCRIPTION OF STRENGTH SCORE
How to use the score: if want users to have very secure passwords set the minimum score required to be 75. If you want the application to have decently secure passwords but be more user friendly then set the minimum score to be 50.

Explaination of how score is built: When hackers look to crack password hashes or discover users passwords they can do it in multiple ways. The password strength score looks to tackle this problem by using multiple algorithms that each take into account the different ways that a password could be discovered. Attack defenses cover things such as rainbow tables, bruteforce techniques, dictionary attacks, shoulder surfing, and other educated brute force guessing techniques.                                                          


                                               OTHER SECURE PASSWORD STORAGE TIPS
When storing passwords in your database it is important to use a secure hashing algorithm that is salted then hashed.

The way to do this will depend on what backend languages and frameworks you are using but the simplest way to do this is to use a prexisting tool that has already been throughly tested. This can prevent simple mistakes leading to your passwords being vulnerable.

An example of a tool that would do this if your backend is node.js is provided here:

https://www.npmjs.com/package/password-hash-and-salt

