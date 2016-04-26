# Javascript conventions

This style guide aims to provide consistent conventions across all Formed products and applications.

1. [Whitespace](#whitespace)
2. [Formatting & Syntax](#formatting)

## 1. <a name="whitespace">Whitespace</a>

- Use spaces over tabs and two (2) spaces of indentation.
  ```javascript
  // Bad spacing.
  function foo() {
  ....const name1;
  .const name2;
  }

  // Good spacing.
  function foo() {
  ..const name;
  }
  ```
- Keep line length to a maximum 80 columns. Exceptions:
  - the line contains a comment with a long URL;
  - the line contains a regex literal;
- Strip all end-of-line whitespace.
- `{}` always have one space before the opening and closing brace.
  ```javascript
  // Bad examples.
  function foo(){
    const name;
  }
  
  if (condition){
   foo();
  }
  
  // Good examples.
  function foo() {
    const name;
  }
  
  if (condition) {
    foo();
  }
  ```
- Any `,` and `;` must not have preceding space.
  ```javascript
  // Bad example.
  const numbers = [1 , 2, 3] ;
  
  // Good exmple.
  const nubers = [1, 2, 3];
  ```
- Any `:` after a property name in an object literal must not have a preceding space and a single space after.
  ```javascript
  // Bad example.
  const obj = {
    foo : 'value'
  };
  
  // Good example.
  const obj = {
    foo: 'value'
  };
  ```
- The `?` and `:` in a ternary operator must have space on both sides.
  ```javascript
  // Bad example.
  const ternary = condtion? value1:value2;
  
  // Good example.
  const ternary = condition ? value1 : value2;
  ```
- No extra whitespace in empty constructs, e.g. `{}`, `[]`, `fn()`.
  ```javascript
  // Bad example.
  const arr = [ ];
  const obj = { };
  foo( );
  
  // Good example.
  const arr = [];
  const obj = {};
  foo();
  ```
- Leave one line of whitespace at end-of-file.

## 2. <a name="formatting">Formatting & Syntax</a>

