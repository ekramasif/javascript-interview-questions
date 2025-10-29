# JavaScript Interview Problems Cheat Sheet: 60 Essential Coding Questions for 2025

> **Master JavaScript interviews with this comprehensive collection of 60 hand-picked coding problems, complete with solutions, time complexity analysis, and expert interview tips.**

---

## 📖 Introduction

Are you preparing for a **JavaScript developer interview** and feeling overwhelmed by the endless list of potential coding questions? You're not alone. Whether you're applying for a frontend developer, full-stack engineer, or Node.js position, mastering **JavaScript interview questions** is crucial for landing your dream job.

This ultimate **JavaScript coding interview cheat sheet** is designed for developers who want to:

✅ **Quickly review** the most commonly asked JavaScript coding problems  
✅ **Understand time complexity** and optimization techniques  
✅ **Learn what to say** during technical interviews to impress interviewers  
✅ **Practice essential patterns** in strings, arrays, algorithms, async/await, and more  

### Why This Guide?

Unlike typical coding question lists, each problem in this guide includes:

- **Clean, production-ready code** using modern ES6+ syntax
- **Interview tips** - exactly what to explain during your interview
- **Time and space complexity** analysis for every solution
- **Real-world applications** so you understand when to use each pattern

### Who Is This For?

- **Junior developers** preparing for their first technical interview
- **Mid-level engineers** brushing up on fundamentals
- **Career switchers** transitioning into web development
- **Self-taught programmers** without a CS degree

### What's Covered?

This comprehensive guide covers **60 JavaScript interview problems** across 8 categories:

🔤 **String Manipulation** - Reverse, palindrome, anagram detection  
📊 **Array Operations** - Two sum, rotation, flattening, chunking  
🧮 **Number Algorithms** - Fibonacci, prime numbers, factorials  
🎯 **Object Handling** - Deep clone, merge, nested access  
⚡ **Async/Promises** - Debounce, throttle, retry logic  
🔍 **Classic Algorithms** - Binary search, sorting, valid parentheses  
🎨 **Practical Utilities** - UUID generation, query parsers, formatters  
🏆 **Advanced Patterns** - Memoization, one-liners, performance optimization  

Each solution is optimized for **readability** and **interview performance**. We prioritize code that's easy to explain under pressure while demonstrating your understanding of JavaScript fundamentals.

### How to Use This Guide

1. **Read through each category** to familiarize yourself with common patterns
2. **Practice explaining** the solutions out loud as if in an interview
3. **Focus on time complexity** - interviewers love candidates who discuss Big O
4. **Memorize the "interview tips"** - these are gold for technical discussions
5. **Try solving problems** before looking at solutions to test your knowledge

### SEO Keywords

*JavaScript interview questions, coding interview preparation, frontend developer interview, JavaScript algorithms, web developer coding test, technical interview questions, JavaScript programming challenges, ES6 interview questions, coding patterns JavaScript, algorithm interview prep, JavaScript developer jobs 2025*

---

## 🔤 String Problems

### 1️⃣ Reverse a String
```javascript
const reverseString = str => [...str].reverse().join('');
console.log(reverseString("hello")); // "olleh"
```
**Interview tip:** "Use spread/reverse/join for O(n) time complexity."

---

### 2️⃣ Check Palindrome
```javascript
const isPalindrome = str => str === [...str].reverse().join('');
console.log(isPalindrome("racecar")); // true
console.log(isPalindrome("hello"));   // false
```
**Interview tip:** "Check if string reads same forwards and backwards."

---

### 3️⃣ Count Vowels
```javascript
const countVowels = str => (str.match(/[aeiou]/gi) || []).length;
console.log(countVowels("hello world")); // 3
```
**Interview tip:** "Use regex with match, handle null case with || []."

---

### 4️⃣ Capitalize First Letter
```javascript
const capitalize = str => str.charAt(0).toUpperCase() + str.slice(1);
console.log(capitalize("hello")); // "Hello"
```
**Interview tip:** "Use charAt(0) and slice(1) for clean solution."

---

### 5️⃣ Title Case
```javascript
const titleCase = str => str.split(' ').map(word => 
  word.charAt(0).toUpperCase() + word.slice(1).toLowerCase()
).join(' ');
console.log(titleCase("hello world")); // "Hello World"
```
**Interview tip:** "Split, map each word, capitalize first letter, join back."

---

