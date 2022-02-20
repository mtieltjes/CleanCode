# Naming

What is the purpose of names? Exactly, they should describe the thing a variable, property, class or function does or represents.

Coming up with names is generally easy, but coming up **good** names is what makes it hard.
Through practice and iterations, keeping these guidelines in mind, coming up with names can become farily straightforward.

Some general rules of thumb:
* Be descriptive and specific, this makes it easier to understand the **purpose**
* Avoid generic names. Failing to do so may lead to confusing the purpose with something else
* Be consistent. If you choose a naming style, stick to that naming style for other parts in the same code

## Guidelines

### Variables & properties
* The name should indicate the type of data being stored in it, therefore receive a **noun** as name (user, database, device)
* If you can be more specific, be more specific (prefer `customer` over `user` if the code is doing customer-specific operations)
* Use short phrases with an adjective (isSomething, somethingExists)
* Avoid shorthands/abbreviations, they may not always be clear

❌ Bad examples
```kotlin
val db: Database
val u1: User
val device: Device
val item: Product
val vw: Brand

val loggedIn: Boolean
val processed: Boolean
val name: Boolean
```

✅ Good eamples
```kotlin
val userDatabase: Database
val user: User // or `administrator`, if you can be more specific
val mobileDevice: Device
val volkswagen: Brand

val isLoggedIn: Boolean
val didProcess: Boolean
val hasName: Boolean
```

### Functions & methods
* Called to execute code, such as performing tasks and operations, so a **verb** is typically in place (`login()`)
* For functions that produce values - especially booleans - go for **short phrases with adjectives** (`isValid()`)
* Avoid names that sound like properties (`email()`), instead prefer actions (`getEmail()`).
* **Be more specific** is you can be. `createUser()` is more specific than just `create()`
* Avoid generic names
* Be **consistent**, if you use `fetchUsers()`, also use `fetchProducts()` and not `getProducts()` in that same code

❌ Bad examples
```kotlin
fun valid(): Boolean
fun create(...): User
fun process()
```

✅ Good eamples
```kotlin
fun isValid(): Boolean
fun createUser(...): User
fun processTransaction()
```

### Classes
* Describe the kind of object it will create, even if it's a static class (static classes will still be used as a container for data/funcitonality)
* Good classnames are just like variable/property names, and therefore a **noun**
* Write names fully, avoid shorthands and abbreviations as they may not always be obvious. (use `EuropeanProduct` and `Volkswagen` instead of `EUProduct` and `VW` )

❌ Bad examples
```kotlin
class CreateUser
class Transact
class Db
```

✅ Good eamples
```kotlin
class UserFactory
class Transaction
class Database
```