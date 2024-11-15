#find -type  f \( -name '#*#' -o -name '*~' \) -print -exec rm -f {} + 

. specifies the current directory (and its subdirectories)
-type f limits the serach to files only (not directories)
-name '#*#' searches for files with  names that begin with #
-name '*~' searches for files with names that end with ~

To search both patterns in one command, use -o (which means "or")

.\(...\) groups the conditions 
Be aware of the space in this syntax, otherwise it will not work!

-print means print all the file found in the command line
-exec means to all the founded files I need to execute the fonction below :
rm -f means we force to clean the file
{}: This is a placeholder for each file name found by find. It’s replaced with each matched file in turn.
+: This ends the -exec command and tells find to pass multiple files at once to rm instead of running rm separately for each file