### 6️⃣ Remove Duplicates from String
```javascript
const removeDuplicates = str => [...new Set(str)].join('');
console.log(removeDuplicates("hello")); // "helo"
```
**Interview tip:** "Use Set for O(n) deduplication, spread back to array."

---

### 7️⃣ Longest Word
```javascript
const longestWord = str => str.split(' ').reduce((longest, word) => 
  word.length > longest.length ? word : longest, ''
);
console.log(longestWord("The quick brown fox")); // "quick"
```
**Interview tip:** "Split and reduce to find maximum length word."

---

### 8️⃣ Check Anagram
```javascript
const isAnagram = (str1, str2) => {
  const normalize = str => str.toLowerCase().split('').sort().join('');
  return normalize(str1) === normalize(str2);
};
console.log(isAnagram("listen", "silent")); // true
```
**Interview tip:** "Sort both strings and compare. O(n log n) time."

---

## 📊 Array Problems

### 9️⃣ Remove Duplicates from Array
```javascript
const removeDuplicates = arr => [...new Set(arr)];
console.log(removeDuplicates([1, 2, 2, 3, 4, 4])); // [1, 2, 3, 4]
```
**Interview tip:** "Set automatically removes duplicates, O(n) time."

---

### 🔟 Find Maximum Number
```javascript
const findMax = arr => Math.max(...arr);
console.log(findMax([1, 5, 3, 9, 2])); // 9
```
**Interview tip:** "Use Math.max with spread operator for simplicity."

---

### 1️⃣1️⃣ Sum of Array
```javascript
const sum = arr => arr.reduce((acc, num) => acc + num, 0);
console.log(sum([1, 2, 3, 4])); // 10
```
**Interview tip:** "Reduce is perfect for accumulation, start with 0."

---

### 1️⃣2️⃣ Flatten Array
```javascript
const flatten = arr => arr.flat(Infinity);
console.log(flatten([1, [2, [3, [4]]]])); // [1, 2, 3, 4]

// Recursive approach
const flattenRecursive = arr => arr.reduce((acc, val) => 
  Array.isArray(val) ? acc.concat(flattenRecursive(val)) : acc.concat(val), []
);
```
**Interview tip:** "Use flat(Infinity) or recursive reduce. Explain both."

---

### 1️⃣3️⃣ Chunk Array
```javascript
const chunk = (arr, size) => {
  const result = [];
  for (let i = 0; i < arr.length; i += size) {
    result.push(arr.slice(i, i + size));
  }
  return result;
};
console.log(chunk([1, 2, 3, 4, 5], 2)); // [[1, 2], [3, 4], [5]]
```
**Interview tip:** "Slice array in chunks using loop. O(n) time."

---

### 1️⃣4️⃣ Find Missing Number
```javascript
const findMissing = arr => {
  const n = arr.length + 1;
  const expectedSum = (n * (n + 1)) / 2;
  const actualSum = arr.reduce((a, b) => a + b, 0);
  return expectedSum - actualSum;
};
console.log(findMissing([1, 2, 4, 5])); // 3
```
**Interview tip:** "Use sum formula n(n+1)/2, compare with actual sum."

---

### 1️⃣5️⃣ Rotate Array
```javascript
const rotate = (arr, k) => {
  k = k % arr.length;
  return [...arr.slice(-k), ...arr.slice(0, -k)];
};
console.log(rotate([1, 2, 3, 4, 5], 2)); // [4, 5, 1, 2, 3]
```
**Interview tip:** "Slice and concatenate. Handle k > length with modulo."

---

### 1️⃣6️⃣ Two Sum Problem
```javascript
const twoSum = (arr, target) => {
  const map = new Map();
  for (let i = 0; i < arr.length; i++) {
    const complement = target - arr[i];
    if (map.has(complement)) return [map.get(complement), i];
    map.set(arr[i], i);
  }
  return null;
};
console.log(twoSum([2, 7, 11, 15], 9)); // [0, 1]
```
**Interview tip:** "Use Map for O(n) solution. Store complement lookup."

---

### 1️⃣7️⃣ Move Zeros to End
```javascript
const moveZeros = arr => {
  const nonZeros = arr.filter(x => x !== 0);
  const zeros = arr.filter(x => x === 0);
  return [...nonZeros, ...zeros];
};
console.log(moveZeros([0, 1, 0, 3, 12])); // [1, 3, 12, 0, 0]
```
**Interview tip:** "Filter non-zeros, then zeros, concatenate."

