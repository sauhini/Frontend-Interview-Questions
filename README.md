# FRONT-END INTERVIEW QUESTIONS :cowboy_hat_face:
There are some questions and answers which are asked repeatedly in various interviews. So, this is the best place to go through and revise things before going to attend any front-end interviews.
**Note: -** Please do not rely on these questions only, as mentioned above these are the pre-interview revision questions.
## JavaScript
### Differences between var, let and const? Output questions using var and const.
**Differences between var, let, and const**
1. **Scope:**
   - **var:** Function-scoped.
   - **let and const:** Block-scoped.
2. **Hoisting:**
   - **var:** Hoisted to the top of its scope and initialized with undefined.
   - **let and const:** Hoisted but not initialized.
3. **Reassignment:**
   - **var and let:** Can be reassigned.
   - **const:** Cannot be reassigned.
4. **Redeclaration:**
   - **var:** Can be redeclared within the same scope.
   - **let and const:** Cannot be redeclared within the same scope.

**Examples**
```
Using var:
function varExample() {
    console.log(x); // undefined (due to hoisting)
    var x = 10;
    console.log(x); // 10
}
varExample();
```
```
Using const:
function constExample() {
    const y = 20;
    console.log(y); // 20
    // y = 30; // Error: Assignment to constant variable.
}
constExample();
```

### Explain scopes in Javascript?
**Scopes in JavaScript**

In JavaScript, scope determines the accessibility (visibility) of variables and functions. There are three main types of scope:

- **Global Scope:**

   - Variables declared outside any function or block are in the global scope.
   - These variables can be accessed from anywhere in the code.
```
var globalVar = "I am global";
function example() {
    console.log(globalVar); // Accessible
}
example();
console.log(globalVar); // Accessible
```
- **Function Scope:**

   - Variables declared within a function are in the function scope.
   - These variables are only accessible within that function.
```
function example() {
    var functionVar = "I am local to the function";
    console.log(functionVar); // Accessible
}
example();
console.log(functionVar); // Error: functionVar is not defined
```
- **Block Scope:**

   - Variables declared with let or const within a block (e.g., inside {}) are in the block scope.
   - These variables are only accessible within that block.
```
{
    let blockVar = "I am block-scoped";
    console.log(blockVar); // Accessible
}
console.log(blockVar); // Error: blockVar is not defined
```
**Scope Chain**

When a variable is accessed, JavaScript looks for it in the current scope. If not found, it moves up to the next outer scope, continuing until it reaches the global scope. This is known as the scope chain.

**Lexical Scope**

JavaScript uses lexical scoping, meaning the scope of a variable is determined by its position in the source code. Nested functions have access to variables declared in their outer scope.

Example of Scope Chain
```
var globalVar = "global";

function outerFunction() {
    var outerVar = "outer";
    
    function innerFunction() {
        var innerVar = "inner";
        console.log(globalVar); // Accessible
        console.log(outerVar);  // Accessible
        console.log(innerVar);  // Accessible
    }
    
    innerFunction();
    console.log(innerVar); // Error: innerVar is not defined
}

outerFunction();
```
Understanding scopes helps in managing variable accessibility and avoiding conflicts in your code.

### What do you understand by an instance variable and a local variable?
**Instance Variable vs. Local Variable**

**Instance Variable**

- **Definition:** An instance variable is declared within a class but outside any method. It is associated with an instance of the class.
- **Scope:** Accessible to all methods in the class.
- **Lifespan:** Exists as long as the object of the class exists.

Example:
```
class Car {
    constructor(brand) {
        this.brand = brand; // Instance variable
    }

    displayBrand() {
        console.log(this.brand); // Accessible here
    }
}

let myCar = new Car("Toyota");
myCar.displayBrand(); // Outputs: Toyota
```
**Local Variable**

- **Definition:** A local variable is declared within a method or a block of code and is only accessible within that specific method or block.
- **Scope:** Limited to the method or block in which it is declared.
- **Lifespan:** Exists only during the execution of the method or block.

Example:
```
function showCar() {
    let carName = "Honda"; // Local variable
    console.log(carName); // Accessible here
}

showCar(); // Outputs: Honda
console.log(carName); // Error: carName is not defined
```
In summary, instance variables are tied to the objects of a class and have a broader scope within the class, while local variables are confined to the method or block where they are declared.

