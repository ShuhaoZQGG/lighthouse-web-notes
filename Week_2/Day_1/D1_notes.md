# Introduction to Asynchronous Programming

### [Compass](https://web.compass.lighthouselabs.ca/days/w02d1)

### [Lecture Notes](https://web.compass.lighthouselabs.ca/days/w02d1/activities/101)

### [Today's Work](https://github.com/ShuhaoZQGG/lotide)

Asynchronous programming is when a unit of work is run **separately** from the **main thread** of the program and **notifies** the program of its **completion**

# **Asynchronous Callbacks**

```jsx
const fs = require("fs");

console.log('BEFORE writeFile call');

fs.writeFile("./test_async.txt", "h3ll0 file!\n", (error) => {
  if (error) {
    // Handle error
    console.log("Failed to write to file");
    return;
  }
  // Success!
  console.log("Successfully wrote to file");
});

console.log('AFTER writeFile call');
```

Output:

```jsx
'BEFORE writeFile call'
'AFTER writeFile call'

if error : "Failed to write to file"
else : "Successfully wrote to file"
```

**Simply put:** *A callback is a function that is to be executed **after** another function has finished executing — hence the name ‘call back’.*

**More complexly put:** *In JavaScript, functions are objects. Because of this, functions can take functions as arguments, and can be returned by other functions. Functions that do this are called **higher-order functions**. Any function that is passed as an argument is called a **callback function**.*

An example of async function :

```jsx
setTimeout(callback, delay)

console.log('first line');
setTimeout(() => {
  console.log('timeout line');
}, 1000);
console.log('last line');

/*
Output:
first line,
last line,

// after 1 s:
timeout line
*/
```