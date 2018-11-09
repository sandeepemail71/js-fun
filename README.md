# js-fun
## Finding elements in array which are not unique in array
### First way
```js
 var arr = [5, 5, 5, 2, 2, 2, 2, 2, 9, 4];
 function count(arr, element){
  var counts = {};

  for (var i = 0; i < arr.length; i++) {
    var num = arr[i];
    counts[num] = counts[num] ? counts[num] + 1 : 1;
    //counts[num] = (counts[num] || 0) + 1     //we can do like that also, even much better way
  }
  return counts[eleement];
}
console.log(count(arr, 5));
```
### Second way
```js
var data = [5, 5, 5, 2, 2, 2, 2, 2, 9, 4]

function count(arr, ele) {
  return arr.reduce((prev, curr) => (prev[curr] = ++prev[curr] || 1, prev), {})[ele];
}
console.log(count(arr, 5));
```
### Third way
```js
var data = [5, 5, 5, 2, 2, 2, 2, 2, 9, 4]

function count(arr, ele) {
  return new Map([...new Set(arr)].map(
        x => [x, arr.filter(y => y === x).length]
    )).get(ele);
}
console.log(count(arr, 5);
```
### Fourth way
```js 
var data = [5, 5, 5, 2, 2, 2, 2, 2, 9, 4]
function count(arr, ele){
  return data.filter(function(value){
      return value === ele;
  }).length;
}
console.log(count(data, 5));
```
