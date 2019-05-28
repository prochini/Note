# JavaScript 網頁事件處理

## eventListener 事件監聽


```javascript
      const elements = document.querySelector('div')
      elements.addEventListener('click', onClick)
      function onClick(){
        alert('Heyyyyy!')
      }
      }
```
[Introduction to events](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events#Event_bubbling_and_capture
)

# callback function 回呼函式

當到餐廳要執行吃飯的動作，但櫃台姊姊說現在客滿哦~豬還再殺~要等40分鐘，你要不要留個電話等到有空位時再打給你，你在回來的時候就準備好空位置和烤乳豬了，就可以開始享用大餐。

辦公室電話響了 (事件被觸發 Event fired) -> 接電話 (處理事件 Event Handler)

> 為何要用 callback function?
為了讓功能模組化，可新增更多功能，讓 function pointer 指到一個實際的函式，會在適當的時間呼叫此 function，把 function 當作參數傳進去使用，則此function就是所謂的 callback function。

callback 是「被動」等待某個條件產生才去執行你寫的 function，
這個條件通常指的是訊息的發生。比如說視窗上某個按鈕被按時，
才會去呼叫你寫的函式，便是「被動」等待 user 去按按鈕。

[為何要用 callback function](http://work.oknow.org/2016/04/callback-function.html)
[重新認識 JavaScript: Day 18 Callback Function 與 IIFE](https://ithelp.ithome.com.tw/articles/10192739)
[callback, promise, async/await 使用方式教學以及介紹 Part I](https://yu-jack.github.io/2018/07/22/promise/)

## 確保執行順序
為了確保先執行 funcA 再執行 funcB
我們在 funcA 加上 callback 參數
```javascript

var funcA = function(callback){
  var i = Math.random() + 1;

  window.setTimeout(function(){
    console.log('function A');

    // 如果 callback 是個函式就呼叫它
    if( typeof callback === 'function' ){
      callback();
    }

  }, i * 1000);
};

var funcB = function(){
  var i = Math.random() + 1;

  window.setTimeout(function(){
    console.log('function B');
  }, i * 1000);
};


// 將 funcB 作為參數帶入 funcA()
funcA( funcB );
```
無論 funcA 在執行的時候要等到天荒地老海枯石爛， funcB 都會癡癡得等等到 console.log('function A'); 之後才執行。

## 模組化
模組化前
```javascript
let calc =function(num1, num2, calcType){
  if(calcType ==='add'){
    return num1+ num2
  }
}

console.log(calc(7,8,'add'))
```
模組化後
```javascript
const add = function(a, b){
return a + b
}

const multiply = function(a, b){
return a * b
}

let calc = function(num1, num2, callback){
 return callback(num1, num2)
}

console.log(calc(7, 8, add))
```
## event (e) 

```javascript
// MouseEvent 顯示滑鼠選取的元素 'click'
const element = document.querySelector('.unicorn')
element.addEventListener('click', function(e){
console.log(e.target)
})
// KeyboardEvent  顯示鍵盤輸入的鍵 'keydown'
window.addEventListener('keydown', function(e){
  console.log(e.key)
})
```
---

## 變更背景的按鈕實作
1. 將 switch 按鈕在 DOM 樹裡的節點位置，儲存再變數 element 中
2. 註冊 click 按鈕事件發生時，執行匿名函式將 body 元素新增/移除 changeColor的 CSS 屬性。
3. click 變更 body 的背景，再 click 就恢復原本 body 的背景。

```javascript
// CSS 
.changeColor{
    background: pink;
}
//HTML  
<button class="switch">press</button>
//JavaScript
const element = document.querySelector('.switch')
element.addEventListener('click', function(e){
  document.querySelector('body').classList.toggle('changeColor')
})
```

---
## 表單驗證邏輯 
- 防止 2 次密碼不同的表單
```javascript
//HTML
  <form action="" class="login">
    <div>ueser:<input type="text"></div>
    <div>password:<input class='psw1'type="password"></div>
    <div>password again:<input class='psw2'type="password"></div>
    <input type="submit">
  </form>
<a href="https://hackmd.io/">HACK</a>
//JavaScript
const element = document.querySelector('.login')
element.addEventListener('submit', function(e){
const psw1 = document.querySelector('.psw1')
const psw2 = document.querySelector('.psw2')
if (psw1.value !== psw2.value){
  e.preventDefault()  
  alert('passwords are diffrent!!!')
}
```
> [name=Ying Chen Chung]
> 
[What Are Event Listeners In JavaScript](https://www.youtube.com/watch?v=jqU3uaRgQyQ)

## 事件傳遞機制

當滑鼠點擊元件，會同時點及該元件的父元件。

```javascript
//HTML
<div class="outer">
  <div class="inner">
    <button class="btn">pork </button>
  </div>
</div>
//JavaScript
      function addEvent(className){
        document.querySelector(className)
        .addEventListener('click',function(){
          alert(className)
        })
      }
      addEvent('.outer')
      addEvent('.inner')
      addEvent('.btn')
```

>回傳內容
>(click).btn => (捕獲)  .outer -> .inner -> .btn ->(冒泡) .btn -> .inner -> .outer
>

## 事件傳遞機制詳解：捕獲與冒泡

[DOM 的事件傳遞機制：捕獲與冒泡](https://blog.techbridge.cc/2017/07/15/javascript-event-propagation/)

```javascript
      function addEvent(className){
        document.querySelector(className)
        .addEventListener('click',function(){
          console.log(className, '捕獲')
        }, true)

        document.querySelector(className)
        .addEventListener('click',function(){
          console.log(className, '冒泡')
        }, false)

      }
```

- stopPropagation()
```javascript
      document.querySelector('.btn')
        .addEventListener('click',function(e){
          e.stopPropagation()
          console.log('.btn 冒泡')
        })
```
## 事件代理
原始 

```javascript
      let num = 5
      const element = document.querySelectorAll('.btn')
      for (var i = 0; i < element.length; i++){
        element[i].addEventListener('click',function(e){
        console.log(e.target.getAttribute('data-value'))
        })
      }
      //動態新增按鈕
      document.querySelector('.add').addEventListener('click',
      function(){
        const btn = document.createElement('button')
        btn.setAttribute('data-value', num)
        btn.innerText =num
        num++
        document.querySelector('.outer').appendChild(btn)
      }
      )
```

優化 自動加 addEventListener

```javascript
//HTML
<div class="outer">
<button class="add">add</button>
<button class="btn" data-value='1'>1</button>
<button class="btn"data-value='2'>2</button>
<button class="btn"data-value='3'>3</button>
<button class="btn"data-value='4'>4</button>
  </div>
  //JS
      let num = 5

      //動態新增按鈕
      document.querySelector('.add').addEventListener('click',
      function(){
        const btn = document.createElement('button')
        btn.setAttribute('data-value', num)
        btn.classList.add('btn')
        btn.innerText =num
        num++
        document.querySelector('.outer').appendChild(btn)
      }
      )

      document.querySelector('.outer').addEventListener('click', 
        function(e){
          if (e.target.classList.contains('btn')){
            alert(e.target.getAttribute('data-value'))
          }         
        }
      )
```

## 綜合示範：簡易密碼產生器
```javascript
<div class="app">
  
  <div><label><input type="checkbox" name="en" >English</label></div> 
  <div><label><input type="checkbox" name="num">Number</label></div>
  <div><label><input type="checkbox" name="sp">Special</label></div>
 <div><button class="btn">產生</button></div>
<div class="result">
  []
</div>
</div>

//JS
document.querySelector('.btn').addEventListener('click',
        function(){
          let char = '';
          if(document.querySelector('input[name=en]').checked){
            char += 'abcdefghijklmnopqrstuvwxyz'
          }

          if(document.querySelector('input[name=num]').checked){
            char += '0123456789'
          }
          if(document.querySelector('input[name=sp]').checked){
            char += '~!@#$%^&*()_+'
          }
          console.log(char)
          let result ='';
          for(let i = 0; i < 10; i++){
            const num = Math.floor(Math.random()*char.length)
            result += char[num]
          }
            document.querySelector('.result').textContent = result 
        }
      )
```