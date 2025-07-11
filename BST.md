Let's break down **Binary Search Tree (BST): Traversal & Height** in simple terms, with examples.

---

## 🌳 Binary Search Tree (BST) Quick Recap:

* A tree where:

  * Left child < Parent
  * Right child > Parent

---

## 🔁 BST Traversal Types

There are 3 main **depth-first** traversal methods:

### 1. **In-order Traversal (Left ➡ Root ➡ Right)**

* **Gives sorted order** in a BST

```js
inOrder(node) {
  if (!node) return;
  this.inOrder(node.left);
  console.log(node.value);
  this.inOrder(node.right);
}
```

### 2. **Pre-order Traversal (Root ➡ Left ➡ Right)**

* Used to copy tree or serialize

```js
preOrder(node) {
  if (!node) return;
  console.log(node.value);
  this.preOrder(node.left);
  this.preOrder(node.right);
}
```

### 3. **Post-order Traversal (Left ➡ Right ➡ Root)**

* Useful for deleting/freeing the tree

```js
postOrder(node) {
  if (!node) return;
  this.postOrder(node.left);
  this.postOrder(node.right);
  console.log(node.value);
}
```

### 4. **Level-order Traversal (Breadth-first)**

* Traverses level by level using a queue

```js
levelOrder() {
  if (!this.root) return;
  let queue = [this.root];
  while (queue.length > 0) {
    let node = queue.shift();
    console.log(node.value);
    if (node.left) queue.push(node.left);
    if (node.right) queue.push(node.right);
  }
}
```

---

## 📏 BST Height

### ➕ What is Height?

* Height = Number of edges on the longest path from a node to a leaf.
* Height of an empty tree = `-1`
* Height of a leaf node = `0`

### ✅ Code to Calculate Height:

```js
height(node = this.root) {
  if (!node) return -1; // base case
  return 1 + Math.max(this.height(node.left), this.height(node.right));
}
```

---

## 🧪 Example

Let’s say this is the BST:

```
       50
     /    \
   30      70
  /  \    /  \
20   40  60  80
```

* **In-order**: `20 30 40 50 60 70 80`
* **Pre-order**: `50 30 20 40 70 60 80`
* **Post-order**: `20 40 30 60 80 70 50`
* **Level-order**: `50 30 70 20 40 60 80`
* **Height**: `2` (50 → 70 → 80)

---

## ✅ Final Tip:

For all traversal methods, you usually need a **recursive function** and optionally an array to store the result instead of `console.log`.

