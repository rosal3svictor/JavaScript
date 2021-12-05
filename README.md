<div align = "center">
  <h1> JavaScript </h1>
</div>

<div align = "center">
  <img
    src = "./assets/javascript_logo.png"
    width = "40%"
    alt = "nodejs-logo" />
</div>

<hr>

## Table of Contents

- [How to open the inspector tools in Chrome](#how-to-open-the-inspector-tools-in-chrome)
- [Brief introduction to JavaScript](#brief-introduction-to-javascript)
- [Values and Variables](#values-and-variables)
- [Variable Naming Conventions](#variable-naming-conventions)
- [Statements and Expresions](#statements-and-expressions)
- [Data Types](#data-types)
- [Value vs References](#values-vs-references)
- [Type systems](#type-systems)

  1. [Type checking](#type-checking)
  2. [Type requirement](#type-requirement)
  3. [Type conversion](#type-conversion)
  4. [Type equivalence or compatibility](#type-equivalence-or-compatibility)
  5. [TypeScript](#typeScript)

- [== vs ===](#==-vs===)
- [Functions](#functions)

# How to open the inspector tools in Chrome

There are 3 ways to accomplish that:

1. command + option + i (MacOS), control + alt + i (Windows)
2. right click and then select option "inspect"
3. On Chrome: Click on view -> developer -> inspect elements.

# Brief introduction to JavaScript

JavaScript is a high-level, prototype-based object oriented, multi-paradigm, interpreted or just-in-time compiled, dymanically-typed, single-threaded, garbage-collected programming language with first-class functions and a non-blocking event loop concurrency model.

Let's deconstruct this to make a little more sense:

- **Programming Language**: It's a tool that allow us to write code that will instruct a computer to do something.
- **Concurrent**: Means multiple computations are happening at the same time.
- **Asynchronous**: Asynchronous code allows the program to be executed immediately where the synchronous code will block further execution of the remaining code until it finishes the current one.
- **Non-Blocking**: Refers to code that doesn't block the execution of the program. By using an event loop: takes long tasks, executed them in the "background", and puts them back in the main thread once they are finished.
- **Dynamically-Typed**: In JavaScript we don't assign data types to variables, instead they only became known when the JavaScript engine executes our code. Also, the type of variables can easily be changed as we re-assign variables.
- **Single-Threaded**: It has only one call stack that is used to execute the program. In computing, _a thread_, is like a set of instructions that is executed in the computer's CPU. So, basically the thread is where our code is actually executed in a machine's processor.
- **Multi-Paradigm**: Meaning that it's so flexible and versatile that we can use all kind of different programming styles such as imperative and declarative programming, and these different styles are different ways to structure our code basically.
- **First-class Functions**: In a language with first-class functions, functions are simply **treated as variables**. We can pass them into other functions, and return them from functions.
- **Object-Oriented**: About the this nature, it is a prototype-based object-oriented approach. What does that mean?

  1. Almost everything in JavaScript is an object except for primitive values: Have you ever wondered why we can create an array and then use the _push_ method on it for example? Well, it's because of the _prototypo inherintance_. Baically we create arrays from an array blueprint, which is like a template, and this is called the _prototype_; This prototype contains all the array methods, and the arrays we create in our code then inherit the methods from the blueprint so that we can use them on the arrays.

- **Multi-paradigm**: A _paradigm_ is an approach and mindset of structuring code, which will direct your coding style and technique. Three popular paradigm are:

  1. Procedural Programming
  2. Object Oriented Programming (OOP)
  3. Functional Programming (FP)s

  They can be clasified between _imperative_ and _declarative_.

- **Interpreted or _just-in-time_ compiled**: The computer processor only understands _0_ and _1_, which is also called _machine code_ and since it's not practical to write, we simply write human-readable JavaScript code which is an abstraction over machine code. But this code, eventually needs to be converted into machine code, and that step can be either compiling or interpreting. This step is neccesary in every programming language, which in JavaScript, it happens inside the JavaScript Engine.
- **Garbage-collected**: It's basically an algorythim inside the JavaScript engine which automatically removes all unused objects from the computer memory.
- **High-Level**: We don't have to worry about complex stuff such as managing the computer's memory while it runs our program. In JavaScript there are many of these so called _abstractions_ that we don't want to worry about. Those things make the language easier to write and learn.

# Values and Variables

- **Value**: It's basically a piece of data so, it's the most fundamental unit of information that we have in programming.
- **Variable**: Imagine a box, within it you can hold some object, for example a book, and we can then write a label on the box to describe what's in it. Later on, when needed, we can find that object by using the label.

# Variable Naming Conventions

1. They must be written using camelCase notation.
2. You cannot use keywords from the language such as `new` or `function`.
3. You are only able to use `$`, `_` , `numbers` and `letters` to declare them. (They cannot start with a number).
4. Do not start a variable with an uppercase letter. That's not illegal, it's just that this kind of variable names for a specific use case which is Object Oriented Programming.
5. Declare only constants using all uppercase letters (it's a convention)
6. Always make **descriptive** the name for variables so, it provides a notion of what it holds.

# Statements and Expressions

All programming languages have _**language syntax**_. It is a set of rules that define how we can combine different symbols to _**produce valid instructions**_ in order _**to create a program**_ that the _**computer understands**_. A computer can't understand a program if it doesn't comply with the language syntax we are using.

In JavaScript we have two syntactic structures to create programs:

An _**expression**_ is a unit of code that produces a value when evaluated, for example: we can compare them with the "words" in the Spanish language.

Let's suppose we have to assign a value to a variable, how do you think we can complete that line of code? Let's start with the most basics:

1. **Primary Expressions**:
   Any small word that produces a value by itself. Yes, any primitive value is a good example.

```JavaScript
                                  'texto'
                                  true
                                  false
                                  null
                                  undefined
                                  Symbol('foo')
                                  90099839723042342234n

```

we can also use certain _reserved words_ of the language like _this_, or the name of other variable. All of them are _**primary expressions**_ since with a single word we are producinga single value.

Another expressions we can use are: _**Objects and arrays**_. On each position of the array we have to define a _**value**_, or something that _**produces a value**_, an expression. The same happens with the object: keys are generally string that do not need _quotes ('', "")_ if the dont have _blank spaces_ in between, and its values are expressions.

2. **Function Expressions**:
   When we write a function in the part of the code where we're expecting a value.

```JavaScript
                      const func = () => console.log('Hello!');
                      numeros.filter(function filtrarPares(number) {
                        return number % 2 === 0;
                      });
```

3. **Objec Properties**:

```JavaScript
                          let unaVariable;
                          const miObjeto = { nombre: 'Sacha' };
                          const miArray = [1, 2 ,3];

                          unaVariable = miObjeto['nombre'];
                          unaVariable = miArray[0];
```

4. **Function Invocation**:
   In JavaScript when we invoke a function we will always have a back a _value_ as a return.

On the other hand, we have _**statements**_. They are **actions** that are executed so the programs carries on the logic we want it to perform.

We can compare it with a normal spoken language: a _statement_ is like a complete sentence and, an _expressions_ are the words that make up that sentence.

```JavaScript
                  if (23 > 10) {
                    const str = '23 is bigger'; //This is an expression
                  }
          //NOTE: This 'statement' does not really produces a value, does it?
```

Now, this difference between expressions and statements is important to know because JavaScript expects statements and expressions in different places. For example, in a template literal we can only insert expressions but not statements

```JavaScript
          console.log(`I'm ${2037 - 1991} years old.`); // This would work
    console.log(`I'm ${if (23 > 10) const str = "23 is bigger"} years old.`);
    // This 👆🏻 won't work. It doesn't even make sense to do something like that.
```

# Data Types

JavaScript has a `dynamic type` which means that variables don't have to manually define the data type of the value they store. Instead, data types are determined **automatically**. The distinction between `value` and `variable` is pretty important, because in JavaScript is the _**value**_ that has a type, not the variable. So, variables simply store values that have a type. We also can assign a new value with a different data type to the same variable previously defined without a problem.

It also has a weak type, which means that we can perform computations among values of different types. Under the hood, JavaScript would make its best effort to concrete the computation you want to perform, making an implicit data type conversion called `Type Coertion` and it has a great impact on how our programs are executed. The data type of a variable is determined when is exceuted the line of code that contains it. It depends on the operation that is being perfomed with it.

```JavaScript
                                      2 + '1' = 21
                                      1 - '2' = -1
```

Due to its particular characteristics, there are two groups of data types:

1. Primitive Types
2. Object Types (Arrays, functions, dates, regular expressions and any literal object)

## Primitive Types

They are basic, immutable values that contain neither methods nor properties.

```JavaScript
          /*If we are in the browser's console*/
          var numero = 2;
          numero.name = "number two";
          numero.name;
          undefined; //the assignment of the new property didn't work

          var text = "Cocina";
          text[0] = "B";
          text //we access the variable
          "Cocina"

          text = "Bocina";
          text //we access the variable
          "Bocina"
```

- String:

1. They allows to represent texts in our programs.
2. They are defined between 2 `doble` or `single` quotes. The important thing here is that we have to use them consistently `'string'` or `"string"` not `'string"`.
3. In ES2015, was introduced another character: the `backtick`. This allows to interpolate a variable or expression within the string:

```JavaScript
              let saludo = `Hola, me llamo ${nombre} ${apellido}.`
```

4. In order to represent them, JavaScript implements an encoding called UTF-16, what allows us to represent characters from many languages, even emojies.
5. There is a string which does not contain length and is called `empty string : ''` and it's mainly used to provide a initial value to a variable.
6. To be able to obtain a string from a varible, it is possible to access the toString() method

```JavaScript
                              "29".toString() = "29"
```

<i>Note: If we use this method we have to make sure that the variable does not contain either `null` or `undefined`. Otherwhise we will get an TypeError: Cannot read property 'toString' of null</i>
or concatenating it with the empty string

```JavaScript
                                  29 + '' = '29'
```

- Number: They are so called floating point numbers, which means that they always have decimals even if we don't see them of define them.

  1. They allow us to represent numbers: positive, negative and decimal.
  2. When it comes to repesent numbers, JavaScript is not accurate

```JavaScript
                           0.1 + 0.2 = 0.30000000000000004
```

or

```JavaScript
        +(0.1 + 0.2).toFixed(40) = 0.3000000000000000444089209850062616169453
```

this behavour also happens in Python, Ruby o Java as well.

This has to do with the way numbers are designed within the programming language, it is used a format called `IEEE 754` and by using it each number takes 64bits (8bites) in memory.

3. The range of numbers we can use on this format goes after

```JavaScript
                          -(2 ** 53) + 1 and (2 ** 53) - 1
```

we can represent numbers beyond those limits, but they are going to be approximations, and if we perform operations with them we will get unexpected results.

```JavaScript
                      numeroMinimo === Number.MIN_SAFE_INTEGER
```

```JavaScript
                          minNumber === Number.MIN_VALUE
```

```JavaScript
                      numeroMaximo === Number.MAX_SAFE_INTEGER
```

```JavaScript
                          maxNumber === Number.MAX_VALUE
```

they limit the range of numbers it which is safe to perform numeric operations, and to verify a number is within the limits we can use

```JavaScript
                        Number.isSafeInteger(19080) === true
```

4. There are two values of type number that goes beyond those numbers

```JavaScript
                  Inifity === number/0 and -Infinity === number/-0
```

any number is not greater of smaller the both of them, they represent approximations.

5. If we make 0/0 we'll get

```JavaScript
                                        NaN
```

it's type number and is what we get when is perfomed an invalid computation.

```JavaScript
                        "hola"/3 === NaN or NaN + 30 === NaN
```

but we have a method to verify it

```JavaScript
                                isNaN(30) ---> false
                                isNaN(NaN) ---> true
```

it's a very special value in JavaScript, it's not equal to anything even itself

```JavaScript
                                NaN === NaN ---> false
```

6. To verify that a number is finite or not we use this method

```JavaScript
                                isFinite(300) === true
                            isFinite(Infinity) === false
```

- Boolean: It's a logical type which can only be _true_ or _false_

  1. Used for taking decisions.
  2. Values evaluated to `false`: `""`, `0`, `null`, `undefined` and `NaN`. Any other value evaluates to `true`. (they're called 'falsy values')

- Null:

  1. It allows to represent the absence of value, it comes handy when whe want to define that a variable is empty or that we do not know its value yet. We can use it to assign a initial value to a variable we know that later on will get a value.
  2. `Null` is a primitive data type even though that the typeof operator returns `object`.

- Undefined:

  1. It means _**unknown data type**_. It's the value that is automatically given to a variable when is declared but not assigned a value. It's a data type different from `null`.
  2. `Undefined` means:

  - A variable was not given a value.
  - It was not received a param.
  - A function call finished without returning a value.

- Symbol: To be reviewed

- BigInt:

  1. It allows us to write integer numbers without limit.
  2. To use is we basically write the number we want to use and add it an `n` at the end. Like follows:

```JavaScript
              let numeroGrande = 8927345254435334599065n
```

we can also use the `Bigint` function to create them based on numbers or strings.

```JavaScript
          let numeroGrande2 = BigInt('8927345254435334599065')
```

How is it that we can do something like this:

```JavaScript
                      let name = "Victor";
                      name.toUppercase()
                      "VICTOR"
```

when we just said that primitive values don't have neither _properties_ or _methods_?

That's because the data types

```JavaScript
                              boolean
                              number
                              string
```

have their equivalents in the object's. For instance:

```JavaScript
                  let name = new String('Victor')
                  name
                  String {"Victor"}

                  let isAGoodDay = new Boolean(true)
                  isAGoodDay
                  Boolean {true}

                  let number = new Number(10)
                  number
                  Number {10}
```

these objects are going to be used by the JavaScript Engine. Each time we want to access to a property or attribute of a primitive value, the JavaScript Engine is going to create one of these objects temporaryly so we can be able to access them. This temporary object as so called _**Object Wrapper**_, that is basically and object that wraps a primitive value when we want to access any property or method of it. This object is goint to be temporary because the engine only uses it for a fraction of time, after being used it is removed from the memory.

# Values vs References

When we declare a variable _fruit_ and assign it the _string_ "banana" we'd be creating a little container in the computer's memory and storing inside of it the value "banana". If next we change the value to the fruit variable, we'd be changing the value that is being stored and the previous value it had would be lost.

<div align="center">
  <img src="./assets/img0.png" alt="image 0" />
</div>

If we create a second variable _fruit2_ and we assign it the variable _fruit_, a copy of the _fruit_ value is created and it's going to be stored as the value for _fruit2_

<div align="center">
  <img src="./assets/img1.png" alt="image 1" />
</div>

<div align="center">
  <img src="./assets/img2.png" alt="image 2" />
</div>

**_NOTE: If a variable contains a primitive value, when it is assigned to another variable, a copy of that value is going to be created fot that other variable, but there's any relationship between them. If you change the value of any, the other one remains with its current value. Variables in JavaScript are independent._**

Now, with objects something different happens. Primitives values are super basic, each one of them is simply the value they represent. Objects are more complex than promitive values, we can stored multiple values in them. To do that, we define its properties and assign a value for each one. And even after created, we can keep adding both properties and values, or delete one if we don't need it anymore.

<div align="center">
  <img src="./assets/img3.png" alt="image 3" />
</div>

In this way, the objects do not occupy a fixed space in the memory of the computer like the primitive values, but their size can change. And the same thing happens with _arrays_, we can either add or remove elements from the array altering the size of memory the occupy.

There's a very important concept to remember ath this, point. **_The HEAP o dynamic memory is the are of the computer's memory designed to stored values._** This espace in memory is ever bigger than the space where primitive values are stored, but it is also slower to be accesed. Why? let's dive into it:

Each time an object is assigned to a variable, JavaScript is going to place that object in any space of memory it finds in the _heap_, and after that it's going to remember the memory address where it was put, and that value is what is stored in to the variable. This is what is known as **_reference_**, the memory position that is used to access to an object.

and what happens when I assign a variable to another variable that is pointing to an object? how is it made?

what's going to happen is that the reference to the object is going to be stored in both variables.

<div align="center">
  <img src="./assets/img4.png" alt="img 4">
</div>

Each one of them is independent, so if we decide to assign a new object to any, its reference is now going to be diferrent in the computer's memory discarding the previous reference but, the other one is going to have its current value.

When there's no reference to an object, the JavaScript engine will know that it can remove that space in memory, leaving it free to be assigned to other objects.

**_NOTE: If we have multiple variables pointing to the same object, and we modify any property from that object using any of them that change is going to be reflected on the object which both of the variables are referencing to._**

<div align="center">
  <img src="./assets/img5.png" alt="img 5">
</div>

When we declare a function, we state the paremeters this is going to receive. So, if we declare a new variable and pass it to the previously defined function what's going to happen is that the value of that variable is going to be copied to the parameter, using the same logic we've already discussed.

<div align="center">
  <img src="./assets/img6.png" alt="img 6">
</div>

How can I pass a copy of the object and not a reference?

It all depends on what the object you are trying to copy is.

But basically, if the object you are trying to copy has only primitive values, you can do it in two ways:

1. _let copyPerson = Object.assign ({}, person);_ What it does is assign to a new empty object all the enumerable properties of the other object with their values. Obviously it creates a new object, a new reference, but its properties are the same.
2. _let anotherPerson = {... person};_ This does basically the same thing. With the spread operator, we are filling a new empty object with all the properties and values ​​of the person object.

This way of copying objects is called shallow copy (shallow copying).

Now what if the person object has more objects inside? As in this case:

```
let person = {name: 'Sacha', pets: ['Haru', 'Yuri'];
```

If we use any of the above methods, what will be copied is the array reference!

```
let personCopy = {... person};
copyPersona.mascotas.push ('Felix');
```

👆 This last line would be modifying the person pet array too!

If we know that the object we want to copy is like this, we are in trouble. Even worse if that object is very large. But do not despair, it has a solution.

One way would be to do:

```
let personCopy = JSON.parse (JSON.stringify (person));
```

In this way, we convert the object to string and then pass it from string to object. Creating a new reference. Just what we wanted.

But if the original object contains functions ... we are in trouble. Functions do not transform well to strings.

We have to do a deep copy in that case.

We can iterate all the properties and copy them recursively. That is, if we see that a property has a value that is an object, an array or a function (something that is not a primitive value) we should copy all those properties and values, checking the same for each of them.

The best solution in these cases would be to use an external library or package, with an already tested and documented solution, which we know works well.

1. One option would be to look for one that works for us in npm: https://www.npmjs.com/search?q=deep%20copy
2. Use lodash's deepClone method: https://lodash.com/docs/#cloneDeep

# Type Systems

Rules that a language imposed in order to classify what value types exists, how we can manipulate them, and what are the valid operations they support to be done between them.

## Type checking

Process of verifying and enforce the existing type restrictions for the language.

<div align="center">
  <img src="./assets/img7.png" alt="img 7">
</div>

This type checking can occur before or during the execution of the program.

1. **Static type checking**: In compiled languages, the compiler takes our code and analyzes it in order to verify the type requirements from the language. It this verification turns out to be successful, the compiler can translate the program to a language that the computer can understand and execute. Otherwise, the executable program cannot be built, never ends up executing. Some of the languages with this type checking are: C#, Go, Java, Scala, Kotlin.

2. **Dynamic type checking**: The type ckecking is done at runtime execution. Interpreted languages like JavaScript, we deliver our code directly to another program that know who to read it and execute it (Any JavaScript Engine). Some of the languages with this type checking are: PHP, Ruby, Python. On this type of checking we cannot know what data type are our variables until the program is run and they start taking values.

## Type Requirement

How demanding is a language to consider that we are making type errors.

## Type Conversion

JavaScript allows making operations among values with different types with no problem, but to make that possible, it will take certain decisions for us:

<div aign="center">
  <img src="./assets/img8.png" alt="image 8"/>
</div>

<div aign="center">
  <img src="./assets/img9.png" alt="image 9"/>
</div>

To avoid this, we can make a explicit type convertion to: string, number, boolean

<div aign="center">
  <img src="./assets/img10.png" alt="image 10"/>
</div>

<div aign="center">
  <img src="./assets/img11.png" alt="image 11"/>
</div>

_**NOTE: We have to use them as functions, not as contructors. If we do so, we're going to be creating objects, not primitive values.**_

There are another ways of making explicit type convertions:

### To a string (if the value is neither null nor undefined):

```
2019 + "" = "2019"
true + "" = "true"
null + "" = "null"
(2019).toString() = "2019"

var valor = true
valor.toString() ---> "true"
```

### To a number:

```
+'1234' = 1234
+'3.14' = 3.14
+true = 1
+false = 0
```

_**NOTE: Either by implicit or explicit conversion, if a value is tried to be converted into a number and that operation cannot be resolved, we will obtain `NaN` as a result.**_

### To a boolean:

<div aign="center">
  <img src="./assets/img12.png" alt="image 12"/>
</div>

There are few exceptions:

<div aign="center">
  <img src="./assets/img13.png" alt="image 13"/>
</div>

## Type Equivalence or Compatibility

How a language determines that a type is **compatible** with another type or **equivalent** to another type.

In Java, for instance, we can create to classes called 'Calculadora 1' y 'Calculadora 2' both of them with a unique method that does the same: it sums two integers. If after that we create a variable with type 'Calculadora 1' called 'calculadora' and we assing it a new instance of 'Calculadora 2', even though the internal structures of both classes are the same, we will have a type error on this language.

That's what is known as \***\*Nominal Type\*\***: Two types are compatible when they have the same name or when one is a subtype of the other (by inheritance).

With the languages having nominal typing programs are often created by writing multiple classes and using many object-oriented programming design patterns. Other languages sharing this typing are: Java, PHP, C#, C++, Swift.

Another type system is **Structural Type**: For two types to be compatible, **it is enough that they share the structure** that interests us.

<div aign="center">
  <img src="./assets/img14.png" alt="image 14"/>
</div>

<div aign="center">
  <img src="./assets/img15.png" alt="image 15"/>
</div>

_**NOTE: Either the Nominal Typing or the Structural Typing are performed statically, that is, before the program is executed.**_

And what about the dynamic typing languages? how they determine that two types are compatible?

These type of languages use somthing called **_Duck Typing_** (o la prueba del pato): it's called like that because it comes from an old saying: If it walks like a duck, swims like a duck, and 'cuack' like a duck, I don't know if it's a duck but I can treat it like one. Taken to programming: **we don't care what type an object has**, as long as it has the attributes and methods we want to access.

Now, as we saw, the dynamic type checking is performed at runtime execution, so:

<div aign="center">
  <img src="./assets/img16.png" alt="image 16"/>
</div>

we're going to have an error type Error while the program is being executed.

<div aign="center">
  <img src="./assets/img17.png" alt="image 17"/>
</div>

## TypeScript

Is a typed superset of JavaScript that compiles to plain JavaScript, built and maintaned by Microsoft. It starts of **the same JavaScript syntax**, but adds **structural type checking** before our program executes.

# == vs ===

JavaScript has two ways of comparing values but, they work differently. Now, when should I use any and why?

### **When to use (strict equality operator) === :**

We check both type and value equality.

<div aign="center">
  <img src="./assets/img18.png" alt="image 18"/>
</div>

<div aign="center">
  <img src="./assets/img19.png" alt="image 19"/>
</div>

NOTE:

1. Strings are case sentitive, be careful with this.
2. Strict equality operator is also known as identity operator: When we use it to compare objects, this operator tell us wheter we are referencing to the same space in memory, or to the same object in memory.

### **When to use (loose equality operator) == :**

<div aign="center">
  <img src="./assets/img20.png" alt="image 20"/>
</div>

why does it happen? when we use this operator JavaScript internally uses what is called _type coercion_. So, results might not meet the expected output.

<div aign="center">
  <img src="./assets/img21.png" alt="image 21"/>
</div>

When it comes to objects or functions, why any of them is working?

<div aign="center">
  <img src="./assets/img22.png" alt="image 22"/>
</div>

the reaons is that that type of resourse is more complex than a primitive value:

<div aign="center">
  <img src="./assets/img23.png" alt="image 23"/>
</div>

<div aign="center">
  <img src="./assets/img24.png" alt="image 24"/>
</div>

<div aign="center">
  <img src="./assets/img25.png" alt="image 25"/>
</div>

<div aign="center">
  <img src="./assets/img26.png" alt="image 26"/>
</div>

<div aign="center">
  <img src="./assets/img27.png" alt="image 27"/>
</div>

<div aign="center">
  <img src="./assets/img28.png" alt="image 28"/>
</div>

The only case for that operation to return TRUE is the both values are the same, which is the reference to a same space in memory:

<div aign="center">
  <img src="./assets/img29.png" alt="image 29"/>
</div>

<div aign="center">
  <img src="./assets/img30.png" alt="image 30"/>
</div>

# Functions

<div align="center">
  <img src="./assets/functions_0.jpeg" alt="image 0" />
  <br/><br/>
  <img src="./assets/functions_1.jpeg" alt="image 1" />
</div>
