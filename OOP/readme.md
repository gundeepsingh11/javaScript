## object literial

######

```javascript
const book1 = {
  title: 'book one',
  author: 'gundeep',
  year: '2013',
  getSummary: function() {
    return `${this.title} was written by ${this.author} in year ${this.year}`;
  },
};

console.log(book1.getSummary());
```

---

## Constructor

```javascript
function Book(title, author, year) {
  this.title = title;
  this.author = author;
  this.year = year;
  this.getSummart = function() {
    return `${this.title} was written by ${this.author} in year ${this.year}`;
  };
}

const book1 = new Book('book one', 'gundeep', '2013');

console.log(book1);
```

---

## Proto

```javascript
function Book(title, author, year) {
  this.title = title;
  this.author = author;
  this.year = year;
}

Book.prototype.getSummary = function() {
  return `${this.title} was written by ${this.author} in year ${this.year}`;
};

// getAge
Book.prototype.getAge = function() {
  const years = new Date().getFullYear() - this.year;
  return `${this.title} is ${years} years old`;
};

// revised year
Book.prototype.revisedYear = function(newYear) {
  this.year = newYear;
  this.revised = true;
};

const book1 = new Book('book one', 'gundeep', '2013');
book1.revisedYear('2018');
console.log(book1);
```

---

## inheritence

```javascript
function Book(title, author, year) {
  this.title = title;
  this.author = author;
  this.year = year;
}

Book.prototype.getSummary = function() {
  return `${this.title} was written by ${this.author} in year ${this.year}`;
};

function Mag(title, author, year, month) {
  Book.call(this, title, author, year);

  this.month = month;
}

Mag.prototype = Object.create(Book.prototype);

const mag1 = new Mag('mag one', 'gundeep', '2019', 'jan');

console.log(mag1);
```

---

## object create

```javascript
const book1 = {
  getSummary: function() {
    return `${this.title} was written by ${this.author} in year ${this.year}`;
  },
  getAge: function() {
    const years = new Date().getFullYear() - this.year;
    return `${this.title} is ${years} years old`;
  },
};

const book = Object.create(book1, {
  title: { value: 'book One' },
  author: { value: 'gundeep' },
  year: { value: 2017 },
});

console.log('hello', book);
```

---

## class in es6

```javascript
class Book {
  constructor(title, author, year) {
    this.title = title;
    this.author = author;
    this.year = year;
  }
  getSummary() {
    return `${this.title} was written by ${this.author} in year ${this.year}`;
  }
}

class Mag extends Book {
  constructor(title, author, year, month) {
    super(title, author, year);
    this.month = month;
  }
}

const mag1 = new Mag('book one', 'gundeep', '2017', 'jan');
console.log(mag1.getSummary());
```