---

### 1️⃣8️⃣ Find Intersection
```javascript
const intersection = (arr1, arr2) => [...new Set(arr1)].filter(x => arr2.includes(x));
console.log(intersection([1, 2, 3], [2, 3, 4])); // [2, 3]
```
**Interview tip:** "Filter first array checking if item exists in second."

---

## 🧮 Number Problems

### 1️⃣9️⃣ Fibonacci Sequence
```javascript
const fibonacci = n => {
  if (n <= 1) return n;
  let a = 0, b = 1;
  for (let i = 2; i <= n; i++) {
    [a, b] = [b, a + b];
  }
  return b;
};
console.log(fibonacci(7)); // 13
```
**Interview tip:** "Iterative approach is O(n) time, O(1) space. Better than recursive."

---

### 2️⃣0️⃣ Check Prime Number
```javascript
const isPrime = num => {
  if (num <= 1) return false;
  for (let i = 2; i <= Math.sqrt(num); i++) {
    if (num % i === 0) return false;
  }
  return true;
};
console.log(isPrime(17)); // true
```
**Interview tip:** "Check divisibility up to sqrt(n) for O(√n) time."

---

### 2️⃣1️⃣ Factorial
```javascript
const factorial = n => n <= 1 ? 1 : n * factorial(n - 1);
console.log(factorial(5)); // 120

// Iterative
const factorialIterative = n => {
  let result = 1;
  for (let i = 2; i <= n; i++) result *= i;
  return result;
};
```
**Interview tip:** "Know both recursive and iterative. Mention tail recursion optimization."

---

### 2️⃣2️⃣ Reverse Number
```javascript
const reverseNumber = num => parseInt([...String(Math.abs(num))].reverse().join('')) * Math.sign(num);
console.log(reverseNumber(12345)); // 54321
console.log(reverseNumber(-123));  // -321
```
**Interview tip:** "Convert to string, reverse, handle negative with Math.sign."

---

### 2️⃣3️⃣ Count Digits
```javascript
const countDigits = num => String(Math.abs(num)).length;
console.log(countDigits(12345)); // 5
```
**Interview tip:** "Convert to string and get length. Handle negatives."

---

## 🎯 Object Problems

### 2️⃣4️⃣ Deep Clone Object
```javascript
const deepClone = obj => JSON.parse(JSON.stringify(obj));
console.log(deepClone({a: 1, b: {c: 2}})); // {a: 1, b: {c: 2}}

// Better with structuredClone
const deepClone2 = obj => structuredClone(obj);
```
**Interview tip:** "JSON method works but loses functions. structuredClone is modern."

---

### 2️⃣5️⃣ Merge Objects
```javascript
const merge = (obj1, obj2) => ({...obj1, ...obj2});
console.log(merge({a: 1}, {b: 2})); // {a: 1, b: 2}

// Deep merge
const deepMerge = (obj1, obj2) => {
  const result = {...obj1};
  for (let key in obj2) {
    if (typeof obj2[key] === 'object' && !Array.isArray(obj2[key])) {
      result[key] = deepMerge(result[key] || {}, obj2[key]);
    } else {
      result[key] = obj2[key];
    }
  }
  return result;
};
```
**Interview tip:** "Spread for shallow, recursive for deep merge."

---

### 2️⃣6️⃣ Group By Property
```javascript
const groupBy = (arr, key) => arr.reduce((acc, obj) => {
  const group = obj[key];
  acc[group] = acc[group] || [];
  acc[group].push(obj);
  return acc;
}, {});

const data = [{type: 'fruit', name: 'apple'}, {type: 'fruit', name: 'banana'}];
console.log(groupBy(data, 'type')); // {fruit: [{...}, {...}]}
```
**Interview tip:** "Reduce with object accumulator. Create arrays on first encounter."

---

### 2️⃣7️⃣ Get Nested Property
```javascript
const getNestedProperty = (obj, path) => path.split('.').reduce((acc, key) => acc?.[key], obj);
console.log(getNestedProperty({a: {b: {c: 42}}}, 'a.b.c')); // 42
```
**Interview tip:** "Split path, reduce with optional chaining for safety."

---

### 2️⃣8️⃣ Compare Objects
```javascript
const isEqual = (obj1, obj2) => JSON.stringify(obj1) === JSON.stringify(obj2);
console.log(isEqual({a: 1}, {a: 1})); // true
```
**Interview tip:** "JSON stringify works for simple cases. Discuss deep comparison."

