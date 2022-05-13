# JSEPA-2: JavaScript coding style and guidelines

## Introduction

This JSEPA aims to provide some general and simple guidelines for anyone. Some more specific recommandations are also yielded here.

## General guidelines

The guidelines provided are here to homogenize the codebase of any application: **every files, every lines, have to look like they were writen by one and only one person, regardless of the number of collaborators.**

### Tabs/space length

According to the knowledge we have at the time writing this text, there is no standard size for indentation. But one agreement emerged from all the sources we read: all the code must have and keep the same tab/space size.

### Expanded syntax

It is better to use an expanded syntax in JavaScript:

=== "✅ Expanded"

    ```js
    function myFunc() {
      console.log("My function here");
      return 3;
    }
    ```

=== "❌ Not expanded"

    ```js
    function myFunc() { console.log("My function here"); return 3; }
    ```

As both syntaxes have the same result, it is preffered to use the expanded one, for readability and understanding the code.

### Comments

A one-line comment in JavaScript is represented by a double slash `//` followed by a single space and the content of the comment.

For a better understanding and reading, a one-line commment must be on one separated line of the code it is commenting:

A multi-line comment is represented by a block containing the content of the comment and surrounded by `/*` (comment opener) and `*/` (comment closer).

For better reading, a multi-line comment must have its comment lines starting with an asterisk (`*`), which must also be aligned with the above (previous) one. The multi-line comment must and with the closing tag (`*/`) in a separated line of the last line of comment, and its asterisk must be aligned with the previous one as well.

=== "✅ //"

    ```js
    // This variabe does x...
    const myVar = 42;

    // My comment
    console.log("Hello");

    // And an other one
    document.location.href = "https://github.com";
    ```

=== "❌ //"

    ```js
    const myVar = 42; // This variabe does x...

    console.log("Hello"); // My comment

    document.location.href = "https://github.com"; // And an other one
    ```

=== "✅ /*"

    ```js
    /* This variable does:
     * x,
     * y,
     * z...
     */
    const myVar = 42;
    ```

=== "❌ /*"

    ```js
    /* This variable does:
      x,
    * y,
     z... */
    const myVar = 42;
    ```

### Coding syntax

Here are some examples of coding style to use for different situations. Those examples are here to improve the consistency fo the coding syntax, help for readability and understanding of the code.

=== "Semicolons"

    By design the code should complies with the [`"use strict";`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Strict_mode) syntax:

    ```js
    // ✅
    const myValue = 9;
    for(let i = 0; i < myValue; i++) {
      let result = myValue + i;
      console.log(result);
    }
    
    // ❌
    const myValue = 9
    for(let i = 0; i < myValue; i++) {
      let result = myValue + i
      console.log(result)
    }
    ```

=== "Control statements"

    The specification for control statements goes like so:

    * No space between the keyword (`if`, `while`...) and the opening parenthesis
    * 1 space between the closing parenthesis and the opening curly bracket

    ```js
    // ✅
    if(condition) {
      code();
    }

    // ❌
    if (condition){
      code();
    }
    ```

=== "Spacing"

    Spacing the code with empty lines is mandatory for good-looking and readable code. Here are some simple rules for spacing:

    * 1 empty line between two methods of a class
    * 2 empty lines around a function
    * 2 empty lines around a class
    * 1 empty line after imports/includes (which should be the first lines of a script)

    ??? info
        The spacing specified here is very inspired by the [PEP-8 convention](https://peps.python.org/pep-0008/) coding style for Python.

    ```js
    // ✅ Good line spacing
    class MyClass {

      constructor() {
        doThings();
      }

      myMethod() {
        doThings();
      }

    }


    function doThings() {
      return 0;
    }

    // ❌ Bad line spacing
    class MyClass {


      constructor() {
        doThings();
      }
      myMethod() {
        doThings();
      }
    }

    function doThings() {
      return 0;
    }
    ```

### Strings

One must prefer to use template litterals instead of string concatenation for code readability:

```js
const value = 42;
const name = "Bob";

// ✅ Template litteral
console.log(`The value is ${value} and the name is ${name}.`);

// ❌ String concatenation
console.log("The value is " + value + " and the name is " + name + ".");
```

## Variables

### Naming

The naming convention in JavaScript for variables is lowerCamelCase, and using a self-explaining name is a must-do (but don't overdo it). Using underscore is also not recommanded:

```js
// ✅ Valid
const myAnimal = "dog";

// ❌ Invalid
const a = "cat";

// ❌ Invalid
const MY_ANIMAL = "bird";

// ❌ Invalid
const theNameOfMyFavouriteAnimalInTheHouseIsTheFollowing = "Oliver";

// ❌ Invalid
const my_animal = "mouse";

// ❌ Invalid
const _myAnimal = "horse";

// ❌ Invalid
const myAnimal__ = "tortoise";
```

It is also preffered to name the variabes according to its purpose:

=== "Booleans"

    Use one of the prefixes `is`, `are` or even `has` to explicit the boolean variable:

    ```js
    let isValid = true;
    let areCarsWorking = false;
    let hasBeenHere = true;
    ```

### Declaring

To declare variables, the intended way is to use either the `const` or `let` keyword. Each one have its own usecase:

* `const`: declaring a constant. It's value is not meant to change. Scope: block.
* `let`: declaring a variable. Scope: block.

```js
// ✅ Valid
const myAnimal = "dog";

// ✅ Valid
let myAnimal = "hamster";

// ❌ Invalid
var myAnimal = "cat";
```

???+ question "Why the `var` keyword is invalid?"
    Well, it is not invalid, but the main purpose of not using it is its scope. `var` is function-scopped, while both `const` and `let` are block-scopped. In addition, `var` is writeable, so there is no warranty for constants defined with `var`, as per definition, are not read-only.

## Functions

## Classes

Unlike variables, classes uses the PascalCase convention:

```js
// ✅ Valid
class MyClass {
  constructor() {
    this.value = 1;
  }
}

// ❌ Invalid
class myClass {
  constructor() {
    this.value = 1;
  }
}
```

## Operations

### Strict comparisons

To compare values of two variables, one must prefer to use strict comparison operations:

```js
const name1 = "John";
const name2 = "James";

// ✅ Valid
if(name1 === name2) {
  return true;
} else if(name1 !== name2) {
  return false;
}

// ❌ Invalid
if(name1 == name2) {
  return true;
} else if(name1 != name2) {
  return false;
}
```

### Boolean tests

For boolean tests, it it preffered to use the shortcodes of expressions instead of explicit testing the values:

```js
// ✅ Valid
if(myVar) {
  doThings();
} else {
  doOtherThing();
}

// ❌ Invalid
if(myVar === true) {
  doThings();
} else {
  doOtherThing();
}
```

### Simplify if possible

For commom operations, it is sometimes possible to simplify the code:

=== "❌ Not optimized"

    ```js
    function myTest(myVar) {
      if(myVar === true) {
        return true;
      } else {
        return false;
      }
    }
    ```

=== "✅ Optimized"

    ```js 
    function myTest(myVar) {
      return myVar; // (1)
    }
    ```
    
    1. At this point, this function is not realistic, but you get the idea for optimization

## Code examples

The following projects are not affiliated with the JSEPA, but are good examples to follow:

* Feel free to push projects here.
