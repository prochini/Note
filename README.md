# JSON
```Javascript
const request = require('request');
request(
    'https://reqres.in/api/users/2', 
    function (error, response, body) {
    const json = JSON.parse(body) // JASON格式的字串
    //console.log(json.data.first_name);
});

const obj ={
    name:'huli',
    job: 'none'
}
console.log(obj)

console.log(JSON.stringify(obj))

```


# request.METHOD()
These HTTP method convenience functions act just like request() but with a default method already set for you:

- request.get(): Defaults to method: "GET".
- request.post(): Defaults to method: "POST".
- request.put(): Defaults to method: "PUT".
- request.patch(): Defaults to method: "PATCH".
- request.del() / request.delete(): Defaults to method: "DELETE".
- request.head(): Defaults to method: "HEAD".
- request.options(): Defaults to method: "OPTIONS".


- 新增使用者/POST/new_user/users
- 刪除使用者/DELETE/delete_user
- 查詢使用者/GET/users_data/:id
- 使用者列表/GET/users_list
- 更改使用者/PATCH/update_user

