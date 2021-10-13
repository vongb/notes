# Variables in [[Bash]] 

## Declaring
Bash can only have **string** variables.

```bash
CITY=New_York  
NAME="John Doe"  
AGE=26  
EMAIL='john@doe.com'  
GRADE=8.43  
EMPLOYED=true
```

> If we did `CITY=New_York` then `CITY` will equal `New` and `York` will be treated as a command.

## Printing
The $ prefix tells `echo` to print the *value* instead of the variable name.
```bash
echo $NAME $AGE $EMPLOYED
> John Doe 26 true
```

## `read` - Reading user input
```bash
# The -n flag prevents a new line from being added
# so the user can input on the same line. (Not supported in sh).
echo -n "Enter a name:"

# Creates a variable called NAME
read NAME

# Print out variable that was just created.
echo "Your name is:" $NAME

> Enter a name: <John Doe
> Your name is: John Doe
```

## ` `` ` & `$()` - Storing a command's output inside a variable
```bash
# Both executes the command and returns the value
PWD=$(pwd)
BASH_VERSION=`bash --version`
```
**Note**: Does not run the command when accessing the variable's value later.

## String interpolation
**Double quotes** are used for string interpolation.
```bash
FIRST_NAME='John'
LAST_NAME='Doe'

echo '$FIRST_NAME $LAST_NAME'
> $FIRST_NAME $LAST_NAME

echo "$FIRST_NAME $LAST_NAME"
> John Doe

# Also works
echo "${FIRST_NAME} ${LAST_NAME}"
> John Doe
```

```bash
FIRST_NAME='John'
LAST_NAME='Doe'

# Concatinate
FULL_NAME=$FIRST_NAME$LAST_NAME

echo $FULL_NAME
> JohnDoe
```

Bash also supports +=

```bash
NUMBER=1
NUMBER+=2
NUMBER+=NUMBER

echo $NUMBER
> 1212
```

## Arguments
When passing a string variable as an argument, Bash breaks the string into differnet words.
```bash
NAME="John Doe Jr"

# Custom args function that counts how many arguments were passed in
args $NAME
> 3

args "$NAME"
> 1

```
