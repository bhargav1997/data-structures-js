## Set

### ✅ What is a **Set** (in programming)?

A **Set** is a **collection of unique items**.
That means:

* **No duplicates allowed**
* Order may not be guaranteed (depends on the language)

---

### 📦 Real-Life Example:

Think of a **stamp collection**:

* You collect unique stamps.
* If someone gives you the same stamp again, you don’t add it again.

---

### 💻 Example in JavaScript:

```javascript
let mySet = new Set();

mySet.add(10);
mySet.add(20);
mySet.add(10); // Duplicate, won't be added again

console.log(mySet); // Output: Set(2) {10, 20}

// Check if a value exists
console.log(mySet.has(10)); // true

// Remove a value
mySet.delete(20);
console.log(mySet); // Set(1) {10}
```

---

### 💻 Example in Python:

```python
my_set = set()

my_set.add(10)
my_set.add(20)
my_set.add(10)  # Duplicate

print(my_set)  # Output: {10, 20}

# Check if value exists
print(10 in my_set)  # True

# Remove a value
my_set.remove(20)
print(my_set)  # {10}
```

---

### 🔁 Common Set Operations:

| Operation               | Description                         |
| ----------------------- | ----------------------------------- |
| `add()`                 | Add an item                         |
| `remove()` / `delete()` | Remove an item                      |
| `has()` / `in`          | Check if an item exists             |
| `size` / `len()`        | Get number of items                 |
| `union`                 | Combine two sets                    |
| `intersection`          | Get common items                    |
| `difference`            | Items in one set but not in another |

---
```js
/* Sets */

function mySet() {
    // the var collection will hold the set
    var collection = [];
    // this method will check for the presence of an element and return true or false
    this.has = function(element) {
        return (collection.indexOf(element) !== -1);
    };
    // this method will return all the values in the set
    this.values = function() {
        return collection;
    };
    // this method will add an element to the set
    this.add = function(element) {
        if(!this.has(element)){
            collection.push(element);
            return true;
        }
        return false;
    };
    // this method will remove an element from a set
    this.remove = function(element) {
        if(this.has(element)){
            index = collection.indexOf(element);
            collection.splice(index,1);
            return true;
        }
        return false;
    };
    // this method will return the size of the collection
    this.size = function() {
        return collection.length;
    };
    // this method will return the union of two sets
    this.union = function(otherSet) {
        var unionSet = new mySet();
        var firstSet = this.values();
        var secondSet = otherSet.values();
        firstSet.forEach(function(e){
            unionSet.add(e);
        });
        secondSet.forEach(function(e){
            unionSet.add(e);
        });
        return unionSet;
    };
    // this method will return the intersection of two sets as a new set
    this.intersection = function(otherSet) {
        var intersectionSet = new mySet();
        var firstSet = this.values();
        firstSet.forEach(function(e){
            if(otherSet.has(e)){
                intersectionSet.add(e);
            }
        });
        return intersectionSet;
    };
    // this method will return the difference of two sets as a new set
    this.difference = function(otherSet) {
        var differenceSet = new mySet();
        var firstSet = this.values();
        firstSet.forEach(function(e){
            if(!otherSet.has(e)){
                differenceSet.add(e);
            }
        });
        return differenceSet;
    };
    // this method will test if the set is a subset of a different set
    this.subset = function(otherSet) {
        var firstSet = this.values();
        return firstSet.every(function(value) {
          return otherSet.has(value);
        });
    };
}
var setA = new mySet();  
var setB = new mySet();  
setA.add("a");  
setB.add("b");  
setB.add("c");  
setB.add("a");  
setB.add("d");  
console.log(setA.subset(setB));
console.log(setA.intersection(setB).values());
console.log(setB.difference(setA).values());

var setC = new Set();  
var setD = new Set();  
setC.add("a");  
setD.add("b");  
setD.add("c");  
setD.add("a");  
setD.add("d");  
console.log(setD.values())
setD.delete("a");
console.log(setD.has("a"));
console.log(setD.add("d"));
```
