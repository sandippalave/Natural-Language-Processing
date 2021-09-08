```python
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
```


```python
import re

string = '''Janice is 22 and Theon is 33
Joey is 21'''
```


```python
ages = re.findall(r'\d{1,3}', string)
ages
```




    ['22', '33', '21']




```python
name = re.findall(r'[A-Z][a-z]*', string)

name
```




    ['Janice', 'Theon', 'Joey']




```python
dicts = {}

x = 0
for d in name:
    dicts[d] = ages[x]
    x+=1
    
print(dicts)
```

    {'Janice': '22', 'Theon': '33', 'Joey': '21'}
    


```python
if re.search('Shivam', 'I am Shivam Thakare'):
    print("'Shivam' is there")
```

    'Shivam' is there
    


```python
str = 'Sat, mat, pat, hat'
with_Sat = re.findall(r'[Shmp]at', str)           # should have character S, h, m or p...
no_Sat = re.findall(r'[shmp]at', str)

print(with_Sat)
print(no_Sat)
```

    ['Sat', 'mat', 'pat', 'hat']
    ['mat', 'pat', 'hat']
    


```python
re.sub('mat','chat',str)
```




    'Sat, chat, pat, hat'




```python
phone = '422-303-6671'

if re.search('\d{3}-\d{3}-\d{4}', phone):          # {3} - exact 3 digits
    print('correct')
else:
    print('wrong')
```

    correct
    


```python
if re.search(r'(\w\s\w)', 'Sandip Palave'):         # {2-20} - within the range of 2 to 20
    print('Sandip Palave')
else:
    print('None')
```

    Sandip Palave
    


```python
# to find or verify the email address..

emailid = 'spalave41@gmail.com'

re.findall(r'\w\S+@\S+', emailid)
```




    ['spalave41@gmail.com']




```python
# for web scrapping...


import urllib
url = 'https://www.msn.com/en-in/news/other/cbse-results-2021-class-10-12-marksheets-to-be-issued-soon-check-cbse-nic-in-to-know-when-to-download/ar-AAOdx7c?ocid=msedgntp'

response = urllib.request.urlopen(url)
html = response.read()                # read the data into text string
htmlstr = html.decode()              # convert the byte string into normal string

pdata = re.findall(r'(\d{4})', htmlstr)

l = []
for i in pdata:
    l.append(i)
print(l)
print('\n Length of l: ', len(l))
```

    ['1999', '2021', '0908', '2389', '4810', '1026', '2021', '0014', '2021', '1604', '0430', '2020', '2020', '0521', '1012', '2021', '2021', '2392', '2021', '5608', '9988', '3276', '7989', '4508', '2021', '0908', '2389', '4810', '0430', '2020', '2020', '0521', '1012', '2020', '1118', '0120', '2021', '0716', '1925', '5110', '2642', '2999', '2021', '2021', '2021', '3450', '9290', '3450', '9290', '1715', '1089', '5110', '2642', '3450', '9290', '1715', '1089', '5110', '2642', '2021', '2392', '2021', '2021', '2392', '2392', '2021', '7417', '2463', '2867', '5127', '5110', '2642', '6376', '6695', '5487', '0162', '2021', '3530', '5110', '2642', '3000', '6376', '6695', '5487', '0162', '2021', '2663', '5967', '2767', '1026', '2767', '1026', '2021', '5110', '2642', '2663', '5967', '3530']
    
     Length of l:  98
    


```python

```
