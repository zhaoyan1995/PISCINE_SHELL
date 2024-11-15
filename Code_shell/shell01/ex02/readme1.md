find . -type f -name "*.sh" -exec basename {} .sh \;

-exec basename{} .sh \; Users basename to print only the file name without the .sh extention. Here:
{} is a placeholder for each file found by find
.sh is passed to basename to remove the .sh extention
\; ends the -exec command
