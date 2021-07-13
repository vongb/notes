# TypeScript & JavaScript

## Try not to `export default`
Try not to do this because exporting a default module for a file allows it to potentially be renamed accidentally when being imported.
``` typescript
// FileA.ts
const subtract = (a: number, b: number): number => a - b;
export const plus = (a: number, b: number): number => a + b;

export default subtract;
```

``` typescript
// FileB.ts
import plus from './FileA.ts'; // plus here is actually the subtract function from FileA

// ...
```
### Solution: 
Try to `export const` instead, the exported const can still be renamed but it has to be done explicitly like:
``` typescript 
import { subtract as minus } from './FileA.ts';
```

---

## Use ?? over || when handling default values
`??` is a **[Nullish coalescing operator](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Nullish_coalescing_operator)** which returns the right hand side when the left side is `null` or `undefined`.

`||` is a [logical OR](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Logical_OR) operator which returns the right hand side when the left hand side is **any falsy** value. This might lead to unexpected behaviour.

``` typescript
const foo = 0 ?? 42;
console.log(foo);
// output: 0
const baz = 0 || 42;
console.log(baz);
// output: 0
```
---

## Computed Property Names (Square brackets as object's key)
ES2015 syntax. Uses the value of the variable as the key to the object's property.

``` typescript
let param = 'size'
let config = {
  [param]: 12,
  ['mobile' + param.charAt(0).toUpperCase() + param.slice(1)]: 4
}

console.log(config);
// {size: 12, mobileSize: 4}
```

---
## Array destructuring
Like object destructuring but based on order and not keys.

``` typescript
const [second, first, _, ...rest] = [1,2,3,4,5,6];

console.log(second);
// 1
console.log(first);
// 2
console.log(_);
// 3
console.log(rest);
// [4,5,6]
```