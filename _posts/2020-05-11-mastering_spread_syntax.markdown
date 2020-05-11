---
layout: post
title:      "Mastering Spread Syntax"
date:       2020-05-11 19:22:41 +0000
permalink:  mastering_spread_syntax
---


Going into my last blog post for the Flatiron program, I assumed that I would want to write something general, retrospective, and reflective. Before I got to this point, I guessed that finishing my final project and getting to this last post would feel like the last final before summer break. Now that I'm here, though, it feels quite different. My fantasies of finally "being finished," of getting so many hours of my life back each week, have morphed into a new hope- that I continue doing what I've been doing for 10 months. I've realized that not only do I need to continue learning and challenging myself constantly once I'm finished with this program, but I also *want* to do just that. Finishing this program marks the end of one journey, but also signifies the beginning of a long road ahead. 

So in the spirit of continual learning, I want to spend my last blog post talking about something that has absolutely stumped me: spread syntax. 

The spread operator is still relatively new, having been introduced with ES6, and it almost seems like magic. I've read and re-read the documentation and explanations and have learned to understand how it's being used in code I read, but still find myself stumped when it comes to actually knowing when, and how, to implement it well in my own code. It's been a source of frustration and confusion, but something that I see to be very useful. Time to really get to know this frenemy.

The spread operator, written as an ellipsis (...), provides a way to work with iterables (arrays or objects). I has a few different capabilities: it can be used to expand arrays, combine arrays, copy arrays and objects, or add arrays/objects to another array/object. 
*Note: Copying and adding to arrays and objects becomes especially useful when using Redux, where our reducers need to maintain immutability of data.*

Essentially, the spread operator takes an array/object and expands it into the set of items it's composed of: 

                     let example = "hello";
                     let chars = [...example];

                    //=> [ 'h', 'e', 'l', 'l', 'o' ]
										

We can use this basic capability to do some more complex things, such as...

**Copying and Combining arrays/objects:
**
   
	 A simple example:
	 
                   const firstObject = { a: 1, b: 2 };
                   const secondObject = { ...o1, b: 3, c: 4};
                   //=> { a: 1, b: 3, c: 4 }
				
	  A more complex usage:
		
		            newArray = [...originalArray.slice(0, index), {new items}, ...originalArray.slice(index+1)]
		            // This usage is essentially inserting the {new items} into the array at a specific index point. 
								

**Replacing Object.assign()**:

Object.assign() copies the values of an array into a new one, thereby maintaining immutable data. We can do the same thing with the spread operator, as it always returns a new object. As stated in the Learn.co curriculum, Object.Assign() can quickly make simple reducers difficult to read given its rather verbose syntax.

               Spread syntax: 
							 let dog = {id: 1, name: 'scooby', color: 'brown', age: 4};
               let olderDog = {...dog, age: dog.age + 1}
							 
							 Object.assign(): 
							 let dog = {id: 1, name: 'scooby', color: 'brown', age: 4};
               let olderDog = Object.assign({}, dog, {age: dog.age + 1})

It's just nicer looking!

**Using spread syntax as a rest operator**

Strangely, the spread operator, which expands enumerables, can also be used to do the exact opposite: combine enumerables into an array. In this usage, it is called the rest operator. The rest operator allows us to pass a function an indefinite number of parameters as an array. Then, when the function is called, the parameters provided when called will be joined together as an array:

              function fun1(...theArgs) {
              console.log(theArgs.length)}
              fun1()  //=> 0
              fun1(5) //=> // 1
              fun1(5, 6, 7) //=> 3
							
**TL;DR**

The spread operator is a magical little item given to us by ES6 that allows us to manipulate data within arrays and objects in a wide variety of different ways, from adding items at any point or index in an original array/object, to combining multiple arrays/objects, to manipulating enumerables creatively, all without sacrificing the simplicity of our syntax. I think the difficulty of mastering the spread syntax comes from its flexibility and multiple uses- because it's multi-talented, it can be hard to pin down. But one thing is for sure: it's a powerful and elegant syntax that not only makes our code look nice, but also cuts down on clutter and allows us to interact with complex arrays and objects in a more simplistic way. Cool!