---

## ⚡ Async/Promise Problems

### 2️⃣9️⃣ Delay Function
```javascript
const delay = ms => new Promise(resolve => setTimeout(resolve, ms));

// Usage
await delay(1000);
console.log('After 1 second');
```
**Interview tip:** "Promise wrapper around setTimeout. Useful for async/await."

---

### 3️⃣0️⃣ Retry Function
```javascript
const retry = async (fn, retries = 3) => {
  for (let i = 0; i < retries; i++) {
    try {
      return await fn();
    } catch (err) {
      if (i === retries - 1) throw err;
    }
  }
};
```
**Interview tip:** "Loop with try-catch, throw on final retry."

---

### 3️⃣1️⃣ Promise.all Implementation
```javascript
const promiseAll = promises => {
  return new Promise((resolve, reject) => {
    const results = [];
    let completed = 0;
    
    promises.forEach((promise, index) => {
      Promise.resolve(promise).then(value => {
        results[index] = value;
        completed++;
        if (completed === promises.length) resolve(results);
      }).catch(reject);
    });
  });
};
```
**Interview tip:** "Track completion count, maintain order, reject on first error."

---

### 3️⃣2️⃣ Debounce
```javascript
const debounce = (fn, delay) => {
  let timeoutId;
  return function(...args) {
    clearTimeout(timeoutId);
    timeoutId = setTimeout(() => fn.apply(this, args), delay);
  };
};

// Usage
const debouncedSearch = debounce(() => console.log('Searching...'), 300);
```
**Interview tip:** "Clear previous timeout, set new one. Good for search inputs."

---

### 3️⃣3️⃣ Throttle
```javascript
const throttle = (fn, delay) => {
  let lastCall = 0;
  return function(...args) {
    const now = Date.now();
    if (now - lastCall >= delay) {
      lastCall = now;
      fn.apply(this, args);
    }
  };
};

// Usage
const throttledScroll = throttle(() => console.log('Scrolling...'), 200);
```
**Interview tip:** "Track last call time, execute if delay passed. Good for scroll/resize."

---

### 3️⃣4️⃣ Async Parallel vs Sequential
```javascript
// Parallel - faster
const parallel = async () => {
  const [result1, result2] = await Promise.all([
    fetch('/api/1'),
    fetch('/api/2')
  ]);
};

// Sequential - slower but dependent
const sequential = async () => {
  const result1 = await fetch('/api/1');
  const result2 = await fetch('/api/2');
};
```
**Interview tip:** "Use Promise.all for parallel, separate awaits for sequential."

---

## 🔍 Algorithm Problems

### 3️⃣5️⃣ Binary Search
```javascript
const binarySearch = (arr, target) => {
  let left = 0, right = arr.length - 1;
  
  while (left <= right) {
    const mid = Math.floor((left + right) / 2);
    if (arr[mid] === target) return mid;
    if (arr[mid] < target) left = mid + 1;
    else right = mid - 1;
  }
  return -1;
};
console.log(binarySearch([1, 2, 3, 4, 5], 3)); // 2
```
**Interview tip:** "O(log n) search on sorted array. Update left/right pointers."

---

### 3️⃣6️⃣ Bubble Sort
```javascript
const bubbleSort = arr => {
  const n = arr.length;
  for (let i = 0; i < n; i++) {
    for (let j = 0; j < n - i - 1; j++) {
      if (arr[j] > arr[j + 1]) {
        [arr[j], arr[j + 1]] = [arr[j + 1], arr[j]];
      }
    }
  }
  return arr;
};
console.log(bubbleSort([5, 3, 8, 4, 2])); // [2, 3, 4, 5, 8]
```
**Interview tip:** "O(n²) time. Swap adjacent if out of order. Not efficient."

---

### 3️⃣7️⃣ Quick Sort
```javascript
const quickSort = arr => {
  if (arr.length <= 1) return arr;
  const pivot = arr[arr.length - 1];
  const left = arr.filter((x, i) => x <= pivot && i < arr.length - 1);
  const right = arr.filter(x => x > pivot);
  return [...quickSort(left), pivot, ...quickSort(right)];
};
console.log(quickSort([5, 3, 8, 4, 2])); // [2, 3, 4, 5, 8]
```
**Interview tip:** "O(n log n) average. Pick pivot, partition, recurse."

