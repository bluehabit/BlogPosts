A constructor function is a single object that we can use as a base to create more objects that are similar. Think of it like a stamp head in a way, once we have the head created we can stamp out as many items as we want all from a single head. We essentially are able to clone the object or constructor function that was originally created.

Here is an example in Javascript:

```
var Bullet = function (x, y, color) {
    this.x = x;
    this.y = y;
    this.color = color;
    this.location = function () {
        console.log("x: " + x + " " + "y: " + y);
    };
};

var bullet1 = new Bullet(5, 10, "Green");
var bullet2 = new Bullet(20, 40, "Blue"); 

bullet1.location(); //Console Logs: x: 5 y: 10
```

In the example above we create a constructor function and give it four properties, by using the this keyword we are binding or assigning those properties to the instance of Bullet.

**Note**: By convention and best practice in Javascript, you should start all constructor functions with a capital letter.

As we can see we are even able to assign functions as properties on our constructor. We then create two new instances of the Bullet Class, bullet1 and bullet2. In Javascript we can use the “new” keyword to create new instances of the class object. You also might notice that we are able to pass in arguments on the fly, this makes it so not all of our instances have to be exactly the same.

Once we create the instance of our class we can then call any of the methods that are on the object. In the example above we call the location method on our object and get back a console log of our coordinates.

There is just one problem with our constructor function above, when you place a function inside of a constructor it recreates that function over and over every instance that gets created. As you can imagine, if you had thousands of instances, this could become a pretty big problem (speed and optimization). Thankfully Javascript has a solution for this problem.

We can use the prototype, this will create only 1 function, no matter how many instances you create. The function is set aside in a little box (figuratively speaking) and can be used by all of the instances when needed.

An example of how the prototype can help us optimize our previous code:

```
Bullet.prototype.location = function () {
    console.log("x: " + this.x + " " + "y: " + this.y);
}
```

Its pretty easy to use the prototype in Javascript but is still considered on of the more complicated parts of the language that most people don’t know much about. Using the prototype can be a good way to show off your Javascript knowledge, but also improves the performance of your code by a handful.
