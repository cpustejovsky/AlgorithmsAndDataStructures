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
3. For loops, loop.length * operationsInsideLoop
   
**auxilary space complexity:** the space required by the algorithm, not including space taken up by inputs.



# Problem Solving
## How to improve problem solving skills
1. Devise a plan for solving problems
2. Master common problem solving patterns (muscle memory)

# Problem Solving Strategy
## 1. Understand the Problem
* Can I restate the question/problem?
* What are the inputs that go into the problems?
* What are the outputs?
* Can the inputs determine the outputs? Do I have enough information (may have to circle back to later)
* How should I label this problem's important pieces of data?
## 2. Explore Concrete Examples
* Start with simple examples
* Progress to more complex exmaples
* Explore examples with empty inputs
* Explore examples with invalid inputs
## 3. Break it down (process is important!)
* Explicitly write out the steps you need to take
* Force yourself to think about the code you'll write
* Catch any lingering conceptual issues or misunderstandings before you dive in
## 4. Solve/Simplify
* If you can't solve the problem, solve a simply problem
* Break problem down to create simpler problem
* Example:
  * Find how to do it for one iteration, then loop it
  * If you don't know something, mention it, account for it, move on, and ignore it (what specific method name to use, etc.)
## 5. Look back and refactor
* Connect the dots, then draw the image you've created with connecting dots. Once you realize it's a penguin, draw the penguin.
* In interview, talk about what you don't like (readability, efficiency, etc.) and how you'd refactor
* Refactoring Questions
  * Can you check the result?
  * Can you get that result a different way?
  * Can you understand the code at a glance? How much time does it take to reason about the code?
  * Is this code re-usable?
  * Can you improve the performance?
  * Are there any other ways to refactor?
  * How have others solved this problem? (Stack Overflow for real world; other applicants/interviewees in the interview context)

# Problem Solving Patterns
## Frequency Counter Pattern
* Uses objects or set to collect values or frequencies of values.
* Often avoids nested loops and results in O(n) time instead of O(n^2)
### Example
```javascript
const validAnagram = (x, y) => {
  if(x.length !== y.length) return false
  let xCounter = {};
  let yCounter = {};
  y.split("").forEach((letter) => {
    yCounter[letter] ? yCounter[letter] += 1: yCounter[letter] = 1;
  });
  x.split("").forEach((letter) => {
    xCounter[letter] ? xCounter[letter] += 1: xCounter[letter] = 1;
  });
  for(let key in xCounter){
    if(xCounter[key] !== yCounter[key]) return false
  }
  return true
};
validAnagram("anagram", "nagaram"); //true
validAnagram("awesome", "awesom"); //false
```

