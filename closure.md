## scope
```js
const b = 20;
function test() {
  const a = 10; // 外面看不到裡面
  console.log(b); // 裡面找不到會到外面找
}

test();
// console.log(a) ReferenceError: a is not defined

```
## closure
```js
function createCounter() {
  let count = 0;
  function addCount() { // 讓外界無法存取 //function 中回傳 function
    count += 1;
    return count;
  }
  return addCount;
}
const counter = createCounter();
console.log(counter());
console.log(counter());
console.log(counter());
console.log(counter());
```
