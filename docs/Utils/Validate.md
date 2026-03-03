# Validate

`APIVERSION: 66`

`STATUS: ACTIVE`

A lightweight, stateless utility class that manages validating arguments.
Provides an easy way to follow a fail-fast principle and a design-by-contract programming approach.


**Author** Oleh Berehovskyi


**Group** Utils

## Methods
### Nullability
##### `public static void notNull(Object obj)`

Checks that the argument reference `obj` is not null.

###### Parameters

|Param|Description|
|---|---|
|`obj`|the object to check for nullity|

###### Throws

|Exception|Description|
|---|---|
|`NullPointerException`|if `obj` is null with the default exception message 'Argument object is null'|


**See** [Validate.isNotNull](Validate.isNotNull)

###### Example
```apex
Validate.notNull('foo'); // valid
Object obj;
Validate.notNull(obj); // throws a NullPointerException
```


##### `public static void notNull(Object obj, String message)`

Checks that the argument reference `obj` is not null.

###### Parameters

|Param|Description|
|---|---|
|`obj`|the object to check for nullity|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`NullPointerException`|if `obj` is null with the custom exception `message`|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.isNotNull](Validate.isNotNull)

###### Example
```apex
Validate.notNull('foo', 'The argument cannot be null'); // valid
Object obj;
Validate.notNull(obj, 'The argument cannot be null'); // throws a NullPointerException
```


##### `public static void notNull(Object obj, String message, List<Object> arguments)`

Checks that the argument reference `obj` is not null.

###### Parameters

|Param|Description|
|---|---|
|`obj`|the object to check for nullity|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`NullPointerException`|if `obj` is null with the custom exception `message`|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.isNotNull](Validate.isNotNull)

###### Example
```apex
Validate.notNull(
    obj,
    'The argument {0} cannot be null',
    new List<String>{ 'obj' }
); // throws a NullPointerException
```


---
### Conditions
##### `public static void isTrue(Boolean condition)`

Checks that the argument `condition` is true.

###### Parameters

|Param|Description|
|---|---|
|`condition`|the boolean expression to check|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `condition` evaluates to false with the default exception message 'Argument condition is false'|
|`NullPointerException`|if `condition` is null with the default exception message 'Argument object is null'|


**See** [Validate.isFalse](Validate.isFalse)


**See** [Assert.isTrue](Assert.isTrue)

###### Example
```apex
Validate.isTrue(i > 0);
Validate.isTrue(response.getStatusCode() == 200);
```


##### `public static void isTrue(Boolean condition, String message)`

Checks that the argument `condition` is true.

###### Parameters

|Param|Description|
|---|---|
|`condition`|the boolean expression to check|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `condition` evaluates to false with the custom exception `message`|
|`NullPointerException`|if `condition` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.isFalse](Validate.isFalse)


**See** [Assert.isTrue](Assert.isTrue)

###### Example
```apex
Validate.isTrue(i > 0, 'The argument value must be positive');
Validate.isTrue(response.getStatusCode() == 200, 'The status code must be 200');
```


##### `public static void isTrue(Boolean condition, Exception exc)`

Checks that the argument `condition` is true.

###### Parameters

|Param|Description|
|---|---|
|`condition`|the boolean expression to check|
|`exc`|the exception to throw|

###### Throws

|Exception|Description|
|---|---|
|`Exception`|if `condition` evaluates to false|
|`NullPointerException`|if `condition` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `exc` is null with the default exception message 'Argument object is null'|


**See** [Validate.isFalse](Validate.isFalse)


**See** [Assert.isTrue](Assert.isTrue)

###### Example
```apex
Validate.isTrue(i > 0, new CustomException());
Validate.isTrue(response.getStatusCode() == 200, new CalloutException());
```


##### `public static void isTrue(Boolean condition, String message, List<Object> arguments)`

Checks that the argument `condition` is true.

###### Parameters

|Param|Description|
|---|---|
|`condition`|the boolean expression to check|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `condition` evaluates to false with the custom exception `message`|
|`NullPointerException`|if `condition` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.isFalse](Validate.isFalse)


**See** [Assert.isTrue](Assert.isTrue)

###### Example
```apex
Validate.isTrue(
    n >= 0,
    'The argument should be positive, actual: {0}.',
    new List<Object>{ n }
);
```


---
### Iterables
##### `public static void notEmpty(Iterable<Object> iterable)`

Checks that the argument `iterable` is not empty.

###### Parameters

|Param|Description|
|---|---|
|`iterable`|the iterable to check for emptiness|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `iterable` is empty with the default exception message 'Argument iterable is empty'|
|`NullPointerException`|if `iterable` is null with the default exception message 'Argument object is null'|


**See** [Validate.noNullElements](Validate.noNullElements)

###### Example
```apex
Validate.notEmpty(new List<Integer>{ 1 }); // valid
Validate.notEmpty(new Set<String>()); // throws an IllegalArgumentException
```


##### `public static void notEmpty(Iterable<Object> iterable, String message)`

Checks that the argument `iterable` is not empty.

###### Parameters

|Param|Description|
|---|---|
|`iterable`|the iterable to check for emptiness|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `iterable` is empty with the custom exception `message`|
|`NullPointerException`|if `iterable` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.noNullElements](Validate.noNullElements)

###### Example
```apex
Validate.notEmpty(new List<Integer>{ 1 }, 'The iterable cannot be empty');
Validate.notEmpty(new Set<String>(), 'The set cannot be empty');
```


##### `public static void notEmpty(Iterable<Object> iterable, String message, List<Object> arguments)`

Checks that the argument `iterable` is not empty.

###### Parameters

|Param|Description|
|---|---|
|`iterable`|the iterable to check for emptiness|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `iterable` is empty with the custom exception `message`|
|`NullPointerException`|if `iterable` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.noNullElements](Validate.noNullElements)

###### Example
```apex
Validate.notEmpty(
    someIterable,
    'The iterable {0} cannot be empty',
    new List<String>{ 'someIterable' }
);
```


##### `public static void noNullElements(Iterable<Object> iterable)`

Checks that the argument `iterable` contains no null elements.

###### Parameters

|Param|Description|
|---|---|
|`iterable`|the iterable to check for null elements|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `iterable` contains a null element with the default exception message 'Argument iterable contains null element'|
|`NullPointerException`|if `iterable` is null with the default exception message 'Argument object is null'|


**See** [Validate.notEmpty](Validate.notEmpty)

###### Example
```apex
Validate.noNullElements(new List<Integer>{ 1 }); // valid
Validate.noNullElements(new Set<String>{ 1, null }); // throws an IllegalArgumentException
```


##### `public static void noNullElements(Iterable<Object> iterable, String message)`

Checks that the argument `iterable` contains no null elements.

###### Parameters

|Param|Description|
|---|---|
|`iterable`|the iterable to check for null elements|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `iterable` contains a null element with the custom exception `message`|
|`NullPointerException`|if `iterable` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.notEmpty](Validate.notEmpty)

###### Example
```apex
Validate.noNullElements(someIterable, 'The iterable cannot contain null elements');
Validate.noNullElements(
    (Iterable<String>) someStringSet,
    'The set cannot contain null elements'
);
```


##### `public static void noNullElements(Iterable<Object> iterable, String message, List<Object> arguments)`

Checks that the argument `iterable` contains no null elements.

###### Parameters

|Param|Description|
|---|---|
|`iterable`|the iterable to check for null elements|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `iterable` contains a null element with the custom exception `message`|
|`NullPointerException`|if `iterable` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.notEmpty](Validate.notEmpty)

###### Example
```apex
Validate.noNullElements(
    someIterable,
    'The iterable {0} cannot contain null elements',
    new List<String>{ 'someIterable' }
);
```


##### `public static void index(Iterable<Object> iterable, Integer index)`

Checks that the `index` is within the bounds of the argument `iterable`.

###### Parameters

|Param|Description|
|---|---|
|`iterable`|the iterable to check|
|`index`|the index to check|

###### Throws