---

### 3️⃣8️⃣ Find Unique Values
```javascript
const findUnique = arr => arr.filter((val, idx) => arr.indexOf(val) === idx);
console.log(findUnique([1, 2, 2, 3, 4, 4])); // [1, 2, 3, 4]
```
**Interview tip:** "Filter where first index equals current index."

---

### 3️⃣9️⃣ Most Frequent Element
```javascript
const mostFrequent = arr => {
  const freq = {};
  let maxCount = 0, result = null;
  
  arr.forEach(val => {
    freq[val] = (freq[val] || 0) + 1;
    if (freq[val] > maxCount) {
      maxCount = freq[val];
      result = val;
    }
  });
  return result;
};
console.log(mostFrequent([1, 3, 2, 3, 3, 1])); // 3
```
**Interview tip:** "Count frequencies with object, track maximum."

---

### 4️⃣0️⃣ Valid Parentheses
```javascript
const isValidParentheses = str => {
  const stack = [];
  const pairs = {'(': ')', '[': ']', '{': '}'};
  
  for (let char of str) {
    if (pairs[char]) {
      stack.push(char);
    } else {
      const last = stack.pop();
      if (pairs[last] !== char) return false;
    }
  }
  return stack.length === 0;
};
console.log(isValidParentheses("({[]})")); // true
```
**Interview tip:** "Use stack. Push opening, pop and match closing."

---

## 🎨 Practical Problems

### 4️⃣1️⃣ UUID Generator
```javascript
const generateUUID = () => {
  return 'xxxxxxxx-xxxx-4xxx-yxxx-xxxxxxxxxxxx'.replace(/[xy]/g, c => {
    const r = Math.random() * 16 | 0;
    const v = c === 'x' ? r : (r & 0x3 | 0x8);
    return v.toString(16);
  });
};
console.log(generateUUID()); // "a3f2b4c5-..."
```
**Interview tip:** "Replace template with random hex values. Version 4 UUID."

---

### 4️⃣2️⃣ Query String to Object
```javascript
const parseQueryString = url => {
  const params = new URLSearchParams(url.split('?')[1]);
  return Object.fromEntries(params);
};
console.log(parseQueryString('https://site.com?name=john&age=30')); 
// {name: 'john', age: '30'}
```
**Interview tip:** "Use URLSearchParams and Object.fromEntries for clean solution."

---

### 4️⃣3️⃣ Cookie Parser
```javascript
const parseCookies = () => {
  return document.cookie.split(';').reduce((acc, cookie) => {
    const [key, value] = cookie.trim().split('=');
    acc[key] = decodeURIComponent(value);
    return acc;
  }, {});
};
```
**Interview tip:** "Split by semicolon, parse key-value pairs, decode URI."

---

### 4️⃣4️⃣ Local Storage Helper
```javascript
const storage = {
  set: (key, value) => localStorage.setItem(key, JSON.stringify(value)),
  get: key => JSON.parse(localStorage.getItem(key)),
  remove: key => localStorage.removeItem(key),
  clear: () => localStorage.clear()
};
```
**Interview tip:** "Wrap localStorage with JSON parsing for objects."

---

### 4️⃣5️⃣ Format Number with Commas
```javascript
const formatNumber = num => num.toLocaleString('en-US');
console.log(formatNumber(1234567)); // "1,234,567"

// Manual
const formatManual = num => num.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',');
```
**Interview tip:** "Use toLocaleString for internationalization. Regex for custom."

---

### 4️⃣6️⃣ Truncate String
```javascript
const truncate = (str, length) => str.length > length ? str.slice(0, length) + '...' : str;
console.log(truncate("Hello World", 8)); // "Hello Wo..."
```
**Interview tip:** "Check length, slice and add ellipsis if needed."

---

### 4️⃣7️⃣ Random Color Generator
```javascript
const randomColor = () => '#' + Math.floor(Math.random() * 16777215).toString(16).padStart(6, '0');
console.log(randomColor()); // "#a3f2b4"
```
**Interview tip:** "Random number 0-16777215 to hex, pad to 6 digits."

---

