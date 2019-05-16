https://medium.com/@Mike_Cheng1208/10%E5%80%8B%E6%96%B0%E6%89%8B%E5%BF%85%E7%9F%A5%E7%9A%84-javascrip-%E5%AF%A6%E7%94%A8%E6%8A%80%E5%B7%A7-75b55d7c3e47

JavaScript 被稱為世界上被誤解最深的程式語言，其原因族繁不及備載，有興趣的朋友可以再google搜尋一下。最主要是今天我要來介紹幾個我覺得是一般新手都應該要知道的一些寫JavaScript的技巧，讓你再學習寫JavaScript的時候可以提升寫code的品質，更可以解決一些後續的問題。

這邊是我自己在工作與教學上面的經驗所彙整出來的，或許你也有其他的想法跟意見，如果有想討論的歡迎在下方留言。

# top1. 宣告變數的時候給預設型別
JavaScript 宣告變數的時候應該要給它預設的類型!
這樣做可以讓接手你的程式的人或是未來的自己再觀看程式碼上面可以清楚的知道這個變數預設給他定義的類型是什麼。
```js
# Bad
var name;
var userData;
var isOpen;
# Good
var name = "";
var userData = [];
var isOpen = false;
```
# top2. 使用 === 來進行判斷
寫判斷式的時候不要再用 == 來判斷，應該全部都改成 ===!
我們都知道JavaScript是一個弱型別語言，使用==來判斷就會出現像是 "1" == 1 是 true 的奇怪現象，為了避免判斷上面出現這種我要Number但是你給我String的情況，我們判斷都應該使用===。
```js
# Bad
if(val == 1){
  console.log('ok')
}
# Good
if(val === 1){
  console.log('ok')
}
```
# top3. 使用 return 代替 if else
if else沒有不好，只是某些情形使用return會讓你的code更直觀 !
我們應該讓看code的人像是再讀code，而不是讀邏輯，這樣可以加快別人理解我們code，也可以避免過於複雜的邏輯。
```js
# Bad
if(value === ""){
  alert("欄位不得為空")
}else{
  // 後續其他動作
}
# Good
if(value === ""){
  alert("欄位不得為空");
  return;
}

// 後續其他動作
```js
# Good
if(value === "") return alert("欄位不得為空");
// 後續其他動作
# top4. 不要直接修改DOM的CSS
再改變DOM元素的style的時候，應該盡量避免直接用JavaScript操作CSS !
直接操作 CSS 會觸發瀏覽器的重新繪製，影響效能，而且接手你專案的人不會知道你用JavaScript去改變style，會增加數倍維護成本，建議是使用add或remove的class方法來取代，當遇到修改style的時候就可以很方便的改CSS就好。

