![JS Logo](./assets/JS-logo2.png)



## Table of contents

- [Promises](#Promises)

## Promises
Promises are objects that represent the eventual outcome of an **asynchronous operation** and its resulting value. 
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

**Promise.all()**