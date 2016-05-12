<!--
Creator: <Name>
Market: SF
-->

![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png)

#Object Oriented Programming

## Why is this important?
<!-- framing the "why" in big-picture/real world examples -->
*This workshop is important because:*

Object oriented programming is a common pattern throughout many languages. It's patterns will enable you to write more readable, organized, and declarative programs.

## What are the objectives?
<!-- specific/measurable goal for students to achieve -->
*After this workshop, developers will be able to:*

- Build practical and useful objects using Javascript constructors
- Demonstrate a working knowledge of  object properties and methods
- Convert previous projects to utilize Object Oriented Programming techniques

## Where should we be now?
<!-- call out the skills that are prerequisites -->
*Before this workshop, developers should already be able to:*

- Comfortably implement JavaScript objects & functions

## Review: What is an Object?

As of today, we have been writing our Javascript code using mainly functions, Strings, numbers, and Arrays.   This has allowed us to parse through data objects given to us, reach out and pull data from the internet, and display it all on a web page!  These are all great accomplishments, but like everything else in the world of programming, there is always a more efficient way of implementing what we have done.

Here's a truncated version of the cohort data we have been using.  Take some time to study the structure and the data types within the data object.

```javascript
var cohort = {
	school: "General Assembly",
	city: "San Francisco",
	course: "Web Development Immersive",
	courseId: "WDI29",
	classroom: "8",
	students: [{
		id: 0,
		lastName: "Conda",
		firstName: "Kabah",
		githubUsername: "kabah"
	}, {
		id: 1,
		lastName: "Mike",
		firstName: "Cheng",
		githubUsername: "mcheng09"
	}, {
		id: 2,
		lastName: "Min",
		firstName: "Kim",
		githubUsername: "petenut"
	}]
}


```

-  Based on our experience in class so far and your familiarity with the above object, consider the following as you read further:
	- How many of the properties in `cohort` are Strings? 
 	- How many of the properties are Arrays?
 	- If there is an array, what data type(s) are the elements inside?

The `cohort` object is a grouping of key & value pairs (known as properties) that describe our class.  
  
```javascript 
school: "General Assembly"
```
In the line above, `school` is the **key** and `"General Assembly"` is the **value**.
 
To access a property, we can use dot-notation or bracket-notation on the key to have the corresponding value returned.
 
 ```javascript
 var GA = cohort.school; //General Assembly
 ```
 
Now the variable `GA` is assigned to the string `General Assembly`.  

How about if we want to access all the cohort's students?

 ```javascript
 var students = cohort.students; //students
 ```
The `cohort.students` array is now accessible by using `students` instead.
Declaring variables and defining them as portions of a larger object helps us create readable and maintainable code.  

*We can assume that an Object is a collection of properties (key & value pairs) that all have some sort of relationship, connected logically to one another.*  

#Quick Challenge

- Add some more properties that would fit into an object describing our cohort (address, floor number, instructors, etc).
- Try to access your new properties from the console to make sure they work.

If everything worked out, you should have a fully functioning `cohort` object, only now with even MORE properties with us to play with!  


##Constructors
For relatively straightforward and small objects, it is perfectly fine to declare them as a variable and define them, as we did with `cohort`.  This is known as a *Literal* object definition.  
Here's a flower using the *Literal* method:

```javascript
// Literal Object Definition
var flower = {
	color : "red",
	petals : 32,
	smells : true
};
```

We *could* create another flower using `Object.create`. For example:

```javascript
// a rose is a flower
var rose = Object.create(flower);
// but, our rose only has 16 petals
rose.petals = 16;
```

The `rose` will share all characteristics of the original `flower`, except it will have 16 petals because we overwrote that property.

Now let's explore a flower using the preferred *constructor* syntax:
 
 ```javascript
 // constructor object definition
 // note: constructors are always capitalized by convention
 function Flower() {
 	this.color = "red";
 	this.petals = 32;
 	this.smells= true;
 }
 ```

