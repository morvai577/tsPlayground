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
