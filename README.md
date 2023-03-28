# Looping Through Arrays

## Learning Goals

- Use a `for` loop to loop through an array
- Use `for...of` to loop through an array

## Introduction

Quite frequently, when we're working with arrays, we need to access each of the
elements in turn and do something with them. As we learned earlier in the Prep
course, the way to accomplish this is by using a loop, for example, a `for` or
`while` loop loop. In this lesson, we will review the workhorse `for` loop and
revisit how to use one to loop through an array.

We will also learn about another type of loop, one that is designed specifically
for looping through arrays: the `for...of` loop.

## Using `for` Loops with Arrays

You learned in Prep how to construct `for` loops to repeat actions some number
of times. To review, the general structure of a `for` loop looks like this:

```js
for ([initialization]; [condition]; [iteration]) {
  [loop body]
}
```

The individual statements are:

- Initialization: Typically used to initialize a **counter** variable.
- Condition: An expression evaluated before each pass through the loop. If this
  expression evaluates to true, the statements in the loop body are executed. If
  the expression evaluates to false, the loop exits.
- Iteration: An expression executed at the end of each iteration. Typically,
  this will involve incrementing or decrementing a counter, bringing the loop
  ever closer to completion.
- Loop body: Code that runs on each pass through the loop.

For example, if we want to log the numbers 1 through 10 to the console, we could
use a `for` loop as follows:

```js
for (let i = 1; i <= 10; i++) {
  console.log(i);
}
```

In the code above:

- The _initialization_ is setting the starting value of our counting variable,
  `i`, to 1.
- The _condition_ is checking that the value of `i` is less than or equal to 10.
- The _iteration_ is incrementing `i` by 1 each time through the loop.
- The _loop body_ is logging the current value of `i` each time through the
  loop.

We can also use `for` loops to loop through an array. In this case, we can use
the value of our counting variable `i` to refer to the index of each element in
the array, and use the condition to stop the loop once we reach the end of the
array. It might look like this:

```js
const planets = [ "Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune" ];
for (let i = 0; i < planets.length; i++) {
  console.log(planets[i]);
}
```

Note the differences between how we've set up this loop vs. the one above:

- We initialized our counter variable to 0 rather than 1. This is because 0 is
  the index of the first element of an array. This is a very common convention,
  often used even if the code _isn't_ being used to loop through an array!
- We are using the length of the array in our condition rather than hard-coding
  a specific value. This means that the loop will still work if we decide to
  include Pluto in our list of planets.
- Our condition uses `<` (less than) for the comparison rather than `<=` (less
  than or equal). Recall that, because the first element of an array is indexed
  by 0, the index of the last element in the array is **one less** than the
  length of the array. Because our list of planets contains 8 values, the index
  of the last planet, Neptune, is 7. If we used `<=` in our loop, the JavaScript
  engine would try to access `planets[8]`, which doesn't exist, and would throw
  an error.

The advantage of `for` loops is that they're very versatile. For pretty much any
circumstance you can think of for which you might need to create a loop, a `for`
loop will work. However, that versatility comes at a price of somewhat
complicated syntax. It takes a fair amount of practice before the process of
setting up the initialization, condition and iteration components becomes second
nature. Furthermore, it seems odd that for a common task like looping through an
array, JavaScript wouldn't provide an easier way. Well, it does.

## Using `for...of` to Loop Through an Array

The `for...of` loop is designed specifically for the purpose of looping through
each of the elements of iterable objects (e.g., arrays) in turn and doing
something with each element.

> Arrays are just one type of _iterable object_ that we can loop through using a
> `for...of` loop. Another one is strings. Yep! We can use a `for...of` loop to
> loop through the "elements" (the characters) of a string! There are other
> iterable objects as well. If you're interested in learning more, check out
> [MDN's `for...of` documentation][for-of].

Using the same example from above and a `for...of` loop, our loop that logs out
each planet in our solar system would look like this:

```js
const planets = [ "Mercury", "Venus", "Earth", "Mars", "Jupiter", "Saturn", "Uranus", "Neptune" ];
for (const planet of planets) {
  console.log(planet);
}
```

The advantages of using the `for...of` loop over a regular `for` loop are:

- You don't need to tell the loop where to start and where to end; JavaScript
  automatically starts with the first element in the array and executes the code
  for each element in turn.
- You don't need to use bracket syntax along with an index variable to access
  each element. Instead, you specify the name of the variable to use to refer to
  each element in turn and the JavaScript engine takes it from there. Note that
  we're using `const` rather than `let` to initialize our counter variable. With
  a `for` loop we have to explicitly re-assign the counter's value; since we no
  longer need to do that with `for...of`, we can use `const` instead.
- The use of a descriptive singular noun for each element of the array and its
  plural form to refer to the array itself is done by convention. It's optional,
  but you'll see it done that way most of the time because it makes it quite
  easy to tell what the loop is doing just by reading the code.
- The syntax of `for...in` loops is simpler and more intuitive than the quite,
  um, "syntax-y" syntax of `for` loops.

## Conclusion

In this lesson, we used two types of loops to loop through an array: a `for`
loop and a `for...of` loop. A bit later in this section, we'll learn about
JavaScript's _iterator methods_, which are even more powerful and _expressive_
(more on that later) ways to interact with each element of an array.

## Resources

- [MDN: for statement][for]
- [MDN: for...of statement][for-of]

[for]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for
[for-of]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...of
