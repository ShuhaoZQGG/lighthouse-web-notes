### [Compass](https://web.compass.lighthouselabs.ca/days/w02d2)

### [Lecture](https://web.compass.lighthouselabs.ca/activities/856/lectures/4806)

# Another Async Callback Example:

## Event Handling User Input

```jsx
// on any input from stdin (standard input), output a "." to stdout
process.stdin.on('data', (key) => {
  process.stdout.write('.');
});

console.log('after callback');
```

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/d04048df-93be-45e0-8dd2-6838f27b4c4c/Untitled.png)

The `on` function is a very common method name for registering callbacks to handle events.

# **Intro to Networking**

A (Computer) Network is when two or more computers are connected and can communicate with each other.

The internet is the world's largest and best known network.

'

# Intro to TCP

**TCP**, which stands for *Transmission Control Protocol*, provides a standard that allows machines to speak to each other.

TCP based communication allows two machines to establish an open channel for two-way data communication. Once a connection is established, both parties can start sending and receiving data until one of them decides that it's had enough and decides to terminate the connection.