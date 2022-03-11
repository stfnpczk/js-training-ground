![JS Logo](./assets/JS-logo2.png)



## Table of contents

- [Promises](#promises)
- [Async Await](#async-await)

## **Promises**
A Promise is an object that handles asynchronus data. This object represents the eventual outcome of an **asynchronous operation** and its resulting value. 
A Promise object can be in one of these **three states**:

  - **pending**: initial state, the operation has not completed yet, neither fulfilled nor rejected
  - **fulfilled**: operation was completed successfully. Promise has settled and now has a resolved value.
  - **rejected**: The operation has failed due to an error of some kind

  If a promise has settled, you're able to perform successive actions with the **higher-order function** `.then()` <br>
  The function can take two **callback functions** as arguments, which are referred to as handlers. When the promise settles, the respective handler is being invoked with that settled value. <br>
  Usually you differentiate between a **success** and a **failure handler**. <br><br>

  Note that `.then()` itself also returns a promise.


```js
const promise = new Promise(executorFunction);
const promise2 = promise.then(handleSuccess, handleFailure);
```

**Chaining Multiple Promises** (Promise Compositon ) <br>
For operations that depend on each other or have to be executed in a certain order, you can chain multiple `then` expressions.

[Pseudo code from MDN-> chained promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise#chained_promises)
```js
myPromise
.then(handleResolvedA)
.then(handleResolvedB)
.then(handleResolvedC)
.catch(handleRejectedAny);
```

As an example, you can think of a request to an API that you await for a response to make yet another request.

**Promise.all()**<br>
If the different operations do not depend on each other and the order of the execution is not important, you should take advantage of concurrency and use the method `Promise.all()`. The method takes an iterable array of promises and returns a single promise. <br>
This single promise settles in one of two ways. Either all promises in the array will resolve and return an array with the respective values, or it gets rejected immediately, as one of the promises in the array throws an error (falling fast). <br> 

```js
Promise.all([promise1, promise2, promise3])
  .then(onFulfill)
  .catch(onReject);
```
<br><br>
## **Async Await**
async .. await syntax was introduced with ECMAScript 2017 and is meant as syntactic sugar, improving readability for complexly nested callback functions within promises. In this syntax, asynchronous code reads much more like traditional synchronous code and is easier to read and write. 

**async keyword** <br>
The `async` keyword is used in front of a function declaration to handle asynchronous code. <br>
Invoking an async function always returns a promise, thus it can be used together with `.then()` and `.catch()` <br>
The return value of an async function can be one of the three:
1. if the function returns nothing, a promise will be returned with a resolved value of undefined 
2. if the function returns a promise that promise is also returned
3. otherwise a promise with the respective resolved value is returned

**await keyword** <br>
The await keyword can only be used inside an async function, it makes the function wait for the promise until it settles. Await is treated like an operator, it awaits the resolution of the promise and either returns the resolved value or throws an error. 

```js
async function fetchData() {
  const response = await fetch($apiEndpoint);
  if(!response.ok) {
    throw new Error(`Request failed!`)
  ...
  }
}
```

Fetch request