# JS CS 2022 :office:

## [Context [this arrow f()]](#this-arrow-f):desert_island:	
## [Array [map filter reduce find]](#map-filter-reduce-find):pushpin:

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
### [this arrow f]
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
-RED
+ Green green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