The constructor method is actually a function that can create unique instances of flower objects every time it is called.  Below, we will create a variable `tulip` that will use the constructor method to create a new object.

```javascript
// the keyword `new` is necessary
var tulip = new Flower();
```

Let us break down a couple concepts introduced with this new line of code:
- The capitalization of `Flower` lets everyone know that `Flower` is an object constructor.  Calling `Flower()` will return a `Flower` object.
- The `new` keyword before our function tells javascript that we are creating a new object that will be independent of any other object.
- We call the flower function, which creates an object with the properties made.  Our object is ready to go!

<img src = http://www.mzephotos.com/wallpapers/roses/red-rose-1024x768.jpg width = 75%>

Accessing the properties of our new `tulip` object is the same as accessing our properties from any other object: we can use either dot or bracket notation.

```javascript
var color = tulip.color; // red
var petalCount = tulip.petals; // 32
var smellsNice = tulip.smells; //true
```

If we wanted to create yet ANOTHER flower, all we have to do is call our function just like we did above.  This time, lets make an object called `lily`.

```javascript
var lily = new Flower();
```

We can access the properties of `lily` in the same manner as we did with `tulip`.

```javascript
var color = lily.color; // red
var petalCount = lily.petals; // 32
var smellsNice = lily.smells; //true
```

I don't know about you, but I generally like my lilies yellow. I have also never heard of a lily with 32 petals, holy smokes!  Can we change our `lily` object to better reflect my perfect lily? You bet!

```javascript
// Changing object property values
lily.color = 'yellow';
lily.petals = 6;
```

That's more like it!  To change the value of the lily object properties. We simply access them with dot or bracket notation.  We then follow with an equals and a new appropriate value.  Couldn't be easier!

<img src = https://seniorhikerphotos.files.wordpress.com/2012/06/lilysarina12052301.jpg width = 75%>

##Object Methods
One of the most powerful features of Javascript Objects are Methods.  Methods are *"functions"* that are predefined and built into an object.  We all know and love `Array` methods like `forEach()`, `map()`, `filter()`, and `reduce()`; these are all Methods of the Array object.  We use arrays so much that Javascript automagically creates them from an Array constructor without us having to instantiate them with `new` like we did above with the flowers.  Thanks, Javascript!

Lets make a simple method in the flower object that outputs to the console whenever we call it.

```javascript
function Flower() {
    this.color = "red";
    this.petals = 32;
    this.smells= true;
    // Demonstrates a simple method in an object
    this.bloom = function() {
        console.log("Look at me!");
    };
}
```

We now have a method inside our flower object called `bloom`.

There's an issue with the above code. If we create multiple flowers we don't if the attributes `color`, `petal`, and `smells` all have different properties. It makes sense for these properties to be different and customizable for each flower. However, all flowers could share the `bloom` method. What we want to avoid is creating an entirely new `bloom` method every time we make a new flower.

```javascript
var lily = new Flower();
var rose = new Flower();

lily.bloom === rose.bloom // false
```

But we want their bloom methods to be the same!

##Prototypes

By adding the method `bloom` to the constructor's **prototype** we can enable all flowers to share a `bloom` method, or any other method for that matter! The prototype is simply the object that can be referenced by all the flower instances.

```javascript
function Flower() {
    this.color = "red";
    this.petals = 32;
    this.smells= true;
}

Flower.prototype = {
  bloom: function() {
    console.log("Look at me!");
  }
}
```

Now try running the same test to see if both flowers share the same `bloom` method.

```javascript
var lily = new Flower();
var rose = new Flower();

lily.bloom === rose.bloom // true
```

###Benefits

- Less wasted memory
- Single source of truth

>What if we edit the prototype *after* the flower instances have been created? Will they update their behavior accordingly?

###More methods

Let's add some more methods to the flower constructor.

