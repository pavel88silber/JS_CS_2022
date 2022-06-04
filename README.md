# JavsScript CheetSheet 2022 :office:

| Context  | Array | Function | OOP |
| ------------- | ------------- | ------------- | ------------- |
|[bind](#bind):cloud_with_lightning:| [Array [map filter reduce find]](#map-filter-reduce-find):pushpin:  | [Callback](#callback):hourglass_flowing_sand: | [Example](#oop-example):dagger:
| [this arrow f() Call Apply](#this-arrow-f-call-apply):desert_island:	  | Content Cell  | coooooooo |

| Request / AJAX  | Promise | Local Storage |
| ------------- | ------------- | ------------- |
|[Fetch](#fetch):stethoscope:| [Promise + Promise.all](#promise-all):rainbow_flag: | [Example](#local-storage):safety_pin: |
| [XMLHttpRequest](#xmlhttprequest):basket: | Content Cell  | coooooooo |

---

### :dagger:
### [OOP Example]

 ---
 ### Create Class
 ```js
 class Valid {
    constructor(email, password, isValid) {
        this.email = email
        this.password = password
        this.isValid = isValid
    }
    validate() {
        if (`${(this.password).length}` >= 6) {
            this.isValid = true
            console.log('isValid = ' + this.isValid);
        } else {
            console.log('isValid = ' + this.isValid);
        }
    }
}
```

---
### Class Extends
```js
class Valid2 extends Valid {
    constructor(email, password, isValid, emailError = '', passwordError = '') {
        super(email, password, isValid)
        this.emailError = emailError
        this.passwordError = passwordError
    }
    // Метод переопределяется если такое же имя в родительском классе
    validate() {
        if (this.password.length >= 6 && this.email) {
            this.isValid = true
            console.log('isValid = ' + this.isValid);
        }

        if (this.password.length < 6) {
            this.isValid = false
            this.passwordError = 'min length 6'
            console.log('isValid = ' + this.isValid);
            console.log('Password Error: ' + this.passwordError);
        }
        if (!this.email) {
            this.emailError = 'emailEmpty'
            console.log('Email Error: ' + this.emailError);
        }
    }
}
```

---
### Instance of Class
```js
let valid6 = new Valid2('qwe@mail.yy', '12345678')

// Class method
valid6.validate()
```

---

### :safety_pin:
### [Local Storage]
```js
const out6 = document.querySelector('.out-6');
const b6 = document.querySelector('#b-6');
const a6 = {
    'hello': 6,
    'hi': 'mahai'
};

const t1 = () => {
    localStorage.setItem("a6_key", JSON.stringify(a6));

    console.log('JSON.stringify: ==> ' + a6);


    const ls6 = localStorage.getItem("a6_key");

    let newLs6 = JSON.parse(ls6);

    console.log('JSON.stringify: ' + newLs6);
    console.log(typeof newLs6); // object

    for (let k in newLs6) {
        out6.innerHTML += `${k} <br>`;
        console.log(k);

    }

}

b6.onclick = () => t1();
localStorage.clear();
```




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

### :basket:
### [XMLHttpRequest]
```js
let xhttp = new XMLHttpRequest()

xhttp.onreadystatechange = function () {
    if (this.readyState == 4 && this.status == 200) {
        myFunction(this.responseText)
    }
}

xhttp.open("GET", "http://localhost:8001?num1=888&num2=88", true)
xhttp.send()

function myFunction(data) {
    console.log(data);
}

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
---
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
