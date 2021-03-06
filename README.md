# algorithms-datastructures

## Bubble Sort
```
Function bubbleSort(arr) {
	Let noSwap = true;
	Const swap = (arr, i,j) => {
		[arr[i], arr[j]] = [arr[j], arr[i]]
	}
	for(let i=arr.length;i>0;i--) {
		noSwap = true
		for(j=0;j<i-1;j++) {
			if(arr[j] > arr[j+1]) swap(arr,j,j+1)
			noSwap = false
		}
		if(noSwap) break;
	}
	Return arr
}
```

## Selection Sort
```
Function selectionSort(arr) {
	Let lowest = null;
	Const swap = (arr, i, j) => {
		[arr[i], arr[j]] = [arr[j], arr[i]]
	}
	for(let i=0;i<arr.length;i++)  {
		Lowest = i;
		for(let j = i+1; j<arr.length;j++) {
			if(arr[j]<arr[lowest] lowest = j
		}
		if(i!== lowest) swap(arr,i,j)
	}
	Return arr
}
```

## Insertion Sort
```
Function insertionSort(arr) {
	for(let i=1;i<arr.length;i++) {
		currentVal = arr[i]
		for(let j=i-1;j>=0 && arr[j] > currentVal; j--) {
			Arr[j+1] = arr[j]
		}
		Arr[j+1] = currentVal
	}
	Return arr
}
```

## Merge Sort
```
Function merge(arr1, arr2) {
	Let i=0;
	Let j=0;
	Const result = []
	while(i<arr1.length && j<arr2.length) {
		if(arr1[i]<arr2[j]) {
			result.push(arr1[i])
			i++
		} else {
			result.push(arr2[j])
			j++
		}
	}
	while(i<arr1.length) {
		result.push(arr1[i])
		i++
	}
	while(j<arr2.length) {
		result.push(arr2[j])
		j++
	}
	Return result
}

Function mergeSort(arr) {
	if(arr.length <= 1) return arr
	Let mid = Math.floor(arr.length/2)
	Let left = mergeSort(arr.slice(0,mid))
	Let right = mergeSort(arr.slice(mid))
	Return merge(left, right)
}
```

## Quick Sort
```
Function pivot(arr, start = 0, end = arr.length-1) {
	Const swap = (arr, i, j) => {
		[arr[i], arr[j]] = [arr[j],arr[i]]
	}

	Let pivot = arr[start]
	Let swapIdx = start

	for(let i=start+1;i<=end;i++) {
		if(pivot > arr[i]) {
			swapIdx++;
			swap(arr, swapIdx, i)
		}
	}
	swap(arr, start, swapIdx)
	Return arr
}

Function quickSort(arr, left = 0, right = arr.length=1) {
	if(left < right) { 
		Let pivotIndex = pivot(arr, left, right) 
		quickSort(arr, left, pivotIndex-1)
		quickSort(arr, pivotIndex+1, right)
	}
	Return arr
}
```

## Singly Linked List
```
class Node {
    constructor(val) {
        this.val = val;
        this.next = null;
    }    
}

class SinglyLinkedList {
    constructor() {
        this.length = 0;
        this.head = null;
        this.tail = null
    }
    push(val) {
        let newNode = new Node(val)
        if(!this.head) {
            this.head = newNode
            this.tail = this.head
        } else {
            this.tail.next = newNode
            this.tail = newNode
        }
        this.length++
        return this
    }
    traverse() {
        var current = this.head;
        while(current) {
            current = current.next
        }
    }
    pop() {
        if(!this.head) return undefined
        var current = this.head;
        var newTail = current;
        while(current.next) {
            newTail = current;
            current = current.next
        }
        this.tail = newTail
        this.tail.next = null
        this.length--
        if(this.length === 0) {
            this.head = null
            this.tail = null
        }
        return current
    }
    shift() {
        if(!this.head) return undefined
        var currentHead = this.head;
        this.head = currentHead.next;
        this.length--;
        return currentHead
     }
     unshift(val) {
         var newNode = new Node(val)
         if(!this.head) {
             this.head = newNode
             this.tail = this.head
         } else {
          newNode.next = this.head
         this.head = newNode
         this.length++
         return this
         }
     }
     get(index) { 
        if(index < 0 || index >= this.length) return null
        var counter = 0;
        var current = this.head
        while(counter !== index) {
            current = current.next
            counter++
        }
        return current
     }
     set(index, val) {
             var foundNode = this.get(index)
             if(foundNode) {
                 foundNode.val = val
                 return true
             }
             return false;
     }
     insert(index, val) {
         if(index < 0 || index > this.length) return false
         if(index === this.length) return !!this.push(val)
         if(index === 0 ) return !!this.unshift(val)
         var newNode = new Node(val)
         var prev = this.get(index - 1)
         var temp = prev.next
         prev.next = newNode;
         newNode.next = temp;
         this.length++
         return true
     }
     remove(index) {
         if(index < 0 || index >= this.length) return undefined
         if(index === 0) return this.shift()
         if(index === this.length-1) return this.pop()
         var previousNode= this.get(index-1)
         var removed = previousNode.next
         previousNode.next = removed.next
         this.length--
         return removed
     }
     reverse() {
        var node = this.head;
        this.head = this.tail
        this.tail = node
        var prev = null
        var next = null
        for(var i=0;i<this.length;i++) {
            next = node.next
            node.next = prev
            prev = node
            node = next
        }
     }
     print() {
         var arr =[]
         var current = this.head
         while(current) {
             arr.push(current.val)
             current = current.next
         }
         console.log(arr)
     }
}
```

