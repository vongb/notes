# Pattern Matching in [[Bash]]

## Glob Patterns
```bash
~$ ls

⥤  
king.db         photographs.txt    readme.md         users.db  
king.txt        photos.db          ring.db           users.txt  
photo.db        photos.txt         ring.txt  
photo.txt       ping.db            usernames.db  
photographs.db  ping.txt           usernames.txt
```

```bash
~$ ls *.db

⥤  
king.db         photographs.db     ping.db        usernames.db  
photo.db        photos.db          ring.db        users.db
```

|	Pattern		|	Example		|	Description 	| Matches 	|
| 	---			|   ---			|	--- 			| --- 	  	|
|	xyz			|	`photo.db`	 |   Exact matches 	 | `photo.db` |
|	\* 			|	`*s.db`		 |	Any characters 	| `photos.db`, `users.db`, etc |
|	?			|	`?ping.db`	 |	Any one character| `king.db`	|
|	[...]		|	`[pr]ing.txt` |	Any one character inside the brackets| `ping.db` `ring.db`|
|	[!...]		|				|					|			|
|	[start-end]	|	`[m-z]ing.*` | Any character in the range |`ping.db` `ping.txt` `ring.db` `ring.txt`|
|	[!start-end]|				|					|			|

## Extended Glob Patterns
Can enable *extended globbing* by using the `shopt -s` command.
```bash
shopt extglob
> extglob 	off

shopt -s extglob
shopt extglob
> extglob 	on
```

### What does `extglob` do?
- You can match multiple patterns like:
```bash
ls *.txt *.db

>king.db photographs.db ping.db usernames.db ...more
```

- Find files that are **NOT** certain extensions
```bash
ls !(*.txt|*.db)

> readme.md
```

|	Pattern		|	Example			|	Description 	|
| 	---			|   -------- |	--- 			| 
|	!(patterns)	|	`!(photo).db` 		|	Anything that does not match the pattern inside the parenthesis but has the **.db** extension.| 
|	?(patterns) |	`photo?(photo).db`	|	Matches zero or one occurrences of the patterns. Matches `photo.db`, `photophoto.db` but NOT `photophotophoto.db` |
|	\*(patterns)|	`photo*(s).t*`	 	|	Matches zero or more patterns. `photo.txt` `photossssss.txt`, `photos.ts`, `photoss.tsx`|
|	+(patterns)	|	`photo+(s).txt` 	|	Matches one or more occurrences of the patterns. `photos.txt``photossssss.txt`, `photos.ts`, `photoss.tsx`|
|	@(patterns) |	`photo@(s).db`		|	Matches one occurrence. `photos.db` |
