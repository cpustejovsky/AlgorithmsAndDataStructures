# Big O Notation

![Big O Notation Chart](images/big-o-chart.png)

## Why Does it matter?

- Provides devs with precise grammar to talk about code performance
  - This helps clarify trade-offs between different approaches
- Knowing how to talk about performance will help identify and notify others about code ineficiencies that may be acting as pain points
- **basically, it provides an objective way to talk about what code is "better" at least from one point of view**
  - We're not going to have a common grammar for readability, brevity, etc., but Big O will allow us one for speed and memory use

## Big O Shorthands

1. Arithmetic and assignment operations are contanst
2. Accessing element of array is also constant
3. For loops, loop.length \* operationsInsideLoop

**auxilary space complexity:** the space required by the algorithm, not including space taken up by inputs.

# Problem Solving

## How to improve problem solving skills

1. Devise a plan for solving problems
2. Master common problem solving patterns (muscle memory)

# Problem Solving Strategy

## 1. Understand the Problem

- Can I restate the question/problem?
- What are the inputs that go into the problems?
- What are the outputs?
- Can the inputs determine the outputs? Do I have enough information (may have to circle back to later)
- How should I label this problem's important pieces of data?

## 2. Explore Concrete Examples

- Start with simple examples
- Progress to more complex exmaples
- Explore examples with empty inputs
- Explore examples with invalid inputs

## 3. Break it down (process is important!)

- Explicitly write out the steps you need to take
- Force yourself to think about the code you'll write
- Catch any lingering conceptual issues or misunderstandings before you dive in

## 4. Solve/Simplify

- If you can't solve the problem, solve a simply problem
- Break problem down to create simpler problem
- Example:
  - Find how to do it for one iteration, then loop it
  - If you don't know something, mention it, account for it, move on, and ignore it (what specific method name to use, etc.)

## 5. Look back and refactor

- Connect the dots, then draw the image you've created with connecting dots. Once you realize it's a penguin, draw the penguin.
- In interview, talk about what you don't like (readability, efficiency, etc.) and how you'd refactor
- Refactoring Questions
  - Can you check the result?
  - Can you get that result a different way?
  - Can you understand the code at a glance? How much time does it take to reason about the code?
  - Is this code re-usable?
  - Can you improve the performance?
  - Are there any other ways to refactor?
  - How have others solved this problem? (Stack Overflow for real world; other applicants/interviewees in the interview context)

# Problem Solving Patterns

## Frequency Counter Pattern

- Uses objects or set to collect values or frequencies of values.
- Often avoids nested loops and results in O(n) time instead of O(n^2)

### Example

```javascript
const validAnagram = (x, y) => {
  if (x.length !== y.length) return false;
  let xCounter = {};
  let yCounter = {};
  y.split("").forEach((letter) => {
    yCounter[letter] ? (yCounter[letter] += 1) : (yCounter[letter] = 1);
  });
  x.split("").forEach((letter) => {
    xCounter[letter] ? (xCounter[letter] += 1) : (xCounter[letter] = 1);
  });
  for (let key in xCounter) {
    if (xCounter[key] !== yCounter[key]) return false;
  }
  return true;
};
validAnagram("anagram", "nagaram"); //true
validAnagram("awesome", "awesom"); //false
```

## Multiple Pointers Pattern

- Creating pointer or values that correspond to an index or position and move towards the beginning, end, or middle based on a certain condition.
- Uses a loop or recursion. The point is to avoid nested loop or O(n^2) complexity

### Example

```javascript
const sumZero = (arr) => {
  if (arr.length < 2) {
    result = "No sums";
    return result;
  }
  let [first, ...rest] = arr;
  if (first + rest[rest.length - 1] === 0) {
    result = [first, rest[rest.length - 1]];
  } else {
    rest.pop();
    sumZero(rest);
  }
  return result;
};

sumZero([-3, -2, -1, 0, 1, 2, 3]); //[-3,3]
sumZero([-3, -2, -1, 0, 1, 2, 4]); //[-2,2]
sumZero([-3, -2, -1, 0, 3, 4, 5]); //"No sums"
```

## Sliding Window Pattern

- This pattern involves creating a window
  - either an array or a number that moves from one position to anther
- Depending on \_\_ condition, window will either increase or closed and create a new window
- Useful for tracking a subset of data in an array, string, etc.

### Example

```javascript
const maxSubarraySum = (arr, num) => {
  let maxSum = 0;
  //checks if array is at least the size of the number of elements to add together
  if (arr.length < num) return null;
  //adds up the first window of numbers
  for (let i = 0; i < num; i++) {
    maxSum += arr[i];
  }
  //sets up tempSum as maxSum
  let tempSum = maxSum;
  //starting at i = num (where previous loop left off), loops through array
  for (let i = num; i < arr.length; i++) {
    //sets adds next element to tempSum and subtracts previous element
    tempSum = tempSum - arr[i - num] + arr[i];
    //compare total
    maxSum = Math.max(maxSum, tempSum);
  }
  return maxSum;
};

maxSubarraySum([2, 6, 9, 2, 1, 8, 5, 6, 3], 3); // 19
```

## Divide and Conquer

- This pattern involves dividing a data set into smaller chunks and then repeating a process with a subset of data.
- Steps:
  1.  Figure out base case
  2.  Divide || Decrease problem until it becomes base case
- For an array, base case is usually `[]`
- How to Quicksort
  1. Pick a pivot
  2. Partition the array into 2 subarrays (elements < pivot, pivot, elements > pivot)
  3. Call quicksort recursively on subarrays

## Recursion

- You make sure you have a base case, you return the right thing, and you call the function until you give it. (see above example for recursion)

### example

```javascript
const factorial = (num) => (num === 0 ? 1 : num * factorial(num - 1));

factorial(1); // 1
factorial(2); // 2
factorial(3); // 6
factorial(4); // 24
factorial(5); // 120
factorial(6); // 720
factorial(7); // 5040
```
