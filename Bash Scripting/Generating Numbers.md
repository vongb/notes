# Generating Numbers in [[Bash]]
## Random numbers with `$RANDOM`
`$RANDOM` will generate a number between `0` to `32767`.

```bash
echo $RANDOM $RANDOM $RANDOM

> 13044 17924 12488
```

## Sequence generation
Can use `{start..stop}` syntax or `seq <start> <step> <stop>` command.
```bash
echo {0..10}
> 0 1 2 3 4 5 6 7 8 9 10

# print from 0 to 10 with custom step 5
echo ${seq 0 5 10} 
> 0 5 10
```
