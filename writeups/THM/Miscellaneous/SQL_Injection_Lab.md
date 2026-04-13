## Things I did and learned in this lab

## How the SQL Injection Works
1 OR 1=1 - This basically is a true or false statement that will always come back as true. With this, it will grab all the usernames in the system, but will use the first. 
You can use this in a username section to make it so that you are always able to log in

-- - or comments - While this may be a tool to help other coders out, we can use this to our advantage. After putting in "1 OR 1=1" we can put in -- to comment out the rest of the 
SQL is making it so we do not have to guess the password. We put the extra - because of MySQL standards.

## Ways you can break into systems
1. If the username or ID in this lab requires an integer, you can put in 1 OR 1=1-- - so that the username will always come

2. If it is a string, we modify the payload slightly to look more like 1' OR '1'='1'-- -

3. If there is a GET request, we will be able to see it in the URL. typing it 1' OR 1=1-- - will allow us to log in

4. If there are implementations to stop a SQL injection, something we might be able to do is submit a valid request and then intercept it and change it. In the lab, I used Burp Suite to 
Capture the outgoing request and change the username from a normal username to my payload.
