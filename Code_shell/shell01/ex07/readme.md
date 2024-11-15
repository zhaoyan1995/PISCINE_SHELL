cat /etc/passwd | sed -r 's/(.*)(:.*){6}/\1/' | sed -n '2~2p' | rev | sort -d -r | sed -n "$FT_LINE1,$FT_LINE2"p | tr '\n' ','|sed 's/,/, /g' |sed -r 's/, $/        ./'


STEP 1: remove the comments followed by the username:
we print the content of /etc/passwd 
we extend a Regex to sort our data, we only want to keep the user name /login name

the structure of each line is like that:

1:2:3:4:5:6:7

1= The username
2= always with x The enrypted password stored in the /etc/shadow file
3= UID The user I is a unique number assigned to each user by the operating system.

4=GID The Group ID refers to the user's primary group. The primary group has the same name as the user. Secondary groups are listed in the /etc/groups file.

5=The home directory (/home/xx) The absolute path to the directory where users are placed when they log in. It contains the user's files and configurations.

The default sehll (bin/bash). The user's default shell that starts when the users logs into the system. 

We only want to obtain the 1 = username

cat /etc/passwd | sed -r 's/(.*)(:.*){6}/\1/' 
So we print it with cat function
then we use send to sort the data with option -r to extend Regex 
the 1 start with .* => we could start with any caracters, and we can not have this part empty, it is the only part that is not empty. 
Then we use () to capture this group 1 as the \1. 
After that we have the rest to clean up :2:3:4:5:6:7
so we use (:.*){6} to repete the expression we don't have to use () to capture this group because this is not the group we want to keep with us.
 
At the end we use \1 to only print the first group, the Username

STEP2 Starting from the 2nd line, we want to keep the every other line, so we use this:

cat /etc/passwd | sed -r 's/(.*)(:.*){6}/\1/' | sed -n '2~2p'|

sed -n means that we only print the line that matches the pattern 
2~2p : the 1st 2 means we start from the 2 line the 2p means that starting from this line we need to skip twice to show the next line. 

STEP3: we reverse the every letter 
we add |rev|

STEP4: we need to sort all the name in reverse alphabetical order 
we add |sort -d -r |
sort -d means that we sort text in alphabetical order if we add -r at the end that means it would be sorted in reverse alphabetical order

STEP5: we need to select from which line to which line we want to display according to then env variable FT_LINE1 and FT_LINE2 
in order to display the line we want, we use this syntat: sed -n x,x+5p  
so that we can see the lien between from xth line to x+5 line

when we need to insert the env variable, we need to editit with caution. 

sed -n "FT_LINE1,FT_LINE2"p 
p means that we print the lines mentionned before, the order is out of the " "
Attention: Don not use '' instead of " ", because if we use ' ' then sed -n will consider FT_LINE1 and FT_LINE2 as a string, which does not make any sens for Linux.



when we need to change the value of the env variables
in the command line we can enter :
export $FT_LINE1=3
export $FT_LINE2=7
so the script takes into accout these two value to execute the script correctly 

STEP6 :  we need to replace the line break by "," for between each username

we add tr '\n' ',' 

STEP7 : we need to add a space after each ",":
sed  's/,/, /g' 
For each "," that we identified we need to substitute it with ", " and the "g" means that we need to apply it for the whole text. 
Here we can't have tr '\n' ', ' because, the tr can only replace a single world at once it will ignore the word after ","



STEP7 : we need to remove the "," at the end of the text and replace it by "      ."
so we need to identify the "," at the end of the text so we use ",$" $ means the end of the sentence after that we replace it by "." when we use sed -r we don't have to add an espace character "\" in front of "." , we only apply it if we use sed without "r" 

So we add :  sed -r 's/, $/     ./'

Be carefule we need to add an space between "," and the end of the sentence $, otherwise the system is not going to recognize the "," at the end of the text and it will not add the "      ." at the end of the text


