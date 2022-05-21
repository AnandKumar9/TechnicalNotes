Variables can be declared with `const` or `var`. While this indicates that they are the let/var equivalent of Swift, I am yet to see if that is also how they actually behave. Also, while statements can be ended with `;` in JavaScript, it does not seem to be mandatory.

It also seems to be the kind of langauge that is not compiled before running. So a syntax error (such as missing '{') seems to cause an error only when the runtime reaches there.

Converting between data types -
```
const expenseMonth = Number(str); // String to Number
const row1Value = simNum.toString() // Number to String
```

Working with an array -
```
// Creating an array
var  monthNames = ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"];

// Check if an element exists in the array
if (!expectedSheetNames.includes(expectedSheetName)) {
  // Append element to array
  expectedSheetNames.push(expectedSheetName)
}

// Length of an array
arr.length
```

Working with a dictionary -
```
var expenseCategoriesInSheet = {"TOTAL":1};
```

Split a string into an array -
```
const expenseAttributes = expenses[outerLoopIndex].split(" : ");
```

```
const str = str1 + " " + str2 // String concatenation
```

`for` loop - There is probably no 'for in' kind of synatx in JavaScript.
```
for (var outerLoopIndex = 0; outerLoopIndex < expenses.length; outerLoopIndex = outerLoopIndex + 1) { }
```