|Exception|Description|
|---|---|
|`IndexOutOfBoundsException`|if `index` is invalid with the default formatted exception message 'Iterable index out of bounds: {0}'|
|`NullPointerException`|if `iterable` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `index` is null with the default exception message 'Argument object is null'|


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.index(
    new List<String>{ 'foo', 'bar' },
    3
); // throws an IndexOutOfBoundsException
```


##### `public static void index(Iterable<Object> objs, Integer index, String message)`

Checks that the `index` is within the bounds of the argument `iterable`.

###### Parameters

|Param|Description|
|---|---|
|`objs`|the iterable to check|
|`index`|the index to check|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IndexOutOfBoundsException`|if `index` is invalid with the custom exception `message`|
|`NullPointerException`|if `iterable` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `index` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.index(
    new List<String>{ 'foo', 'bar' },
    3,
    'Invalid index'
); // throws an IndexOutOfBoundsException
```


##### `public static void index(Iterable<Object> iterable, Integer index, String message, List<Object> arguments)`

Checks that the `index` is within the bounds of the argument `iterable`.

###### Parameters

|Param|Description|
|---|---|
|`iterable`|the iterable to check|
|`index`|the index to check|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IndexOutOfBoundsException`|if `index` is invalid with the custom exception `message`|
|`NullPointerException`|if `iterable` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `index` is null with the default exception message 'Argument object is null'|
|`IndexOutOfBoundsException`|if `index` is less than 0 with the custom exception `message`|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.index(
    new List<String>{ 'foo', 'bar' },
    3,
    'Invalid index: {0}',
    new List<Integer>{ 3 }
); // throws an IndexOutOfBoundsException
```


---
### Strings
##### `public static void notBlank(String str)`

Checks that the argument string `str` is not whitespace nor empty (''), nor null.

###### Parameters

|Param|Description|
|---|---|
|`str`|the string to check for not being blank|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `str` is whitespace or empty ('') with the default exception message 'Argument string is blank'|
|`NullPointerException`|if `str` is null with the default exception message 'Argument object is null'|


**See** [Validate.notEmpty](Validate.notEmpty)

###### Example
```apex
Validate.notBlank(' '); // throws an IllegalArgumentException
```


##### `public static void notBlank(String str, String message)`

Checks that the argument string `str` is not whitespace nor empty (''), nor null.

###### Parameters

|Param|Description|
|---|---|
|`str`|the string to check for not being blank|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `str` is whitespace or empty ('') with the custom exception `message`|
|`NullPointerException`|if `str` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.notEmpty](Validate.notEmpty)

###### Example
```apex
Validate.notBlank(
    ' ',
    'The string cannot be blank'
); // throws an IllegalArgumentException
```


##### `public static void notBlank(String str, String message, List<Object> arguments)`

Checks that the argument string `str` is not whitespace nor empty (''), nor null.

###### Parameters

|Param|Description|
|---|---|
|`str`|the string to check for not being blank|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `str` is whitespace or empty ('') with the custom exception `message`|
|`NullPointerException`|if `str` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.notEmpty](Validate.notEmpty)

###### Example
```apex
Validate.notBlank(
    ' ',
    'The string cannot be blank. {0}',
    new List<String>{ 'Status code: 400' }
); // throws an IllegalArgumentException
```


##### `public static void notEmpty(String str)`

Checks that the argument string `str` is not empty (''), nor null.

###### Parameters

|Param|Description|
|---|---|
|`str`|the string to check for not being empty|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `str` is empty ('') with the default exception message 'Argument string is empty'|
|`NullPointerException`|if `str` is null with the default exception message 'Argument object is null'|


**See** [Validate.notBlank](Validate.notBlank)

###### Example
```apex
Validate.notEmpty(''); // throws an IllegalArgumentException
```


##### `public static void notEmpty(String str, String message)`

Checks that the argument string `str` is not empty (''), nor null.

###### Parameters

|Param|Description|
|---|---|
|`str`|the string to check for not being empty|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `str` is empty ('') with the custom exception `message`|
|`NullPointerException`|if `str` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.notBlank](Validate.notBlank)

###### Example
```apex
Validate.notEmpty(
    '',
    'The string cannot be empty'
); // throws an IllegalArgumentException
```


##### `public static void notEmpty(String str, String message, List<Object> arguments)`

Checks that the argument string `str` is not empty (''), nor null.

###### Parameters

|Param|Description|
|---|---|
|`str`|the string to check for not being empty|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `str` is empty ('') with the custom exception `message`|
|`NullPointerException`|if `str` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.notBlank](Validate.notBlank)

###### Example
```apex
Validate.notEmpty(
    '',
    'The string cannot be empty. {0}',
    new List<String>{ 'Status code: 400' }
); // throws an IllegalArgumentException
```


##### `public static void minLength(String str, Integer min)`

Checks that the argument string `str` length is at least `min`.

###### Parameters

|Param|Description|
|---|---|
|`str`|the string to check|
|`min`|the inclusive minimum string length|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `str.length()` is less than `min` with the default formatted exception message 'Argument string length is less than {0}'|
|`NullPointerException`|if `str` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `min` is null with the default exception message 'Argument object is null'|


**See** [Validate.lengthBetween](Validate.lengthBetween)

###### Example
```apex
Validate.minLength('ab', 3); // throws an IllegalArgumentException
```


##### `public static void minLength(String str, Integer min, String message)`

Checks that the argument string `str` length is at least `min`.

###### Parameters

|Param|Description|
|---|---|
|`str`|the string to check|
|`min`|the inclusive minimum string length|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `str.length()` is less than `min` with the custom exception `message`|
|`NullPointerException`|if `str` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `min` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.lengthBetween](Validate.lengthBetween)

###### Example
```apex
Validate.minLength(
    'ab',
    3,
    'The string length should be at least 3'
); // throws an IllegalArgumentException
```


##### `public static void minLength(String str, Integer min, String message, List<Object> arguments)`

Checks that the argument string `str` length is at least `min`.

###### Parameters

|Param|Description|
|---|---|
|`str`|the string to check|
|`min`|the inclusive minimum string length|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `str.length()` is less than `min` with the custom exception `message`|
|`NullPointerException`|if `str` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `min` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.lengthBetween](Validate.lengthBetween)

###### Example
```apex
Validate.minLength(
    'ab',
    3,
    'The string length should be at least {0}',
    new List<Object>{ 3 }
); // throws an IllegalArgumentException
```


##### `public static void maxLength(String str, Integer max)`

Checks that the argument string `str` length is at most `max`.

###### Parameters

|Param|Description|
|---|---|
|`str`|the string to check|
|`max`|the inclusive maximum string length|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `str.length()` is greater than `max` with the default formatted exception message 'Argument string length is greater than {0}'|
|`NullPointerException`|if `str` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `max` is null with the default exception message 'Argument object is null'|


**See** [Validate.lengthBetween](Validate.lengthBetween)

###### Example
```apex
Validate.maxLength('abcd', 3); // throws an IllegalArgumentException
```


##### `public static void maxLength(String str, Integer max, String message)`

Checks that the argument string `str` length is at most `max`.

###### Parameters

|Param|Description|
|---|---|
|`str`|the string to check|
|`max`|the inclusive maximum string length|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `str.length()` is greater than `max` with the custom exception `message`|
|`NullPointerException`|if `str` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `max` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.lengthBetween](Validate.lengthBetween)

###### Example
```apex
Validate.maxLength(
    'abcd',
    3,
    'The string length should be at most 3'
); // throws an IllegalArgumentException
```


##### `public static void maxLength(String str, Integer max, String message, List<Object> arguments)`

Checks that the argument string `str` length is at most `max`.

###### Parameters

|Param|Description|
|---|---|
|`str`|the string to check|
|`max`|the inclusive maximum string length|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `str.length()` is greater than `max` with the custom exception `message`|
|`NullPointerException`|if `str` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `max` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.lengthBetween](Validate.lengthBetween)

###### Example
```apex
Validate.maxLength(
    'abcd',
    3,
    'The string length should be at most {0}',
    new List<Object>{ 3 }
); // throws an IllegalArgumentException
```


##### `public static void lengthBetween(String str, Integer minInclusive, Integer maxInclusive)`

Checks that the argument string `str` length is between `minInclusive` and `maxInclusive`.

###### Parameters

|Param|Description|
|---|---|
|`str`|the string to check|
|`minInclusive`|the inclusive minimum string length|
|`maxInclusive`|the inclusive maximum string length|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `str.length()` is not within the specified range with the default formatted exception message 'Argument string length {0} is not between inclusive range from {1} to {2}'|
|`NullPointerException`|if `str` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `minInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `maxInclusive` is null with the default exception message 'Argument object is null'|


