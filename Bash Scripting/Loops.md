# Loops in [[Bash]]
## `for` loop
Required keywords are: `for`, `do`, and `done`.
```bash
for iterator
do
	# do stuff
done
```

### Basic `for:in`
```bash
for WORD in Hello world; do
	echo "Word: $WORD"
done

> Word: Hello
> Word: world
```


### Using variables as input into the loop
Each word will be split up into [[#Arguments|separate arguments]]
```bash
FRUITS="Mango Apple Banana"

for FRUIT in $FRUITS; do
	echo "Fruit: $FRUIT"
done

> Fruit: Mango
> Fruit: Apple
> Fruit: Banana
```

If we want it to be one word:
```bash
for FRUIT in "$FRUITS"; do
	echo "Fruit: $FRUIT"
done

> Fruit: Mango Apple Banana
```

### Passing commands at run time
```bash
# filename: forloop.sh
for FRUIT; do
	echo "Fruit: $FRUIT"
done
# end of file

-------------------------

# runtime:
~$ bash forloop.sh Mango Banana Apple
> Fruit: Mango
> Fruit: Banana
> Fruit: Apple
```

### Using output from comands
Can use both \`\` or $() syntax. See [[#Storing a command's output inside a variable]]
```bash
for FILE in `ls *.json`; do
	echo "File: $FILE"
done

# Directory has: users.json, photos.json, & comments.json
> File: users.json
> File: photos.json
> File: comments.json
```

### Java style for-loops
```bash
for (( i = 0; i < 5; i ++ )); do
	echo "Number: $i"
done

> Number: 0
> Number: 1
> Number: 2
> Number: 3
> Number: 4
```

Using multiple variables:
```bash
# Loop that doubles a variable's value.
for (( n = 0, i = 1; n < 5; n++, i += i )); do
	echo -n "$i, "
done
echo "" # new line since -n tag does not print a new line

> 1, 2, 4, 8, 16
```

### Running the for-loop infinitely breaking with `exit`
```bash
COUNTER=0

for ((;;)); do
	if [ $COUNTER -lt 5 ]; then
		exit
	else
		COUNTER++
		echo "Current number: $COUNTER"
	fi
done
```

## `while` loop
The `while` loop uses the same [[Conditional Statements#Comparison operators]] as [[Conditional Statements#if else block]]
```bash
NUMBER=1

while [ $NUMBER -lt 5 ]; do
	echo "Number: $((NUMBER++))"
done

> Number: 1
> Number: 2
> Number: 3
> Number: 4
```

Can run **infinitely** with `while :` and break with `exit`

## `until` loop
Opposite to `while`
```bash
NUMBER=1

until [ $NUMBER == 4 ]; do
	echo "Number: $((NUMBER++))"
done

> Number: 1
> Number: 2
> Number: 3
```