## Indexed Array
Standard array, 0-indexed
### Declaration
Option 1:
`arr=(a b c d e f)`
Option 2:
`declare -a name`
### Assignment
`arr[index]=value`
## Associative Array
Like a dictionary, indices are arbitrary strings
### Declaration
`declare -A name`
You can also declare initial values like this:
`declare -A name=([key1]=value1 [key2]=value2)`
or
`declare -A name=(k1 v1 k2 v2 k3 v3)`
You can use quotes if names include spaces
### Assignment
`name[index]=value`
index can be arbitrary string