**See** [Validate.minLength](Validate.minLength)


**See** [Validate.maxLength](Validate.maxLength)

###### Example
```apex
Validate.lengthBetween('abcd', 5, 10); // throws an IllegalArgumentException
```


##### `public static void lengthBetween(String str, Integer minInclusive, Integer maxInclusive, String message)`

Checks that the argument string `str` length is between `minInclusive` and `maxInclusive`.

###### Parameters

|Param|Description|
|---|---|
|`str`|the string to check|
|`minInclusive`|the inclusive minimum string length|
|`maxInclusive`|the inclusive maximum string length|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `str.length()` is not within the specified range with the custom exception `message`|
|`NullPointerException`|if `str` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `minInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `maxInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.minLength](Validate.minLength)


**See** [Validate.maxLength](Validate.maxLength)

###### Example
```apex
Validate.lengthBetween(
    'abcd',
    5,
    10,
    'The string length is out of range'
); // throws an IllegalArgumentException
```


##### `public static void lengthBetween(String str, Integer minInclusive, Integer maxInclusive, String message, List<Object> arguments)`

Checks that the argument string `str` length is between `minInclusive` and `maxInclusive`.

###### Parameters

|Param|Description|
|---|---|
|`str`|the string to check|
|`minInclusive`|the inclusive minimum string length|
|`maxInclusive`|the inclusive maximum string length|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `str.length()` is not within the specified range with the custom exception `message`|
|`NullPointerException`|if `str` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `minInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `maxInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.minLength](Validate.minLength)


**See** [Validate.maxLength](Validate.maxLength)

###### Example
```apex
Validate.lengthBetween(
    'abcd',
    5,
    10,
    'The string length should be between {0} and {1}',
    new List<Object>{ 5, 10 }
); // throws an IllegalArgumentException
```


##### `public static void index(String str, Integer index)`

Checks that the `index` is within the bounds of the argument string `str`.

###### Parameters

|Param|Description|
|---|---|
|`str`|the string to check|
|`index`|the index to check|

###### Throws

|Exception|Description|
|---|---|
|`IndexOutOfBoundsException`|if `index` is invalid with the default formatted exception message 'String index out of bounds: {0}'|
|`NullPointerException`|if `str` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `index` is null with the default exception message 'Argument object is null'|


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.index('foo', 3); // throws an IndexOutOfBoundsException
```


##### `public static void index(String str, Integer index, String message)`

Checks that the `index` is within the bounds of the argument string `str`.

###### Parameters

|Param|Description|
|---|---|
|`str`|the string to check|
|`index`|the index to check|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IndexOutOfBoundsException`|if `index` is invalid with the custom exception `message`|
|`NullPointerException`|if `str` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `index` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.index(
    'foo',
    3,
    'Invalid index'
); // throws an IndexOutOfBoundsException
```


##### `public static void index(String str, Integer index, String message, List<Object> arguments)`

Checks that the `index` is within the bounds of the argument string `str`.

###### Parameters

|Param|Description|
|---|---|
|`str`|the string to check|
|`index`|the index to check|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IndexOutOfBoundsException`|if `index` is invalid with the custom exception `message`|
|`NullPointerException`|if `str` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `index` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.index(
   'foo',
    3,
    'Invalid index: {0}',
    new List<Integer>{ 3 }
); // throws an IndexOutOfBoundsException
```


##### `public static void matches(String str, String regex)`

Checks that the argument string `str` matches the `regex`.

###### Parameters

|Param|Description|
|---|---|
|`str`|the string to check for matching|
|`regex`|the regular expression to match against|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `str` does not match the `regex` with the default formatted exception message 'Argument string {0} does not match the pattern {1}'|
|`NullPointerException`|if `str` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `regex` is null with the default exception message 'Argument object is null'|


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.matches('foo', '\\d+'); // throws an IllegalArgumentException
```


##### `public static void matches(String str, String regex, String message)`

Checks that the argument string `str` matches the `regex`.

###### Parameters

|Param|Description|
|---|---|
|`str`|the string to check for matching|
|`regex`|the regular expression to match against|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `str` does not match the `regex` with the custom exception `message`|
|`NullPointerException`|if `str` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `regex` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.matches(
    'foo',
    '\\d+',
    'Custom message'
); // throws an IllegalArgumentException
```


##### `public static void matches(String str, String regex, String message, List<Object> arguments)`

Checks that the argument string `str` matches the `regex`.

###### Parameters

|Param|Description|
|---|---|
|`str`|the string to check for matching|
|`regex`|the regular expression to match against|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `str` does not match the `regex` with the custom exception `message`|
|`NullPointerException`|if `str` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `regex` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|

###### Example
```apex
Validate.matches(
    'foo',
    '\\d+',
    'The string {0} does not match the pattern {1}.',
    new List<String>{ 'foo', '\\d+' }
); // throws an IllegalArgumentException
```


##### `public static void email(String email)`

Checks that the argument `email` is valid. Please note that this validation method isn't fully RFC 5322 and RFC 6531 compliant e.g. does not support non-ASCII characters.

###### Parameters

|Param|Description|
|---|---|
|`email`|the email to validate|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `email` is invalid with the default formatted exception message 'Argument email {0} is invalid'|
|`NullPointerException`|if `email` is null with the default exception message 'Argument object is null'|


**See** [Validate.matches](Validate.matches)

###### Example
```apex
Validate.email('john.doe＠example.com'); // valid
Validate.email('john.doe.example.com'); // throws an IllegalArgumentException
Validate.email('＠example.com'); // throws an IllegalArgumentException
```


##### `public static void email(String email, String message)`

Checks that the argument `email` is valid. Please note that this validation method isn't fully RFC 5322 and RFC 6531 compliant e.g. does not support non-ASCII characters.

###### Parameters

|Param|Description|
|---|---|
|`email`|the email to validate|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `email` is invalid with the custom exception `message`|
|`NullPointerException`|if `email` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.matches](Validate.matches)

###### Example
```apex
Validate.email(
    'john.doe.example.com',
    'Invalid email address'
); // throws an IllegalArgumentException
```


##### `public static void email(String email, String message, List<Object> arguments)`

Checks that the argument `email` is valid. Please note that this validation method isn't fully RFC 5322 and RFC 6531 compliant e.g. does not support non-ASCII characters.

###### Parameters

|Param|Description|
|---|---|
|`email`|the email to validate|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `email` is invalid with the custom exception `message`|
|`NullPointerException`|if `email` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.matches](Validate.matches)

###### Example
```apex
Validate.email(
    'john.doe.example.com',
    'The email address {0} is not valid',
    new List<String>{ 'john.doe.example.com' }
); // throws an IllegalArgumentException
```


##### `public static void creditCard(String card)`

Checks that the argument `card` is valid using <a href="https://en.wikipedia.org/wiki/Luhn_algorithm">Luhn algorithm</a>.

###### Parameters

|Param|Description|
|---|---|
|`card`|the credit card to validate|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `card` is invalid with the default formatted exception message 'Argument credit card {0} is invalid'|
|`NullPointerException`|if `card` is null with the default exception message 'Argument object is null'|


**See** [Validate.matches](Validate.matches)

###### Example
```apex
Validate.creditCard('1234-5678-9012-3452'); // valid
Validate.creditCard('4417123456789113'); // valid
Validate.creditCard('0000000000000001'); // throws an IllegalArgumentException
```


##### `public static void creditCard(String card, String message)`

Checks that the argument `card` is valid using <a href="https://en.wikipedia.org/wiki/Luhn_algorithm">Luhn algorithm</a>.

###### Parameters

|Param|Description|
|---|---|
|`card`|the credit card to validate|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `card` is invalid with the custom exception `message`|
|`NullPointerException`|if `card` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.matches](Validate.matches)

###### Example
```apex
Validate.creditCard(
    '0000000000000001',
    'Invalid credit card number'
); // throws an IllegalArgumentException
```


##### `public static void creditCard(String card, String message, List<Object> arguments)`

Checks that the argument `card` is valid using <a href="https://en.wikipedia.org/wiki/Luhn_algorithm">Luhn algorithm</a>.

###### Parameters

|Param|Description|
|---|---|
|`card`|the credit card to validate|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `card` is invalid with the custom exception `message`|
|`NullPointerException`|if `card` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.matches](Validate.matches)

###### Example
```apex
Validate.creditCard(
    '0000000000000001',
    'Invalid credit card number {0}',
    new List<String>{ '0000000000000001' }
); // throws an IllegalArgumentException
```


---
### State
##### `public static void fail()`

Unconditionally throws an `IllegalStateException`.

###### Throws

|Exception|Description|
|---|---|
|`IllegalStateException`|with the default exception message 'Argument state is invalid'|


**See** [Validate.state](Validate.state)

###### Example
```apex
Validate.fail(); // throws an IllegalStateException
```


##### `public static void fail(String message)`

Unconditionally throws an `IllegalStateException`.

###### Parameters

|Param|Description|
|---|---|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalStateException`|with the custom exception `message`|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.state](Validate.state)

