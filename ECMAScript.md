```js 
var a = 1; //全域變數 a
function test(){
  console.log('1.', a);//找a ,找有沒有a函式,找區域變數,var a提升尚未賦值,所以是 undefined 
  var a = 7;// a 賦值 7
  console.log('2.', a);// 7
  a++;//a 賦值 8
  var a;//var重複宣告a 直接忽略
  inner();// 執行函式inner
  console.log('4.', a); // inner 執行完，a 已被賦值 30
  function inner(){ 
    console.log('3.', a); //印出目前的 a ,inner區域內沒有宣告 a,向外到 test 找 a, 找到目前 test的 a 為 8
    a = 30;//a 賦值為 30
    b = 200;// b 再區域變數未宣告，b 宣告變成全域變數
  }
}
test();//執行程式
console.log('5.', a); // 找全域變數的 a ， 1
a = 70;//a 賦值為70
console.log('6.', a);// 70
console.log('7.', b);// 200
```
