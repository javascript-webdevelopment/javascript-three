# Javascript Three

In this lecture we go over array methods, gain a better understanding with objects, learn the spread operator, and use nested for loops.

## Arrow Functions

Arrow functions are another way we can write a function. I personally prefer using arrow functions because I believe it's cleaner syntax and more modern.

```javascript
// function declaration
function myFunc(){
    // logic here
};

// function expression
const myFunc = function(){
    // logic here
};

// arrow function
const myFunc = () => {
    // logic here
};
```

Notice how we don't use the keyword `function` and that we also use an `=>`.

If we single line the logic of our arrow function, we do not need to use the keyword `return`.

```javascript
function sayName(name){
    return name;
}

// now lets turn it into an arrow function
const sayName = (name) => name;
```

## Array Methods

Array methods are built in functions that we can execute on an `Array` datatype. 

### For Each

`.forEach()` accepts a callback function as an argument and executes that callback function for each element in an array.

```javascript
 const myArray = [1,2,3,4,5];

 myArray.forEach(function(element, index, array){
     console.log(element);
 });

//  Result:
// 1
// 2
// 3
// 4
// 5
```

Syntax:

```javascript
.forEach(function(element, index, array){
    // the logic to execute on each element in the array
})
```

The callback functions has three parameters by default:

`element` - this is the current element that us being processed in the array and is required

`index` - this is an optional parameter we can set, but this is the index value for the current element being processed in th array.

`array` - this is the current array being processed. So in the example above, array would be `myArray`

This array method does not have a return value.

### Map

`.map()` accepts a callback function as an argument and executes that function for every element on the array. However, map returns a new array with the results of that callback function execution.

```javascript
const myArray = [1,2,3,4,5];

let mappedArray = myArray.map(function(element, index, array){
    return element + 2;
});

console.log(mappedArray) // result: [3,4,5,6,7];
```

Syntax:

```javascript
.map(function(element, index, array){
    // the logic performed on each element in the array that is returned into a new array
});
```

`element` - this is the current element that us being processed in the array and is required

`index` - this is an optional parameter we can set, but this is the index value for the current element being processed in th array.

`array` - this is the current array being processed. So in the example above, array would be `myArray`

Map will return the results of the callback function into a new array so we will store that new array into a variable.

### Filter

`.filter()` accepts a callback function as an argument and executes the function on each element in the array. Filter creates a new array with the results from the callback function. The callback function will test for a condition and only return the result into the new array if it only passes the condition.

```javascript
const myArray = [1,2,3,4,5];

let filteredArray = myArray.filter(function(element, index, array){
    return element % 2 === 0;
});

console.log(filteredArray); // result: [2,4];
```

Syntax:

```javascript
.filter(function(element, index, array){
    // logic to filter elements into a new array
});
```

`element` - this is the current element that us being processed in the array and is required

`index` - this is an optional parameter we can set, but this is the index value for the current element being processed in th array.

`array` - this is the current array being processed. So in the example above, array would be `myArray`

The callback function will check for a specific condition, and only return the elements that pass that condition into the new array.

### Reduce

`.reduce()` executes a reducer function (we pass this as a callback) on each element in an array and returns a single value.

```javascript
const myArray = [1,2,3,4,5];

let reducedValue = myArray.reduce(function(accum, element, index, array){
    return accum + element;
});

console.log(reducedValue) // result: 15
```

Syntax:

```javascript
.reduce(function(accum, element, index, array){
    // logic to accumulate 
}, initialValue);
```

`accum` - this is the accumlator, it accumulates the value return from the previous callback

`element` - this is the current element that us being processed in the array and is required

`index` - this is an optional parameter we can set, but this is the index value for the current element being processed in th array.

`array` - this is the current array being processed. So in the example above, array would be `myArray`

`initialValue` - this will be whatever we decide the accumulater to start as, if nothing is provided the accumulater starts as the first item in the array.

The reduce function will return a single value that results from the callback function being executed.

## Objects

### Deleting Properties

