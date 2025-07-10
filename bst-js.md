```
class Node {
  constructor(data, left = null, right = null) {
    this.value = data;
    this.left = left;
    this.right = right;
  }
}

class BST {
  constructor() {
    this.root = null;
  }

  insert(value) {
    const newNode = new Node(value);

    if (!this.root) {
      this.root = newNode;
      return;
    }

    let current = this.root;

    while (true) {
      if (value < current.value) {
        // Go Left
        if (!current.left) {
          current.left = newNode;
          return;
        }
        current = current.left;
      } else {
        // Go Right
        if (!current.right) {
          current.right = newNode;
          return;
        }
        current = current.right;
      }
    }
  }

  contains(value) {
    let current = this.root;

    while (current) {
      if (value === current.value) return true;
      current = value < current.value ? current.left : current.right;
    }

    return false;
  }

  inOrder(node = this.root) {
    if (!node) return;
    this.inOrder(node.left);
    console.log(node.value);
    this.inOrder(node.right);
  }

  delete(value, node = this.root) {
    if (!node) return null;

    if (value < node.value) {
      node.left = this.delete(value, node.left);
    } else if (value > node.value) {
      node.right = this.delete(value, node.right);
    } else {
      // Node Found
      // Case 1: No children
      if (!node.left && !node.right) return null;

      // Case 2: One child
      if (!node.left) return node.right;
      if (!node.right) return node.left;

      // Case 3: Two children
      const min = this.findMin(node.right);
      node.value = min.value;
      node.right = this.delete(min.value, node.right);
    }

    return node;
  }

  findMin(node) {
    while (node.left) {
      node = node.left;
    }
    return node;
  }
}

// Usage
const tree = new BST();
tree.insert(50);
tree.insert(30);
tree.insert(70);
tree.insert(20);
tree.insert(40);
tree.insert(60);
tree.insert(80);

console.log(tree.contains(60)); // true
console.log(tree.contains(25)); // false

console.log("Before Deletion:");
tree.inOrder(); // 20 30 40 50 60 70 80

tree.delete(70);

console.log("After Deletion of 70:");
tree.inOrder(); // 20 30 40 50 60 80


```