### what is a Closure and their  benefits and drawback. Give one realtime scenario where we can use it ?
**What is a Closure?**

A closure in JavaScript is a function that retains access to its lexical scope, even when the function is executed outside that scope. In simpler terms, a closure allows a function to access variables from an outer function even after the outer function has finished executing.

**Benefits of Closures**

1. **Encapsulation:** Closures allow you to create private variables that cannot be accessed from outside the function.
2. **Stateful Functions:** They enable functions to maintain state across multiple invocations.
3. **Modularity:** Closures help in organizing code into smaller, reusable modules.
4. **Memory Efficiency:** They can help manage memory by retaining only the necessary variables.

**Drawbacks of Closures**

1. **Memory Overhead:** Closures can increase memory usage because they keep references to outer scope variables.
2. **Debugging Difficulty:** It can be challenging to debug closures due to their complex scope chains.
3. **Potential Memory Leaks:** If not managed properly, closures can lead to memory leaks by holding onto references that are no longer needed.
4. **Performance Issues:** Heavy use of closures can sometimes lead to slower code execution.
   
**Real-time Scenario:** Creating a Counter

A common real-time use case for closures is creating a counter function that maintains its count across multiple calls.
```
function createCounter() {
    let count = 0; // Private variable

    return function() {
        count += 1;
        return count;
    };
}

const counter = createCounter();

console.log(counter()); // Outputs: 1
console.log(counter()); // Outputs: 2
console.log(counter()); // Outputs: 3
```
In this example, the createCounter function returns a closure that has access to the count variable. Each time the returned function is called, it increments and returns the updated count, demonstrating how closures can maintain state.

### How do you update values of the array     const arr = [1,2,5];
You can update the values of an array declared with const because const only prevents reassignment of the variable itself, not the mutation of the array's contents. Here are a few ways to update the values in the array const arr = [1, 2, 5];:

**1. Direct Assignment**

You can directly assign new values to specific indices of the array.
```
const arr = [1, 2, 5];
arr[2] = 3; // Update the third element
console.log(arr); // Outputs: [1, 2, 3]
```
**2. Using Array Methods**
You can use various array methods to update the array.

push (**adds elements to the end**):
```
const arr = [1, 2, 5];
arr.push(4); // Adds 4 to the end
console.log(arr); // Outputs: [1, 2, 5, 4]
```
pop (**removes the last element**):
```
const arr = [1, 2, 5];
arr.pop(); // Removes the last element
console.log(arr); // Outputs: [1, 2]
```
splice (**adds/removes elements at specific indices**):
```
const arr = [1, 2, 5];
arr.splice(2, 1, 3); // Removes 1 element at index 2 and adds 3
console.log(arr); // Outputs: [1, 2, 3]
```
3. Using map to Create a New Array
   
If you need to update all elements based on a condition, you can use map to create a new array.
```
const arr = [1, 2, 5];
const newArr = arr.map(num => num === 5 ? 3 : num); // Replace 5 with 3
console.log(newArr); // Outputs: [1, 2, 3]
```
These methods allow you to update the values within the array while keeping the array itself constant.

### find the element in array (big o notation )

**Finding an Element in an Array: Big O Notation**

When finding an element in an array, the time complexity depends on the method used:

**1. Linear Search:**

- Description: Checks each element one by one until the desired element is found or the end of the array is reached.
- Big O Notation: O(n), where n is the number of elements in the array.
- Example:
     ```
      function linearSearch(arr, target) {
          for (let i = 0; i < arr.length; i++) {
              if (arr[i] === target) {
                  return i; // Element found
              }
          }
          return -1; // Element not found
      }
   
      const arr = [1, 2, 3, 4, 5];
      console.log(linearSearch(arr, 3)); // Outputs: 2
     ```

**Binary Search (for sorted arrays):**
- Description: Repeatedly divides the search interval in half. Starts with the middle element and eliminates half of the remaining elements each time.
- Big O Notation: O(logn), where n is the number of elements in the array.
- Example:
    ```
      function binarySearch(arr, target) {
          let left = 0;
          let right = arr.length - 1;
      
          while (left <= right) {
              const mid = Math.floor((left + right) / 2);
      
              if (arr[mid] === target) {
                  return mid; // Element found
              } else if (arr[mid] < target) {
                  left = mid + 1;
              } else {
                  right = mid - 1;
              }
          }
          return -1; // Element not found
      }
      
      const sortedArr = [1, 2, 3, 4, 5];
      console.log(binarySearch(sortedArr, 3)); // Outputs: 2
   ```
