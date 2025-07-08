Absolutely! Here's an easy explanation of **Queues** and **Priority Queues** with simple JavaScript examples:

---

## 📦 **Queue**

A **Queue** is a data structure that works like a **line at a ticket counter**.

> **FIFO** – First In, First Out
> (The first person in line gets served first)

---

### ✅ Real-Life Analogy:

* People standing in line.
* First person enters first, leaves first.

---

### 💻 Queue in JavaScript:

```javascript
let queue = [];

// Enqueue – Add items at the end
queue.push("A");
queue.push("B");
queue.push("C");

console.log(queue); // ['A', 'B', 'C']

// Dequeue – Remove from the front
let first = queue.shift();
console.log(first); // 'A'
console.log(queue); // ['B', 'C']
```

---

### 📌 Common Queue Operations:

| Operation | Description                 |
| --------- | --------------------------- |
| `push()`  | Add to the end (enqueue)    |
| `shift()` | Remove from front (dequeue) |
| `length`  | Number of items             |

---

## 🚨 **Priority Queue**

A **Priority Queue** is like a **hospital emergency room**:

* Patients with **higher priority** are treated **before others**, even if they came later.

---

### ✅ Real-Life Analogy:

* Person with chest pain (priority high) goes first.
* Person with fever (priority low) waits.

---

### 💻 Priority Queue in JavaScript:

We'll use an array of objects with `value` and `priority`.

```javascript
class PriorityQueue {
  constructor() {
    this.items = [];
  }

  // Enqueue with priority
  enqueue(value, priority) {
    const newItem = { value, priority };
    let added = false;

    // Insert in correct position based on priority
    for (let i = 0; i < this.items.length; i++) {
      if (priority < this.items[i].priority) {
        this.items.splice(i, 0, newItem);
        added = true;
        break;
      }
    }

    // If not inserted, push at the end
    if (!added) {
      this.items.push(newItem);
    }
  }

  // Dequeue – remove highest priority item (lowest number)
  dequeue() {
    return this.items.shift();
  }

  print() {
    console.log(this.items);
  }
}

// Usage
const pq = new PriorityQueue();

pq.enqueue("Chest pain", 1);  // High priority
pq.enqueue("Fever", 3);       // Low priority
pq.enqueue("Broken arm", 2);  // Medium

pq.print();
// Output: [{value: 'Chest pain', priority: 1}, {value: 'Broken arm', priority: 2}, {value: 'Fever', priority: 3}]

console.log(pq.dequeue()); // {value: 'Chest pain', priority: 1}
```

```js
/* Queues */

function Queue () { 
    collection = [];
    this.print = function() {
        console.log(collection);
    };
    this.enqueue = function(element) {
        collection.push(element);
    };
    this.dequeue = function() {
        return collection.shift(); 
    };
    this.front = function() {
        return collection[0];
    };
    this.size = function() {
        return collection.length; 
    };
    this.isEmpty = function() {
        return (collection.length === 0); 
    };
}

var q = new Queue(); 
q.enqueue('a'); 
q.enqueue('b');
q.enqueue('c');
q.print();
q.dequeue();
console.log(q.front());
q.print();


function PriorityQueue () {
    var collection = [];
    this.printCollection = function() {
      (console.log(collection));
    };
    this.enqueue = function(element){
        if (this.isEmpty()){ 
            collection.push(element);
        } else {
            var added = false;
            for (var i=0; i<collection.length; i++){
                 if (element[1] < collection[i][1]){ //checking priorities
                    collection.splice(i,0,element);
                    added = true;
                    break;
                }
            }
            if (!added){
                collection.push(element);
            }
        }
    };
    this.dequeue = function() {
        var value = collection.shift();
        return value[0];
    };
    this.front = function() {
        return collection[0];
    };
    this.size = function() {
        return collection.length; 
    };
    this.isEmpty = function() {
        return (collection.length === 0); 
    };
}

var pq = new PriorityQueue(); 
pq.enqueue(['Beau Carnes', 2]); 
pq.enqueue(['Quincy Larson', 3]);
pq.enqueue(['Ewa Mitulska-Wójcik', 1])
pq.enqueue(['Briana Swift', 2])
pq.printCollection();
pq.dequeue();
console.log(pq.front());
pq.printCollection();

```
