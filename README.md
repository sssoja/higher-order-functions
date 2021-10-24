<h1>Functions as Parameters</h1>
<p>Since functions can behave like any other type of data in JavaScript, it might not surprise you to learn that we can also pass functions (into other functions) as parameters. A higher-order function is a function that either accepts functions as parameters, returns a function, or both! We call the functions that get passed in as parameters and invoked callback functions because they get called during the execution of the higher-order function.</p>

When we pass a function in as an argument to another function, we don’t invoke it. Invoking the function would evaluate to the return value of that function call. With callbacks, we pass in the function itself by typing the function name without the parentheses (that would evaluate to the result of calling the function):

<code>
const timeFuncRuntime = funcParameter => {
   let t1 = Date.now();
   funcParameter();
   let t2 = Date.now();
   return t2 - t1;
}
 
const addOneToOne = () => 1 + 1;
 
timeFuncRuntime(addOneToOne);
</code>

<p>We wrote a higher-order function, <code>timeFuncRuntime()</code>. It takes in a function as an argument, saves a starting time, invokes the callback function, records the time after the function was called, and returns the time the function took to run by subtracting the starting time from the ending time.</p>

<p>We then invoked <code>timeFuncRuntime()</code> first with the <code>addOneToOne()</code> function - note how we passed in <code>addOneToOne</code> and did not invoke it.</p>

<code>
timeFuncRuntime(() => {
  for (let i = 10; i>0; i--){
    console.log(i);
  }
});
</code>

<p>
In this example, we invoked <code>timeFuncRuntime()</code> with an anonymous function that counts backwards from 10. Anonymous functions can be arguments too!
</p>

Taken from [Codeacademy's](https://www.codecademy.com/courses/introduction-to-javascript/lessons/higher-order-functions/exercises/functions-as-parameters) tutorial on Higher-Order Functions.
