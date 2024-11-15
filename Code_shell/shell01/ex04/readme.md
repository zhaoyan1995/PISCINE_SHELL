groups $FT_USER | tr ' ' ',' | tr -d '\n'

Explanation we print the list of the group in which it contains this user's name this env variable $FT_USER and then we move the empty space by ',' with function tr , after that we remove the line break of the text

In the command line, don't forget to export FT_USER=yan or FT_USER=lilou to change the value of the env variable