We can use the `delete` statement to remove a property from an object.

```javascript
const myCar = {
    make: 'tesla',
    model: 'model x'
};

delete myCar.model;

console.log(myCar) // result: {make: 'tesla'};
```

It's important to note that `delete` only remove propeties and their values not the object itself.

### Looping Through Objects

We can loop through objects to access their key/value  by using a `for in` loop.

```javascript
const myCar = {
    make: 'tesla',
    model: 'model x'
};

for(let key in myCar){
    console.log(key)
}

// result:
// make
// model
```

The `key` in the loop can be used to reference the property name.

### Copying An Object

```javascript
const myCar = {
    make: 'tesla',
    model: 'model x'
};

const newCar = myCar;

delete newCar.make;

console.log(myCar) // result: {model: 'model x'};
```

Notice how deleting the make property from `newCar` it actually removes it from `myCar`. This is because when we assign an object to another variable, that variable acts like a point to the actual object that's in memory. To avoid this, we need to create a whole new object.

`Object.assign()` - this is the function we can run to create a new object from another object.

```javascript
const myCar = {
    make: 'tesla',
    model: 'model x'
};

const newCarObj = Object.assign({}, myCar);

delete newCarObj.make;

console.log(myCar) // result {make: 'tesla', model: 'model x'};
```

We pass in the objects we want to copy from into the `Object.assign()` function.

Now when we delete the property from `newCarObj`, since it is a brand new object, it removes it only from that object and `myCar` is not mutated in any way.

### Object Destructering

Object destructering can be used to pull preoperties off of an object and store them independently in a variable.

```javascript
const myCar = {
    make: 'tesla',
    model: 'model x'
};

// destructering
const {make, model} = myCar;

// we can now access those properties as independent variables
console.log(make) // 'tesla'
console.log(model) // 'model x'
```

Notice that we use the `{}` to destructer from an object. I like to think about this as the curly braces are hands are they are just grabbing properties off of the object.

### Spread Operator

The spread operator can be used to copy values from an array into a new array or key/value pairs from an object to another object.

```javascript
const candies = ['shockers', 'sprees', 'nerds rope'];

const newCandiesArray = [...candies]
```

Above we are creating a new variable to store the new array. Inside of the square brackets, we prefx the variable `candies` with the spread operator `...`. This pretty much takes all of the elements from `candies` and puts them in the `newCandiesArray`.

We can also spread the properties from an object to a new object.

```javascript
const myCar = {
    make: 'tesla',
    model: 'model x'
};

const newCar = {...myCar};
```

Notice how it's almost the same exact syntax as doing it with the array, but this time we are speading the key/values pair into a set of curly bracres or `object literals`.

#### Spread Operator In Function Argument

The `rest parameter syntax` is what is known as using the spread operator in the arguments of a function, this allows us to represent an indefinite number of arguments as an array.

```javascript
function myFunc(...args){
    console.log(args);
}

myFunc();

// result:
// [*,*,*] the array will be filled with however many args that we throw in.
```

It's important to note that it will put all arguments into an array when using the rest parameter syntax.

### Nested Data

Nested data in javascript is when we have objects inside of objects, arrays inside of array, objects inside of arrays,or arrays inside of objects, and etc.

We can use nested loops to access nested data.


`Nested For Loop`

```javascript
let nestedArrays = [[1,2], [3,4], [5,6]];

for(let i = 0; i < nestedArrays.length; i++){
    // nested loop, this will loop through the array at the current index value
    for(let j = 0; j < nestedArrays[i].length; j++){
        // this time we create another variable as a counter and use bracket notation to access the nested array
        console.log(i,j)
    }
}
```

`Nested For In`

```javascript
const people = {
    tayte: {
        favCandy: 'shockers'
    },
    matt: {
        favCandy: 'kitkat'
    },
    catie: {
        favCandy: 'n/a'
    }
};

for(let person in people){
    // nested for in loop
    for(let candy in people[person]){
        console.log(people[person][candy]);
    }
};
```