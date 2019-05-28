# JavaScript 與瀏覽器的溝通

## 執行 JavaScript 的一百種方式
1. `<script src="">` 
2. node.js vs browser瀏覽器.js 差異
  - 支援語法差異ex: require

## DOM (Document Object Model)是什麼？
* 把 Document 轉換成 Object，把HTML的文件轉換成很多節點，用JavaScript 去拿到節點拿來作改變，瀏覽器會依照JavaScript 的寫法去作呈現，作為JavaScript, HTML, browser之間的橋梁。
* 瀏覽器中用來表示文件的 API 可允許程式和程式碼之間的應用，是一個介面呈現瀏覽器是怎麼看你的HTML檔案，依序變更使用者看到的內容。
* DOM 定義程式腳本可以向瀏覽器詢問目前頁面內容和資訊，並告知瀏覽器目前想要提供給使用者的內容。
* 瀏覽器讀了HTML之後，會將文件以樹狀結構物件模型，許多分支和節點，本個節點內都有一個物件，DOM允許程式語言可以對任何節點存取和互動，節點可以被新增、移動和變更。事件監聽可以被新增到節點中，當發生事件時會被觸發。

## DOM 樹運用

1. 選取元素或節點
2. 操作元素

每個節點都是一個物件，程式碼會存取這個 DOM 樹，任何對 DOM 樹的改變都會反映在瀏覽器上。
1. 文件節點 Document
2. 標籤元件節點
3. 屬性節點
4. 文字節點 
![](https://i.imgur.com/q2lLbQa.png)

---
## 步驟1 選取元素：getElement 
- querySelector:　選擇第一個符合 css選擇的元素。
```javascript
const myElem = document.querySelector(css selector);
```
- querySelectorAll: 回傳所有符合選擇條件的元素。
```javascript
const elements = document.querySelectorAll(css selector);
var a = document.getElementById("myDiv").querySelectorAll("p");  
```
## 步驟2 操作元素:

- 改變 CSS
```javascript
elements.style.background = 'rainbow' 
```

- 改變 class

```javascript
elements.classList.add('changeColor') //新增 class 
elements.classList.remove('unicorn')  //移除 class
elements.classList.toggle('alligator')//開關 class 有到無 無到有
```
- 改變屬性 Attribute
```javascript
elements.setAttribute("class", "democlass")
```


- 改變元素裡的文字內容
```javascript
elements.textContent = "I changed my mind."
console.log(elements.textContent)
```
- 增加或移除 HTML 文件內容
不適合用於讓使用者輸入的文字加入至頁面中，會有XSS的安全性風險。
```javascript
elements.innerHTML = 'I get rid of everything in element.'  
console.log(elements.outerHTML) //可看元素完整狀態
```
- DOM 控制處理 新增和刪除元素
```javascript
新增元素到任一樹節點下，作為子節點
const item =document.createElement('article')
elements.appendChild(item)
```

```javascript
刪除一父節點下的子節點元素
const item =document.querySelector('div a')
elements.removeChild(item)
```
