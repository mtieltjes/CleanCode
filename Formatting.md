# Formatting

Formatting your code means exactly that, giving your code a structure.
Properly formatted code is easier to read and provides a better way to find grouped concepts.

# Vertical formatting

Vertical formatting means using the vertical space of your code file.
This can be about space between functions, but also grouping similar functions together for readability.

## Blank lines
* Use blank lines to keep code concepts separated (validation vs creation)
* Keep close concepts togheter

❌ Bad example
```kotlin
fun login(email: String, password: String) {
    if (!isEmailValid(email) || !isPasswordValid(password)) throw InputError()
    val user = findUserByEmail(email)
    val passwordIsValid = compareEncryptedPassword(user.password, password)
    if (passwordIsValid) { createSession() } else { throw InvalidCredentialsError() }
}

fun signup(email: String, password: String) {
    if (!isEmailValid(email) || !isPasswordValid(password)) throw InputError()
    val user = User(email, password)
    user.saveToDatabase()
}
```

✅ Good eample
```kotlin
fun login(email: String, password: String) {
    if (!isEmailValid(email) || !isPasswordValid(password)) {
        throw InputError()
    }

    val user = findUserByEmail(email)

    val passwordIsValid = compareEncryptedPassword(user.password, password)

    if (passwordIsValid) {
        createSession()
    } else {
        throw InvalidCredentialsError()
    }
}

fun signup(email: String, password: String) {
    if (!isEmailValid(email) || !isPasswordValid(password)) {
        throw InputError()
    }

    val user = User(email, password)
    user.saveToDatabase()
}
```

## Vertical density/distance

Vertical **density** is all about keeping related code concepts kept **together**.

Vertical **distance** on the other hand means that unrelated concepts should be **separated**

❌ Bad example
```kotlin
fun signup(email: String, password: String) {
    val user = User(email, password)

    if (!isEmailValid(email) || !isPasswordValid(password)) {
        throw InputError()
    }

    user.saveToDatabase()
}
```

Here we have user creation, and input validation mixed up.
Instead, the user creation is related in concept to the user storage, while input validation is a separate concern.
Therefore, we break the input validation of the creation with a blank line, and keep the creation and storing of the user together:

✅ Good eample
```kotlin
fun signup(email: String, password: String) {
    if (!isEmailValid(email) || !isPasswordValid(password)) {
        throw InputError()
    }

    val user = User(email, password)
    user.saveToDatabase()
}
```

The same concept holds for functions and methods:

❌ Bad example
```kotlin
fun validateEmail(email: String) {}

fun login(email: String, password: String) {}

fun validatePassword(password: String) {}
```

✅ Good eample
```kotlin
fun login(email: String, password: String) {}

fun validateEmail(email: String) {}

fun validatePassword(password: String) {}
```

## Ordering functions/methods
* Prefer ordering function in the order they are called

❌ Bad example
```kotlin
fun validateEmail(email: String) {
    if (!email.matches(emailRegex)) {
        throw InputError()
    }
}

fun validate(email: String, password: String) {
    validateEmail(email)
    validatePassword(password)
}

fun login(email: String, password: Password) {
    validate(email, password)
}

fun validatePassword(password) {
    if (!password.matches(passwordRegex)) {
        throw InputError()
    }
}
```

✅ Good eample
```kotlin
fun login(email: String, password: Password) {
    validate(email, password)
}

fun validate(email: String, password: String) {
    validateEmail(email)
    validatePassword(password)
}

fun validateEmail(email: String) {
    if (!email.matches(emailRegex)) {
        throw InputError()
    }
}

fun validatePassword(password) {
    if (!password.matches(passwordRegex)) {
        throw InputError()
    }
}
```

## Code splitting

Sometimes the code gets so large that multiple concepts are getting mixed up in the same file, like multiple class definitions.
If those concepts are not closely related to eachother, it is a good practice to split that code in multiple files and use imports to use that code.
This keeps an individual code file readable, because it represents only one concept.

✅ Good eample
```kotlin
import InputValidator

fun login(email: String, password: String) {
    InputValidator.validate(email, password)
}
```

# Horizontal formatting
Just because code fits into 1 line, doesn't mean it's good code

* Keep lines relatively short
* Use short names

❌ Bad example
```kotlin
val loggedInUserAuthenticatedByEmailAndPassword = if(email != null && password != null) login(email, password) else login(getEmail(), getPassword())
```

✅ Good eample
```kotlin
if (email != null && password != null) {
    email = getEmail()
    password = getPassword()
}
val loggedInUser = login(email, password)
```