## Doubly Linked List
```
class Node {
  constructor(val) {
    this.val = val;
    this.next = null;
    this.prev = null;
  }
}

class DoublyLinkedList {
  constructor() {
    this.head = null;
    this.tail = null;
    this.length = 0;
  }
  push(val) {
    var newNode = new Node(val);
    if (this.length === 0) {
      this.head = newNode
      this.tail = newNode
    } else {
      this.tail.next = newNode
      newNode.prev = this.tail
      this.tail = newNode
    }
    this.length++;
    return this
  }
  pop() {
    if (!this.head) return undefined
    var poppedNode = this.tail;
    if (this.length === 1) {
      this.head = null;
      this.tail = null;
    } else {
      this.tail = poppedNode.prev;
      this.tail.next = null;
      poppedNode.prev = null;
    }
    this.length--;
    return poppedNode;
  }
  shift() {
    if (this.length === 0) return undefined;
    var oldHead = this.head;
    if (this.length === 1) {
      this.head = null;
      this.tail = null;
    } else {
      this.head = oldHead.next;
      this.head.prev = null;
      oldHead.next = null;
    }
    this.length--
    return oldHead
  }
  unshift(val) {
    var newNode = new Node(val);
    if (this.length === 0) {
      this.head = newNode
      this.tail = newNode
    } else {
      this.head.prev = newNode
      newNode.next = this.head
      this.head = newNode
    }
    this.length++
    return this
  }
  get(index) {
    if(index<0||  index>=this.length) return null;
    let count, current;
    if(index <= this.length/2) {
      count = 0
      current = this.head
      while (count !== index) {
        current = current.next;
        count++
      }
    } else {
      count = this.length-1
      current = this.tail
      while(count !== index) {
        current = current.prev
        count--
      }
    }
    return current
  }
  set(index, val) {
    let foundNode = this.get(index)
    if(foundNode !== null) {
      foundNode.val = val
      return true
    }
    return false
  }
  insert(index, val) {
    if (index < 0 || index > this.length) return undefined
    if(index === 0 ) return !!this.unshift(val)
    if(index === this.length) return !!this.push(val)

    let newNode = new Node(val)
    let beforeNode = this.get(index-1)
    let afterNode = beforeNode.next

    beforeNode.next = newNode, newNode.prev = beforeNode
    newNode.next = afterNode, afterNode.prev = newNode
    this.length++
    return true
  }
  remove(index) {
    if (index < 0 || index >= this.length) return undefined
    if (index === 0) return !!this.shift()
    if (index = this.length -1 ) return !!this.pop()
    let removeNode = this.get(index)
    removeNode.prev.next = removeNode.next
    removeNode.next.prev = removeNode.prev
    removeNode.next = null
    removeNode.prev = null
    this.length--
    return removeNode
  }
}
```

## Tree Traversal - Breadth First Search
```
class Node {
    constructor(value){
        this.value = value;
        this.left = null;
        this.right = null;
    }
}

class BinarySearchTree {
    constructor(){
        this.root = null;
    }
    insert(value){
        var newNode = new Node(value);
        if(this.root === null){
            this.root = newNode;
            return this;
        }
        var current = this.root;
        while(true){
            if(value === current.value) return undefined;
            if(value < current.value){
                if(current.left === null){
                    current.left = newNode;
                    return this;
                }
                current = current.left;
            } else {
                if(current.right === null){
                    current.right = newNode;
                    return this;
                } 
                current = current.right;
            }
        }
    }
    find(value){
        if(this.root === null) return false;
        var current = this.root,
            found = false;
        while(current && !found){
            if(value < current.value){
                current = current.left;
            } else if(value > current.value){
                current = current.right;
            } else {
                found = true;
            }
        }
        if(!found) return undefined;
        return current;
    }
    contains(value){
        if(this.root === null) return false;
        var current = this.root,
            found = false;
        while(current && !found){
            if(value < current.value){
                current = current.left;
            } else if(value > current.value){
                current = current.right;
            } else {
                return true;
            }
        }
        return false;
    }
    BFS(){
        var node = this.root,
            data = [],
            queue = [];
        queue.push(node);

        while(queue.length){
           node = queue.shift();
           data.push(node.value);
           if(node.left) queue.push(node.left);
           if(node.right) queue.push(node.right);
        }
        return data;
    }
}
```