###### Example
```apex
Validate.fail('Custom message'); // throws an IllegalStateException
```


##### `public static void fail(Exception exc)`

Unconditionally throws the provided exception.

###### Parameters

|Param|Description|
|---|---|
|`exc`|the exception to throw|

###### Throws

|Exception|Description|
|---|---|
|`Exception`|the provided `exc`|
|`NullPointerException`|if `exc` is null with the default exception message 'Argument object is null'|


**See** [Validate.state](Validate.state)

###### Example
```apex
Validate.fail(new CustomException('Error message')); // throws a CustomException
```


##### `public static void fail(String message, List<Object> arguments)`

Unconditionally throws an `IllegalStateException`.

###### Parameters

|Param|Description|
|---|---|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalStateException`|with the custom exception `message`|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.state](Validate.state)

###### Example
```apex
Validate.fail(
    'Duplicate key {0} (attempted merging values {1} and {2}).',
    new List<Object>{ key, oldValue, newValue }
); // throws an IllegalStateException
```


##### `public static void state(Boolean condition)`

Checks that the stateful argument `condition` is true.

###### Parameters

|Param|Description|
|---|---|
|`condition`|the boolean expression to check|

###### Throws

|Exception|Description|
|---|---|
|`IllegalStateException`|if `condition` evaluates to false with the default exception message 'Argument state is invalid'|
|`NullPointerException`|if `condition` is null with the default exception message 'Argument object is null'|


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.state(response.getStatusCode() == 200);
```


##### `public static void state(Boolean condition, String message)`

Checks that the stateful argument `condition` is true.

###### Parameters

|Param|Description|
|---|---|
|`condition`|the boolean expression to check|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalStateException`|if `condition` evaluates to false with custom exception `message`|
|`NullPointerException`|if `condition` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.state(response.getStatusCode() == 200, 'Custom message');
```


##### `public static void state(Boolean condition, String message, List<Object> arguments)`

Checks that the stateful argument `condition` is true.

###### Parameters

|Param|Description|
|---|---|
|`condition`|the boolean expression to check|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalStateException`|if `condition` evaluates to false with the custom exception `message`|
|`NullPointerException`|if `condition` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|

###### Example
```apex
Validate.state(
    !map.containsKey(key),
    'Duplicate key {0} (attempted merging values {1} and {2}).',
    new List<Object>{ key, oldValue, newValue }
); // throws an IllegalStateException
```


---
### Numbers
##### `public static void positive(Decimal value)`

Checks that the argument decimal `value` is positive.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not positive with the default formatted exception message 'Argument decimal {0} is not positive'|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|


**See** [Validate.notNegative](Validate.notNegative)


**See** [Validate.negative](Validate.negative)

###### Example
```apex
Validate.positive(-1); // throws an IllegalArgumentException
```


##### `public static void positive(Decimal value, String message)`

Checks that the argument decimal `value` is positive.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not positive with the custom exception `message`|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.notNegative](Validate.notNegative)


**See** [Validate.negative](Validate.negative)

###### Example
```apex
Validate.positive(
    -1,
    'The value should be positive'
); // throws an IllegalArgumentException
```


##### `public static void positive(Decimal value, String message, List<Object> arguments)`

Checks that the argument decimal `value` is positive.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not positive with the custom exception `message`|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.notNegative](Validate.notNegative)


**See** [Validate.negative](Validate.negative)

###### Example
```apex
Validate.positive(
    -1,
    'The value {0} should be positive',
    new List<Object>{ -1 }
); // throws an IllegalArgumentException
```


##### `public static void notNegative(Decimal value)`

Checks that the argument decimal `value` is non-negative.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is negative with the default formatted exception message 'Argument decimal {0} is negative'|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|


**See** [Validate.positive](Validate.positive)


**See** [Validate.negative](Validate.negative)

###### Example
```apex
Validate.notNegative(-1); // throws an IllegalArgumentException
```


##### `public static void notNegative(Decimal value, String message)`

Checks that the argument decimal `value` is non-negative.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is negative with the custom exception `message`|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.positive](Validate.positive)


**See** [Validate.negative](Validate.negative)

###### Example
```apex
Validate.notNegative(
    -1,
    'The value should be non-negative'
); // throws an IllegalArgumentException
```


##### `public static void notNegative(Decimal value, String message, List<Object> arguments)`

Checks that the argument decimal `value` is non-negative.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is negative with the custom exception `message`|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.positive](Validate.positive)


**See** [Validate.negative](Validate.negative)

###### Example
```apex
Validate.notNegative(
    -1,
    'The value {0} should be non-negative',
    new List<Object>{ -1 }
); // throws an IllegalArgumentException
```


##### `public static void negative(Decimal value)`

Checks that the argument decimal `value` is negative.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not negative with the default formatted exception message 'Argument decimal {0} is not negative'|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|


**See** [Validate.positive](Validate.positive)


**See** [Validate.notNegative](Validate.notNegative)

###### Example
```apex
Validate.negative(1); // throws an IllegalArgumentException
```


##### `public static void negative(Decimal value, String message)`

Checks that the argument decimal `value` is negative.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not negative with the custom exception `message`|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.positive](Validate.positive)


**See** [Validate.notNegative](Validate.notNegative)

###### Example
```apex
Validate.negative(
    1,
    'The value should be negative'
); // throws an IllegalArgumentException
```


##### `public static void negative(Decimal value, String message, List<Object> arguments)`

Checks that the argument decimal `value` is negative.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not negative with the custom exception `message`|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.positive](Validate.positive)


**See** [Validate.notNegative](Validate.notNegative)

###### Example
```apex
Validate.negative(
    1,
    'The value {0} should be negative',
    new List<Object>{ 1 }
); // throws an IllegalArgumentException
```


##### `public static void between(Decimal startInclusive, Decimal endInclusive, Decimal value)`

Checks that the argument decimal `value` is between the two inclusive values.

###### Parameters

|Param|Description|
|---|---|
|`startInclusive`|the inclusive start value|
|`endInclusive`|the inclusive end value|
|`value`|tha value to validate|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if the `value` is not within the specified range with the default formatted exception message 'Argument {0} is not between inclusive range from {1} to {2}'|
|`NullPointerException`|if `startInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `endInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.between(1, 10, 5); // valid
```


