# tsPlayground

## Type Script compiler
Used to transforms .ts files into .js files with JavaScript syntax for browsers to understand and execute.

The compiler takes the simple and easy to read code you write in TypeScript and convert it into ES5 compliant JavaScript. Sometimes, like in the case of types, the declaration of the type is totally removed and only the variable is left because types do not exist in JavaScript ES5. This process is called **transcompilation** or **transpilation**, which is the translation of source code in one programming language into source code for another programming language, and is carried out by a compiler.

The TypeScript compiler, named tsc, is written in TypeScript and can be used in any JavaScript host. The current version of the TypeScript compiler is 2.3.

### TypeScript compiler commands
The most important TypeScript compiler command is the compilation command. This is the basic form for this command: ```tsc myscript.ts```

If no errors are found during compilation, The output of this command is a JavaScript file with the same name but with a .js extension (in this case it is going to be myscript.js). If the compiler finds any errors in the code, it will display them in the command window and no .js file will be produced until you fix the errors in the TypeScript file and rerun the tsc command.

The output .js file is the actual JavaScript file that will run in the browser and it is also the file that you will import into your html file in the:
```
<script> tag:

<script src="./myscript.js"></script>
```

#### Compiler Options
The above tsc command is in the most basic form because no compiler options are specified. There are many compiler options that you can use with the tsc command to control the compilation to your preference. For example: ```tsc myscript.ts --noImplicitAny```

The ```--noImplicitAny``` option tells the compiler to check the TypeScript code and raise an error on expressions and declarations with an implied any type. the default value for this option is false, which means it is turned off by default.

Some options require a parameter too like the --target option, it requires you to specify the ECMAScript target version you would like your TypeScript file to be compiled into. For example: ```tsc myscript.ts --target "ES5"```

Two other options that are worth mentioning are the --module and the --outfile options. We will be using those two options later on in this course.

Detailed list on all Compiler Options can be found in the language handbook (http://www.typescriptlang.org/docs/handbook/compiler-options.html)

## Type Script compiler

### The advantages of using types
As the name implies, TypeScript is all about types. This is considered the main advantage in TypeScript. If you are a .Net developer or a developer who writes code in other languages like C#, C++, Java, ..etc, you may know the benefits of types and you may find it uncomfortable to program in a world where types do not exist as in JavaScript.

The main advantage of types is type safety which means the compiler and the development supporting tools can **catch** potential problems in your application during development rather than running into exceptions at the runtime.

TypeScript is a strongly typed superset of JavaScript. It is a compiled rather than an interpreted language; which means errors can be caught and fixed before the code runs. This is a huge advantage not found in JavaScript even to catch type mismatch issues which many times JavaScript fails to catch until the code is executed.

For example:

```
// in JavaScript
function add(x, y){ return x + y; }
```

In the above function declaration, we are not using types for the function parameters, the reader can't tell if this is an arithmetic function that is supposed to add two numbers and return the summation, or if it is a function that adds two words to each other and return a concatenation of two strings. in this case both of the following calls may work in JavaScript:

```
add (1, 4);      		// result: 5 
add("Birth", "day");    // result: 'Birthday' 
add("1", "day");    	// result: '1day'
```

However, think of cases when things go wrong and a string value is passed to the function while the application is supposed to add numbers, although this may work in the application, it may result in different behavior than what the application is supposed to do in the first place and eventually runtime exceptions happen because the rest of the application is assuming numeric values as result. Similarly, calling the function add(1, "day") is also acceptable in JavaScript but will result in unexpected behavior in runtime.

```
// in TypeScript
function add(x: number, y: number) { return x + y; }
```

In the above function declaration, the developer is giving consent that the add function is an arithmetic function that is supposed to take two numbers and return the summation result. in that case passing anything else other than a number value will result in an error. For example calling the function add("sun", "shine") will result in a compilation error and the code cannot be executed until the error is fixed.

```
// in TypeScript
function add(x: string, y: string) { return x + y; }
```

Similarly, in the above function declaration, the developer is giving consent that the add function is a function that operates on text and is supposed to take two words and return a new word that is the combination of the two input words. In that case passing anything else other than a string value will result in an error. For example calling the function add(1, 3) will result in a compilation error and the code can not be executed until the error is fixed.

By using types here you can save a lot of time debugging and trying to trace down and fix a problem when using no types as in JavaScript.

Another advantage when using types is the semantics you give to your code which allows other developers who might be working on your code to understand your intentions and understand how the code is supposed to work.
