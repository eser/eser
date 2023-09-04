# Programlama Dili Projem

## Özellikler:

## Güvenlik:

- Bound checking
- No variable shadowing / hoisting
- No implicit type conversion
- No implicit return
- Readonly function args by default
- Non-nullable types by default
- No global variables

## Veri Yapıları:

- Golang-style duck typing
- Immutable data types and structures by default
- Enums
- Tuples (multiple values)
- Sum types
- Result types
- Nullable types
- Reference types (for non-readonly parameters)

## Hızlandırıcılar:

- String interpolation
- Returning multiple values with tuples
- Unicode by default
- Number separators
- Binary, octal, hexadecimal literals
- Bitwise operators
- nameof operator
- Type aliases
- Range slicing (allows negative indexes)

## Stil:

- // for comments
- ; for next line separator (not for ending)
- _ for discarded values/parameters (undefined)
- "" for quotes
- `` for template strings
- :abc tagging scopes
- [abc] for statement/expression scopes
- -> for lambda
- i -> for lambda with a parameter
- i, j -> for lambda with multiple parameters
- {} for multiline scope
- -> {} also for multiline scope
- i -> { } for multiline scope with a parameter
- i, j -> { } for multiline scope with multiple parameters
- "a" for literal string
- 5 or 5.5 for literal number
- 0b1010 for binary literal number
- 0o755 for octal literal number
- 0x1F for hexadecimal literal number
- 1_000_000 for number with separators
- ([1, 2, 3]) for literal array
- (1, 2, 3) for literal tuple
- ({ "a": 1, b: 2, [c]: 3 }) for literal object

## Döngüler ve şartlar:

- map loop only iterates iterators (allows async and generators too) =>
  `map [iterator] i -> i++` // multiline and returns the last value like 2 =>
  `map [iterator] i -> yield i++` // inline and yields all values like [0, 1, 2]
  => `map [iterator] i -> { i++; return i }` // multiline and returns the last
  value like 2 => `map [iterator] i -> { i++; yield i }` // multiline and yields
  all values like [0, 1, 2]

- reduce loop iterates iterators and reduces them to a single value =>
  `reduce 1, [iterator] &i -> i++` // inline and returns the last reduced value
  like 5 => `reduce 1, [iterator] &i -> yield i++` // inline and yields all
  values like [1, 3, 5] => `reduce 1, [iterator] &i -> { i++; return i }` //
  multiline and returns the last reduced value like 5 =>
  `reduce 1, [iterator] &i -> { i++; yield i }` // multiline and yields all
  reduced values like [1, 3, 5]

- while loop only checks conditions => `while [i < 5] -> i++` // inline and
  returns the last value like 5 => `while [i < 5] -> yield i++` // inline and
  yields all values like [0, 1, 2, 3, 4] => `while [i < 5] { i++; return i }` //
  multiline and returns the last value like 5 =>
  `while [i < 5] { i++; yield i }` // multiline and yields all values like [0,
  1, 2, 3, 4]

- if statement only checks conditions => `if [i < 5] -> i` // inline and returns
  i if the condition is true => `if [i < 5] -> i, -> i + 5` // inline and
  returns i if the condition is true, otherwise returns i + 5 =>
  `if [i < 5] { return i }` // multiline and returns i if the condition is true
  => `if [i < 5] { return i } { return i + 5 }` // multiline and returns i if
  the condition is true, otherwise returns i + 5

- match statement => match [value] ([a] -> 5, [b] -> 6, 7) // inline and returns
  5 if value == a, 6 if value == b, otherwise 7 => match ([value == a] -> 5,
  [value == b] -> 6, 7) // inline and returns 5 if value == a, 6 if value == b,
  otherwise 7 => match [value] ([a] -> { return 5 } [b] -> { return 6 } { return
  7 }) // multiline and returns 5 if value == a, 6 if value == b, otherwise 7 =>
  match [value] ([value == a] -> { return 5 } [value == b] -> { return 6 } {
  return 7 }) // multiline and returns 5 if value == a, 6 if value == b,
  otherwise 7

## Tanımlar:

- def i = 5 // immutable variable with literal initialization
- def mut i = 5 // mutable variable with literal initialization
- def fn = -> 5 // inline function with no parameters
- def fn = i -> i + 5 // inline function with a parameter
- def fn = i -> { return i + 5 } // multiline function with a parameter
- def fn = i, j -> i + j // multiline function with multiple parameters
- def fn = { } // multiline function with no parameters
- def fn = i -> { } // multiline function with a parameter
- def fn = i, j -> { } // multiline function with multiple parameters

## Örnekler:

### Hello World

```
def main = {
  print("Hello World")
}
```

### Fibonacci

```
def main = {
  def fib = -> {
    def a = 0
    def b = 1

    while [a < 34] {
      yield a
      &a, &b = b, a + b
    }
  }

  map [fib] i -> print(i++) // prints [0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
}
```

### Named scopes

```
def main = {
  def a = true
  def b = true

  def res = if [a] :parent {
    if [b] {
      parent::yield 1
    }

    yield 2
  }

  print(res) // prints [1, 2]
}
```

### Run named scopes without knowing the parent's actual name

```
def fn = :upper a -> {

  if [a == 0] -> upper::call(1) + 1

  return 5
}
```

### Package imports

```
from "npm:os" import os

print(os.arch()) // prints "x64"
```

### Web server

```
from "npm:express@^4.0.0" import express

def app = express()

app.get("/health", -> "")
app.get("/", req, res -> `Hello ${req.query.name}`)

app.listen(3000)
```

### Types

```
type User = {
  name: string
  age: number
  address: {
    street: string
    city: string
  }
}

def main = {
  def user: User = ({
    "name": "John Doe"
    "age": 30
    "address": ({
      street: "Main Street"
      city: "New York"
    })
  })

  print(user.name) // prints "John Doe"
}
```
