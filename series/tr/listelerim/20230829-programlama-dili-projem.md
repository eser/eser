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
- ; for next "line" separator (not for ending, it's almost same with \n)
- _ for discarded values/parameters (undefined)
- "" for quotes
- `` for template strings
- @tag is tagging prefix
- @tag:value is tagging prefix with value
- () -> for lambda
- (i) -> for lambda with a parameter
- (i, j) -> for lambda with multiple parameters
- () {} for multiline scope
- (i) { } for multiline scope with a parameter
- (i, j) { } for multiline scope with multiple parameters
- "a" for literal string
- 5 or 5.5 for literal number
- 0b1010 for binary literal number
- 0o755 for octal literal number
- 0x1F for hexadecimal literal number
- 1_000_000 for number with separators
- (1, 2, 3) for literal array/tuple
- { "a": 1, b: 2, [c]: 3 } for literal object

## Döngüler ve şartlar:

- map loop only iterates iterable things (allows async and generators too)
  - `map [iterable], (i) -> i++` // multiline and returns the last value like 2
  - `map [iterable], (i) -> yield i++` // inline and yields all values like [0, 1, 2]
  - `map [iterable], (i) -> { i++; return i }` // multiline and returns the last value like 2
  - `map [iterable], (i) -> { i++; yield i }` // multiline and yields all values like [0, 1, 2]

- reduce loop iterates iterable things and reduces the result into a single value
  - `reduce 1, [iterable], (i) -> i++` // inline and returns the last reduced value like 5
  - `reduce 1, [iterable], (i) -> yield i++` // inline and yields all values like [1, 3, 5]
  - `reduce 1, [iterable], (i) { return i++ }` // multiline and returns the last reduced value like 5
  - `reduce 1, [iterable], (i) { yield i++ }` // multiline and yields all reduced values like [1, 3, 5]

- while loop only checks conditions
  - `while i < 5, () -> i++` // inline and returns the last value like 5
  - `while i < 5, () -> yield i++` // inline and yields all values like [0, 1, 2, 3, 4]
  - `while i < 5, () { return i++ }` // multiline and returns the last value like 5
  - `while i < 5, () { yield i++ }` // multiline and yields all values like [0, 1, 2, 3, 4]

- if statement only checks conditions
  - `if i < 5, () -> i` // inline and returns i if the condition is true
  - `if i < 5, () -> i; else () -> i + 5` // inline and returns i if the condition is true, otherwise returns i + 5
  - `if i < 5, () { return i }` // multiline and returns i if the condition is true
  - `if i < 5, () { return i }; else { return i + 5 }` // multiline and returns i if the condition is true, otherwise returns i + 5

- match statement
  - match [value], { [a]: 5, [b]: 6, _: 7 } // inline and returns 5 if value == a, 6 if value == b, otherwise 7
  - match { [value == a]: 5, [value == b]: 6, _: 7 } // inline and returns 5 if value == a, 6 if value == b, otherwise 7
  - match [value] ([a] -> { return 5 } [b] -> { return 6 } { return 7 }) // multiline and returns 5 if value == a, 6 if value == b, otherwise 7
  - match [value] ([value == a] -> { return 5 } [value == b] -> { return 6 } { return 7 }) // multiline and returns 5 if value == a, 6 if value == b, otherwise 7

## Tanımlar:

- def i = 5 // immutable variable with literal initialization
- def @mut i = 5 // mutable variable with literal initialization
- def fn = () -> 5 // inline function with no parameters
- def fn = (i) -> i + 5 // inline function with a parameter
- def fn = (i, j) -> i + j // multiline function with multiple parameters
- def fn = () { return 5 } // multiline function with no parameters
- def fn = (i) { return i + 5 } // multiline function with a parameter
- def fn = (i, j) { return i + j } // multiline function with multiple
  parameters

## Örnekler:

### Hello World

```
def main = () {
  print "Hello World"
}
```

JavaScript equivalent:
```js
const main = () => {
  console.log("Hello World");
}
```

### FizzBuzz

```
def main = () {
  map range(0, 100), (i) {
    print if i % 15 == 0, -> "FizzBuzz"
    else if i % 3 == 0, -> "Fizz"
    else if i % 5 == 0, -> "Buzz"
    else i
  }
}
```

JavaScript equivalent:
```js
const main = () => {
  for (let i = 0; i <= 100; i++) {
    let result;

    if (i % 15 === 0) { result = "FizzBuzz"; }
    else if (i % 3 === 0) { result = "Fizz"; }
    else if (i % 5 === 0) { result = "Buzz"; }
    else { result = i; }

    console.log(result);
  }
}
```

### FizzBuzz 2

```
def main = () {
  print (map range(0, 100), (i) {
    return if i % 15 == 0, -> "FizzBuzz"
    else if i % 3 == 0, -> "Fizz"
    else if i % 5 == 0, -> "Buzz"
    else i
  })
}
```

JavaScript equivalent:
```js
const main = () => {
  const result = [];

  for (let i = 0; i <= 100; i++) {
    if (i % 15 === 0) { result.push("FizzBuzz"); }
    else if (i % 3 === 0) { result.push("Fizz"); }
    else if (i % 5 === 0) { result.push("Buzz"); }
    else { result.push(i); }
  }

  console.log(result);
}
```

### Named scopes

```
def main = () {
  def a = true
  def b = true

  def res = if a, @id:parent {
    if b, {
      parent::yield(1)
    }

    yield 2
  }

  print res // prints [1, 2]
}
```

JavaScript equivalent:
```js
const main = () => {
  const a = true;
  const b = true;

  const gen = (function* () {
    if (a) {
      if (b) {
        yield 1;
      }

      yield 2;
    }
  });

  const res = [];
  for (const item of gen()) {
    result.push(item);
  }

  console.log(res);
}
```

### Fibonacci

```
def main = () {
  def fib = () @id:fib {
    def a = 1
    def b = 1

    while a <= 34, {
      fib::yield a
      &a, &b = b, a + b
    }
  }

  map fib, (i) -> print i // prints [1, 1, 2, 3, 5, 8, 13, 21, 34]
}
```

JavaScript equivalent:
```js
const main = () => {
  const fib = function* () {
    let a = 1;
    let b = 1;

    while (a <= 34) {
      yield a;
      [a, b] = [b, a + b];
    }
  }

  for (const i of fib()) {
    console.log(i);
  }
}
```


### Run named scopes without knowing the parent's actual name

```
def fn = @id:upper (a) {
  if a == 0, () -> upper::call(1) + 1

  return 5
}
```

JavaScript equivalent:
```js
const fn = (a) => {
  if (a === 0) { return fn(1) + 1; }

  return 5;
}
```

### Package imports

```
from "npm:os" import os

print os.arch // prints "x64"
```

JavaScript equivalent:
```js
import os from "npm:os";

console.log(os.arch());
```

### Web server

```
from "npm:express@^4.0.0" import express

def app = express

app.get "/health", () -> ""
app.get "/", (req, res) -> `Hello ${req.query.name}`

app.listen 3000
```

JavaScript equivalent:
```js
import express from "npm:express@^4.0.0";

const app = express();

app.get("/health", (req, res) => "");
app.get("/", (req, res) => `Hello ${req.query.name}`);

app.listen(3000);
```

### Types: Interfaces

```
type User = interface {
  lastname: string
  address: {
    city: string
  }
}

def main = {
  def user = @t:User {
    firstname: "John"; lastname: "Doe"
    age: 30
    address: {
      street: "Main Street"
      city: "New York"
    }
  }

  print user.name // prints "John Doe"
}
```

### Types: Records

```
type User = record {
  firstname: string
  lastname: string
  age: number
  address: {
    street: string
    city: string
  }
}

def main = {
  def user = @t:User {
    firstname: "John"; lastname: "Doe"
    age: 30
    address: {
      street: "Main Street"
      city: "New York"
    }
  }

  print user.name // prints "John Doe"
}
```

### Types: Enums

```
type Color = enum {
  Red
  Green
  Blue
}

def color = @t:Color Red
```

### Types: Aliases

```
type Color = enum {
  Red
  Green
  Blue
}

type ColorAlias = Color

def color = @t:ColorAlias Red
```

### Types: Sum types

```
type Color = enum {
  Red
  Green
  Blue
}

type Size = enum {
  Small
  Medium
  Large
}

type ColorOrSize = Color|Size

def color = @t:ColorOrSize Red
```
