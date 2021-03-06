# js-oo-patterns
Different Object-Oriented JS Patterns

## Return new object from function

```javascript
function createDog(name) {
  const obj = {}; // or new Object(); but typically this isnt necessary
  obj.name = name;
  obj.howlName = function() {
    console.log('Hello my name is: ', this.name);
  }
  
  return obj;
}

const dog = createDog('Hank');
dog.howlName(); // output: 'Hello my name is: Hank'
```

**Cons:**
* Verbose, you need to create getters and setters
* Full access to properties (eg: `dog.name`) which can bipass logic and data security


## Constructor function

```javascript
function Dog(name) {
  this.name = name;
  this.howlName = function() {
    console.log('Hello my name is: ', this.name);
  }
}

const dog = new Dog('Fluffy');
dog.howlName(); // output: 'Hello my name is: Fluffy'
```

**Pros:**
* No need to create getters and setters

**Cons:**
* Full access to properties (eg: `dog.name`) which can bipass logic and data security


## Constructor function & adding to prototype

```javascript
function Dog(name) {
  this.name = name;
}

Dog.prototype.howlName = function() {
  console.log('Hello my name is: ', this.name);
}

const dog = new Dog('Fluffy');
dog.howlName(); // output: 'Hello my name is: Fluffy'
```

## Constructor function with inheritance

```javascript
function Animal(name) {
  this.name = name;
}

function Dog(name, tailLength) {
  Animal.call(this, name);
  this.tailLength = tailLength;
}

// Link prototypes and add prototype methods
Dog.prototype = Object.create(Animal.prototype);

Animal.prototype.sayName = function() {
  console.log('Hello my name is: ', this.name);
}

Dog.prototype.sayLength = function() {
  console.log('My tail length is: ', this.tailLength);
}

const dog = new Dog('Fluffy', 23);
dog.sayName(); // output: 'Hello my name is: Fluffy'
dog.sayLength(); // output: 'My tail length is: 23'
```

## Object constructor

```javascript
const dog = Object();

dog.name = 'Tyson';
dog.howlName = function() {
  console.log('Hello my name is: ', this.name);
}
```

## Object.create

```javascript
const dog = {
  howlName: function() {
    console.log('Hello my name is: ', this.name);
  }
};

const myDog = Object.create(dog);
myDog.name = 'Bob';
myDog.howlName();
```

## Object.create with inheritance

```javascript
const dog = {
  bark: function() {
    console.log('Bark!');
  },
  howlName: function() {
    console.log('Hello my name is: ', this.name);
  }
};

const myDog = Object.create(dog);
myDog.bark(); // prints: Bark!
myDog.name = "Bill";

const billTheDog = Object.create(myDog);
myDog.howlName(); // prints: Hello my name is: Bill
```

**Note differences between `Object.assign()` from MDN:** `Object.create` method creates a new object, using an existing object as the prototype of the newly created object (so can be specifically used for inheritance)
The `Object.assign()` method on the other hand is used to copy the values of all enumerable own properties from one or more source objects to a target object. It will return the target object.

## class keyword

```javascript
class Dog {
  constructor(name) {
    this.name = name;
  }
  
  howlName() {
    console.log('Hello my name is: ', this.name);
  }
}

const myDog = new Dog('Snowy');
myDog.howlName();
```

## class keyword with inheritance

```javascript
class Animal {
  constructor(name) {
    this.name = name;
  }
}

class Dog extends Animal {
  constructor(name) {
    super(name);
  }
  
  howlName() {
    console.log('Hello my name is: ', this.name);
  }
}

const myDog = new Dog('Snowy');
myDog.howlName();
```
