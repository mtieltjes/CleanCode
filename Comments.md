# Comments

Comments are meant to help us understand code that can not be inferred from the code itself.
What it should not do is describe exactly what the code is already telling us.

Lets have a look at bad and good commenting practices

## Bad comments

First, lets discuss bad comments.
These are the comments that you should avoid having in your code.

### Dividers & markers

Code does not need dividers and markers.
If your code is clean, it's already obvious what the different parts of the code are.
Markers will only clutter up the code, making it **harder** to analyze the file.

❌ Bad practice
```kotlin
// !!!!!!!
// CLASSES
// !!!!!!!

class User { ... }

class Product { ... }

// !!!!!!!
// MAIN
// !!!!!!!

val user = User(..)
```

### Redundant information

When your code is clean, a function name already tells you what its purpose is.
By adding comments that repeat this, not only do you have redundancy but also if you refactor a function name the comment can easily get outdated

❌ Bad practice
```kotlin
fun createUser() { // creating a new user
    ...
}
```

These comments can even become confusing if functions either have poor naming, or the comment is wrongly describing it

### Commented out code

Everyone does this from time to time, commenting out code.

**Just delete it**

With proper source control (eg Git) you do not need to keep commented code, you can always bring back the old code if you need it.
Commented code only clutters your code file, and rarely gets cleaned up when it can.

❌ Bad practice
```kotlin
fun createUser() {
    ...
}

// fun createProduct() {
//     ...
// }
```

### Misleading comments

The worst kind of comments are the ones that will throw off the reader.
Instead of helping, the comment will only confuse the reader.
As a result, you will have to analyze the complete function to find out its actual purpose.

❌ Bad practice
```kotlin
fun login() { // create a new user
    ...
}
```

## Good comments

Comments don't improve your code function-wise, but here are a couple of comments that make sense and help understanding code.

### Legal info

Some projects/companies require some legal information attached to the code.
Good practice is to have these as a header of the file, that way it will not get in the way but is immediately visible to readers.

✅ Good eample
```kotlin
/**
 * This file is created under <License>.
 * (c) Company (year)
 */

class User { ... }
```

### Explanations

When you have clean code, having to explain certain lines is rare.
Hoever, in some cases -even with proper naming- makes sense.

Regular expressions are notoriously hard to read. Just by looking at it, you don't always get a clear view of what it does.
In these cases, comments would actually benefit your code readability.

✅ Good eample
```js
// Min. 8 character, at least: one letter, one number, one special character
const passwordRegex = /^(?=.*[A-Za-z])(?=.*\d)(?=.*[@$!%*#?&])[A-Za-z\d@$!%*#?&]{8,}$/
```

### Warnings

In some other rare cases, a warning could make sense.
For example if a unit test may take a long time to complete or if a certain functinoality won't work in certain cases

✅ Good eample
```kotlin
fun fetchTestData() { ... } // requires local dev server
```

### TODO notes

Leaving TODO notes _can_ be useful, if used correctly.
TODO notes are basically note-to-self's, or statements that explain why some code might be missing.

It's always better to implement a feature completely or not at all -or in incremental steps where 'todo' comments can be left out-, but sometimes todos can help you mark work that is still to be done.
Most IDE's can help you find open TODO's.

Some projects or organisations require you to only check in work attached to an issue/ticket.
This usually means that todo's will never be picked up, unless they are attached to such a ticket that is meant to fix this.
To help developers find tickets that will implement a certain todo, or the other way around, find todo's attached to a ticket, some number or link to the ticket should be attached to the TODO.


❌ Bad practice
```kotlin
fun login(email: String, password: String) {
    // todo
}
```

✅ Good eample
```kotlin
fun login(email: String, password: String) {
    // todo: add password validation
    or
    // todo: <link to ticket>
}
```
