## Stack

A **stack** is a **data structure** that works like a **pile of plates** — you can only take the top plate off or put a new one on the top. It follows the rule:

> **LIFO** – Last In, First Out
> (Last item added is the first one to come out)

---

### 🧠 Think of it like:

You’re stacking books one on top of another:

* You put Book A.
* Then Book B.
* Then Book C.

Now to get Book A, you first need to remove Book C and B — the **last book placed (C)** comes **out first**.

---

### ✅ Real-life Example:

* **Undo** feature in MS Word: Each action goes on the stack. Undo takes the last action first.
* **Back** button in browser: Last visited page is on top.

---

### 💻 Code Example in JavaScript:

```javascript
let stack = [];

// Add (push) items
stack.push('A');
stack.push('B');
stack.push('C');

console.log(stack); // ['A', 'B', 'C']

// Remove (pop) the top item
let topItem = stack.pop();
console.log(topItem); // 'C'
console.log(stack);   // ['A', 'B']
```

---

### 📌 Common Stack Operations:

| Operation   | Description                           |
| ----------- | ------------------------------------- |
| `push()`    | Add item on top                       |
| `pop()`     | Remove item from top                  |
| `peek()`    | Look at the top item without removing |
| `isEmpty()` | Check if the stack is empty           |

---

```js
/* Stacks! */

// functions: push, pop, peek, length

var letters = []; // this is our stack

var word = "freeCodeCamp"

var rword = "";

// put letters of word into stack
for (var i = 0; i < word.length; i++) {
   letters.push(word[i]);
}

// pop off the stack in reverse order
for (var i = 0; i < word.length; i++) {
   rword += letters.pop(); 
}

if (rword === word) {
   console.log(word + " is a palindrome.");
}
else {
   console.log(word + " is not a palindrome.");
}



// Creates a stack
var Stack = function() {
    this.count = 0;
    this.storage = {};
  
    // Adds a value onto the end of the stack
    this.push = function(value) {
        this.storage[this.count] = value;
        this.count++;
    }
    
    // Removes and returns the value at the end of the stack
    this.pop = function() {
        if (this.count === 0) {
            return undefined;
        }

        this.count--;
        var result = this.storage[this.count];
        delete this.storage[this.count];
        return result;
    }
    
    this.size = function() {
        return this.count;
    }
    
    // Returns the value at the end of the stack
    this.peek = function() {
        return this.storage[this.count-1];
    }
}

var myStack = new Stack();

myStack.push(1);
myStack.push(2);
console.log(myStack.peek());
console.log(myStack.pop());
console.log(myStack.peek());
myStack.push("freeCodeCamp");
console.log(myStack.size());
console.log(myStack.peek());
console.log(myStack.pop());
console.log(myStack.peek());
```