##### `public static void between(Decimal startInclusive, Decimal endInclusive, Decimal value, String message)`

Checks that the argument decimal `value` is between the two inclusive values.

###### Parameters

|Param|Description|
|---|---|
|`startInclusive`|the inclusive start value|
|`endInclusive`|the inclusive end value|
|`value`|tha value to validate|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if the `value` is not within the specified range with the custom exception `message`|
|`NullPointerException`|if `startInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `endInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.between(
    1,
    10,
    11,
    'The value is out of range'
); //throws an IllegalArgumentException
```


##### `public static void between(Decimal startInclusive, Decimal endInclusive, Decimal value, String message, List<Object> arguments)`

`SUPPRESSWARNINGS`

Checks that the argument decimal `value` is between the two inclusive values.

###### Parameters

|Param|Description|
|---|---|
|`startInclusive`|the inclusive start value|
|`endInclusive`|the inclusive end value|
|`value`|tha value to validate|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if the `value` is not within the specified range with the custom exception `message`|
|`NullPointerException`|if `startInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `endInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.between(
    1,
    10,
    11,
    'The value {0} is out of range {1} - {2}',
    new List<Decimal>{ 11, 1, 10 }
); // throws an IllegalArgumentException
```


##### `public static void pastOrPresent(Date value)`

Checks that the argument date `value` is in the past or present.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not in the past or present with the default formatted exception message 'Argument date {0} is not in the past or present'|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|


**See** [Validate.futureOrPresent](Validate.futureOrPresent)


**See** [Validate.past](Validate.past)


**See** [Validate.future](Validate.future)

###### Example
```apex
Validate.pastOrPresent(Date.today().addDays(1)); // throws an IllegalArgumentException
```


##### `public static void pastOrPresent(Date value, String message)`

Checks that the argument date `value` is in the past or present.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not in the past or present with the custom exception `message`|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.futureOrPresent](Validate.futureOrPresent)


**See** [Validate.past](Validate.past)


**See** [Validate.future](Validate.future)

###### Example
```apex
Validate.pastOrPresent(
    Date.today().addDays(1),
    'The date should be in the past or present'
); // throws an IllegalArgumentException
```


##### `public static void pastOrPresent(Date value, String message, List<Object> arguments)`

Checks that the argument date `value` is in the past or present.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not in the past or present with the custom exception `message`|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.futureOrPresent](Validate.futureOrPresent)


**See** [Validate.past](Validate.past)


**See** [Validate.future](Validate.future)

###### Example
```apex
Validate.pastOrPresent(
    Date.today().addDays(1),
    'The date {0} should be in the past or present',
    new List<Object>{ Date.today().addDays(1) }
); // throws an IllegalArgumentException
```


##### `public static void futureOrPresent(Date value)`

Checks that the argument date `value` is in the future or present.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not in the future or present with the default formatted exception message 'Argument date {0} is not in the future or present'|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|


**See** [Validate.pastOrPresent](Validate.pastOrPresent)


**See** [Validate.past](Validate.past)


**See** [Validate.future](Validate.future)

###### Example
```apex
Validate.futureOrPresent(Date.today().addDays(-1)); // throws an IllegalArgumentException
```


##### `public static void futureOrPresent(Date value, String message)`

Checks that the argument date `value` is in the future or present.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not in the future or present with the custom exception `message`|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.pastOrPresent](Validate.pastOrPresent)


**See** [Validate.past](Validate.past)


**See** [Validate.future](Validate.future)

###### Example
```apex
Validate.futureOrPresent(
    Date.today().addDays(-1),
    'The date should be in the future or present'
); // throws an IllegalArgumentException
```


##### `public static void futureOrPresent(Date value, String message, List<Object> arguments)`

Checks that the argument date `value` is in the future or present.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not in the future or present with the custom exception `message`|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.pastOrPresent](Validate.pastOrPresent)


**See** [Validate.past](Validate.past)


**See** [Validate.future](Validate.future)

###### Example
```apex
Validate.futureOrPresent(
    Date.today().addDays(-1),
    'The date {0} should be in the future or present',
    new List<Object>{ Date.today().addDays(-1) }
); // throws an IllegalArgumentException
```


##### `public static void past(Date value)`

Checks that the argument date `value` is in the past.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not in the past with the default formatted exception message 'Argument date {0} is not in the past'|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|


**See** [Validate.pastOrPresent](Validate.pastOrPresent)


**See** [Validate.futureOrPresent](Validate.futureOrPresent)


**See** [Validate.future](Validate.future)

###### Example
```apex
Validate.past(Date.today()); // throws an IllegalArgumentException
```


##### `public static void past(Date value, String message)`

Checks that the argument date `value` is in the past.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not in the past with the custom exception `message`|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.pastOrPresent](Validate.pastOrPresent)


**See** [Validate.futureOrPresent](Validate.futureOrPresent)


**See** [Validate.future](Validate.future)

###### Example
```apex
Validate.past(
    Date.today(),
    'The date should be in the past'
); // throws an IllegalArgumentException
```


##### `public static void past(Date value, String message, List<Object> arguments)`

Checks that the argument date `value` is in the past.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not in the past with the custom exception `message`|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.pastOrPresent](Validate.pastOrPresent)


**See** [Validate.futureOrPresent](Validate.futureOrPresent)


**See** [Validate.future](Validate.future)

###### Example
```apex
Validate.past(
    Date.today(),
    'The date {0} should be in the past',
    new List<Object>{ Date.today() }
); // throws an IllegalArgumentException
```


##### `public static void future(Date value)`

Checks that the argument date `value` is in the future.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not in the future with the default formatted exception message 'Argument date {0} is not in the future'|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|


**See** [Validate.pastOrPresent](Validate.pastOrPresent)


**See** [Validate.futureOrPresent](Validate.futureOrPresent)


**See** [Validate.past](Validate.past)

###### Example
```apex
Validate.future(Date.today()); // throws an IllegalArgumentException
```


##### `public static void future(Date value, String message)`

Checks that the argument date `value` is in the future.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not in the future with the custom exception `message`|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.pastOrPresent](Validate.pastOrPresent)


**See** [Validate.futureOrPresent](Validate.futureOrPresent)


**See** [Validate.past](Validate.past)

###### Example
```apex
Validate.future(
    Date.today(),
    'The date should be in the future'
); // throws an IllegalArgumentException
```


##### `public static void future(Date value, String message, List<Object> arguments)`

Checks that the argument date `value` is in the future.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not in the future with the custom exception `message`|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.pastOrPresent](Validate.pastOrPresent)


**See** [Validate.futureOrPresent](Validate.futureOrPresent)


**See** [Validate.past](Validate.past)

###### Example
```apex
Validate.future(
    Date.today(),
    'The date {0} should be in the future',
    new List<Object>{ Date.today() }
); // throws an IllegalArgumentException
```


##### `public static void pastOrPresent(Datetime value)`

Checks that the argument datetime `value` is in the past or present.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not in the past or present with the default formatted exception message 'Argument datetime {0} is not in the past or present'|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|


**See** [Validate.futureOrPresent](Validate.futureOrPresent)


**See** [Validate.past](Validate.past)


**See** [Validate.future](Validate.future)

###### Example
```apex
Validate.pastOrPresent(Datetime.now().addMinutes(1)); // throws an IllegalArgumentException
```


##### `public static void pastOrPresent(Datetime value, String message)`

Checks that the argument datetime `value` is in the past or present.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not in the past or present with the custom exception `message`|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.futureOrPresent](Validate.futureOrPresent)


**See** [Validate.past](Validate.past)


**See** [Validate.future](Validate.future)

###### Example
```apex
Validate.pastOrPresent(
    Datetime.now().addMinutes(1),
    'The datetime should be in the past or present'
); // throws an IllegalArgumentException
```


##### `public static void pastOrPresent(Datetime value, String message, List<Object> arguments)`

