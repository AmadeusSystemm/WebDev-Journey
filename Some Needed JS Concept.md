- it is expected to have some basic knowledge of JavaScript already.
## Callbacks
- apparently its just like recursion where a function can call itself 
## Promises

- ![[Pasted image 20240630235237.png]]
- so promise with .then is basically the above cycle
- for async await syntax and a little recap watch this youtube to jog your memory
- https://youtu.be/1Z7FjG--F20?si=gwY15OWUkkhObCOM

## Assignments Week -1

1)
  ```
```Write a function `isAnagram` which takes 2 parameters and returns true/false if those are anagrams or not.
  What's Anagram?
  - A word, phrase, or name formed by rearranging the letters of another, such as spar, formed from rasp.

```

```js
function isAnagram(str1,str2){
	if (str1.length !== str2.length){
	return false;	
	elseif(str1.toLowerCase().sort()!==str2.toLowerCase().sort()){
	return false;
		}
	}	
	else{
	return true;
	}
}

```

2)
```
  Implement a function `calculateTotalSpentByCategory` which takes a list of transactions as parameter
  and return a list of objects where each object is unique category-wise and has total price spent as its value.
  transactions is an array where each
  Transaction - an object like 
        {
		id: 1,
		timestamp: 1656076800000,
		price: 10,
		category: 'Food',
		itemName: 'Pizza',
	}
  Output - [{ category: 'Food', totalSpent: 10 }] // Can have multiple categories, only one example is mentioned here

```

```js
function calculateTotalSpentByCategory(transactions){
	let finalTotal=[];
	transactions.forEach(()=>{
		const thing1 = transaction.category;
		const price = transaction.price;
		finalTotal.push(`category:${thing}`,`totalSpent:${price}`)
	})
}
```
3)
```
  Write a function `findLargestElement` that takes an array of numbers and returns the largest element.
  Example:
  - Input: [3, 7, 2, 9, 1]
  - Output: 9
```

```js

function findLargestElement(numbers) {
    let largest = 0;
    for(let i = 0; i < numbers.length; i++) {
        if(numbers[i] > largest) {
            largest = numbers[i];
        }
    }
    return largest;
}

```

## Mediums

1)
```/*
  Implement a function `countVowels` that takes a string as an argument and returns the number of vowels in the string.
  Note: Consider both uppercase and lowercase vowels ('a', 'e', 'i', 'o', 'u').

  Once you've implemented the logic, test your code by running
    
  To Run file -> PS C:\Users\chand\Desktop\100xdevs_2.0\0-1\week1\assignments\mediun> npx jest ./tests/countVowels.test.js

  */
```

```js
function findVowels(strings){
	vowels ='aAeEiIoOuU';
	count=0;
	for(let i =0 ; i < strings.length;i++){
	if(strings.indexOf(strings[i])!==1){
		count++;
		}
	}
}
```

2)
```
  Implement a function `isPalindrome` which takes a string as argument and returns true/false as its result.
  Note: the input string is case-insensitive which means 'Nan' is a palindrom as 'N' and 'n' are considered case-insensitive.

```

```js
function isPalindrome(str) {

    let j = str.length - 1;
    for (let i = 0; i < str.length / 2; i++) {

        if (str[i] != str[j]) {

            return false;

        }

        j--;

    }

    return true;

}
```

3)
```/*
Write a function that calculates the time (in seconds) it takes for the JS code to calculate sum from 1 to n, given n as the input.
Try running it for
1. Sum from 1-100
2. Sum from 1-100000
3. Sum from 1-1000000000
Hint - use Date class exposed in JS
There is no automated test for this one, this is more for you to understand time goes up as computation goes up
*/
```

```js

function calculateTime(n) {
    let x = 0;
    for(let i=0; i<=n; i++) {
        x += i;
    }
    return x;    
}
const beforeDate = new Date();
const beforeTimeinMs = beforeDate.getTime();
calculateTime(1000000000);
const afterDate = new Date();
const afterTimeinMs = afterDate.getTime();

console.log(afterTimeinMs - beforeTimeinMs);
```

## hard

1)
```/*
  Implement a class `Calculator` having below methods
    - initialise a result variable in the constructor and keep updating it after every arithmetic operation
    - add: takes a number and adds it to the result
    - subtract: takes a number and subtracts it from the result
    - multiply: takes a number and multiply it to the result
    - divide: takes a number and divide it to the result
    - clear: makes the `result` variable to 0
    - getResult: returns the value of `result` variable
    - calculate: takes a string expression which can take multi-arithmetic operations and give its result
      example input: `10 +   2 *    (   6 - (4 + 1) / 2) + 7`
      Points to Note: 
        1. the input can have multiple continuous spaces, you're supposed to avoid them and parse the expression correctly
        2. the input can have invalid non-numerical characters like `5 + abc`, you're supposed to throw error for such inputs

  Once you've implemented the logic, test your code by running
*/

```

```js
class Calculator {
  // initialise a result variable in the constructor and keep updating it after every arithmetic operation
  constructor() {
    this.result = 0;
  }

  add(num) {
    this.result += num;
  }
  subtract(num) {
    this.result -= num;
  }
  multiply(num) {
    this.result *= num;
  }
  divide(num) {
    if(num === 0) {
      throw new Error('Cannot divide by zero');
    }
    this.result /= num;
  }
  clear() {
    this.result = 0;
  }
  getResult() {
    return this.result;
  }
  calculate(e){
    // Evaluates the expression and stores the result in this.result
    try{
      this.result = eval(e);
    }catch(err){
      throw new Error('Invalid expression');
    }
    // Throws error if result is Infinity
    if(this.result === Infinity){
      throw new Error('Invalid expression');
    }
    this.result = Math.round(this.result * 100) / 100;
    return this.result;
  }
	//must retry this as i easily forget.
}

```

2)
```/*
  Implement a class `Todo` having below methods
    - add(todo): adds todo to list of todos
    - remove(indexOfTodo): remove todo from list of todos
    - update(index, updatedTodo): update todo at given index
    - getAll: returns all todos
    - get(indexOfTodo): returns todo at given index
    - clear: deletes all todos

  Once you've implemented the logic, test your code by running
*/
```

```js
class Todo {
    constructor() {
        this.todos = [];
    }
    add(todo) {
        this.todos.push(todo);
    }

    remove(indexOfTodo) {
      if(indexOfTodo < 0 || indexOfTodo >= this.todos.length){
        throw new Error('Invalid index');
        return
      }
      this.todos.splice(indexOfTodo, 1);
    }

    update(index, updatedTodo) {
      if(index < 0 || index >= this.todos.length){
         throw new Error('Invalid index');
        return
      }
      this.todos[index] = updatedTodo;
    }

    getAll() {
      return this.todos;
    }

    get(indexOfTodo) {
      if(indexOfTodo < 0 || indexOfTodo >= this.todos.length){
        // throw new Error('Invalid index');
        return null;
      }
      return this.todos[indexOfTodo];
    }

    clear() {
      this.todos = [];
    }
}

//must retry next weekend

```