- Factory Function
```js
function createCircle(radius) {
  return {
    radius,
    draw() {
      console.log('draw');
    },
  };
}
const circle = createCircle(1);
```
- Constuctor Function
```js
function Circle(radius) {
  console.log('this', this);
  this.radius = radius;
  this.draw = function () {
    console.log('draw');
  };
}
const another = new Circle(1);
```