### 4️⃣8️⃣ Get Age from Birthday
```javascript
const getAge = birthday => {
  const today = new Date();
  const birth = new Date(birthday);
  let age = today.getFullYear() - birth.getFullYear();
  const monthDiff = today.getMonth() - birth.getMonth();
  if (monthDiff < 0 || (monthDiff === 0 && today.getDate() < birth.getDate())) age--;
  return age;
};
console.log(getAge('1990-05-15')); // 34 (as of 2024)
```
**Interview tip:** "Calculate year difference, adjust for month/day not reached."

---

### 4️⃣9️⃣ Shuffle Array
```javascript
const shuffle = arr => {
  const result = [...arr];
  for (let i = result.length - 1; i > 0; i--) {
    const j = Math.floor(Math.random() * (i + 1));
    [result[i], result[j]] = [result[j], result[i]];
  }
  return result;
};
console.log(shuffle([1, 2, 3, 4, 5]));
```
**Interview tip:** "Fisher-Yates algorithm. Swap random elements backward."

---

### 5️⃣0️⃣ Memoization
```javascript
const memoize = fn => {
  const cache = {};
  return (...args) => {
    const key = JSON.stringify(args);
    if (key in cache) return cache[key];
    cache[key] = fn(...args);
    return cache[key];
  };
};

const slowFib = n => n <= 1 ? n : slowFib(n - 1) + slowFib(n - 2);
const fastFib = memoize(slowFib);
console.log(fastFib(40)); // Much faster!
```
**Interview tip:** "Cache results by stringified arguments. Huge performance boost."

---

## 🏆 Bonus: Advanced One-Liners

```javascript
// 51. Remove falsy values
const compact = arr => arr.filter(Boolean);

// 52. Get unique by property
const uniqueBy = (arr, key) => [...new Map(arr.map(x => [x[key], x])).values()];

// 53. Pick object properties
const pick = (obj, keys) => Object.fromEntries(keys.map(k => [k, obj[k]]));

// 54. Omit object properties
const omit = (obj, keys) => Object.fromEntries(Object.entries(obj).filter(([k]) => !keys.includes(k)));

// 55. Sleep function
const sleep = ms => new Promise(resolve => setTimeout(resolve, ms));

// 56. Random integer in range
const randomInt = (min, max) => Math.floor(Math.random() * (max - min + 1)) + min;

// 57. Check if empty object
const isEmpty = obj => Object.keys(obj).length === 0;

// 58. Clamp number
const clamp = (num, min, max) => Math.min(Math.max(num, min), max);

// 59. Average of array
const average = arr => arr.reduce((a, b) => a + b, 0) / arr.length;

// 60. Range array
const range = (start, end) => Array.from({length: end - start + 1}, (_, i) => start + i);
```

---

## 💡 Interview Strategy Tips

### Time Complexity Quick Reference:
- **O(1)** - Constant: Direct access, hash lookup
- **O(log n)** - Logarithmic: Binary search, balanced trees
- **O(n)** - Linear: Single loop, filter, map
- **O(n log n)** - Linearithmic: Efficient sorting (merge/quick)
- **O(n²)** - Quadratic: Nested loops, bubble sort
- **O(2ⁿ)** - Exponential: Fibonacci recursive

### When Asked About a Problem:
1. **Clarify** - Ask about edge cases, input size, constraints
2. **Example** - Walk through a simple example
3. **Approach** - Explain your strategy before coding
4. **Code** - Write clean, readable code
5. **Test** - Mention edge cases you'd test
6. **Optimize** - Discuss time/space complexity improvements

### Common Follow-ups:
- "What's the time complexity?" → Always be ready to answer
- "How would you optimize this?" → Discuss trade-offs
- "What if input is very large?" → Talk about performance
- "What edge cases exist?" → null, empty, negative, duplicates

### Good Practices to Mention:
- "I'd add input validation"
- "I'd handle null/undefined cases"
- "I'd write unit tests for this"
- "I could optimize with memoization/caching"
- "I'd use TypeScript for better type safety"

---

## 🎯 Quick Reference Table

| Problem Type | Best Approach | Time Complexity |
|-------------|---------------|-----------------|
| Search sorted | Binary search | O(log n) |
| Search unsorted | Linear/Hash | O(n) or O(1) |
| Sort | Quick/Merge sort | O(n log n) |
| Duplicates | Set/Hash map | O(n) |
| Two pointer | Array problems | O(n) |
| Stack | Parentheses/undo | O(n) |
| Recursion | Tree/divide-conquer | Varies |
| DP/Memo | Optimization | O(n) space |

Good luck with your interviews! 🚀
