# Pure Function

Given same input, always same output expected

```javascript
function increment(obj) {
	return obj.count++;
} 

const obj = {count: 2};
increment(obj); // 2
increment(obj); // 3
increment(obj); // 4
```

How to make it pure....

```javascript
function increment(obj) {
	return {count: obj.count + 1};
} 

const obj = {count: 2};
increment(obj); // 3
increment(obj); // 3
increment(obj); // 3
```

** Reducer approach to deal with pure function **

```javascript
function reducer(state, action) {
	switch(action.type) {
		case: 'INCREMENT':
			return {count: state.count + 1};
	}
}
```

Benefits- 

	- Easy testibility (just call function directly, not need of mock obj)
	- Easy undo/redo ( as we not destroying prev state )
	- debugging

# Immutability

An immutable object is an object whose state can not be changed after creation

## Why immutability

- predictability
- performance 
- undo/redo changes

## Mutability in Javascript

These are immutable by design.

- Object
- Array
- Function

```javascript
const o = {name: 'John'};
o.age = 20;

console.log(o); // {name: 'John', age: 20}

const arr = [1, 2];
arr.push(10);

console.log(arr); // [1, 2, 10]
```

How to make Object/Array immutable?

```javascript
// Object iimutability
const o = {name: 'John'};
const o1 = Object.assign({}, o, { age: 20});
const o2 = {...o, age: 20}; // ES6
console.log(o); // {name: 'John'}

// Array iimutability
const arr = [1, 2];
const myarr = [...arr, 10]; // [1, 2, 10]
console.log(arr); // [1, 2]
```

## Immutability in Javascript

- String
- Number

```javascript
const s = 'Hemant';
s.toUpperCase(); // HEMANT
console.log(s); // Hemant
```





