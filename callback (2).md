同步  阻塞
const result = getdata()
console.log(result)

HW2 遇到的問題
1. 就是" 新增留言後更新最新留言 "的部分
2. addEventListener('load')一直以為 load 是 window 在 load 所以一定要 reload
3. reload 連續發送留言有些留言成功，但有些留言消失，發現是 POST 的 AJAX 還沒有建立成功，就馬上 GET 所以撈不到最新的留言，後來把 addcomment 改成同步，也可能是　POST 被　reload　打斷。
4. 以為 getcomment 結果都沒有更新留言，我以為完全沒更新，後來才發現滾動軸一直變長，只有一樣的迴圈重複跑，所以看起來都一樣。
5. 不太確定是因為改成 AJAX 改成同步還是因為有用 callback 才成功拿到最新留言，或只是把舊留言清掉，不知道我這樣寫對不對，callback 的概念是知道，但是實際應用方面一直很弱該怎麼辦 QQ 我要用但不知道怎麼用，每次都卡死在這。
6. addeventlistener 要怎麼帶參數進去也很傷腦筋，還有 callback 怎麼帶參數進去，比如要加括號還是帶變數
7. 嘗試了 setInterval 每 5 秒發送一個 POST 取得最新的包括同學的留言，要是發現 json[0].id > 舊的json[0].id，就定時新增那幾個留言，嘗試把 function 提取出來一直失敗，實作的部分作不出來就先放著，感覺現在的網站也不會這樣搞 XD 太消耗資源。
8. 變樹命名的問題，每發一個 request 所有變數的名稱都要取新的嗎? ex: request, xhm, http 
9. 用 debugger 看他跑了好幾次，POST 的 status 都沒在變，不然想說要是 create 成功再撈留言。
10. 真的卡很久~要是沒靠同學幫忙也是過不了~不知道關鍵字是什麼~查到很多 jQuery Ajax 看起來很好用
11. 事件排序的部分要怎麼辦阿~如果有一堆 request 又有 一堆 event 感覺就很難控制。
12. 看到留言成功刷新，真的感動不行 T_T 


也只有這段時間有實間好好享受自己 DIY 純JS 的樂趣吧~ 之後就直接拿別人的東西來用了
由奢入儉難，由儉入奢易