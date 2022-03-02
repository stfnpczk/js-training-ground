![JS Logo](./assets/JS-logo2.png)

# JavaScript 

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

**Chaining Multiple Promises**