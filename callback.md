```js
function first(){
  // Simulate a code delay
  setTimeout( function(){
    console.log(1);
  }, 0 );
}
function second(){
  console.log(2);
}
first();
second();
```
就算response有延遲，JavaScript還是會稱職的一行一行繼續執行下去，根本不管你有沒有收到第一個的response，然後依賴第一個函式回傳值的第二的函式就失效了。
callback 是一個方式確保他會按照你要的順序一個接著一個跑，第一個跑完收到response之後，拿到資料後才去跑下一個。
我已為用setTimeOut就可以拖延時間就能照我的意思跑，但考慮到諸多環境因素，沒拿到回傳值就繼續跑爆掉的機率還是很高。
後來才發現setTimeOut 都被拿來當不良示範，警示大家要用callback 可...可惡...為什麼學一半就去亂試偏方XD 
