# js-fun

## Frequency of a given number in given Array
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
### Second way usin reduce fn
```js
var data = [5, 5, 5, 2, 2, 2, 2, 2, 9, 4]

function count(arr, ele) {
  return arr.reduce((prev, curr) => (prev[curr] = ++prev[curr] || 1, prev), {})[ele];
}
console.log(count(arr, 5));
```
### Third way using Map
```js
var data = [5, 5, 5, 2, 2, 2, 2, 2, 9, 4]

function count(arr, ele) {
  return new Map([...new Set(arr)].map(
        x => [x, arr.filter(y => y === x).length]
    )).get(ele);
}
console.log(count(arr, 5);
```
### Fourth way using filter
```js 
var data = [5, 5, 5, 2, 2, 2, 2, 2, 9, 4]
function count(arr, ele){
  return data.filter(function(value){
      return value === ele;
  }).length;
}
console.log(count(data, 5));
```

## Count frequency of a letter in given word or Sentence(case sensitive)
```js
var s="ABRACADABRA";
function frequencyOfLetter(str, letter){
 return s.split('').reduce((a, c)=>{a[c]++?0:a[c]=1;return a},{})[letter];
}
console.log(frequencyOfLetter(s, 'A');
```


## an array containing many duplicat element but one unique element find out unique integer 
###  O(2n): loop + loop => O(n) + O(n) space
```js
function find_unique(array) {
  var n = array.length;
  var hash = {}, result = null;

  for (var i = 0; i < n; i++) {
    if (array[i] in hash) {
      hash[array[i]] += 1;
    } else {
      hash[array[i]] = 1;
    }
  }

  for (var j in hash) {
    if (hash[j] == 1) {
      result = j;
    }
  }

  return result;
}
var uni1 = find_unique_hash([1, 1, 5, 5, 3, 6, 6]);
```
### O(n) with no space: deep into Bits for solution
```js
function find_unique(array) {
  var result = 0, n = array.length;

  for (var i = 0; i < n; i++) {
    result ^= array[i]; 
  }

  return result;
}
var uni2 = find_unique_xor([1, 1, 5, 5, 3, 6, 6]);
```
##### [source](https://gist.github.com/isRuslan/4e5171a810a4c5e1db98)


## Find Unique elements in Array
### First way
```js
Array.prototype.unique = function() {
    var arr = [];
    for(var i = 0; i < this.length; i++) {
        if(!arr.includes(this[i])) {
            arr.push(this[i]);
        }
    }
    return arr; 
}
var data = [1, 1, 5, 5, 3, 6, 6];
console.log(data.unique);
```
### second way  ``(O(n * log(n)))`` 
```js
function uniqueElements(data) {
    return data.filter(function (a) {
        return data.indexOf(a) === data.lastIndexOf(a)
    });
}
var sampleValues = [1, 4, 5, 2, 'a', 'e', 'b', 'e', 2, 2, 4];
var uniqueValues = uniqueElements(sampleValues);
console.log(uniqueValues);
```

### Third way (using Set data structure)
```js
var sampleValues = [1, 4, 5, 2, 'a', 'e', 'b', 'e', 2, 2, 4];
var uniqueValues = [...new Set(sampleValues)]; 
console.log(uniqueValues); //[1, 4, 5, 2, "a", "e", "b"]
```
## Finding Non unique element in array
```js
function nonUnique(data) {
    return data.filter(function (a) {
        return data.indexOf(a) !== data.lastIndexOf(a)
    });
}
var sampleValues = [1, 4, 5, 2, 'a', 'e', 'b', 'e', 2, 2, 4];
console.log(nonUnique(sampleValues));

```
