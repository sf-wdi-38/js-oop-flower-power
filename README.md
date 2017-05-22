# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) Flower Power: Object Oriented Programming in JavaScript

### Why is this important?
*This workshop is important because:*

Object oriented programming is a common pattern throughout many languages. Its patterns will enable you to write more readable, organized, and declarative programs.

### What are the objectives?
*After this workshop, students will be able to:*

- Build practical and useful objects using Javascript constructors
- Demonstrate a working knowledge of object properties and methods
- Design object types in JavaScript using Object Oriented Programming techniques
- Understand the difference between pseudo-classical and prototypal inheritance in JavaScript

### Where should we be now?
*Before this workshop, students should already be able to:*

- Create and manipulate JavaScript objects
- Write and interpret JavaScript functions

### Review
Work with a partner and write your answers.

1. What is an object? How does it hold data? What are two ways we can access things inside of an object?
2. If an object contains a function, how can we call it?

```javascript
var obj = {
  name: "Justin Castilla",
  employer: "General Assembly",
  sayHello: function() {
    console.log("Hello, my name is " + this.name);
  }

};

// what code would you write here to call the function?
```

3. What is the `this` keyword used for?
4. Think back to looping through an array - if you wanted to put data in your page fron an array of objects, would you be able to easily loop through it and add the URLs to the page? Why or why not? How would you go about doing this? Use pseudocode.

```javascript
var myArray = [
  {
    url: "www.google.com",
    description: "The searching people"
    // other data
  },
  {
    URL: "www.generalassemb.ly",
    info: "The teaching people"
    // other data
  },
  {
    link: "www.jquery.com",
    details: "The $ people",
    // other data
  },
  {
    pageUrl: "developer.mozilla.org",
    pageDescription: "The Firefox people",
    // other data
  }
];
```
### Constructors
For relatively straightforward and small objects, it is perfectly fine to declare them as a variable and define them.  This is what we've been doing when we've created objects so far, and it's known as a *Literal* object definition.

Here's a flower using the *Literal* method:

```javascript
// Literal Object Definition
var flower = {
	color : "red",
	petals : 32,
	smells : true
};
```

There are a few other patterns we can use to create objects.

We *could* create another flower using `Object.create`. For example:

```javascript
// a rose is a flower
var rose = Object.create(flower);
// now rose is { color : "red", petals : 32, smells : true }
// but, our rose only has 16 petals
rose.petals = 16;
// now rose is { color : "red", petals : 16, smells : true }
```

The `rose` will share all characteristics of the original `flower`, except it will have 16 petals because we overwrote that property.

Using `Object.create` is limited, though. It means we have to remember what all of the properties are that we want to change, and change them manually for that object. Instead, we prefer to use the **constructor** syntax. Let's explore what a Flower constructor might look like:

 ```javascript
 // constructor object definition
 // note: constructors are always capitalized by convention
 function Flower(color, petals, smells) {
 	this.color = color;
 	this.petals = petals;
 	this.smells = smells;
 }
 ```

The constructor is actually a function that can create unique instances of flower objects every time it is called.  Below, we create a new object using the constructor and store it in a variable `tulip`.

```javascript
// the keyword `new` is necessary
var tulip = new Flower("purple", 8, false);
```

Let's break down a couple concepts introduced with this new line of code:
- The capitalization of `Flower` lets everyone know that `Flower` is an object constructor.  Calling `Flower()` with `new` will return a `Flower`-type object.
- The `new` keyword tells JavaScript that we are creating a new object instance that will be independent of any other object.
- We call the `Flower` function, which creates an object with the properties from the constructor.  Our object is ready to go!
- We pass in parameters to our constructor to set up our object in the way we've defined. This ensures that all of our `Flower` objects will have the same properties, set in the same way, by the same constructor.

