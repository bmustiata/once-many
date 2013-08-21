once-many
=========

once-many provides a library that creates an iterator object that will return once the first value it was created with,
 and afterwards it will keep returning the second value.

For this example it will concatenate 10 'a' values, with commas - since the first value is "".

```
var onceMany = require("once-many").onceMany;

var comma = onceMany("", ", "),
    result = "";

for (var i = 0; i < 10; i++) {
    result += comma.next() + "a";
}
```

If the values to onceMany are functions, they will be evaluated with whatever parameters are sent to the onceMany.next()
method.

This algorithm comes handy whenever there is an algorithm that has a different first execution, of the kind:
```
var firstReached = false;

while (whatever) {
    if (!firstReached) {
        someValue = // some first reached value processing.
        firstReached = true;
    } else {
        someValue = // some afterwards reached value processing.
    }
}
```
