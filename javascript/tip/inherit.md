# 상속

ES5
```js
function Person(name, age) {
  this.name = name;
  this.age = age;
}
```

```js
function Student(name, age, grade) {
  Person.call(this, name, age);
  this.grade = grade;
}

Student.prototype = Object.create(Person.prototype);
Student.prototype.constructor = Student;
```
ES6
```js
// ES
class Student extends Person {
  constructor(name, age, grade) {
    super(name, age);
    this.grade = grade;
  }
}
```

```js
// ES6
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }
}
```