Checks that the argument datetime `value` is in the past or present.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not in the past or present with the custom exception `message`|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.futureOrPresent](Validate.futureOrPresent)


**See** [Validate.past](Validate.past)


**See** [Validate.future](Validate.future)

###### Example
```apex
Validate.pastOrPresent(
    Datetime.now().addMinutes(1),
    'The datetime {0} should be in the past or present',
    new List<Object>{ Datetime.now().addMinutes(1) }
); // throws an IllegalArgumentException
```


##### `public static void futureOrPresent(Datetime value)`

Checks that the argument datetime `value` is in the future or present.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not in the future or present with the default formatted exception message 'Argument datetime {0} is not in the future or present'|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|


**See** [Validate.pastOrPresent](Validate.pastOrPresent)


**See** [Validate.past](Validate.past)


**See** [Validate.future](Validate.future)

###### Example
```apex
Validate.futureOrPresent(Datetime.now().addMinutes(-1)); // throws an IllegalArgumentException
```


##### `public static void futureOrPresent(Datetime value, String message)`

Checks that the argument datetime `value` is in the future or present.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not in the future or present with the custom exception `message`|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.pastOrPresent](Validate.pastOrPresent)


**See** [Validate.past](Validate.past)


**See** [Validate.future](Validate.future)

###### Example
```apex
Validate.futureOrPresent(
    Datetime.now().addMinutes(-1),
    'The datetime should be in the future or present'
); // throws an IllegalArgumentException
```


##### `public static void futureOrPresent(Datetime value, String message, List<Object> arguments)`

Checks that the argument datetime `value` is in the future or present.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not in the future or present with the custom exception `message`|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.pastOrPresent](Validate.pastOrPresent)


**See** [Validate.past](Validate.past)


**See** [Validate.future](Validate.future)

###### Example
```apex
Validate.futureOrPresent(
    Datetime.now().addMinutes(-1),
    'The datetime {0} should be in the future or present',
    new List<Object>{ Datetime.now().addMinutes(-1) }
); // throws an IllegalArgumentException
```


##### `public static void past(Datetime value)`

Checks that the argument datetime `value` is in the past.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not in the past with the default formatted exception message 'Argument datetime {0} is not in the past'|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|


**See** [Validate.pastOrPresent](Validate.pastOrPresent)


**See** [Validate.futureOrPresent](Validate.futureOrPresent)


**See** [Validate.future](Validate.future)

###### Example
```apex
Validate.past(Datetime.now()); // throws an IllegalArgumentException
```


##### `public static void past(Datetime value, String message)`

Checks that the argument datetime `value` is in the past.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not in the past with the custom exception `message`|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.pastOrPresent](Validate.pastOrPresent)


**See** [Validate.futureOrPresent](Validate.futureOrPresent)


**See** [Validate.future](Validate.future)

###### Example
```apex
Validate.past(
    Datetime.now(),
    'The datetime should be in the past'
); // throws an IllegalArgumentException
```


##### `public static void past(Datetime value, String message, List<Object> arguments)`

Checks that the argument datetime `value` is in the past.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not in the past with the custom exception `message`|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.pastOrPresent](Validate.pastOrPresent)


**See** [Validate.futureOrPresent](Validate.futureOrPresent)


**See** [Validate.future](Validate.future)

###### Example
```apex
Validate.past(
    Datetime.now(),
    'The datetime {0} should be in the past',
    new List<Object>{ Datetime.now() }
); // throws an IllegalArgumentException
```


##### `public static void future(Datetime value)`

Checks that the argument datetime `value` is in the future.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not in the future with the default formatted exception message 'Argument datetime {0} is not in the future'|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|


**See** [Validate.pastOrPresent](Validate.pastOrPresent)


**See** [Validate.futureOrPresent](Validate.futureOrPresent)


**See** [Validate.past](Validate.past)

###### Example
```apex
Validate.future(Datetime.now()); // throws an IllegalArgumentException
```


##### `public static void future(Datetime value, String message)`

Checks that the argument datetime `value` is in the future.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not in the future with the custom exception `message`|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.pastOrPresent](Validate.pastOrPresent)


**See** [Validate.futureOrPresent](Validate.futureOrPresent)


**See** [Validate.past](Validate.past)

###### Example
```apex
Validate.future(
    Datetime.now(),
    'The datetime should be in the future'
); // throws an IllegalArgumentException
```


##### `public static void future(Datetime value, String message, List<Object> arguments)`

Checks that the argument datetime `value` is in the future.

###### Parameters

|Param|Description|
|---|---|
|`value`|tha value to validate|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `value` is not in the future with the custom exception `message`|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.pastOrPresent](Validate.pastOrPresent)


**See** [Validate.futureOrPresent](Validate.futureOrPresent)


**See** [Validate.past](Validate.past)

###### Example
```apex
Validate.future(
    Datetime.now(),
    'The datetime {0} should be in the future',
    new List<Object>{ Datetime.now() }
); // throws an IllegalArgumentException
```


##### `public static void between(Date startInclusive, Date endInclusive, Date value)`

Checks that the argument date `value` is between the two inclusive values.

###### Parameters

|Param|Description|
|---|---|
|`startInclusive`|the inclusive start value|
|`endInclusive`|the inclusive end value|
|`value`|tha value to validate|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if the `value` is not within the specified range with the default formatted exception message 'Argument {0} is not between inclusive range from {1} to {2}'|
|`NullPointerException`|if `startInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `endInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.between(
   Date.today(),
   Date.today().addDays(2),
   Date.today().addDays(1)
); // valid
```


##### `public static void between(Date startInclusive, Date endInclusive, Date value, String message)`

Checks that the argument date `value` is between the two inclusive values.

###### Parameters

|Param|Description|
|---|---|
|`startInclusive`|the inclusive start value|
|`endInclusive`|the inclusive end value|
|`value`|tha value to validate|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if the `value` is not within the specified range with the custom exception `message`|
|`NullPointerException`|if `startInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `endInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.between(
    Date.today(),
    Date.today().addDays(2),
    Date.today().addDays(3),
    'The value is out of range'
); //throws an IllegalArgumentException
```


##### `public static void between(Date startInclusive, Date endInclusive, Date value, String message, List<Object> arguments)`

`SUPPRESSWARNINGS`

Checks that the argument date `value` is between the two inclusive values.

###### Parameters

|Param|Description|
|---|---|
|`startInclusive`|the inclusive start value|
|`endInclusive`|the inclusive end value|
|`value`|tha value to validate|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if the `value` is not within the specified range with the custom exception `message`|
|`NullPointerException`|if `startInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `endInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.between(
    Date.today(),
    Date.today().addDays(2),
    Date.today().addDays(3),
    'The value {0} is out of range {1} - {2}',
    new List<Date>{
        Date.today(),
        Date.today().addDays(2),
        Date.today().addDays(3)
    }
); // throws an IllegalArgumentException
```


##### `public static void between(Datetime startInclusive, Datetime endInclusive, Datetime value)`

Checks that the argument datetime `value` is between the two inclusive values.

###### Parameters

|Param|Description|
|---|---|
|`startInclusive`|the inclusive start value|
|`endInclusive`|the inclusive end value|
|`value`|tha value to validate|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if the `value` is not within the specified range with the default formatted exception message 'Argument {0} is not between inclusive range from {1} to {2}'|
|`NullPointerException`|if `startInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `endInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.between(
   Datetime.now(),
   Datetime.now().addDays(2),
   Datetime.now().addDays(1)
); // valid
```


##### `public static void between(Datetime startInclusive, Datetime endInclusive, Datetime value, String message)`

Checks that the argument datetime `value` is between the two inclusive values.

###### Parameters

