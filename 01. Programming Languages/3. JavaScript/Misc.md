#### Code editors

Visual Studio Code (free) and WebStorm (paid) are two famous full-fledged IDEs. Common lighweight editors for doing quick things are Atom, Sublime, Vim, Emacs.

#### Useful links

[JavaScript.info tutorial](https://javascript.info) <br>
[Latest ECMA specifications](https://tc39.github.io/ecma262/) <br>
[The main JavaScript reference (Mozilla)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference) <br>
[Browser-based support for various features](https://caniuse.com) <br>
[A similar comparison across even non-browser engines](https://kangax.github.io/compat-table) <br>

#### JavaScript.info coverage so far - <br>
Language sections: 1, 2, 4 <br>
Browser sections: <br>
Additional articles sections: <br>

Skipped - <br>
4.8: Object to primitive conversion <br>
5.6: Iterables <br>
5.8: WeakMap, WeakSet <br>
6.9: func.call, func.apply <br>
6.10: Function Binding <br>
8.3: Native prototypes <br>
9.5: Extending built-in classes <br>
12.2: Async iteration and generators <br>
14.4: Reference Type <br>

12/25 - 11 chapters left. 11*10 = 110 hrs, so 10 days? That is Jan 4th. Is that worth it. Well if I really have learnt an important language by the end of it, I think yes.

#### String operations

##### String interpolation

```
console.log(`${a} - ${b}`);
```

##### Checking if a string satisfies a particular regex

```javascript
if (/^\d{1,2}\/\d{1,2}\/\d{4}$/.test(value[0])) { 
  .... 
}
```

##### Add a prefix if string length is less than some particular length

The below example prefixes a zero if length is less than 2.

```swift
const prefixZeroIfNeeded = (str) => str.toString().padStart(2, '0'); // Actually a lambda/inline function kind of thing

const newFromDateValue = `${year} ${prefixZeroIfNeeded(month)} ${prefixZeroIfNeeded(day)}`;
```



#### Misc.

##### `eval`

A call to `eval(code)` runs the string of code and returns the result of the last statement. Its not a great practice to use it though and hence should be used only when really necessary. It can also access outer local variables.

```
eval("let x = 5; function f() {}");
alert(typeof x);
```

##### Currying

`Currying` is a transform that makes f(a,b,c) callable as f(a)(b)(c). Its not some built-in thing, but just a way of transforming functions. ([Link](https://javascript.info/currying-partials#summary))

