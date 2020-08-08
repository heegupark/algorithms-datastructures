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
	Let lowest = Infinity;
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
