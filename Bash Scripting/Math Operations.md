# [[Bash]] Math Operations
## `let` - Evaluates the expression and declares a variable
`let` evaluates the expression in the string given to it. So you can use regular operations like:
- `+`
- `-`
- `*`
- `/`
- `%`
- `++`
- `--`

```bash
# Important that there is no space between 
# 1+1 or else + will be treated like a command. See [[#Declaring]]
let RESULT=1+1
echo $RESULT
> 2

# BETTER
let RESULT="1 + 1"
> echo $RESULT
> 2

# Best
let "RESULT = 5 * 5" 	# 25
let "RESULT % 5" 		# 0
let "RESULT++"			# 1
let "RESULT += 4"		$ 5
```

## `expr` - Evaluates the expression and prints the result
```bash
expr 1 + 1
> 2

RESULT=$(expr 3 \* 3)
echo $RESULT
> 9
```

## Double parentheses
Syntax: `$((expression))`. Flexible as you can execute the expression without printing or storing by dropping the `$`.
```bash
NUM=5  
(( NUM+=NUM )) 	# 10
(( NUM++ )) 		# 11  
(( NUM = $NUM - 3)) # 8

echo $NUM
> 8
```
