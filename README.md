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

## The advantages of using types
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

## How to declare variable in TypeScript

### Variable Declarations in TypeScript
let and const are two relatively new types of variable declarations in JavaScript which TypeScript supports.

using let keyword

**syntax**
```
let variableName: variableType = value;
// or  
let variableName: variableType;
```

**example**
```
let x: number = 5;
// or  
let x: number;
```
**let** is a keyword which tells the compiler here comes a new declaration of a variable. let is similar to var, which has been the keyword to declare variables in JavaScript. However, let was introduced to allow users to avoid some of the common issues that users run into when using var in JavaScript. It is then highly recommended to use let.

**variableName** is any name that you would like to give to your variable. any name can be used as a variable name except the language reserved words like names of types, the word if, while, ...etc. As a best practice, it is recommended to use meaningful names for your variables.

**the colon :** is a separator between the variable name and the variable type. The colon tells the compiler that the following keyword is the type of the variable whose name was just given before the colon.

**variableType** this is the type of the variable. it can be any of the types keywords in TypeScript like number, string, boolean, ...etc. Types will be covered in more details in the upcoming lessons.

**the equal sign =** is the assignment symbol. Use the assignment symbol if you are going to assign a value for the variable at the time of declaration. otherwose, this can be leftout until it is time to assign a value for the variable.

**value** this is the value that you want to assign to the variable. It has to fit in the declared variable type or else the TypeScript compiler will give an error.

**Notice that:**

semicolons **;** are used in TypeScript at the end of a complete code sentence. Semicolons are optional in both JavaScript and TypeScript. However, using semicolon is recommended for many reasons of which code readability is the most important. there are rules regulating when a semicolon is used and when not. Semicolons are not used with loop definitions or if statements definitions for example. As we get more hands on coding in the course you will learn when to use a semicolon and when not and the compiler will be a good guide too.

**using const keyword**
const declarations are another way of declaring variables. They are like let declarations but, as their name implies, their value cannot be changed once they are bound which means you can't reassign them.

**example**
const pi = 3.14;

**Types in TypeScript vs. JavaScript**

***Types in TypeScript vs. JavaScript***
JavaScript uses **dynamic types** while TypeScript uses static types which is also referred to as strongly typed types.

JavaScript uses types like numbers, string, dates, ..etc. However, when you use variables in JavaScript you are not explicit about the type of the variable, in fact you do not explicitly mention the type of the variable using a type keyword. However, the type of the variable is just inferred from the value you assign to the variable. This also means there is no enforcement on the variable to stay in that type or to hold values that are compatible with that type. This is referred to as dynamic types. In JavaScript, the type of the variable is given from the value the variable holds. If the value changes, the type of the variable also changes to fit the new value. It is therefore considered a dynamic type.

TypeScript is different - variables are **explicit** about their types and the value assigned to a variable has to comply with the variable type or an error is given during compilation. Once defined with a type, a variable cannot change its type in TypeScript, it is therefore considered strongly typed. For example:

```
let x: number;  // x is explicitly declared of type number
x = 3;          // correct assignment 
x = "hi";       // incorrect assignment
```

In TypeScript, if a variable is not explicitly assigned a type when it is defined, then the type is inferred from the first assignment or the initialization of the variable and then it is then considered a strongly typed variable with the inferred type. For example:

```
let y = 10;   // y is now a strongly typed as number due to type inference
y = "hello"; // incorrect because y should hold only numbers
```

In TypeScript, this is an error, because the first assignment of the number 3 to x makes TypeScript compiler considered x a strongly typed variable with type number which can not accept a string value as in "hi".

Note that in JavaScript, this is ok because types are dynamic and can change based on the value the variable holds in each assignment.

## Classification of types in TypeScript

### Classification of types in TypeScript
types are classified into two main classes in TypeScript

#### 1. Basic or Primitive Types
  1. boolean
  2. number
  3. string
  4. array
  5. tuple
  6. enum
  7. null
  8. undefined
  9. any
  10. void: exists purely to indicate the absence of a value, such as in a function with no return value.

#### 2. Complex or Non-Primitive Types
  1. class
  2. interface

