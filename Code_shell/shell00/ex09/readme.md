The objective of this exercise is to allow us to use "file" fonction and to know why we use the magic file to figure out some special file type.

Normally, we use file <file name> to figure out the file type
ex: 
file zhaoyan.txt (with the text "hello world" in it)
output will be : hello.txt: ASCII text

Actually, once we enter the file function, it will search the magic file in the /usr/share/misc/magic.mgc, by searching in the magic.mgc file, it will convert the data into the type file in word such as "ASCII text" etc. 

We can also create our own magic file to define a special file type.

Step 1:
We create a file named ft_magic in the directory ex09
After that, we edit this file with the content below:
41 string 42 42 file type

"41" means the place of the 41th byth in this file
"string" means the type of the content
The 1st "42" means that after 41th byth there will be string "42" in this file 
The last text "42 file type" means the name of the file type


To test the result: we can create a file named "myfile" like that:
1234567891234567891234567891234567891234542

we create 41 bypes before enterring 42

then we test the file with magic file in the command line:
file -m ft_magic myfile
The output of the command line is :myfile: 42 file type
Attention: "-m" is mandatory ft_magic is the magic.mgc in this case is the magic file to verify the file type and we finish by the file we want to test at the end

 -m, --magic-file magicfiles
               Specify an alternate list of files and directories containing magic.  This can be a single item, or a  colon-sepa‐
               rated list.  If a compiled magic file is found alongside a file or directory, it will be used instead.
