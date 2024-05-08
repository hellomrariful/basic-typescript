# Handling Asynchronous Operations in TypeScript

In JavaScript and TypeScript, asynchronous programming allows us to work with tasks that don't complete immediately, such as reading files or making network requests. It enables non-blocking operations, enhancing the efficiency of our programs.

## Callbacks and Promises

Traditionally, callbacks and promises were used to handle asynchronous tasks in JavaScript and TypeScript.

### Callbacks

Callbacks involve passing a function as an argument to another function. When the asynchronous task completes, the callback function is called with the result.

```typescript
function fetchData(callback: (data: any) => void) {

    setTimeout(() => {
        const data = 'Some data';
        callback(data);
    }, 1000);
}

// Usage
fetchData((data) => {
    console.log(data);
});
```

## Promises
promise is a powerful tool for working with asynchronous operations in TypeScript. For example, if you use a promise to fetch the data from an API, Then for use promise, you create a new instance of the promise class and pass it a function that performs the asynchronous operation.

Once the promise is created, you can attach a callback to using the then method. These callback will be called when the promise is over, with the resolved value passed as a parameter. If the promise is rejected, you can attach a error handler using the catch method.

```typescript

const myPromise = new Promise((resolve, reject) => {
  if(data){
    resolve(data);
  }
});

myPromise
  .then((result) => {
    // Handle the successful result from here
  })
  .catch((error) => {
    // Handle the error from here
  });

```

## async/await
As we know that TypeScript is a superset of JavaScript, so async/await works the same, but with some extra benefits and most importantly type safety. Basically, async/await provides a cleaner syntax for handling asynchronous operations, making code easier to read and write.

On the other hand, An async function always returns a promise. Even though if you omit the promise keyword explicitly, the compiler will wrap your function in an immediately resolved promise.


```typescript
async function fetchData() {
    // Simulate fetching data asynchronously
    const response = await fetch('https://api.example.com/data');
    const data = await response.json();
    return data;
}

// Usage
(async () => {
    try {
        const data = await fetchData();
        console.log(data);
    } catch (error) {
        console.error(error);
    }
})();


```

## Benefits of async/await in TypeScript
- Cleaner Syntax: async/await simplifies asynchronous code, making it easier to understand and maintain.
- Sequential Execution: It allows us to write asynchronous code that looks synchronous, enabling sequential execution of asynchronous tasks.
- Error Handling: Error handling with async/await is straightforward, using try-catch blocks for synchronous-style error handling.
- Type Safety: TypeScript provides type checking for async/await, enhancing code safety and preventing common errors.

#### In summary, async/await in TypeScript offers a modern and efficient way to handle asynchronous operations, improving code readability and maintainability.