## Basic types

### Introduction
It is a fundamental part when we program applications to be able to work with some of the simplest units of data like: numbers, strings, boolean values, and the like. TypeScript supports much the same types as you would expect in JavaScript, with a convenient enumeration type thrown in to help things along.

**Here are the basic types in TypeScript**

### Boolean
The most basic datatype is the simple true/false value, which JavaScript and TypeScript call a boolean value.

```let isDone: boolean = false;```

### Number
As in JavaScript, all numbers in TypeScript are floating point values. These floating point numbers get the type number. In addition to hexadecimal and decimal literals, TypeScript also supports binary and octal literals introduced in ECMAScript 2015.

```
let decimal: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
```

### String
Another fundamental part of creating programs in JavaScript for webpages and servers alike is working with textual data. As in many programming languages, we use the type string to refer to these textual datatypes. As in JavaScript, TypeScript uses either double quotes (") or single quotes (') to surround string data.

```
let color: string = "blue";
color = 'red';
```

You can also use template strings, which can span multiple lines and have embedded expressions. These strings are surrounded by the backtick/backquote (`) character, and embedded expressions are of the form ${ expr }.

```
let fullName: string = `Bob Bobbington`;
let age: number = 37;
let sentence: string = `Hello, my name is ${ fullName }. 
    I'll be ${ age + 1 } years old next month.`;
```

This is equivalent to declaring sentence like so:

```
let sentence: string = "Hello, my name is " + fullName + ".\n\n" +
    "I'll be " + (age + 1) + " years old next month.";
```

TypeScript allows you to use an array of string manipulation functions with your string data types like: slicing your string, spliting, searching for certain characters, ...etc.

### Array
TypeScript, like JavaScript, allows you to work with arrays of values. Array types can be written in one of two ways. In the first, you use the type of the elements followed by [] to denote an array of that element type:

```
let list: number[] = [1, 2, 3];
```

The second way uses a generic array type, ```Array<elemType>```:

```
let list: Array<number> = [1, 2, 3];
```

### Tuple
Tuple types allow you to express an array where the type of a fixed number of elements is known, but need not be the same. For example, you may want to represent a value as a pair of a string and a number:

```
// Declare a tuple type
let x: [string, number];
// Initialize it
x = ["hello", 10]; // OK
// Initialize it incorrectly
x = [10, "hello"]; // Error
```

When accessing an element with a known index, the correct type is retrieved:

```
console.log(x[0].substr(1)); // OK
console.log(x[1].substr(1)); // Error, 'number' does not have 'substr'
```

### Enum
A helpful addition to the standard set of datatypes from JavaScript is the enum. As in languages like C#, an enum is a way of giving more friendly names to sets of numeric values.

```
enum Color {Red, Green, Blue}
let c: Color = Color.Green;
```

By default, enums begin numbering their members starting at 0. You can change this by manually setting the value of one of its members. For example, we can start the previous example at 1 instead of 0:

```
enum Color {Red = 1, Green, Blue}
let c: Color = Color.Green;
```

Or, even manually set all the values in the enum:

```
enum Color {Red = 1, Green = 2, Blue = 4}
let c: Color = Color.Green;
```

A handy feature of enums is that you can also go from a numeric value to the name of that value in the enum. For example, if we had the value 2 but weren't sure what that mapped to in the Color enum above, we could look up the corresponding name:

```
enum Color {Red = 1, Green, Blue}
let colorName: string = Color[2];


alert(colorName);
```

### Any
We may need to describe the type of variables that we do not know when we are writing an application. These values may come from dynamic content, e.g. from the user or a 3rd party library. In these cases, we want to skip type-checking and let the values pass through compile-time checks. To do so, we label these with the any type:

```
let notSure: any = 4;
notSure = "maybe a string instead";
notSure = false; // okay, definitely a boolean
```

The ```any``` type is a powerful way to work with existing JavaScript, allowing you to gradually opt-in and opt-out of type-checking during compilation.

The any type is also handy if you know some part of the type, but perhaps not all of it. For example, you may have an array but the array has a mix of different types:

```
let list: any[] = [1, true, "free"];

list[1] = 100;
```

### Void
void is a little like the opposite of any. void means the absence of having any type at all. void type is mainly used as the return type of functions that do not return a value:

```
function warnUser(): void {
    alert("This is my warning message");
}
```

Declaring variables of type void is not useful because you can only assign ```undefined``` or ```null``` to them:

```let unusable: void = undefined;```

### Null and Undefined
In TypeScript, both ```undefined``` and ```null``` actually have their own types named ```undefined``` and ```null``` respectively. Much like ```void```, they're not extremely useful on their own:

```
// Not much else we can assign to these variables!
let u: undefined = undefined;
let n: null = null;
```

By default ```null``` and ```undefined``` are subtypes of all other types. That means you can assign ```null``` and ```undefined``` to something like a ```number```.

## Type any

### Avoid using any
TypeScript adds optional static types to JavaScript. Types are used to place static constraints on program entities such as functions, variables, and properties so that compilers and development tools can offer better verification and assistance during software development. TypeScript’s static compile-time type system closely models the dynamic run-time type system of JavaScript, allowing programmers to accurately express the type relationships that are expected to exist when their programs run and have those assumptions pre-validated by the TypeScript compiler. TypeScript’s type analysis occurs entirely at compile-time and adds no run-time overhead to program execution. Since types are optional in TypeScript, the language allows you to use dynamic types in a sense similar to the JavaScript world. The key word for that is to use *any* as the type of your variable when you declare it. This tells the TypeScript compiler to ignore this variable type and treat it as a dynamic type just like JavaScript. It tells the compiler not to do any checks on the values assigned to that variable and hence you can assign anything to that variable at any time with any type. any is useful in some situations like when there is no defined type for the value you want to assign to your variable as when you are using older JavaScript libraries that have no object model defined for TypeScript yet (more about this is covered in the definitely typed project in module 4). In those situations, any is your saver. However, it is highly recommended to avoid using any as much as possible and only use it in situtations when no other type works.

**example:** avoid using any

```
let x; === let x: any; //back to JavaScript world
x = 3;
x = "hi";
```

## Type Assertions
Sometimes you'll end up in a situation where you'll know more about a value than TypeScript does. Usually this will happen when you know the type of some entity could be more specific than its current type.

**Type assertions** are a way to tell the compiler "trust me, I know what I'm doing." A type assertion is like a type cast in other languages, but performs no special checking or restructuring of data. It has no runtime impact, and is used purely by the compiler. TypeScript assumes that you, the programmer, have performed any special checks that you need.

Type assertions have two forms. One is the "angle-bracket" syntax < >:

```let someValue: any = "this is a string";```

```let strLength: number = (<string>someValue).length;```

And the other is the as-syntax:

```
let someValue: any = "this is a string";

let strLength: number = (someValue as string).length;
```

The two samples are equivalent. Using one over the other is mostly a choice of preference; however, when using TypeScript with JSX, **only** as-style assertions are allowed.

## Interfaces
One of TypeScript's core principles is that type-checking focuses on the **shape** that values have. This is sometimes called **"duck typing"** or **"structural subtyping"**. In TypeScript, interfaces fill the role of naming these types, and are a powerful way of defining **contracts** within your code as well as contracts with code outside of your project.

Note: If you come from another language, such as C# or Java, you may be used to the fact that interfaces are explicitly implemented. Although explicitly implementing an interface is an option in TypeScript (see Class Types ), it is not a requirement. If an instance of an object satisfies the shape of an interface, then the object can be assigned to any variable defined as that interface type. Equally, that object can also be passed as an argument to a function that requires the interface type as a parameter.

### Example Interface
```
function printLabel(labelledObj: { label: string }) {
    console.log(labelledObj.label);
}

let myObj = {size: 10, label: "Size 10 Object"};
printLabel(myObj);
```

The type-checker checks the call to ```printLabel```. The ```printLabel``` function has a single parameter that requires that the object passed in has a property called ```label``` of type string. Notice that our object actually has more properties than this, but the compiler only checks that at least the ones required are present and match the types required. There are some cases where TypeScript isn't as lenient, which we'll cover in a bit.










