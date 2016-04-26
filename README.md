# Javascript conventions

This style guide aims to provide consistent conventions across all Formed products and applications.

## Table of Contents <a name="top"></a>
1. [Spacing](#spacing)
2. [Blocks](#blocks)
3. [Semicolons](#semicolons)
4. [Strings](#strings)
5. [Functions](#functions)
6. [Objects](#objects)
7. [Arrays](#arrays)

## 1. Spacing <a name="whitespace"></a>

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
- **Object declarations** should span multiple lines with one propery per line.
  - Exception: Object does not exceed the maximum line length of 80 characters.
    - Single line object declaration needs to obey `{}` spacing rule.
  ```javascript
  // Bad multi-line declaration example.
  const location = {
    address: 'market street', city: 'philadelphia' };
  
  // Bad single line declaration example.
  const name = {first: 'christopher'};
  
  // Good single line declaration example.
  const name = { first: 'christopher' };
    
  // Good multi-line declaration example.
  const location = {
    address: 'maket street',
    city: 'philadelphia'
  };
  ```
- **Array declarations** should be single line; unless it exceeds the max line length.  Then seperate each item in array on separte line.
  - `[]` Should have no space after opening `[` and no preceding space before `]`.
  - Single line declarations should have one spacing after each item in array except for last item.
  - Multi-line declarations should have closing `]` on its own line.
  - Spacing rules for `,` apply here as well.
  ```javascript
  // Bad examples.
  const numbers = [ 1, 2, 3 ];
  const cities = ['atlanta','boston','los angeles','new york','philadelphia','san francisco'];
  
  // Good examples.
  const numbers = [1, 2, 3];
  const letters = [
    'atlanta',
    'boston',
    'los angeles',
    'new york',
    'philadelphia',
    'san francisco'
  ];
  ```
- **Function calls** should be single line unless it exceeds maximum line length, or it helps in readability.
  - Should be no space immediately after opening `(` or preceding a closing `)`.
  - All arguments should be preceded by a space; unless first argument.
  ```javascript
  // Bad examples.
  fn(arg1,arg2,arg3);
  fn(arg1 ,arg2 ,arg3);
  
  // Good Examples.
  fn(arg1, arg2, arg3);
  
  fn(
    function success() {
      return 'successful';
    },
    function error() {
      return 'error';
    }
  );
  ```
- Leave one line of whitespace at end-of-file.
[back to top](#top)

## 2. Blocks <a name="blocks"></a>

- All multi-line blocks should use braces.
  ```javascript
  // Bad example.
  if (condition)
    return true;
  
  if (condition)
    return true;
  else
    return false;
  
  // Good examples.
  if (condition) {
    return true;
  }

  if (condition) return true;
  ```
- Multi-line blocks with `if` and `else` should have the `else` placed on a new line immmediately after the closing `if` brace.
  ```javascript
  // Bad example.
  if (condition) {
    return true;
  } else {
    return false;
  }
  
  // Good example.
  if (condition) {
    return true;
  }
  else {
   return false;
  }
  ```
[back to top](#top)
  
## 3. Semicolons <a name="semicolons"></a>
  
Always use semicolons.  Don't rely on automatic Semicolon Insertion (ASI).
  
```javascript
// Bad examples.
const name = 'christopher'
  
(function foo() {
  return true
}())
  
// Good examples.
const name = 'christopher';
  
(function foo() {
  return true;
}());
```
[back to top](#top)
  
## 4. Strings <a name="strings"></a>
  
- Use single-quotes for string literals.
- It is okay to use double quotes inside a string literal.
  ```javascript
  // Bad example.
  const str = "lorem ipsum";
    
  // Good example.
  const str = 'lorem ipsum';
  const doubleQuote = 'lorem "ipsum"';
  ```
- Use string concantenation for strings that exceed max line length.
- Always opt-in for template strings over concatentation when inserting dynamic values.
  ```javascript
  // Bad example.
  function sayName(name) {
    return 'Hi my name is ' + name '.';
  }
    
  // Good example.
  function sayName(name) {
    return 'Hi my name is ${name}.';
  }
  ```
- Use of `eval()` on a string is strictly prohibited.
  
[back to top](#top)

## 5. Functions <a name="functions"></a>

- Prefer function declarations over function expresssions.
  - Avoid creating anonymous functions.
  ```javascript
  // Bad example.
  const fn = function () {
  };
  
  const controller = {
    get: function (req, res, next) {
    },
    
    post: function (req, res, next) {
    }
  };
  
  // Good example.
  const controller = {
    get: function get(req, res, next) {
    },
    
    post: function post(req, res, next) {
    }
  };

  function fn() {
  }
  ```
- Wrap immediatly invoked function expression in parentheses.
  ```javascript
  // Bad example.
  (function () {
  })();
  
  // Good example.
  (function() {
  }());
  ```
- Naming a parameter `arguments` is strictly prohibited.
  ```javascript
  // Bad example.
  function bad(arguments) {
  }
  
  // Good example.
  function good(args) {
  }
  ```
- Declaring functions in non-function blocks is prohibited. e.g `if`, `else`, `while`, etc.
- Using the Function constructor to create a new function is prohibited.

[back to top](#top)

## 6. Object <a name="objects"></a>

- Creating objects should be done using the shorthand `{}` syntax.
  ```javascript
  // Bad example.
  const obj = new Object();
  
  // Good example.
  const obj = {};
  ```
- Use object method shorthand (when available).
  ```javascript
  // Bad example.
  const obj = {
    myMethod: function () {}
  };
  
  // Good example.
  const obj = {
    myMethod() {}
  };
  ```
- Use property value shortand (when available).
  ```javascript
  const city = 'philadelphia';
  const state = 'pennsylvania';

  // Bad example.
  const address = {
    city: city,
    state: state
  };
  
  // Good example.
  const address = {
    city,
    state
  };
  ```
- Place shorthand properties at the beginning of object declaration.
  ```javascript
  const city = 'philadelphia';
  const state = 'pennsylvania';
  
  // Bad example.
  const address = {
    street: 'market',
    city,
    state,
    country: 'united states'
  };
  
  // Good example.
  const address = {
   city,
   state,
   street: 'market',
   country: 'united states'
  };
  ```
  
[back to top](#top)

## 7. Arrays <a name="arrays"></a>

- Creating arrays should be done using the shorthand `[]` syntax.
  ```javascript
  // Bad example;
  const arr = new Array();
  
  // Good example.
  const arr = [];
  ```
- Use `Array.push` to add items to an array rather than direct assignment.
  ```javascript
  const arr = [];
  
  // Bad example.
  arr[arr.length] = 'foobar';
  
  // Good example.
  arr.push('foobar');
  ```

[back to top](#top)
