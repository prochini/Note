```js

console.log(b)
var b = 10


===

var b // 只有宣告會提升
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
```

```js
```
