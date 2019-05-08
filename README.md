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
