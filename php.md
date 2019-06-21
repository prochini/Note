## 後端到底是?
1. 有一個`伺服器`來處理 Request & Response
2. 需要`寫程式`來處理
3. 需要有`資料庫`儲存資料

伺服器 Apaache
寫程式 PHP
資料庫 MySQL

## PHP 語法基礎
- 用 . 拼接字串
1. 變數前一定要加 $ 
2. 結尾一定要加分號
```php
<?php
$a = 1;
$b ="bbbbb";
echo $a . $b;
?>
```

- if ..else 

1. 少個 ; 也不行

```php
	$score = 70;
	if ($score > 60) {
		echo"pass";
	} else {
		echo"fail";
    }
```

- for 迴圈
1. 變數前一定要加 $ 
2. 空行 ."<br>" 加HTML標籤
3. 可檢視網頁原始碼
```php
	for ($i = 1; $i <= 10; $i++){
		echo $i."<br>";
    }
```
- Array
1. var_dump($arr) 印出 value, type
2. print_r 印出value
3. array 長度

```php
	$arr = array(1, 2, 3, 4, "prochini");
	echo sizeof($arr) . "<br>";
	var_dump($arr);
	print_r($arr);
```
- function 變數

```php
function add($a, $b){
	return $a +$b;
}
echo add(1, 5);
```

##  Apache 與 PHP 原理簡介

- 機制
request => apache => (php => html) => apache => response

- server 決定 response 的網址

- apache server: 程式
function server(request) {
    ...
    $output = handle_request(user.php)
    return $output
}

### 資料庫系統
- server => 程式: 專門處理 request 跟 response 的程式
- 資料庫系統 => 程式: 專門處理資料的程式

1. relational database 關聯式資料庫
- MySQL
- PostgreSQL
2. NoSQL (Not only SQL)

## MySQL 簡介

Table schema 簡介

- 結構
- 名稱/型態

## MySQL 語法基礎
- 查詢 Select
- 新增 Insert
- 修改 Update
- 刪除 Delete

## 實戰：Job board 職缺報報
Job board，職缺報報
要寫出一個管理後台管理職缺，基本 CRUD
還要實作簡單的前台讓大家看有哪些職缺 


前台
index.php 展現所有職缺
job.php?id=1


管理後台
admin.php 展示所有職缺
add.php 新增職缺
update.php 更改職缺

資料結構
職缺 => ???
1. 職缺名稱
2. 職缺說明
3. 職缺連結
4. 職缺連結

# get 的方式
？　ｉｄ　代在網址上
http://localhost/JOB/delete.php?id=14

更多語法
- 引入其他檔案
`<?php require_once('./conn.php') ?>`
- FETCH_ASSOC : 返回在結果集中返回的按列名索引的數組。

- 建立連線
qli('localhost', 'my_user', 'my_password', 'my_db');`

- 選擇要顯示的項目
`sql ='SELECT * from jobs ORDER BY created_at DESC';`

SQL資料類型
- CHAR : 上限255，固定長度，不足的地方自動補空白，讀取數據時需再處理刪除空格
- VARCHAR : 可變動長度
- TEXT : 不可限長度

BLOG

BLOG 

資料結構

產品樣貌

分類功能、發表文章、ABOUT

index,php
article.php
about.php

admin.php
add.php
handle_add.php
delete.php


標籤TAG
側邊攔
NAV BAR
所有文章


單一文章頁面


## article 
- id
- title
- comtent
- category_id
- created_at 

## catagories
- id 
- name
