# JSEPA-2: JavaScript coding style and guidelines

## Introduction

This JSEPA aims to provide some general and simple guidelines for anyone. Some more specific recommandations are also yielded here.

## General guidelines

### Expanded syntax

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



## Variables