|Param|Description|
|---|---|
|`startInclusive`|the inclusive start value|
|`endInclusive`|the inclusive end value|
|`value`|tha value to validate|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if the `value` is not within the specified range with the custom exception `message`|
|`NullPointerException`|if `startInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `endInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.between(
    Datetime.now(),
    Datetime.now().addDays(2),
    Datetime.now().addDays(3),
    'The value is out of range'
); //throws an IllegalArgumentException
```


##### `public static void between(Datetime startInclusive, Datetime endInclusive, Datetime value, String message, List<Object> arguments)`

`SUPPRESSWARNINGS`

Checks that the argument datetime `value` is between the two inclusive values.

###### Parameters

|Param|Description|
|---|---|
|`startInclusive`|the inclusive start value|
|`endInclusive`|the inclusive end value|
|`value`|tha value to validate|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if the `value` is not within the specified range with the custom exception `message`|
|`NullPointerException`|if `startInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `endInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.between(
    Datetime.now(),
    Datetime.now().addDays(2),
    Datetime.now().addDays(3),
    'The value {0} is out of range {1} - {2}',
    new List<Datetime>{
        Datetime.now(),
        Datetime.now().addDays(2),
        Datetime.now().addDays(3)
    }
); // throws an IllegalArgumentException
```


##### `public static void between(Time startInclusive, Time endInclusive, Time value)`

Checks that the argument time `value` is between the two inclusive values.

###### Parameters

|Param|Description|
|---|---|
|`startInclusive`|the inclusive start value|
|`endInclusive`|the inclusive end value|
|`value`|tha value to validate|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if the `value` is not within the specified range with the default formatted exception message 'Argument {0} is not between inclusive range from {1} to {2}'|
|`NullPointerException`|if `startInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `endInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.between(
   Time.newInstance(0, 0, 0, 0),
   Time.newInstance(0, 0, 0, 0).addHours(2),
   Time.newInstance(0, 0, 0, 0).addHours(1)
); // valid
```


##### `public static void between(Time startInclusive, Time endInclusive, Time value, String message)`

Checks that the argument time `value` is between the two inclusive values.

###### Parameters

|Param|Description|
|---|---|
|`startInclusive`|the inclusive start value|
|`endInclusive`|the inclusive end value|
|`value`|tha value to validate|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if the `value` is not within the specified range with the custom exception `message`|
|`NullPointerException`|if `startInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `endInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.between(
    Time.newInstance(0, 0, 0, 0),
    Time.newInstance(0, 0, 0, 0).addHours(2),
    Time.newInstance(0, 0, 0, 0).addHours(3),
    'The value is out of range'
); //throws an IllegalArgumentException
```


##### `public static void between(Time startInclusive, Time endInclusive, Time value, String message, List<Object> arguments)`

`SUPPRESSWARNINGS`

Checks that the argument time `value` is between the two inclusive values.

###### Parameters

|Param|Description|
|---|---|
|`startInclusive`|the inclusive start value|
|`endInclusive`|the inclusive end value|
|`value`|tha value to validate|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if the `value` is not within the specified range with the custom exception `message`|
|`NullPointerException`|if `startInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `endInclusive` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `value` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.between(
    Time.newInstance(0, 0, 0, 0),
    Time.newInstance(0, 0, 0, 0).addHours(2),
    Time.newInstance(0, 0, 0, 0).addHours(3),
    'The value {0} is out of range {1} - {2}',
    new List<Datetime>{
        Time.newInstance(0, 0, 0, 0),
        Time.newInstance(0, 0, 0, 0).addHours(2),
        Time.newInstance(0, 0, 0, 0).addHours(3)
    }
); // throws an IllegalArgumentException
```


---
### Methods consistent with System.Assert class
##### `public static void areEqual(Object obj1, Object obj2)`

Checks that the arguments `obj1` and `obj2` are equal.

###### Parameters

|Param|Description|
|---|---|
|`obj1`|the first object to compare|
|`obj2`|the second object to compare|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if the `obj1` and `obj2` are not equal with the default formatted exception message 'Arguments {0} and {1} are not equal'|


**See** [Assert.areEqual](Assert.areEqual)

###### Example
```apex
Validate.areEqual('foo', 'foo'); // valid
Validate.areEqual('foo', 'bar'); // throws an IllegalArgumentException
```


##### `public static void areEqual(Object obj1, Object obj2, String message)`

Checks that the arguments `obj1` and `obj2` are equal.

###### Parameters

|Param|Description|
|---|---|
|`obj1`|the first object to compare|
|`obj2`|the second object to compare|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if the `obj1` and `obj2` are not equal with the custom `message`|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Assert.areEqual](Assert.areEqual)

###### Example
```apex
Validate.areEqual(
   'foo',
   'bar',
   'Arguments are not equal'
); // throws an IllegalArgumentException
```


##### `public static void areEqual(Object obj1, Object obj2, String message, List<Object> arguments)`

Checks that the arguments `obj1` and `obj2` are equal.

###### Parameters

|Param|Description|
|---|---|
|`obj1`|the first object to compare|
|`obj2`|the second object to compare|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if the `obj1` and `obj2` are not equal with the custom `message`|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Assert.areEqual](Assert.areEqual)

###### Example
```apex
Validate.areEqual(
   'foo',
   'bar',
   'Arguments {0} and {1} are not equal',
   new List<String>{ 'foo', 'bar' }
); // throws an IllegalArgumentException
```


##### `public static void areNotEqual(Object obj1, Object obj2)`

Checks that the arguments `obj1` and `obj2` are not equal.

###### Parameters

|Param|Description|
|---|---|
|`obj1`|the first object to compare|
|`obj2`|the second object to compare|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if the `obj1` and `obj2` are equal with the default formatted exception message 'Arguments {0} and {1} are equal'|


**See** [Assert.areNotEqual](Assert.areNotEqual)

###### Example
```apex
Validate.areNotEqual('foo', 'bar'); // valid
Validate.areNotEqual('foo', 'foo'); // throws an IllegalArgumentException
```


##### `public static void areNotEqual(Object obj1, Object obj2, String message)`

Checks that the arguments `obj1` and `obj2` are not equal.

###### Parameters

|Param|Description|
|---|---|
|`obj1`|the first object to compare|
|`obj2`|the second object to compare|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if the `obj1` and `obj2` are equal with the custom `message`|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Assert.areNotEqual](Assert.areNotEqual)

###### Example
```apex
Validate.areNotEqual(
   'foo',
   'foo',
   'Arguments are equal'
); // throws an IllegalArgumentException
```


##### `public static void areNotEqual(Object obj1, Object obj2, String message, List<Object> arguments)`

Checks that the arguments `obj1` and `obj2` are not equal.

###### Parameters

|Param|Description|
|---|---|
|`obj1`|the first object to compare|
|`obj2`|the second object to compare|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if the `obj1` and `obj2` are equal with the custom `message`|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Assert.areNotEqual](Assert.areNotEqual)

###### Example
```apex
Validate.areNotEqual(
   'foo',
   'foo',
   'Arguments {0} and {1} are equal',
   new List<String>{ 'foo', 'bar' }
); // throws an IllegalArgumentException
```


##### `public static void isFalse(Boolean condition)`

Checks that the argument `condition` is false.

###### Parameters

|Param|Description|
|---|---|
|`condition`|the boolean expression to check|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `condition` evaluates to true with the default exception message 'Argument condition is true'|
|`NullPointerException`|if `condition` is null with the default exception message 'Argument object is null'|


**See** [Assert.isFalse](Assert.isFalse)


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.isFalse(i > 0);
Validate.isFalse(response.getStatusCode() != 200);
```


##### `public static void isFalse(Boolean condition, String message)`

Checks that the argument `condition` is false.

###### Parameters

|Param|Description|
|---|---|
|`condition`|the boolean expression to check|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `condition` evaluates to true with the custom exception `message`|
|`NullPointerException`|if `condition` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Assert.isFalse](Assert.isFalse)


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.isFalse(
    i < 0,
    'The argument value must be positive'
);
Validate.isFalse(
    response.getStatusCode() == 400,
    'The status code must not be 400'
);
```


##### `public static void isFalse(Boolean condition, String message, List<Object> arguments)`

