### [Compass](https://web.compass.lighthouselabs.ca/days/w02d4)

### [Lecture](https://web.compass.lighthouselabs.ca/activities/153/lectures/4809)

### [Today's Work](https://github.com/ShuhaoZQGG/iss_spotter)

# JSON

JSON is a data format that underpins many modern web services. It stands for **JavaScript Object Notation**, and it's actually a subset of the JavaScript language.

JSON is built on two structures:

- A collection of name/value pairs.
- An ordered list of values.

### JSON.parse()

> Parse a string as JSON, optionally transform the produced value and its properties, and return the value.
> 

### JSON.stringify()

> Return a JSON string corresponding to the specified value, optionally including only certain properties or replacing property values in a user-defined manner.
> 

# API (Application Programming Interface)

It allows one piece of software talk to another

## Rest (Representational State Transfer) API

Client ⇒ HTTP ⇒ Server

# Promises

**An official introductory description:** A promise represents the eventual result of an asynchronous operation. The primary way of interaction with a promise is through its `then` method, which registers callbacks to receive either a promise’s eventual value or the reason why the promise cannot be fulfilled.

- A promise is an object
- Promises do not rely on anything other than basic JavaScript
- As of ES6, JavaScript has promises supported natively in its code. In other words, they are built into the language (via `Promise`)

## Comparison between non-promise and promise:

```jsx
// clepto.js
gotoTheirHouse(billy, () => {
  pretendToBeFriends(billy, () => {
    stealWhenNotLooking(billy.mixtapes, (items) => {
      hideInBackpack(items, () => {
        console.log("I don't feel well. I gotta go home now Billy!");
      });
    });
  });
});
```

```jsx
// clepto_promises.js
gotoTheirHouse(billy)
  .then(pretendToBeFriends)
  .then(stealWhenNotLooking)
  .then(hideInBackpack)
  .then(() => {
    console.log("I don't feel well. I gotta go home now Billy!");
  });
```