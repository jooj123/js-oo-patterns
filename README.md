# js-oo-patterns
Different Object-Oriented JS Patterns

## Return new object from function

```javascript
function createDog(name) {
  const obj = {};
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

## Object constructor

```javascript
const dog = Object();

dog.name = 'Tyson';
dog.howlName = function() {
  console.log('Hello my name is: ', this.name);
}
```
