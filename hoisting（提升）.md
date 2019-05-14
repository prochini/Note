```js

console.log(b)
var b = 10


===

var b // 只有宣告會提升  (我要宣告一個變數 b )undefined
console.log(b)
b = 10//賦值沒有提升


```

```js
test()//呼叫函式會提升

function test(){
  console.log(123)
}
====

function test(){
  console.log(123)
}
test()
```

```js
var test // 宣告提升了
test()  // 執行函式，發現 test is not a function ，目前為undefined

function (){
  console.log(3)
}
===

test()

var test = function (){
  console.log(3)
}
```

```js
let a  = 'global'
function test() {

  console.log(a)
  var a = 'local' //undefined
  let a = 'local' // a is not defined
}

test()
```

```js

function test() {
 console.log(a)
 a() // 呼叫函式 a 第2個 函式蓋掉第一個
  var a = 'local';
  function a(){
    console.log('first')
  } 
  function a(){
    console.log('after') //after
  }
}

test()
```

```js
function test(a){
  console.log(a);
  var a = 456
}
test (123) // 會以參數優先

```

```js
function test(a){
  console.log(a);
  var a = 456
  function a(){} //會以 function 優先
}
test (123) 

```

總結 :

提升的優先順序為
1. function
2. arguments
3. vars

```js
function test(a){ // 宣告參數 a
   var a  ; //我想要宣告(被忽略)
   let a ; //SyntaxError: Identifier 'a' has already been declared
  console.log(a);// 印出賦值 a
   a =456  // 重新賦值
  console.log(a);// 印出賦值a
}
test (123) 
```

```js
```

```js
```
