# Testing React

## What query should I use?
This priority [list](https://testing-library.com/docs/queries/about/#priority) of React Testing Library is very useful.

Summary: Try to use queries which most closely resembles how your user would interact with your page. Try to query by **role/content** than IDs because your user would look for things based on role/content rather the IDs.

Try to avoid `getByTestId` because the user cannot see or hear this. Only use it when you need to test something like dynamic text. Using this makes your tests really prone to breaking when something changes in the code. It depends on a really specific way the DOM is laid out and not necessarily how your user sees it.

---

## Common React Testing Library Mistakes
The following are points I've encountered from this [article from kentcdodds](https://kentcdodds.com/blog/common-mistakes-with-react-testing-library) on React Testing Library.

---

### 👉 Use `screen` instead of destructuring queries from render
``` typescript
// ❌
const {getByRole} = render(<Example />)
const errorMessageNode = getByRole('alert')
// ✅
render(<Example />)
const errorMessageNode = screen.getByRole('alert')
```
>The benefit of using screen is you no longer need to keep the render call destructure up-to-date as you add/remove the queries you need. You only need to type screen. and let your editor's magic autocomplete take care of the rest.

I think what he means by "up-to-date" here is when you need to change your query from `getByRole` to, say, `getByTitle` then you only have to change it at `screen.` than having to change it at two places.

---

### 👉 Use `@testing-library/user-event` over `fireEvent`
User-event more closely resembles how the user interaction will happen. `fireEvent.change` triggers a single change event but `.type` also triggers events like `keyDown`, `keyPress`, and `keyUp` which reflects how a change will happen normally.


``` typescript
// ❌
fireEvent.change(input, {target: {value: 'hello world'}})
// ✅
userEvent.type(input, 'hello world')
```

---

### 👉 ONLY use `queryBy*` when looking for non-existence
>The only reason the query* variant of the queries is exposed is for you to have a function you can call which does not throw an error if no element is found to match the query...

---