![](https://cloud.githubusercontent.com/assets/3254910/17949473/5e17a92a-6a0a-11e6-90fb-2294c3d1b6e9.png)


Accessing the properties of our new `tulip` object is the same as accessing our properties from any other object: we can use either dot or bracket notation.

```javascript
var color = tulip.color; // purple
var petalCount = tulip.petals; // 8
var smellsNice = tulip.smells; //false
```

If we wanted to create yet **another** flower, all we have to do is call our function just like we did above.  This time, lets make an object called `lily`.

```javascript
var lily = new Flower("yellow", 6, true);
```

We can access the properties of `lily` in the same manner as we did with `tulip`.

```javascript
var color = lily.color; // yellow
var petalCount = lily.petals; // 6
var smellsNice = lily.smells; //true
```

We can also change these properties, just as we can with any other object. What happens if our lily grows an extra petal?

```javascript
// Changing object property values
lily.petals = 7;
```

That's more like it!  To change the value of the lily object properties, we simply access them with dot or bracket notation.  We then follow with a single equals assignment operator and give a new appropriate value.  Couldn't be easier!

![](https://seniorhikerphotos.files.wordpress.com/2012/06/lilysarina12052301.jpg)

### Object Methods
One of the most powerful features of Javascript Objects are Methods.  Methods are *functions* that are predefined and built into an object.  We all know and love `Array` methods like `forEach()`, `map()`, `filter()`, and `reduce()`; these are all methods of the `Array` object.  We use arrays so much that Javascript gives us the shorthand `[]` syntax to create them instead of calling the `Array` constructor with `new` to make instances, like we did above with the flowers.  Thanks, Javascript!

Lets make a simple method in the flower constructor that outputs to the console whenever we call it.

```javascript
 function Flower(color, petals, smells) {
    this.color = color;
    this.petals = petals;
    this.smells= smells;
    // Demonstrates a simple method in an object
    this.bloom = function() {
        console.log("Look at me!");
    };
}
```

The new flower instances will have a method inside called `bloom`.

```js
var sunflower = new Flower("yellow", 54, false);
sunflower.bloom();
// prints out "Look at me!"
```

<img alt="sunflowers by skyseeker on flickr" src="https://cloud.githubusercontent.com/assets/3254910/17949651/461f09f2-6a0b-11e6-96fb-31c01b5f978a.png" width="50%">



### Independent Practice: Customization

* How could we refactor the parameters that the `Flower` constructor accepts so it takes in a single object that contains all the attributes of the instance we are initializing? Refactor the constructor to enable this code:

```javascript
var options = {petals: 65, color: "pink", smells: false};
var chrysanthemum = new Flower(options);
```

<details>
<summary>Example solution</summary>

```javascript
function Flower(options) {
    this.color = options.color;
    this.petals = options.petals;
    this.smells = options.smells;
    this.bloom = function() {
        console.log("Look at me!");
    };
}
```
</details>

* How can we make the petal count to default to 10, if not otherwise specified? Enable this code:

```javascript
var options = {color: "pink", smells: false};
var chrysanthemum = new Flower(options);
// inspect instance
chrysanthemum;
// => Flower {color: "pink", petals: 10, smells: false}
```

<details>
<summary>Example solution</summary>

```javascript
function Flower(options) {
    this.color = options.color;
    this.petals = options.petals || 10;
    this.smells = options.smells;
    this.bloom = function() {
        console.log("Look at me!");
    };
}
```
</details>

## Prototypes

Flowers can now be created with unique attributes, which is awesome. On the other hand, you may notice that all flowers could share the `bloom` method. Right now, though, each flower instance has a separate bloom method.

```javascript
var lily = new Flower("yellow", 6, true);
var rose = new Flower("white", 24, true);

lily.bloom === rose.bloom // false
```

We want their bloom methods to be the same! Next, we'll see how to avoid creating an entirely new `bloom` method every time we make a new flower.

<img src="https://media.giphy.com/media/10nccX8vZPEeA0/giphy.gif" alt="blooming flower gif" width="50%">

By adding the method `bloom` to the constructor's **prototype** we can enable all flowers to share a `bloom` method, or any other method for that matter! Shared attributes can also be added to the prototype, but they're less common.  The prototype is simply an object that can be referenced by all the flower instances.

```javascript
function Flower(color, petals, smells) {
   this.color = color;
   this.petals = petals;
   this.smells= smells;
}

Flower.prototype.bloom = function() {
  console.log("Look at me!");
}
```

Now try running the same test from above to see if both flowers share the same `bloom` method.

```javascript
var lily = new Flower();
var rose = new Flower();

lily.bloom === rose.bloom // true
```

#### Benefits

- Less wasted memory
- Single source of truth

>What if we edit the prototype *after* the flower instances have been created? Will they update their behavior accordingly?

#### More methods

Let's add some more methods to the flower constructor.

```javascript
function Flower(color, petals, smells) {
   this.color = color;
   this.petals = petals;
   this.smells= smells;
}

Flower.prototype.bloom = function() {
  console.log("Look at me!");
}
Flower.prototype.smellsGood = function() {
// use `this` to access the instance's attributes
  if (this.smells) {
    return 'This flower smells amazing!';
  } else {
    return 'What a noxious weed!';
  }
}
Flower.prototype.describe = function() {
  console.log("This flower is " + this.color + ".");    
}
```
Methods can also access properties within the object with the `this` identifier rather than using dot or bracket notation.

#### Check for Understanding: `wilt` and `water`
- Create a `wilt()` method that decrements a flower's petal count by one. :(
- Create a `water()` method that increments a flower's petal count by one. :)

### Independent Practice: Modeling Flowers

Take 10 minutes to create a flower instance based on the flower on your table. Decide amongst your tablemates the type of flower, the flower's main color, number of petals, and whether or not it smells pretty. Think up some other possible properties or methods and add them too!

...

Now we should have a flower instance for each of our actual flowers.

Let's source the best new properties that were created on constructors and integrate them into a universal flower constructor.

### Constructor and Prototype Review

**Constructors**

* variables and functions are declared once for each instance
* when you update the constructor, previously created instances DON'T update
* data is "embedded" in each instance

**Prototypes**

* all instances share the same function and variable declarations
* when you update the prototype, previously created instances DO get the updates
* data is "referenced" from the prototype copy

**Instance variables and functions**

* adds variable or function directly to the instance
* overwrites constructor properties/methods by replacing them
* overwrites prototype properties/methods by being earlier on the lookup chain!

**Static variables and functions**

* add values or behaviors directly to the constructor function
* these attributes are not specific to any one instance but apply to the type
* examples: Math.PI, Apartments.all



### Independent Practice: Object-In-Object

<img src="https://cloud.githubusercontent.com/assets/3254910/17948758/fe31c9e4-6a06-11e6-8c59-c68d975c02a8.png" alt="flower vase image from homeheavenimages on flickr" width=80%>


1. Create a vase object which contains an array of flower objects and a `capacity` attribute that says how many flowers the vase can hold.

  <details><summary>sample solution</summary>
   ```js
   function Vase (capacity){
   	this.capacity = capacity || 12;
   	this.flowers = [];
   }
   ```
  </details>

1. Create a method `placeFlower` that accepts a `Flower` object as a parameter and inserts the flower into the array. What if the vase is too small? Update your method so that it checks whether the vase is already holding its capacity of flowers before it adds the extra flower.
    <details><summary>sample solution</summary>
   ```js
   Vase.prototype.placeFlower = function(flower){
     if (this.flowers.length < this.capacity){
       this.flowers.push(flower);
     } else {
       console.error("no room for more flowers!");
     }
   }
   ```
  </details>

1. Create an `addWater` method for a vase that calls the `water` method of each flower inside.
    <details><summary>sample solution</summary>
   ```js
   Vase.prototype.addWater = function(){
     this.flowers.forEach(function(flower){
       flower.water();
     });
   }
   ```
  </details>

1. Feel free to add more properties or methods for your `Vase` object type.

### Prototypal vs Pseudo-Classical Inheritance

> Note: This is an advanced topic; if you're confused at this point, you should put the majority of your effort into understanding how constructors work, and how to write one for a new class of object that you want to define, NOT into this section.

So far, we have talked mostly about what is considered _pseudo-classical inheritance_ when we extend properties of an object or class to a new instance. This is called _pseudo-classical_ for JavaScript because it mimics the structure of inheritance in more traditional class-based languages such as Java or C++. It's also similar to how inheritance will work in Ruby.

Some programmers and engineers consider _prototypal inheritance_ to be more appropriate, clear, and/or efficient in JavaScript. This is a matter of opinion of course, but it's worthwhile to examine the difference.

Let's continue the lovely flower examples.

Here's an example of _pseudo-classical_ inheritance:

```js
function Flower(name, numPetals, color, seasonality) {
	this.name = name;
	this.numPetals = numPetals;
	this.color = color;
	this.seasonality = seasonality;
}

Flower.prototype.bloom = function() {
    return "A " + this.color + " " + this.name " has " + this.numPetals.toString() + " petals."
};

var Daisy = new Flower("daisy", 34, "white and yellow", "perrenial");

var Tulip = new Flower("tulip", 6, "red", "annual");
```

 <details><summary>What do you notice?</summary>

 * There is a class that serves as a blueprint.
 * The flower instances called `Daisy` and `Tulip` "build" flowers to the specs of the blueprint.

   _Note: This is also called a constructor pattern. Using the `.prototype` method is also a way of implementing pseudo-classical inheritance._
 </details>


...and here's the same idea, but with _prototypal inheritance_:

```js
var Flower = {
	bloom: function {
		return "A " + this.color + " " + this.name " has " + this.numPetals.toString() + " petals."
	}
}

var Daisy = Object.create(Flower, {
	name: {
		value: "daisy"
		}
	},
	numPetals: {
		value: 34
		}
	},
	color: {
		value: "white and yellow"
		}
	},
	seasonality: {
		value: "perrenial"
		}
	}
});

/* alternatively to the above
Object.create() explicit method,
you may use a factory function: */

function flowerFactory(name, numPetals, color, seasonality) {
	var flower = Object.create(Flower);
	flower.name = name;
	flower.numPetals = numPetals;
	flower.color = color;
	flower.seasonality = seasonality;
	return flower;
}

var Tulip = flowerFactory("tulip", 6, "red", "annual");


```

 <details><summary>What's different here?</summary>

 * New flowers are created from the existing Flower variable.
 * We build flowers based on existing flowers.
 * We can use a factory method to create instances of flowers.
</details>

So which should you use? The answer is a matter of opinion. Here is one popular [StackOverflow post](http://stackoverflow.com/questions/2800964/benefits-of-prototypal-inheritance-over-classical) on the matter.

### Independent Practice

* _Discuss:_ What are the relative merits and drawbacks of each type of inheritance in JavaScript? Make a pro's and con's list for each.

* _Bonus:_ Demonstrate your knowledge of each type of inheritance by writing a code for a `Mushroom` "class" that can be inherited from, and building a few instances such as `Shitake` and `Nightshade`.



### Closing Thoughts

* Would you typically put the methods or attributes in the prototype?
* When would we use static methods?

### Further Suggested Resources

- [Lynda.com's "What is object-oriented language" video](https://www.youtube.com/watch?v=SS-9y0H3Si8)
- [MDN's Introduction to Object-Oriented JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Introduction_to_Object-Oriented_JavaScript)
- [MDN's Reference on Inheritance and the Prototype Chain](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)