```javascript
function Flower() {
    this.color = "red";
    this.petals = 32;
    this.smells= true;
}

Flower.prototype = {
  bloom: function() {
    console.log("Look at me!");
  },
  smellsGood: function() {
  // use `this` to access the instance's attributes
    if (this.smells) {
      return 'This flower smells amazing!';
    } else {
      return 'What a noxious weed!';
    }
  },
  describe: function() {
    console.log("This flower is " + this.color + ".");    
  }
}
```
Methods can also access properties within the object with the `this` identifier rather than using dot or bracket notation.

###Quick Challenge - Wilt & water
- Create a wilt() method that decrements each flower by one petal. :(
- Create a water() method that increments each flower by one petal. :)

##Customization

Wouldn't it be nice if at the moment we instantiate a flower we could also define its properties?

```javascript
var chrysanthemum = new Flower("pink", 65, false);
```

Such that the `chrysanthemum` is pink with 65 petals and doesn't smell good.

<details>
<summary>Challenge: how could we refactor the original flower constructor to accomplish this?</summary>

```javascript
function Flower(color, petals, smells) {
    this.color = color;
    this.petals = petals;
    this.smells = smells;
}
```
</details>

##Modeling Flowers

Take 10 minutes to create a flower instance based on the flower on your table. Decide amongst your
tablemates the type of flower, the flower's main color, number of petals, and whether or not it smells pretty. Think up some other possible properties or methods and add them too!

...

Now we should have a flower instance for each of our actual flowers.

Let's source the best new properties that were created on their constructors and integrate them into a universal flower constructor.

##Cross-Pollination

Now that we are awesome Flower experts, lets try our hand at cross pollinating two flower objects. Cross pollinating is beyond the realm of an individual flower and could therefore live on the Flower constructor itself. Another examples of this would be `create`, `new`, or `destroy`. These are all *meta* actions of a flower; a flower cannot create itself! They are called **static methods**.

To exemplify this let's create a static method (also sometimes refered to as a class method) called `crossPollinate` as opposed to the instance methods we've been making (i.e. `bloom`)
- The method will take two flower instances as arguments.    
- Return a new flower intance that is a mix of both "parent" colors. (i.e. red, yellow = "red-yellow"; we don't care about the color wheel).
- Make the new petal count an average between the two parents' petal counts.
- The smellPretty gene is recessive, unfortunately. This means that a flower will smell pretty IF and only IF both flowers smell pretty.  

<details>
<summary>Example solution</summary>

```javascript
// constructor
function Flower(color, petals, smells) {
    this.color = color;
    this.petals = petals;
    this.smells = smells;
}

// static methods
Flower.crossPollinate = function(momFlower, dadFlower) {
  var color = momFlower.color + "-" + dadFlower.color;
  var petals = (momFlower.petals + dadFlower.petals) / 2;
  var smells = momFlower.smellsGood && dadFlower.smellsGood;
  var babyFlower = new Flower(color, petals, smells);
  return babyFlower;
}

// instance methods
Flower.prototype = {
  bloom: function() {
    console.log("Look at me!");
  },
  smellsGood: function(answer) {
    if (answer) {
      return 'This flower smells amazing!';
    } else {
      return 'What a noxious weed!';
    }
  },
  describe: function() {
    // Demonstrates use of local object variables
    // use `this` to access the instance's attributes
    console.log("This flower is " + this.color + ".");    
  }
}


var lily = new Flower("blue", 32, true);
var rose = new Flower("green", 12, true);

var rily = Flower.crossPollinate(rose, lily)
```

</details>

*Thought experiment: Maybe we create a different intermediary object, called Bee, which would facilitate cross-pollination and return a new flower? Flowers don't just bash their heads together and make new flowers in the real world, they need bees!  What are some methods we could assign to a Bee object?*


##Closing Thoughts

* Why is using a prototype?
* Would you typically put the methods or attributes in the prototype?
* When would we use static methods?

Further Suggested Reading:

- [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Introduction_to_Object-Oriented_JavaScript)
