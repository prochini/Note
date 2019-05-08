# JSON
```
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