## Tree Traversal - Depth First Search(Pre Order)
```
class Node {
    constructor(value){
        this.value = value;
        this.left = null;
        this.right = null;
    }
}

class BinarySearchTree {
    constructor(){
        this.root = null;
    }
    insert(value){
        var newNode = new Node(value);
        if(this.root === null){
            this.root = newNode;
            return this;
        }
        var current = this.root;
        while(true){
            if(value === current.value) return undefined;
            if(value < current.value){
                if(current.left === null){
                    current.left = newNode;
                    return this;
                }
                current = current.left;
            } else {
                if(current.right === null){
                    current.right = newNode;
                    return this;
                } 
                current = current.right;
            }
        }
    }
    find(value){
        if(this.root === null) return false;
        var current = this.root,
            found = false;
        while(current && !found){
            if(value < current.value){
                current = current.left;
            } else if(value > current.value){
                current = current.right;
            } else {
                found = true;
            }
        }
        if(!found) return undefined;
        return current;
    }
    contains(value){
        if(this.root === null) return false;
        var current = this.root,
            found = false;
        while(current && !found){
            if(value < current.value){
                current = current.left;
            } else if(value > current.value){
                current = current.right;
            } else {
                return true;
            }
        }
        return false;
    }
    DFSPreOrder() {
        const data = []
        function traverse(node) {
            data.push(node.value)
            if(node.left) {
                traverse(node.left)
            }
            if(node.right) {
                traverse(node.right)
            }
        }
        traverse(this.root)
        return data;
    }
}
```


## Tree Traversal - Depth First Search(Post Order)
```
class Node {
    constructor(value){
        this.value = value;
        this.left = null;
        this.right = null;
    }
}

class BinarySearchTree {
    constructor(){
        this.root = null;
    }
    insert(value){
        var newNode = new Node(value);
        if(this.root === null){
            this.root = newNode;
            return this;
        }
        var current = this.root;
        while(true){
            if(value === current.value) return undefined;
            if(value < current.value){
                if(current.left === null){
                    current.left = newNode;
                    return this;
                }
                current = current.left;
            } else {
                if(current.right === null){
                    current.right = newNode;
                    return this;
                } 
                current = current.right;
            }
        }
    }
    find(value){
        if(this.root === null) return false;
        var current = this.root,
            found = false;
        while(current && !found){
            if(value < current.value){
                current = current.left;
            } else if(value > current.value){
                current = current.right;
            } else {
                found = true;
            }
        }
        if(!found) return undefined;
        return current;
    }
    contains(value){
        if(this.root === null) return false;
        var current = this.root,
            found = false;
        while(current && !found){
            if(value < current.value){
                current = current.left;
            } else if(value > current.value){
                current = current.right;
            } else {
                return true;
            }
        }
        return false;
    }
    DFSPostOrder() {
        const data = []
        function traverse(node) {
            if(node.left) {
                traverse(node.left)
            }
            if(node.right) {
                traverse(node.right)
            }
            data.push(node.value)
        }
        traverse(this.root)
        return data;
    }
}
```


## Tree Traversal - Depth First Search(In Order)
```
class Node {
    constructor(value){
        this.value = value;
        this.left = null;
        this.right = null;
    }
}

class BinarySearchTree {
    constructor(){
        this.root = null;
    }
    insert(value){
        var newNode = new Node(value);
        if(this.root === null){
            this.root = newNode;
            return this;
        }
        var current = this.root;
        while(true){
            if(value === current.value) return undefined;
            if(value < current.value){
                if(current.left === null){
                    current.left = newNode;
                    return this;
                }
                current = current.left;
            } else {
                if(current.right === null){
                    current.right = newNode;
                    return this;
                } 
                current = current.right;
            }
        }
    }
    find(value){
        if(this.root === null) return false;
        var current = this.root,
            found = false;
        while(current && !found){
            if(value < current.value){
                current = current.left;
            } else if(value > current.value){
                current = current.right;
            } else {
                found = true;
            }
        }
        if(!found) return undefined;
        return current;
    }
    contains(value){
        if(this.root === null) return false;
        var current = this.root,
            found = false;
        while(current && !found){
            if(value < current.value){
                current = current.left;
            } else if(value > current.value){
                current = current.right;
            } else {
                return true;
            }
        }
        return false;
    }
    DFSInOrder() {
        const data = []
        function traverse(node) {
            if(node.left) {
                traverse(node.left)
            }
            data.push(node.value)          
            if(node.right) {
                traverse(node.right)
            }
        }
        traverse(this.root)
        return data;
    }
}
```
