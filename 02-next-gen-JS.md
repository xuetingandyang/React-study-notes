## Next Generation JavaScript

Before diving into React, it's important to make sure you're familiar with these concepts in next gen JS.

### Variables

- While `var` still works in ES6, you're encouraged to work with either `let` or `const`
- `let`: (like "new" "var") use it if you want to create a variable that really is a variable 
- `const`: (mostly cases) use it if you want to create a constant value, or something you create once and never change

### Arrow Functions

- Arrow functions look like this: 

	```javascript
	function myFunc() {
		...
	}

	const myFunc = () => {
		return something;
	}
	```
- If there's only one argument we could ommit the parentheses: 
	
	```javascript
	const myFunc  = name => {
		return console.log(name);
	}
	```
- If you have a function with no arguments or more than one argument - you must use parentheses:
	
	```javascript
	const myFunc = () => {
		return console.log('Hi!');
	}
	```
	
	```javascript
	const myFunc = (name, age) => {
		return console.log(name, age);
	}
	```
- If you **only have a return statement** inside your function you can ommit the curly braces and the return keyword:
	
	```javascript
	const multiply = number => number * 2;
	``` 

### Exports and Imports (Modules)
	
- The idea behind modules is that inside JS files we can `import` content from another file
- To access functionality in another file, you need to `export` it to make it available, and to also `import` it in another file to get access to it
- You can either export as default by using `export default ...;` or by a given name, like so: `export const myData = ... ;`. If we just export one thing from a file, this will be the default export. The named exports specifically target something in the file.
	- For Default export:
	```javascript
	import person from './person,js'
	import prs from './person.js'
	```
	- For named export:
	```javascript
	import { smith } from './utility,js'
	import {smith as Smth} from './utility.js'
	import * as bundled from './utility.js'
	```
- In the importing file, you'll need to add: `import nameOfMyChoice from `./path-to-file.js ;` when it's a default export 
- If it's a named export, we need to use the specific name in the file `import { smth } from './path-to-file.js';`. One workaround this is to write: `import { smth as myNameOfChoice } from './path-to-file.js';` . You can also import everyhing from the file using the `*` operator.

### Classes

- Classes are a feature which basically replace constructor
functions and prototypes
- Classes are used to define blueprints for JS objects
- Classes support inheritance
	- `class Person extends Master`
- Classes can include properties and methods 
- We create an instance of a class with the key word `new`
	```javascript
	class Person {
		constructor () {
			this.name = 'Michal';
		}
		printMyName() {
			console.log(this.name);
		}
	}
	const person = new Person();
	person.printMyName();
	```
- We can create another class which has a constructor, and if Person `extends` the class `human` we inherit its method 
	- (note that we also added `super()` to execute the parent constructor as well): 
	
	```javascript
	class Human {
		constructor () {
			this.gender = 'Female';
		}
		printGender() {
			console.log(this.gender);
		}
	}
	
	class Person extends Human {
		constructor () {
          super();
          this.name = 'Michal';
		}
		printMyName() {
			console.log(this.name);
		}
	}
	const person = new Person();
	person.printMyName();
	person.printGender();
	```
- We can skip the constructor function call, and this way not use the `this` keyword: 

	```javascript
	myMethod = () => {...}
	```
- Another thing we can ommit is the `super()` but we could only run this code using ES6/Babel to convert is to JSX: 

	```javascript
	class Human {
	    gender = 'Male';
	
	    printGender = () => {
	        console.log(this.gender);
	    }
	}
	
	class Person extends Human {
	    name = 'Michal';
	    gender= 'Female';
	
	    printMyName = () => {
	        console.log(this.name);
	    }
	}
	const person = new Person();
	person.printMyName();
	person.printGender();
	```

### Spread and Rest Operator
	
- The Spread operator `...` is used to split up array elements OR object properties

	```javascript
	const newArray = [...oldArray, 1, 2]
	const newObject = {...oldObject, newProp: 5}
	```

- The Rest operator `...` is used to merge a list of function arguments into an array: 

	```javascript
	function sortArgs(...args) {
		return args.sort();
	}
	```
	
### Destructuring

- Easily extracts array elements or object properties and store them in variables
- Why is this different from `spread`? Spread takes all elements / properties. Destructuring allows you to pull out single elements or properties, and store them in variables! For both arrays and objects
- Array destructuring: 

	```javascript
	[a, , c] = ['Hello', 'World', 'lala'];
	console.log(a); //Hello
	console.log(c); //lala
	```
- Object destructuring: 

	```javascript
	{name} = {name: 'Michal', location: 'London'};
	console.log(name); // Michal
	console.log(location); // undefined, since we did not pull out location here
	```

### Reference and Primitive Types

- Primitive types: numbers, strings, booleans 
	- reassign/copy the value
- Reference types: objects and arrays
	- reassign/copy the reference (point to SAME memory address)
	- To really copy, use spread operator `...`
	```javascript
	const person = {
		name: 'Max'
	};

	const secondPerson = {
		...person
	};

	```


### Refresh Array Functions
```javascript
const numbers = [1, 2, 3];
const doubleArray = numbers.map(num => num * 2);
```