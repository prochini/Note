https://notfalse.net/http-series

1. 建構一個 XMLHttpRequest 物件:
var xhr = new XMLHttpRequest();

2.
https://lidemy-book-store.herokuapp.com/posts?_limit=20&_sort=id&_order=desc

說明	Method	path	參數	範例
獲取所有留言	GET	/posts	_limit:限制回傳資料數量, _sort:要排序的欄位, _order:順序，可填 asc 或 desc	/posts?_limit=20
新增留言	POST	/posts	content: 內容	無


let id = 'ry76htktupl8mlicd29yf9xhrc2opo'

curl -H 'Accept: application/vnd.twitchtv.v5+json' \
-H 'Client-ID: ry76htktupl8mlicd29yf9xhrc2opo' \
-X GET 'https://api.twitch.tv/kraken/streams/?game=League%20of%20Legends&limit=20'

Query string parameters
In the reference documentation for endpoints, query string parameters are listed where they apply to an endpoint. The syntax for using query string parameters is as follows:

<URL for the endpoint, with required params>?<query param 1>=<value 1>&<query param 2>=<value 2>...
For example, the Get Feed Posts endpoint has three optional query string parameters, limit, cursor, and comments. If all three query string parameters are used, the URL is:

https://api.twitch.tv/kraken/feed/<feed user ID>/posts?limit=<limit value>&cursor=<cursor value>
&comments=<comments value>

//offset = (page - 1) * itemsPerPage + 1.
// loadData('.loadMore', '&offset=21');


var xhr = new XMLHttpRequest;
console.log('UNSENT: ', xhr.status);

xhr.open('GET', '/server');
console.log('OPENED: ', xhr.status);

xhr.onprogress = function () {
  console.log('LOADING: ', xhr.status);
};

xhr.onload = function () {
  console.log('DONE: ', xhr.status);
};

xhr.send();

/**
 * Outputs the following:
 *
 * UNSENT: 0
 * OPENED: 0
 * LOADING: 200
 * DONE: 200
 */