**Summary**

   **- Linear Search: O(n)** - Suitable for unsorted arrays or when the array is small.
   
   **- Binary Search: O(log n)** - Efficient for large, sorted arrays.

### array = [2,5,7,8,3,9,1] :- maximum difference between array elements of those  --- asked the approach

Here's a JavaScript implementation of the approach:
```
function findMaxDifference(arr) {
    if (arr.length < 2) return 0; // Edge case: Not enough elements

    let minElement = arr[0];
    let maxDifference = arr[1] - arr[0];

    for (let i = 1; i < arr.length; i++) {
        if (arr[i] - minElement > maxDifference) {
            maxDifference = arr[i] - minElement;
        }
        if (arr[i] < minElement) {
            minElement = arr[i];
        }
    }

    return maxDifference;
}

const arr = [2, 5, 7, 8, 3, 9, 1];
console.log(findMaxDifference(arr)); // Outputs: 7 (difference between 9 and 2)
```

**Time Complexity**

- Time Complexity: O(n), where n is the number of elements in the array. This is because we only traverse the array once.
- Space Complexity: O(1), as we are using a constant amount of extra space.

### Remove duplicates in a given array

You can remove duplicates from an array in JavaScript using several methods. Here are a few common approaches:

**1. Using a Set**
   
A Set is a collection of unique values. You can convert the array to a Set and then back to an array.
```
const arr = [2, 5, 7, 8, 3, 9, 1, 2, 5];
const uniqueArr = [...new Set(arr)];
console.log(uniqueArr); // Outputs: [2, 5, 7, 8, 3, 9, 1]
```

**2. Using filter and indexOf**
   
You can use the filter method to include only elements whose index matches their first occurrence in the array.
```
const arr = [2, 5, 7, 8, 3, 9, 1, 2, 5];
const uniqueArr = arr.filter((value, index) => arr.indexOf(value) === index);
console.log(uniqueArr); // Outputs: [2, 5, 7, 8, 3, 9, 1]
```

**3. Using reduce and includes**
   
You can use the reduce method to build a new array that includes only unique elements.
```
const arr = [2, 5, 7, 8, 3, 9, 1, 2, 5];
const uniqueArr = arr.reduce((acc, value) => {
    if (!acc.includes(value)) {
        acc.push(value);
    }
    return acc;
}, []);
console.log(uniqueArr); // Outputs: [2, 5, 7, 8, 3, 9, 1]
```

**4. Using forEach and includes**
   
You can iterate over the array and add elements to a new array only if they are not already present.
```
const arr = [2, 5, 7, 8, 3, 9, 1, 2, 5];
const uniqueArr = [];
arr.forEach(value => {
    if (!uniqueArr.includes(value)) {
        uniqueArr.push(value);
    }
});
console.log(uniqueArr); // Outputs: [2, 5, 7, 8, 3, 9, 1]
```

These methods will help you remove duplicates from an array efficiently.

### write a program to check the number of occurrence of a character of a string

```
function countOccurrences(str, char) {
    let count = 0;
    for (let i = 0; i < str.length; i++) {
        if (str[i] === char) {
            count++;
        }
    }
    return count;
}

const string = "hello world";
const character = "o";
const result = countOccurrences(string, character);
console.log(`The character '${character}' occurs ${result} times in the string "${string}".`);
// Outputs: The character 'o' occurs 2 times in the string "hello world".
```

### Write the code for palindrome and check whether string "abccba" is a palindrome or not

```
function isPalindrome(str) {
    // Remove non-alphanumeric characters and convert to lowercase
    const cleanedStr = str.replace(/[^a-zA-Z0-9]/g, '').toLowerCase();
    // Compare the string with its reversed version
    return cleanedStr === cleanedStr.split('').reverse().join('');
}

const testString = "abccba";
const result = isPalindrome(testString);
console.log(`The string "${testString}" is ${result ? '' : 'not '}a palindrome.`);
// Outputs: The string "abccba" is a palindrome.
```

