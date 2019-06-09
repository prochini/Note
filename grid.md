## Grid
.grid{
    display:grid;
    grid-gap: 6px;
    grid-template-columns: repeat(auto-fill, minmax(10em, 1fr))
}
### 點線面

- 面
- 線
- 設定間距

## 用法

- grid gap
## 格線列

## 格線欄
.container{
    display:grid;

}

## 區域名稱
grid-area

## 塞到隔線
適合建立主版型
.container{
    font-size: 30px;
    width: 100%;
    height: 800px;
    outline:2px solid #f00;
    display:grid;
    grid-template-rows:1fr 1fr 1fr 1fr;
    grid-template-columns: 25% 25% 25% 25%;
    grid-template-areas:
    "B3 . B1 B1 "
    "B3 . B1 B1"
    "B3 . B2 B2"
    "B3 . B2 B2";
    grid-gap: 10px;
    padding: 10px;
}
.AA{ grid-area: B1;
    background: #faa;
}
.BB{ grid-area: B2;
background: #afa; 
}
.CC{ grid-area: B3; 
background: #aff;
}