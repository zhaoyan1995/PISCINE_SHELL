Definition of chmod
In Unix and Unix-like operating systems, chmod is the command and system call used to change the access permissions and the special mode flags (the setuid, setgid, and sticky flags) of file system objects (files and directories). Collectively these were originally called its modes,[1] and the name chmod was chosen as an abbreviation of change mode.[2]

Code for chmod to change mod of a file or a directory
7	4(r) + 2(w) + 1(x)	rwx	read, write and execute
6	4(r) + 2(w)     	rw-	read and write
5	4(r)        + 1(x)	r-x	read and execute
4	4(r)            	r--	read only
3	       2(w) + 1(x)	-wx	write and execute
2	       2(w)     	-w-	write only
1	              1(x)	--x	execute only
0	0                	---	none

To create a symLink (rapid acces to go to an another directory) we need to use the command lien below: 
ln -s xxxx(the existing file which we want to create a quick access with) xxxx(the name we give for this symlink) 

here is an example:
original ls -l 
drwx--xr-x 2 yan yan 4096 Nov 10 17:24 test0
-rwx--xr-- 1 yan yan    0 Nov 10 17:26 test1
dr-x---r-- 2 yan yan 4096 Nov 10 17:24 test2
-r-----r-- 1 yan yan    0 Nov 10 17:26 test3
-rw-r----x 1 yan yan    0 Nov 10 17:26 test4
-r-----r-- 1 yan yan    0 Nov 10 17:26 test5

We want to create a symLink (a quick access) for the directory test0 in the current directory.
We use the commande line below: 
ln -s test0 test6  
that means we want to create a quick access for the directory test0 in the current directory and we give a name for this symLink "test6"
ln - make links between files
ln -s make symbolic links instead of hard links


update version for the resultat of ls -l
drwx--xr-x 2 yan yan 4096 Nov 10 17:24 test0
-rwx--xr-- 1 yan yan    0 Nov 10 17:26 test1
dr-x---r-- 2 yan yan 4096 Nov 10 17:24 test2
-r-----r-- 1 yan yan    0 Nov 10 17:26 test3
-rw-r----x 1 yan yan    0 Nov 10 17:26 test4
-r-----r-- 1 yan yan    0 Nov 10 17:26 test5
lrwxrwxrwx 1 yan yan    5 Nov 10 20:22 test6 -> test0

ps:
Systematically, the chmod is always 777 for link test6 in Linux system. it is useless to change the mode of a symLink 

However, if we want to change if we can use the commande line below:
function ls() { /usr/bin/ls "$@" | sed s/lrwxrwxrwx/lrwxr-xr-x/g; }
Warning: it only works if we execute this function and we don't close the current terminal window, the mode for Symlink test06 will go back to 777 if we open another ubuntu terminal window.

tar - an archiving utility
tar -cf exo2.tar *  
this function above is to create a file tar that includes all the file and directories in the directory ex02, * means every element in the current directory.
