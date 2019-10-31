## Web Storage API

response

A -> login -> server

A with cookie -> server
cookie: 通行證 passport ，一個小型文字檔，會自動帶到server

Cookie 的用途
Cookie 是造訪的網站所建立的檔案。這些檔案透過儲存瀏覽資訊，提供更便利的線上體驗。
網站可以利用 Cookie 進行以下操作：
- 保持登入狀態
- 記住網站偏好設定
- 提供所在地相關的內容


---
## Window.localStorage
 Web Storage API 提供訪問本地的 session 或 local storage，可添加、修改或刪除儲存的數據。
localStorage 裡儲存的資料沒有有效期限
### Methods
- Storage.setItem()
When passed a key name and value, will add that key to the storage, or update that key's value if it already exists.
- Storage.getItem()
  When passed a key name, will return that key's value.
[Storage
](https://developer.mozilla.org/en-US/docs/Web/API/Storage)
示範: 
```js

<body>
<div class="app"><input class="text"><button>save</button>
</div>

<script>

  const saveValue = window.localStorage.getItem('content') 
  // 使用 key 取得 value

  document.querySelector('.text').value = saveValue 

  //把 input 的值指定為 localStorage 的 value

  document.querySelector('button').addEventListener('click', function(){
    const val = document.querySelector('.text').value 
    //按下按鈕取得 input 的值
    window.localStorage.setItem('content', val)
    //將 key 'content' 和 value 存入 localStorage

  })
    </script>
</body>

```
## Window​.session​Storage
session​Storage 裡面儲存的值會在頁面關閉後清除 the content in the storage will be cleared once you close the page.
