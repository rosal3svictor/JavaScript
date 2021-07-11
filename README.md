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

- [Variable Naming Conventions](#variable-naming-conventions)
- [Data Types](#data-types)
- [Value vs References](#values-vs-references)
- [Type systems](#type-systems)

  1. [Type checking](#type-checking)
  2. [Type requirement](#type-requirement) 
  3. [Type conversion](#type-conversion)
  4. [Type equivalence or compatibility](#type-equivalence-or-compatibility)
  5. [TypeScript](#typeScript)

- [== vs ===](#==-vs===)

# Variable Naming Conventions
1. They must be written using camelCase style.
2. You cannot use keywords from the language such as `new` or `function`.
3. You are only able to use `$`, `_` , `numbers` and `letters` to declare them. (They cannot start with a number).

# Data Types

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

1) _let copyPerson = Object.assign ({}, person);_ What it does is assign to a new empty object all the enumerable properties of the other object with their values. Obviously it creates a new object, a new reference, but its properties are the same.
2) _let anotherPerson = {... person};_ This does basically the same thing. With the spread operator, we are filling a new empty object with all the properties and values ​​of the person object.

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

1) One option would be to look for one that works for us in npm: https://www.npmjs.com/search?q=deep%20copy
2) Use lodash's deepClone method: https://lodash.com/docs/#cloneDeep

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

_**NOTE: Either by implicit or explicit conversion, if a value is tried to be converted into a number and that operation cannot be resolved, we will obtain ```NaN``` as a result.**_

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

That's what is known as **__Nominal Type__**: Two types are compatible when they have the same name or when one is a subtype of the other (by inheritance).

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
