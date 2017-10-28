# Javascript best coding practices

### Use === Instead of ==

JavaScript utilizes two different kinds of equality operators: === | !== and == | != It is considered best practice to always use the former set when comparing.

```
   "If two operands are of the same type and value, then === produces true and !== produces false." - JavaScript: The Good Parts
```

However, when working with == and !=, you'll run into issues when working with different types. In these cases, they'll try to coerce the values, unsuccessfully.

### Eval = Bad

For those unfamiliar, the "eval" function gives us access to JavaScript's compiler. Essentially, we can execute a string's result by passing it as a parameter of "eval".

Not only will this decrease your script's performance substantially, but it also poses a huge security risk because it grants far too much power to the passed in text. Avoid it!

### Don't Use Short-Hand

Technically, you can get away with omitting most curly braces and semi-colons. Most browsers will correctly interpret the following:
```
if(someVariableExists)
  x = false
```
However, consider this:
```
if(someVariableExists)
  x = false
  anotherFunctionCall();
```
One might think that the code above would be equivalent to:
```
if(someVariableExists) {
  x = false;
  anotherFunctionCall();
}
```

Unfortunately, he'd be wrong. In reality, it means:
```
if(someVariableExists) {
  x = false;
}
anotherFunctionCall();
```
As you'll notice, the indentation mimics the functionality of the curly brace. Needless to say, this is a terrible practice that should be avoided at all costs. The only time that curly braces should be omitted is with one-liners, and even this is a highly debated topic.

```
if(2 + 2 === 4) return 'nicely done';
```


### Utilize JS Lint
[JSLint](http://www.jslint.com/) is a debugger written by Douglas Crockford. Simply paste in your script, and it'll quickly scan for any noticeable issues and errors in your code.
```
    "JSLint takes a JavaScript source and scans it. If it finds a problem, it returns a message describing the problem and an approximate location within the source. The problem is not necessarily a syntax error, although it often is. JSLint looks at some style conventions as well as structural problems. It does not prove that your program is correct. It just provides another set of eyes to help spot problems."
    - JSLint Documentation
```
Before signing off on a script, run it through JSLint just to be sure that you haven't made any mindless mistakes.

### Declare Variables Outside of the For Statement

When executing lengthy "for" statements, don't make the engine work any harder than it must. For example:

##### Bad
```
for(var i = 0; i < someArray.length; i++) {
   var container = document.getElementById('container');
   container.innerHtml += 'my number: ' + i;
   console.log(i);
}
```

 Notice how we must determine the length of the array for each iteration, and how we traverse the dom to find the "container" element each time -- highly inefficient!

##### Better
```
var container = document.getElementById('container');
for(var i = 0, len = someArray.length; i < len;  i++) {
   container.innerHtml += 'my number: ' + i;
   console.log(i);
}
```

### Reduce Globals

"By reducing your global footprint to a single name, you significantly reduce the chance of bad interactions with other applications, widgets, or libraries."
- Douglas Crockford

```
var name = 'Jeffrey';
var lastName = 'Way';

function doSomething() {...}

console.log(name); // Jeffrey -- or window.name
```
##### Better
```
var DudeNameSpace = {
   name : 'Jeffrey',
   lastName : 'Way',
   doSomething : function() {...}
}
console.log(DudeNameSpace.name); // Jeffrey
```

 Notice how we've "reduced our footprint" to just the ridiculously named "DudeNameSpace" object.
