# Objects and Context

## Learning Objectives

### Objects
- Explain how objects are defined as data structures
- Create objects using object literal syntax.
- Practice interacting with properties of literal objects.
- Explain nested data structures.
- Explain the difference between object properties and methods.
- Write an object method.

### Context
- Explain Javascript 'context' and what the value of the 'this' keyword refers to
- Explain what the default context of Javascript executing in the browser is
- Use the 'this' keyword to set and retrieve a property in a Javascript function
- Use bind to create a new method bound to an object context
- Use apply/call to execute a method in a different context

## Framing (5 / 05)
[// Todo]: # ( Framing needs to be overhauled )

This lesson will cover two concepts that are crucial for encapsulation and abstraction in Javascript: Objects and Context. Objects allow us to box up multiple functions and data under a single variable. Context is similar to scope.

To explore these concepts we will be looking at a series of examples that unveil the mechanics of scope and context. Through comparing and contrasting code examples look that seem similar yet contain important differences, we'll highlight how scope and context operate in Javascript. The examples ultimately aim to illustrate that the way that code is written and structured affects ***how and where its program data (its variables or references) can be accessed***.

[// Todo]: # (Double-check Objects section time. Markings claim it's ~85 mins)

## Intro to Objects (5 / 00)

Before we start to talk about objects, let's visit a site some of you may be familiar with,
[Amazon](https://www.amazon.com). If we type in some random thing to search for you'll notice all the results have similar properties. Things like, price, title, reviews, Prime eligibility and picture.

Turns out, in programming, we need a way to encapsulate logic about things in the real world and represent them in our programs. In Javascript, these things are objects.

In JavaScript, objects are collections of properties(key-value pairs). We can add or remove these properties as we please. The simplest way to create an object is by using a curly brace notation (also known as object literal notation).

```js
var car = {
  make: "Honda",
  model: "Civic",
  year: 1997
}
```

Objects are a complex data type - usually referred to as an *unordered* list (or dictionary/hash/map).
* They are a collection of key-value pairs called properties.
* The keys which we explicitly state when defining a property are analogous to our array indexes. They are how we access the associated value (more below).

> In the above example, the variable `car` points to an object literal. This particular object has 3 properties: `make`, `model` and `year`.

### Turn and Jot: Model WDI Student (5 / 00)

You're goal is to pseudo-code an object literal:

* In pairs, spend 2 minutes thinking about what attributes a WDI student should have (think of at least 5!).
* Take 3 minutes to construct your object literal with appropriate key value pairs by drawing it on the table
* **Bonus - One key value pair contains an array**

### You DO: Interacting with Objects (30 / 00)

**Read through the below, and then complete the exercise with your partner**

#### Create

We already saved a sample object to a `car` variable. We did this using **object literal notation**.

```js
var car = {
  make: "Honda",
  model: "Civic",
  year: 1997,

  // NOTE: Keys with a "-" in their name must be surrounded by quotation marks.
  "tire-type": "Goodyear"
}
```

#### Read

To access object properties, we use either dot (`.property`) or bracket (`["property"]`) notation.

```js
console.log( car.make );
console.log( car["make"] );

// What happens when we try to access a property yet to be defined?
console.log( car.owner )

// NOTE: When accessing properties whose keys have a "-" in them, you must use bracket notation.
console.log( car["tire-type"] );
```

#### Update

To update an object property, we place it on the left side of an assignment statement.

```js
car.year = 2003
```

We can also create brand new properties for an object after it's initialized using this method.

```js
// Now our car has a smell property equal to "Leathery Boot". We did not initially declare this property.
car.smell = "Leathery Boot"
```

#### Delete

If you want to delete an object property entirely, use the `delete` keyword.
* This deletes the whole key-value pair, not just the value.
* You won't do this often.

```js
delete car.smell
```

#### Iterating through an Object

Like arrays, you can use a loop to iterate through an object. Say we want to print out all of an object's keys...

```js
// Iterate through object keys
for (attribute in car) {
  console.log( attribute );
}
```
> Knowing this, how could we go about getting all the values in an object?

Javascript objects also have native methods that take care of this for us...
```js
// .keys()
Object.keys( car );
```

### Exercise

Create a variable named `wdiStudent` and assign it to an object literal.

1. Give your student at least three properties.
2. One must have a key that contains a hyphen.
3. One must contain an array or object.
4. Update two properties, one of which is the hyphenated.
5. Give your student a new property using dot or bracket notation.
6. Delete one attribute.
7. Iterate through and print out all of the student's key-value pairs.

**Bonus:** Write a function that returns your `wdiStudent` object

> [Solution](https://gist.github.com/nolds9/efdb0a320e7143f42e96)

### Nested Collections (5 / 00)

Object properties aren't limited to simple data types. We can also nest collections inside of collections.

```js
var car = {
  make: "Honda",
  model: "Civic",
  year: 1997,

  // An array within an object.
  gears: ["Reverse", "Neutral", "1", "2", "3", "4"],

  // An object within an object.
  engine: {
    horsepower: "6 horses",
    pistons: 12,
    fast: true,
    furious: false
  }
}
```

**Q** In the above examples, how do we access...
* "Neutral" (i.e., array value within an object)?
* "6 horses" (i.e., object value within an object)?

### Break (10 / 00)

## Methods (15 / 00)

Methods are functions that are attached to some object.

```js
// Our car now has a drive method...
var car = {
  make: "Honda",
  model: "Civic",
  color: "red",
  drive: function(){
    console.log("vroom vroom");
  },

  // Methods can take arguments
  gps: function( location ){
    console.log( "Beep boop, driving to " + location );
  },
  paint: function( newColor ){
    console.log( "Your car has been painted " + newColor );
    car.color = newColor;
  }
}

// We can run the car's two methods like so...
car.drive();
car.paint( "blue" );
console.log( "Car color is: " + car.color );
```

With methods as part of our Javascript toolbox, we now have a cool interface with which we can interact with our objects.
* Why would custom methods be a preferred way to modify object properties vs. using object literal notation?

We've only scratched the surface for objects. We're going to dive much deeper into them later on in the course.

> If you're looking for a sneak peak into the power of objects and functions, we recommend reading [The Secret Life of JS Objects](http://eloquentjavascript.net/06_object.html) chapter in Eloquent JS

### Bonus
### You Do: Big Ol' Twitter Object (15 / 00)

As this course continues you will encounter plenty of Javascript objects in the wild. Spend **10 minutes** on the following...
* Follow the link below and answer the questions in bold.
* Along with each answer, write down how we would access the property in question.
* Let's do the first one together...

[Twitter JSON Exercise](https://github.com/ga-dc/big_ole_twitter_object)


## [Context](context.md)

## Break (10 / 90)

## HW: Calculator

[Javascript Calculator](https://github.com/ga-dc/js-calculator)

## Closing, Q&A, Review LO's (10 / 150)

1. Does a function need an input, output, and side-effect to work?
2. What's difference between calling and referencing a function?
3. What's difference between function expressions and declarations?
4. How are objects like dictionaries?
5. What's difference between a property and a method?

## Further Reading / Resources

* [Javascript Scoping and Hoisting](http://www.adequatelygood.com/JavaScript-Scoping-and-Hoisting.html)
* [The Secret Life of JS Objects](http://eloquentjavascript.net/06_object.html)
* [Secrets of the Javascript Ninja](http://webandbeer.com.ar/wp-content/uploads/2014/11/SecretsOfTheJavaScriptNinja.pdf)
* [JS for Cats](http://jsforcats.com/)
* [CoderByte Challenges](https://coderbyte.com/challenges/)
