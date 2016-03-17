# Console API
*Origin Link: <https://developer.chrome.com/devtools/docs/console-api>, <https://developer.chrome.com/devtools/docs/console>*

## Console Format Specifier
Format Specifier    | Description
:-------------------| :-----------
%s                  | Formats the value as a string.
%d or %i            | Formats the value as an integer.
%f                  | Formats the value as a floating point value.
%o                  | Formats the value as an expandable DOM element.
%O                  | Formats the value as an expandable JavaScript object.
%c                  | Formats the output string according to CSS styles you provide.

## Console API Reference

* **console.log(object [, object, ...])**
    The behavior of calling console.log is equivalent to calling console.dir on Javascript obejct(non-dom), or calling console.dirxml on HTML element(dom).

* **console.info(object [, object, ...])**
* **console.debug(object [, object, ...])**
* **console.warn(object [, object, ...])**
* **console.error(object [, object, ...])**

---

* **console.dir(object)**
    Prints a JavaScript representation of the specified object.

* **console.dirxml(object)**
    Prints an XML representation of the specified object.
    * `%O` is a shortcut for dir.
    * `%o` acts either as dir or dirxml depending on the object type (non-dom or dom)

---

* **console.table(object[, object])**

    > console.table([{a:1, b:2, c:3}, {a:"foo", b:false, c:undefined}]);
    > console.table([[1,2,3], [2,3,4]]);

    The second parameter to table() is optional. You may define an array containing the property strings you wish to display.
    
    ```js
    function Person(firstName, lastName, age) {
        this.firstName = firstName;
        this.lastName = lastName;
        this.age = age;
    }
    var family = {};
    family.mother = new Person("Susan", "Doyle", 32);
    family.father = new Person("John", "Doyle", 33);
    family.daughter = new Person("Lily", "Doyle", 5);
    family.son = new Person("Mike", "Doyle", 8);
    console.table(family, ["firstName", "lastName", "age"]);
    ```

---

* **console.group(object[, object, ...])**
* **console.groupCollapsed(object[, object, ...])**
* **console.groupEnd()**

---

* **console.assert(expression, object)**
    If the specified expression is false, the message is written to the console along with a stack trace. Failing expressions are `false`, `0`, `null`, or `undefined`.

    > console.assert(false, "value of expression is false");

---

* **console.clear()**

---

* **console.count(label)**

    > console.count("Executed times:");

---

* **console.time(label)**
* **console.timeEnd(label)**

    ```js
    console.time("Array initialize");
    var array= new Array(1000000);
    for (var i = array.length - 1; i >= 0; i--) {
        array[i] = new Object();
    };
    console.timeEnd("Array initialize");
    ```

* **console.timeStamp([label])**

---

* **console.profile([label])**
* **console.profileEnd()**

    ```js
    console.profile("init")
    console.profileEnd("init")
    ```

* **console.trace(object)**
    Prints a stack trace from the point where the method was called, including links to the specific lines in the JavaScript source. 

---

**debugger**
The global debugger function causes Chrome to stop program execution and start a debugging session at the line where it was called. 
**Note:** The debugger command is not a method of the console object.

