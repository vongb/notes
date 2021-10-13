# [[Bash]] Conditional Statements

## `test` command
Returns **0 if true** (0 exit code is success) and **1 if false**. MAKES COMPLETE SENSE.
```bash
# -gt (Greater than) >
# -lt (Less than) <
test 5 -gt 9
echo $?
> 1
```

## AND/OR
```bash
[ 5 -gt 3 ] || [ 6 -lt 5 ]
echo "Result: $?"
> 0 # True because status codes

[ 5 -gt 3 ] && [ 6 -lt 5 ]
echo "Result: $?"
> 1 # False because status codes are great
```

## `if/else` block
```bash
if [ conditional expression ]; then
	# if code
else
	# else code
fi
```

```bash
# Else ifs
if [ conditional expression ]; then
	# if code
elif [ conditional expression ]; then
	# else if code
else
	# else code
fi
```

```bash
# Nested if/else
if [ conditional expression ]; then
	# if code
else
	# else code
	
	if [ conditional expression 2 ]; then
		# nested if code
	else
		# nested else code
	fi
fi
```

### Comparison operators
Bash uses different comparators for strings and numbers.

**Strings**

Operator 	| Purpose	
--------- 	| --------- 
	=		| Equal
	== 		| Equal
	!= 		| Not Equal
	\<		| is less than in ASCII
	\>		| is greater than in ASCII 	
	-z		| if string is empty or null
	-n		| Equal 					


**Numbers**

Operator	|	Purpose
---------	| ------------
	-eq		|	is equal
	-ne		|	is not equal
	-lt		|	is less than
	-le		|	less than or equal to
	-gt		|	is greater than
	-ge		|	is greater than or equal to


## Using [[Variables]]
```bash
PROCEED=YES

if [ "$PROCEED" = "YES" ]; then
	echo "Doing stuff"
fi
```