Checks that the argument `condition` is false.

###### Parameters

|Param|Description|
|---|---|
|`condition`|the boolean expression to check|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `condition` evaluates to true with the custom exception `message`|
|`NullPointerException`|if `condition` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Assert.isFalse](Assert.isFalse)


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.isFalse(
    response.getStatusCode() == 400,
    'The status code must not be {0}',
    new List<Integer>{ 400 }
);
```


##### `public static void isInstanceOfType(Object obj, Type expectedType)`

Checks that the argument `obj` is the instance of type.

###### Parameters

|Param|Description|
|---|---|
|`obj`|the object to validate|
|`expectedType`|the expected type for the object|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if the `obj` is not an instance of `expectedType` with the default formatted exception message 'Argument object is not an instance of {0}. Actual type: {1}'|
|`NullPointerException`|if `expectedType` is null with the default exception message 'Argument object is null'|


**See** [Assert.isInstanceOfType](Assert.isInstanceOfType)

###### Example
```apex
Validate.isInstanceOfType('hello', String.class); // valid
Validate.isInstanceOfType('hello', Integer.class); // throws an IllegalArgumentException
```


##### `public static void isInstanceOfType(Object obj, Type expectedType, String message)`

Checks that the argument `obj` is the instance of type.

###### Parameters

|Param|Description|
|---|---|
|`obj`|the object to validate|
|`expectedType`|the expected type for the object|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if the `obj` is not an instance of `expectedType` with the custom exception `message`|
|`NullPointerException`|if `expectedType` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Assert.isInstanceOfType](Assert.isInstanceOfType)

###### Example
```apex
Validate.isInstanceOfType(
    'hello',
    Integer.class,
    'Invalid type'
); // throws an IllegalArgumentException
```


##### `public static void isInstanceOfType(Object obj, Type expectedType, String message, List<Object> arguments)`

Checks that the argument `obj` is the instance of type.

###### Parameters

|Param|Description|
|---|---|
|`obj`|the object to validate|
|`expectedType`|the expected type for the object|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if the `obj` is not an instance of `expectedType` with the custom exception `message`|
|`NullPointerException`|if `expectedType` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Assert.isInstanceOfType](Assert.isInstanceOfType)

###### Example
```apex
Validate.isInstanceOfType(
    'hello',
    Integer.class,
    'Expected Type: {0}',
    new List<String>{ 'Integer' }
); // throws an IllegalArgumentException
```


##### `public static void isNotInstanceOfType(Object obj, Type notExpectedType)`

Checks that the argument `obj` is not the instance of type.

###### Parameters

|Param|Description|
|---|---|
|`obj`|the object to validate|
|`notExpectedType`|the not expected type for the object|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if the `obj` is an instance of `notExpectedType` with the default formatted exception message 'Argument object is an instance of {0}'|
|`NullPointerException`|if `notExpectedType` is null with the default exception message 'Argument object is null'|


**See** [Assert.isNotInstanceOfType](Assert.isNotInstanceOfType)

###### Example
```apex
Validate.isNotInstanceOfType('hello', Integer.class); // valid
Validate.isNotInstanceOfType('hello', String.class); // throws an IllegalArgumentException
```


##### `public static void isNotInstanceOfType(Object obj, Type notExpectedType, String message)`

Checks that the argument `obj` is not the instance of type.

###### Parameters

|Param|Description|
|---|---|
|`obj`|the object to validate|
|`notExpectedType`|the not expected type for the object|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if the `obj` is an instance of `notExpectedType` with the custom exception `message`|
|`NullPointerException`|if `notExpectedType` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Assert.isNotInstanceOfType](Assert.isNotInstanceOfType)

###### Example
```apex
Validate.isNotInstanceOfType(
    'hello',
    String.class,
    'Invalid type'
); // throws an IllegalArgumentException
```


##### `public static void isNotInstanceOfType(Object obj, Type notExpectedType, String message, List<Object> arguments)`

Checks that the argument `obj` is not the instance of type.

###### Parameters

|Param|Description|
|---|---|
|`obj`|the object to validate|
|`notExpectedType`|the expected type for the object|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if the `obj` is not an instance of `notExpectedType` with the custom exception `message`|
|`NullPointerException`|if `notExpectedType` is null with the default exception message 'Argument object is null'|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Assert.isNotInstanceOfType](Assert.isNotInstanceOfType)

###### Example
```apex
Validate.isNotInstanceOfType(
    'hello',
    String.class,
    'Unexpected Type: {0}',
    new List<String>{ 'String' }
); // throws an IllegalArgumentException
```


##### `public static void isNotNull(Object obj)`

Checks that the argument reference `obj` is not null. Unlike [Validate.notNull](Validate.notNull) throws `IllegalArgumentException` when the `obj` is null.

###### Parameters

|Param|Description|
|---|---|
|`obj`|the object to check for nullity|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `obj` is null with the default exception message 'Argument object is null'|


**See** [Assert.isNotNull](Assert.isNotNull)


**See** [Validate.notNull](Validate.notNull)


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.isNotNull('foo'); // valid
Object obj;
Validate.isNotNull(obj); // throws an IllegalArgumentException
```


##### `public static void isNotNull(Object obj, String message)`

Checks that the argument reference `obj` is not null. Unlike [Validate.notNull](Validate.notNull) throws `IllegalArgumentException` when the `obj` is null.

###### Parameters

|Param|Description|
|---|---|
|`obj`|the object to check for nullity|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `obj` is null with the custom exception `message`|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Assert.isNotNull](Assert.isNotNull)


**See** [Validate.notNull](Validate.notNull)


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Object obj;
Validate.isNotNull(
    obj,
    'The object cannot be null'
); // throws an IllegalArgumentException
```


##### `public static void isNotNull(Object obj, String message, List<Object> arguments)`

Checks that the argument reference `obj` is not null. Unlike [Validate.notNull](Validate.notNull) throws `IllegalArgumentException` when the `obj` is null.

###### Parameters

|Param|Description|
|---|---|
|`obj`|the object to check for nullity|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `obj` is null with the custom exception `message`|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Assert.isNotNull](Assert.isNotNull)


**See** [Validate.notNull](Validate.notNull)


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Object obj;
Validate.isNotNull(
    obj,
    'Custom exception {0}',
    new List<String>{ 'argument' }
); // throws an IllegalArgumentException
```


##### `public static void isNull(Object obj)`

Checks that the argument reference `obj` is null.

###### Parameters

|Param|Description|
|---|---|
|`obj`|the object to check for nullity|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `obj` is not null with the default formatted exception message 'Argument object is not null. Actual value: {0}'|


**See** [Assert.isNull](Assert.isNull)


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Object obj;
Validate.isNull(obj); // valid
Validate.isNull('foo'); // throws an IllegalArgumentException
```


##### `public static void isNull(Object obj, String message)`

Checks that the argument reference `obj` is null.

###### Parameters

|Param|Description|
|---|---|
|`obj`|the object to check for nullity|
|`message`|the required custom exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `obj` is not null with the custom exception `message`|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Assert.isNull](Assert.isNull)


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.isNull('foo', 'Custom message'); // throws an IllegalArgumentException
```


##### `public static void isNull(Object obj, String message, List<Object> arguments)`

Checks that the argument reference `obj` is null.

###### Parameters

|Param|Description|
|---|---|
|`obj`|the object to check for nullity|
|`message`|the required formatted exception message|
|`arguments`|the optional values for the formatted exception message|

###### Throws

|Exception|Description|
|---|---|
|`IllegalArgumentException`|if `obj` is not null with the custom exception `message`|
|`NullPointerException`|if `message` is null with the default exception message 'Exception message cannot be null'|


**See** [Assert.isNull](Assert.isNull)


**See** [Validate.isTrue](Validate.isTrue)

###### Example
```apex
Validate.isNull(
    'foo',
    'Argument is not null. Actual value: {0}',
    new List<String>{ 'foo' }
); // throws an IllegalArgumentException
```


---
