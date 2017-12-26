# Promise Anti-Patterns and Common Mistakes

### Anti-Pattern: Nested Promises ("Promise Hell")

(1) Linearly dependent Promises

Example task: execute getBook(), readBook(book) and returnBook(book) in order

_anti-pattern version_

```javascript
getBook()
  .then((book) => {
    return readBook(book)
      .then((book) => {
        return returnBook(book);
      });
  });
```

_refactored version_

```javascript
getBook()
  .then(book => readBook(book))
  .then(book => returnBook(book));
```

(2) Independent Promises

Example task: execute getA(), getB() and getC() in parallel

_anti-pattern version_

```javascript
getA()
  .then(() => {
    return getB()
      .then(() => {
        return getC();
      });
  });
```

_refactored version_

```javascript
Promise.all([getA(), getB(), getC()]);
```

(3) multiple dependent Promises

Example task: execute connectDB(), findAllBooks(db), getCurrentUser(db), getRecommendations(books, user) in order

_anti-pattern version_

```javascript
connectDB()
  .then((db) => {
    return findAllBooks(db)
      .then((books) => {
        return getCurrentUser(db)
          .then((user) => {
            return getRecommendations(books, user);
          });
      });
  });
```

_refactored version_

```javascript
const databasePromise = connectDatabase();
const booksPromise = databasePromise.then(findAllBooks);
const userPromise = databasePromise.then(getCurrentUser);
Promise.all([bookPromise, userPromise])
  .then([books, user] => getRecommendations(books, user));
```

### Anti-Pattern: Glorified Callbacks
Use `somethingAsync().then(success).catch(err)` instead of `somethingAsync().then(success, err)` often leads to unhandled errors and nested Promises.

_anti-pattern version_

```javascript
somethingAsync().then(function(result) {  
  // handle success
},
function(err) {  
  // handle error
});
```

_refactored version_

```javascript
somethingAsync()  
  .then(function(result) { 
    // handle success 
  })
  .catch(function(err) {
    // handle error
  });
```
It's best practice to add `catch()` to the end of the Promise chain for error handling. See [eslint-plugin-promise rule: catch-or-return](https://github.com/xjamundx/eslint-plugin-promise#rule-catch-or-return) for more examples.

### Common Mistake: Not Returning in `.then()`
Inside a `.then(function() { })` function, there are three things can be done:
1. return another promise
2. return a synchronous value (or undefined)
3. throw a synchronous error

It's best practice to always `return` inside `.then()`. See [eslint-plugin-promise rule: always-return](https://github.com/xjamundx/eslint-plugin-promise#rule-always-return) and [We have a problem with promises by Nolan Lawson](https://pouchdb.com/2015/05/18/we-have-a-problem-with-promises.html) for more examples.

**Always return or throw from inside a then() function as best practice.**

### Common Mistake: Passing a non-function to `.then()`
If you accidentally pass a non-function to `.then()`, it actually interprets as `.then(null)` which causes the previous promise's result fall thourgh.

```javascript
Promise.resolve('foo').then(Promise.resolve('bar')).then(function (result) {
  console.log(result);
});
```
..._is equivalent to_

```javascript
Promise.resolve('foo').then(null).then(function (result) {
  console.log(result);
});
```
that prints out `foo` instead of `bar`.

_refectored version_
```javascript
Promise.resolve('foo').then(function () {
  return Promise.resolve('bar');
}).then(function (result) {
  console.log(result);
});
```

---
Reference:
- [Promise Patterns & Anti-Patterns by Dave Atchley](http://www.datchley.name/promise-patterns-anti-patterns/)
- [How to escape Promise Hell by Ronald Chen](https://medium.com/@pyrolistical/how-to-get-out-of-promise-hell-8c20e0ab0513)
- [Promise Anti Patterns - Bluebird Wiki](https://github.com/petkaantonov/bluebird/wiki/Promise-anti-patterns#the-thensuccess-fail-anti-pattern)
- [We have a problem with promises by Nolan Lawson](https://pouchdb.com/2015/05/18/we-have-a-problem-with-promises.html)
- [eslint-plugin-promise by xjamundx](https://github.com/xjamundx/eslint-plugin-promise)