# Bad
document.getElementById("dom").style.color = '#f00';
# Good
//css
.textRed{
  color: #f00;
}
//javascript
document.getElementById("dom").classList.add('textRed');
document.getElementById("dom").classList.remove('textRed');
```
# top5. 簡單的動畫不要用 JavaScript 函式庫
請善用 css3 的 transition，動態也比較順暢
初學者學習到一些像是 jquery 的 javascript 函式庫時候就會喜歡把所有的動態交給函式庫來做，例如hover一個按鈕改變顏色或是選單跑出來等等，但是這樣在行動裝式上面會很卡不流暢，所以像是簡單的動態都其實可以交給css3 的transition來處理，會順暢很多。
```js
# Bad
// Js (jquery)
$("#btn").on('hover', function(){
    $(this).animate({top: "200"}, 300);
})
# Good
// CSS
#btn{
   top: 0px;
   transition: top 0.3s;
}
#btn:hover{
   top: 200px;
}
```
# top6. 篩選資料你應該用 filter
善加利用filter來篩選資料可以提高code的可讀性
蠻多人喜歡篩選資料的時候透過for迴圈在裡面用 if 來篩選資料，不能說是錯，但是code看起來很冗長，不漂亮，我們應該使用filter來做資料的篩選。
```js
# Bad
var arr = [];
for(var i = 0; i < data.length; i++){
   if(data[i].money > 300){
      arr.push(data[i]);
   }
}
# Good
var arr = data.filter(function(obj){
    return obj.money > 300;
})
```
# top7. 妥善利用 console.log 來 debug
用console.log來確認程式的運行流程，避免程式執行跟自己想的不一樣!
我們都是用console.log來確認變數的內容，卻很少利用console.log來判斷程式的執行順序，尤其是遇到跟非同步執行有關的問題更應該先確保程式流程沒錯。
```js
# Bad
// 這是一個錯誤的例子
// 非同步，因為資料還沒有回來所以 return 的資料是空陣列
function getData(){
   var data = [];
   axios.get("/api/userData").then(function (response) {
       data = response.data;
   })
   .catch(function (error) {
       console.error(error);
   })
   return data;
}
var res = getData();  // ---->  []
# Good
// 雖然是錯誤的例子，但是在每個執行接 console.log()
// 透過這樣的 console.log() 方式可以清楚知道程式運行流程
function getData(){
   console.log(1);
   var data = [];
   console.log(2);
   axios.get("/api/userData").then(function (response) {
       console.log(3);
       data = response.data;
       console.log(4);
   })
   .catch(function (error) {
       console.error(error);
   })
   console.log(5);
   return data;
}
var res = getData();  // ---->  []
// log : 1 -> 2 -> 5 -> 3 -> 4
// 從這邊可以清楚知道程式不是照自己想的 1 -> 2 -> 3 -> 4 -> 5 這樣執行的
// 方便我們 debug
```
# top8. 整合 <script> 載入的進入點
主程式不要分檔寫，以確保程式流程 !
不要依照設計稿的區塊來分檔寫 js，應該要將主程式集中，尤其是在做區塊的非同步處理然後要跨區塊做資料溝通時，分檔撰寫只會給自己找麻煩。
```js
# Bad
<script src="./js/jquery.min.js"></script>
// 以下都是主程式
<script src="./js/slidshow.js"></script>
<script src="./js/banner.js"></script>
<script src="./js/tab.js"></script>
<script src="./js/login.js"></script>
<script src="./js/index.js"></script>
# Good
<script src="./js/jquery.min.js"></script>
<script src="./js/index.js"></script>
# top9. 不要操作原始陣列
當傳入array進去函式裡面進行操作的時候，我們應該先拷貝一份陣列 !
傳入函式的array因為記憶體指向都是同一個，所以如果我們把傳入的array直接操作會修改到原始資料，為了避免這種情況我們應該要用slice(0)先複製一份陣列再來操作。

# Bad
function Num(list){
   list.push("9");
}
var arr = [1,2,3];
Num(arr);
console.log(arr)  // ---> [1, 2, 3, "9"]

# Good
function Num(list){
    var newArr = list.slice(0)
    newArr.push("9");
}
var arr = [1,2,3];
Num(arr); 
console.log(arr)  // ---> [1, 2, 3]
```
# top10. 不要bind this
this的指向一直都是JavaScript中最令人頭疼的問題，尤其是為了用function來模擬class的使用上面，常常需要讓綁定事件內this指向到function ( class )的實體上，所以常會使用到bind，使用bind會造成函式的記憶體增加，我們應該使用變數來儲存this來調用，而不是bind。
```js
# Bad
function Apple(){
    this.name = "mike";
    var btn = document.getElementById("btn");
    btn.addEventListener("click", function(){
        alert(this.name);
    }.bind(this));
}
new Apple();

# Good
function Apple(){
    this.name = "mike";
    var self = this;
    var btn = document.getElementById("btn");
    btn.addEventListener("click", function(){
        alert(self.name);
    });
}
new Apple();
```
這邊就是我整理出來的10個新手必知的 JavaScript 實用技巧，其實還有很多東西可以說，不過偏向概念不是技巧的我就沒有放上來了，下次可以在寫一篇概念篇。

我覺得上面列出的技巧只要平常在寫code的時候多加注意，是可以避免很多新手常遇到的問題，也可以更加了解JavaScript這個語言的。

我跟 hiskio 合作推出JavaScript入門到中階的線上課程，目前好評預售中，有興趣的朋友可以參考看看。

現代 JavaScript 職人之路-入門、進階、實戰、面試詳解組合
