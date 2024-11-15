This exercise is to display the list of groups for which the login
groups $FT_USER => print the list of groups for the user who logs in. But it was separated by espace not comma
so we need to reedit the text.

so we use "tr" function

tr [string1] [string2] means we find all the elements that correspond string1 and replace all of them by string 2
so the function is tr ' ' ','

and then we don't want to keep the new command line below the output of this bash file so we need to delete the new line

tr -d '\n' means that we delete the line break 换行符


