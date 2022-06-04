# JS CS 2022 :office:

| Context  | Array | Function |
| ------------- | ------------- | ------------- |
|[bind](#bind):cloud_with_lightning:| [Array [map filter reduce find]](#map-filter-reduce-find):pushpin:  | [Callback](#callback):hourglass_flowing_sand: |
| [this arrow f() Call Apply](#this-arrow-f-call-apply):desert_island:	  | Content Cell  | coooooooo |

| HEADER  | HEADER | HEADER |
| ------------- | ------------- | ------------- |
|[Fetch](#fetch):stethoscope:| [Promise + Promise.all](#promise-all):rainbow_flag: | 456 |
| [Bind](#bind):funeral_urn:	  | Content Cell  | coooooooo |

---
### :pushpin:
### [map filter reduce find]
- **Array.prototype.map()** takes an array, does something on its elements and returns an array with the transformed elements.
- **Array.prototype.filter()** takes an array, decides element by element if it should keep it or not and returns an array with the kept elements only
- **Array.prototype.reduce()** takes an array and aggregates the elements into a single value (which is returned)
- **Array.prototype.find()** takes an array, and returns the first element that satisfies the provided condition.

```js
const numbers = [0, 1, 2, 3, 4, 5, 6];
const doubledNumbers = numbers.map(n => n * 2); // [0, 2, 4, 6, 8, 10, 12]
const evenNumbers = numbers.filter(n => n % 2 === 0); // [0, 2, 4, 6]
const sum = numbers.reduce((prev, next) => prev + next, 0); // 21
const greaterThanFour = numbers.find((n) => n>4); // 5
```

```js
const students = [
  { name: "Nick", grade: 10 },
  { name: "John", grade: 15 },
  { name: "Julia", grade: 19 },
  { name: "Nathalie", grade: 9 },
];

const aboveTenSum = students
  .map(student => student.grade) // we map the students array to an array of their grades
  .filter(grade => grade >= 10) // we filter the grades array to keep those 10 or above
  .reduce((prev, next) => prev + next, 0); // we sum all the grades 10 or above one by one

console.log(aboveTenSum) // 44 -- 10 (Nick) + 15 (John) + 19 (Julia), Nathalie below 10 is ignored
```
---
### :desert_island:	
### [this arrow f Call Apply]
```js
// Контекст = область видимости + переменная this
// this = ссылка на объект, которая вызывает код в данный момент
```
```diff
-В стрелочной функции нет своего контеста (указывает на window)
```
```js
function f1(n) {
    this.textContent = n
    console.log(this)
}

document.querySelector('#btn-1').addEventListener("click", () => {
    f1.call(document.querySelector('#btn-2'), 'Harry') // bind context to (btn-2) + pass argument
})
```
```diff
! apply так же как и call но аргумент массив
```
### :funeral_urn:
### [Bind]
```js
//code
```
---
### :stethoscope:
### [Fetch]
```js
fetch('http://localhost:8001?num1=1&num2=88')
    .then(response => response.json())
    .then(console.log('Fetch Request '))
    .then(iJson => console.log(iJson))

    .then(data => {
        console.log(data);
        console.log(`Status => ${data.status}`);
        console.log(`URL => ${data.url}`);
        res = data
        return console.log(res);
    })
```
---
### :rainbow_flag:
### [Promise All]
```js
let num1 = new Promise((resolve, rej) => {
    fetch('http://localhost:8001?name=Kolya',
        // method: "GET",
        { mode: 'no-cors' },
        { responseType: 'json' }
    )
        .then(data => {
            resolve(data.text())
            // console.log(data);
        })
})

let num2 = new Promise((res, rej) => {
    fetch('http://localhost:8001?name2=Tuzik', {
        method: "GET",
        mode: 'no-cors'
    })
        .then(data => {
            console.log(data.text());
            res(data.text())
        })
})

let arr = [num1, num2]

Promise.all(arr).then(value => {
    console.log(value[1]);
    console.log(value[0]);
})
```

---


### :hourglass_flowing_sand:
### [Callback]
```js
function f1a(arr, cbFunc, where) {
    let newArr = arr.map(item => myPow(item))
    cbFunc(where, newArr)
}

const out3 = document.querySelector('.o3')

const myPow = num => Math.pow(num, 3)

function drawThis(block, elem) {
    block.textContent += elem
}

f1a([1, 2, 3, 4, 5], drawThis, out3)
```



---

```diff
-RED
+ Green green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
