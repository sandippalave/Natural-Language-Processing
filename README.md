A RegEx is a string that cantains the special symbols and characters to extract the information from given data..
Python privides re module to use the regular expressions.
import re

Generally, we write regular expression as raw strings (normal string prefixed by r or R)..r'm\w\w'
if you don't want to write r then you can write it as - 'm\\w\\w'


to substitute -->   re.sub(old_str, new_str, string)
to match -->     re.match(str, string)      it searches for the 'str' in the beginning of the 'string',if found then returns it
                                                 to access use group() method..
to search --> re.search(str, string)         it searches for 'str' in the 'string' from beginning to end and returns first                                                          occurence of matching string.. use group() method
           --> re.findall(regexp, string)     it searches for a 'str' from beggining to end, and returns all the objects in the 
                                               form of list.  
         --> re.split(regexp, string)             it splits the string according to regular expression and resultant pieces are                                                  returned as a list..  
         
         
         
         
Sequence characters in Regular Expression: 
\d    --   Digits(0 to 9)
\D    --   Non-digits
\s    --   white spaces 
\S    --   non-white space character
\w    --   Alphanumeric (A-Z, a-z, 0-9)
\W    --   non-alphanumeric
\b    --   a space around words
\A    --   Matches only at start of the string
\Z    --   Matches only at end of the string



Quantifiers in Regular Expression:
+       --   1 or more repetitions of preceding regexp
*       --   0 or more repetitions
?       --   0 or 1 repetitions
{m}     --   Exactly m occurances
{m,n}   --   From m to n, m defaults to 0, n to infinity




Special Characters in Regular Expression:
\           --  Escape special character nature   (r'\m\w\w'  --> raw string, we can also write it as 'm\\w\\w')
.           --  Matches any character except new line
^           --  Matches beginning of a string
$           --  Matches ending of a string
[  ]        --  Denotes a set of possible characters e.g [A-Z] i.e. from A to Z
[^  ]       --  Matches every characters except the ones inside brackets.
(   )       --  Matches the regular expression inside the paranthesis
R|S         --  Matches either regex R or regex S
