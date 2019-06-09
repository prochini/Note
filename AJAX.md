# 課程總結

該有的基礎
1. 更改介面
2. 事件監聽
3. 交換資料

## 綜合示範：抓取資料並顯示
- JSON.parse(): 使用 server 取得的 JSON 格式資料一定是字串，將 JSON 轉換成 JavaScript 的 object。
- JSON.stringify(): 將數據送發到 server 時，資料必須是字串，將 JavaScript 的 object 轉成 JSON。
- body 是 JavaScript 動態產生的，搜尋引擎是看不到網頁原始碼裡的 JSON 資料，內容畫面是在 client 端渲染出來的。
```js

<style> 
.profile{
  display:inline-flex;
  border: 1px solid brown;
  align-items: center;
  margin: 20px;
}
</style>
<body>
  <div class="app">
      <div class="profile">
        </div>
  </div>
  <script src="test.js"></script>
</body>

const request = new XMLHttpRequest();
const container = document.querySelector('.app');
request.addEventListener('load', () => {
  if (request.status >= 200 && request.status < 400) {
    const response = request.responseText;
    const json = JSON.parse(response);
    const users = json.data;
    for (let i = 0; i < users.length; i += 1) {
      const div = document.createElement('div');
      div.classList.add('profile');
      div.innerHTML = `
      <div class="first_name">${users[i].first_name}</div>
      <div class="last_name">${users[i].last_name}</div>
      <img src="${users[i].avatar}" alt="avatar">
      `;
      container.appendChild(div);
    }
  } else {
    console.log(request.status);
  }
});
request.onerror = () => {
  console.log('error');
};
request.open('GET', 'https://reqres.in/api/users', true);

request.send(null);

```

## 傳送資料的第一種方式：表單 form

純粹透過 HTML form 使用 POST 參數到指定網頁去，browser 得到 reponse 後會直接 跳轉到 他 render 出來的網頁。 

```html
<div class="app">  
  <form class="text" method="POST" action="https://www.google.com">
    name:<input name="name">
    <input type="submit">
  </form>
</div>
```
發 request 到新的頁面去，並得到回應的資料
![表單 form](https://i.gyazo.com/02f2222a295ada4a66a6d5e7f0c93180.png)

reponse 回傳什麼結果就顯示什麼結果 
[![Image from Gyazo](https://i.gyazo.com/36fabc56bc79089525aa6e1733314110.png)](https://gyazo.com/36fabc56bc79089525aa6e1733314110)

缺點: 會換頁，直接送出結果

## 傳送資料的第二種方式：ajax
Asynchronous JavaScript And XML 非同步和伺服器交換JSON

![AJAX](https://cdn-images-1.medium.com/max/1600/1*6PasVp89PTHbDvYJ-Zq8ZQ.png)

### The XMLHttpRequest object 
可以在背底裡暗中和 server 交換資料，所以可以只更新部分網頁，不需要重新載入整個網頁。
- 創建 XMLHttpRequest 物件 
` var xhttp = new XMLHttpRequest(); `

### AJAX - Send a Request To a Server
- open (method, url, async)
method: the type of request: GET or POST
url: the server (file) location
async: true (asynchronous) or false (synchronous)
- send() 
send()	Sends the request to the server (used for GET)
send(string)	Sends the request to the server (used for POST)

```js
const request = new XMLHttpRequest();
request.open('GET', 'https://reqres.in/api/users', true);

// If specified, responseType must be empty string or "text"
request.responseType = 'text';

request.onload = function () {
    
        if (request.status >= 200 && request.status < 400) {
          console.log(request.response);
          console.log(request.responseText);
        }
    
};

request.send(null);
```
- addEventListener + XMLHttpRequest
```js

const request = new XMLHttpRequest()
request.addEventListener('load',function(){
  if (request.status >= 200 && request.status < 400) {
    console.log(request.responseText);
  } else {
    console.log(request.status)
  } 
}
)
request.onerror = function(){
  console.log('error')
}
request.open('GET', 'https://reqres.in/api/users', true);

request.send(null);
```
- Network 成功打開寶箱
Request URL: https://reqres.in/api/users
Request Method: GET
Status Code: 200  (from disk cache)
Remote Address: 104.27.134.11:443
Referrer Policy: no-referrer-when-downgrade

## Same origin policy 同源政策
[好文推薦](https://blog.techbridge.cc/2017/05/20/api-ajax-cors-and-jsonp/)
- 禁止進入 (瀏覽器會把不同源的網頁擋掉)
Access to XMLHttpRequest at 'https://google.com/' from origin 'http://127.0.0.1:5500' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource.

- Same origin policy 同源政策
兩份網頁俱備相同協定 http | https 、相同 port、相同主機位置 domain。

- 跨來源資源共用(CROS)記載

- 唯一解藥
server 端 Response Headers 需加上 access-control-allow-origin: *
繞所有的 origin 都可以存取


## 瀏覽器安全性

## JSONP

## 單向傳送資料的延伸應用（email 與追蹤）

<img wigth='1' height='1' src ='http://prochinicompany.com/users_open/id'/>






