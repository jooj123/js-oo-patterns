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
}

const dog = createDog('Hank');
dog.howlName(); // output: 'Hello my name is: Hank'
```

## Constructor function

```javascript
function Dog(name) {
  this.name = name;
  this.howlName = function() {
    console.log('Hello my name is: ', this.name);
  }
}

const dog = new Dog('Daisy');
dog.howlName(); // output: 'Hello my name is: Daisy'
```

## Constructor function with inheritance

```javascript
function Dog(name) {
  this.name = name;
}

Dog.prototype.howlName = function() {
  console.log('Hello my name is: ', this.name);
}

const dog = new Dog('Daisy');
dog.howlName(); // output: 'Hello my name is: Daisy'
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
