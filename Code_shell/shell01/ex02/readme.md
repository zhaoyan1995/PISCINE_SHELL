find -type f -name "*.sh" | sed 's/\.sh$//' | sed 's/^\.\///'

Step 1 Using find function to find out all the file contain .sh:
find . -type f -name "*.sh"

Step 2 Get rid of ".sh" for the end of each file name found

sed 's/\.sh$//'

s means substitute

s/oldtext/newtext 
the old test here is ".sh" and we want to replace it by ""
\. means that it presnts "." in reality, because "." without \ = . which means that any charactar in the text 
$ means the end of the file name, which means that we only get rid of the .sh at the end of the file name.

// means the new text 

together means that we get rid of .sh for all the file displayed in the command line

the second sed means we need to get rid of ./ at the beginning of each file name

^ means the beginning of the filename

\. = . for the file name

\/ = / for the file name 
