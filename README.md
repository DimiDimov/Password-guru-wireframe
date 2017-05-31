# Password-guru-wireframe
Password Guru is a library that makes it simple to help your users choose safe passwords. It provides quick feedback that helps them avoid frustration in the process of creating an account while checking their passwords against attacks that real hackers use. 

                                                       QUICK SETUP
Setting up Password Guru on your site it just takes 3 easy steps to access the algorithms then a quick implementation.

                                                            1
Get the source code by either copy and pasting the **FrontEndPassStrengthCheck.js** 
or using git clone then dragging the file into your repository.


                                                            2
In your html include a reference to  FrontEndPassStrengthCheck.js like shown below.                                                 
**<script src="FrontEndPassStrengthCheck.js"></script>**

                                                            3
From your main javascript that handles the create account page just call the method 
guruStrengthTest() and pass in the user's username and password as shown below:                                                         

**passguruReturnArray = guruStrengthTest(username, password);**

You will be returned an array of scores that are determined using our algorithm. 
The strengthResult array that is returned is in the form below.

Indexes 1-5 are boolean, with a value of of true representing a failure in the category.                                                                          
[                                                                                                                                       
0: Overall strength score (explaination below),                                                                      
1: The password length is under 8 characters,                                                                            
2: The password has a password from a common password list,                                                                         
3: The password has a word from a common word list,                                                                         
4: The password contains too many of the same character,                                                         
5: The password is too similar to the username,                                                                            
6: A string recommendation that can be displayed to show to the user of how to make a stronger password. This 
   recommendation is based on the users lowest individual strength score.                                                               
   ]                                                                          

You can then use these values to easily provide feedback to users. 

                                                  EXAMPLE OF IMPLEMENTATION

Lets say that you are using JQuery to extract your HTML inputs to use in your javascript.
You would grab the username and password with lines of code like this:
                                                                                                                                      
**var username = $("#username").val();**                                                                                                 
**var password = $("#password").val();**                                                                                        
From this point you will need to verify the strength of your users password to prevent their information being stolen
You can simply call the Password Guru function check strength                                                                          

**var strengthResult = guruStrengthTest(username, password);**

**more javascript?**                                                 


                                                  DESCRIPTION OF STRENGTH SCORE
How to use the score: if having very secure passwords is important to your site, then the recommended minimum score you should set your application to use is 75. If you want the application to have decently secure passwords but be more user friendly, the recommended minimum score is 50.

Explaination of how score is built: When hackers look to crack password hashes or discover user passwords, they use multiple techniques
such as brute forcing, comparisons to precomputed hashes, and making common substitutions and additions to common terms. The password
strength score looks to tackle this problem by using multiple algorithms that each take into account the different ways that a password
could be discovered. Attack defenses cover things such as rainbow tables, bruteforce techniques, dictionary attacks, shoulder surfing,
and other educated brute force guessing techniques.                                                          


                                               OTHER SECURE PASSWORD STORAGE TIPS
When storing passwords in your database it is important to use a secure hashing algorithm that is salted then hashed.

The way to do this will depend on what backend languages and frameworks you are using, but the simplest way to do this is to use a 
prexisting tool that has already been throughly tested. This can prevent simple mistakes leading to your passwords being vulnerable.

An example of a tool that would do this if your backend is node.js is provided here:

https://www.npmjs.com/package/password-hash-and-salt
