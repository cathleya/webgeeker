# ES6 : new String methods

## 1 .startsWith()

```js
const course = 'RFB1';

course.startsWith('RFB');
//true
course.startsWith('rfb');
//false

const flightNumber = '20-AC2018-jz';

flightNumber.startsWith('AC');
//false
flightNumber.startsWith('AC', 3);
//true

``` 

## 2  .endsWith()

```js
const flightNumber = '20-AC2018-jz';
flightNumber.endsWith(`jz`);
//true
flightNumber.endsWith(`JZ`);
//false
const accountNumber = '825242631RT0001';
accountNumber.endsWith('RT');
//false
accountNumber.endsWith('RT', 11);
//true

``` 

## 3 .includes() ? .contains()

> 作为一个旁白，它最初应该被称为.contains()，但它已经改变为.includes()，因为与MooTool库的一些冲突和他们修改原型的方式。

```js
const flightNumber = '20-AC2018-jz';
flightNumber.includes('AC');
//true
flightNumber.includes('ac');
//false

``` 

## 4 .repeat() and String Padding

```js
const make = 'BMW';
const model = 'x5'
const colour = 'Royal Blue';

const leftPad = (str, length = 10) => {
    return `${' '.repeat(length - str.length)}${str}`;
}

console.log(leftPad(make));
console.log(leftPad(model));
console.log(leftPad(colour));

``` 

![ES6 new String repeat() & right-align.png](ES6 new String repeat() & right-align.png)

## errors

> error1

![ES6 new-error.png](./ES6%20new-error.png)


> error2

![ES6 new-error2.png](./ES6%20new-error2.png)



ref link:  
http://wesbos.com/new-es6-string-methods/

https://gist.github.com/xgqfrms-GitHub/8b20b576edb8c9e74e6dfae2655c7077
