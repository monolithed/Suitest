# Suitest

Suitest provides easy unit testing for JavaScript code

* Very simple to use
* Client-side and server-side (including NodeJS) support
* One of the most lightweightest libraries for unit testing
* Support for working with asynchronous code


##Synopsis:

```javascript
.test( name, callback, [, context ] );
.exec( x, [, y, context ] );
.done( [ name ] );
.text( description );
.stop();
.is();
```

### Screenshot;

![Suitest](http://habrastorage.org/storage2/3da/9a6/450/3da9a6450bae8151d3f8e46034bcca9b.png "Suitest")

### .test ( name, callback, [, context ] );

```javascript
var unit = new Suitest;

unit.test('test name', function(unit) {
	unit.exec(true, 1); // true
	unit.done();
});
```

### .exec ( x, [, y, context ] );


*Using with one parameter:*

```javascript
unit.exec(true); // true
```

*Using with two parameter:*

```javascript
unit.exec(true, 1); // true, because default operation is ==
```

*Using with three parameters:*

```javascript
unit.exec(true, 1, '==='); // false, because true and 1 are not equivalent
```


### .done ( [ name ] );

*Simple using:*

```javascript
unit.done();
```

*Testing asynchronous code:*

```javascript
unit.test('test name', function(unit) {
	setTimeout(function() {
		unit.exec(true, 1); // true
		unit.done();
	}, 2000);
});
```

### .text( description );

```javascript
unit.text('Test description');
```

### .stop ();

```javascript
unit.stop();
```


### is()

```javascript
unit.exec(true, 1);
unit.is(); // true
```


## Chaining (Fluent interface)


```javascript
var unit = new Suitest;

unit
.test('test 1', function(unit) {
	unit.exec(true, 1).done();
})

.test('test 2', function(unit) {
	unit.text('test description').exec(true, 1).done();
})

.test('test 2', function(unit) {
	if (!unit.exec(true, 1).is())
		unit.stop();
});
```


##.

* License
   Suitest is licensed under the MIT (MIT_LICENSE.txt) license

* Copyright (c) 2012 [Alexander Guinness] (https://github.com/monolithed)