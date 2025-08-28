
---

## Time & Space Complexity

- ***Big O Notation*** -  describes how the runtime (or memory usage) of an algorithm grows relative to the input size (**n**). It focuses on the worst-case scenario for scalability.

1. **O(1):** *Constant time* – independent of input size.
2. **O(log n):** *Logarithmic time* – reduces the problem size with each step.
3. **O(n):** *Linear time* – grows linearly with input size.
4. **O(n log n):** *Log-linear time* – commonly seen in efficient sorting algorithms like merge sort.
5. **O(n²):** *Quadratic time* – performance degrades significantly for larger inputs.
6. **O(2ⁿ):** *Exponential time* – grows rapidly; impractical for large inputs. Example: Recursive solutions for the Tower of Hanoi.

---

## Data Structures 

- ***Data structures*** deals with organized ways to store and manage data.

### Linear Data Structures

- Data is organized sequentially. 
- Each element is connected to a previous and next element in a linear order.

#### 1. Arrays
- Fixed size collection of homogeneous elements. 
- Stored as a contiguous memory locations.
- Every element occupies same amount of space in memory,
- Accessible via index.
- An array of objects stores the reference to those objects.
- Disadvantages: fixed length, costly insertions & deletions.
- *Time Complexity*: Retrieval of element with index = **O(1)**; Retrieval of element without index/add element = **O(n)**
#### 2.Linked Lists
- Dynamic sized collection nodes.
- Connected via pointers.
- Each node consists of: ***Data*** (value stored in the node); ***Pointer*** (reference to next node in sequence)

#### 3. Stacks 
- Follows Last In First Out (LIFO).
- Operations: ***Push*** (add element to top of stack), ***Pop*** (remove element from top of stack); ***Peek*** (view top element without removing it).

#### 4. Queues
- Follows First In First Out (FIFO).
- Operations: ***Enqueue*** (ad element to rear of queue), ***Dequeue*** (remove element from front of queue), ***Peek*** (view front element without removing it).
##### 4.1 Priority Queue
- A special type of queue where each element is associated with a priority, and elements are dequeued based on their priority rather than the order they were enqueued.
- Implemented efficiently using heaps: 
	- Min-Heap for **lowest priority first**.
    - Max-Heap for **highest priority first**.

### Non Linear Data Structures

- Data is organized hierarchically or in connected in complex relationships.

#### 1. Trees 
- Non-linear, hierarchical structure with root node and child nodes.
- **Root Node**: The node with no parents.
- **Edge**: The link from the parent node to the child node.
- **Leaf Node**: Nodes with no children. 
- **Height of a Tree** - the number of edges on the longest path from a node to a leaf. A tree with only one node has zero height.
- **Depth of a Tree** - the number of edges from the root to a node.
- For a given tree, depth and height returns the same value but may be different for individual nodes.
- Traversals: 
	1. **In-order** (*left subtree->root->right subtree*)
	2. **Pre-order** (*root->left subtree->right subtree*)
	3. **Post-order** (*left subtree->right subtree->root*)
	4. **Level-order** (each node is visited level-wise in increasing order of levels from left to right)
##### 1.1 Skew Trees
- If every node in a tree has only one child then we call such a tree a skew tree.
	- **Left Skew Tree**: Every node has only a left child.
	- **Right Skew Trees**: Every node has only the right child.
##### 1.2 Heap
- A heap is a **complete binary tree** that satisfies the *heap property*:
    1. **Min-Heap**: Parent value ≤ Child values. Root node contains the *minimum* value.
    2. **Max-Heap**: - Parent value ≥ Child values. Root node contains the *maximum* value.

```C++
void PreOrder(Node* root) {
	if(root == nullptr)
		return;
	std::cout << root->data;
	PreOrder(root->left);
	PreOrder(root->right);
}
void PreOrder(Node* root) {
	if(root == nullptr)
		return;
	PreOrder(root->left);
	std::cout << root->data;
	PreOrder(root->right);
}
void PostOrder(Node* root) {
	if(root == nullptr)
		return;
	PreOrder(root->left);
	PreOrder(root->right);
	std::cout << root->data;
}
void LevelOrder(Node* root) {
	if(!root)
		return;
	std::queue<int> q;
	q.push(root);
	while(!q.empty()) {
		Node *temp = q.pop();
		std::cout << temp->data;
		if(temp->left)
			q.add(temp->left);
		if(temp->right)
			q.add(temp->right);
	}
}
```

- **Construction of Trees**: If we are given two traversal sequences, and one of the traversal methods is *in-order* then the tree can be constructed uniquely, otherwise not.

#### 2. Graphs 
- A collection of nodes (vertices) connected by edges.
- **Vertices (or Nodes):** Represent entities.
- **Edges (or Links):** Represent connections or relationships between vertices
1. **Directed Graph:** Edges have a direction (e.g., A→B).
2. **Undirected Graph:** Edges have no direction (e.g., A−B).
- Graph Representation:
1. **Adjacency Matrix** - A **2D matrix** where `matrix[i][j]=1` if there is an edge between vertex i and j; otherwise 0.
2. **Adjacency List** - A list of vertices, where each vertex points to a list of its adjacent vertices.

### Hash-based Data Structures

- Uses a hash function to map data (keys) to memory locations (buckets).

8. HashMap - collection of key-value pairs where keys are unique.
9. HashSet - a collection of unique elements with no duplicates.

--- 

## Algorithms

- ***Algorithms*** are step-by-step procedures to solve problems efficiently.

### A) Sorting Algorithms

- Used to sort the elements in a DS.
- **Stable Sort** - preserves the relative ordering of duplicate items.
* **In-place Algorithms** - does not require additional/temporary arrays. All operations are performed on the input array itself.

#### A1. Bubble Sort
- A comparison-based algorithm where adjacent elements are swapped if they are in the wrong order.
- Stable sort & In-place algo.
- *Time Complexity*: Best case (already sorted) = **O(n)**; Worst case = **O(n^2)**

```C++
void BubbleSort(int arr[], int n)
{
    for(int i=0; i<n-1; i++)
    {
        for(int j=i+1; j<n; j++)
        {
            if(arr[i] > arr[j]) 
                swap(arr[i], arr[j]);
        }
    }
}
```
#### A2. Selection Sort
- Find smallest element and swap with first unsorted index.
- Unstable sort & In-place algo.
- *Time Complexity*: **O(n^2)**

```C++
void SelectionSort(int arr[], int n)
{
    for(int i=0; i<n-1; i++) 
    {
        int smallestIdx = i;
        for(int j=i+1; j<n; j++) 
        {
            if(arr[j] < arr[smallestIdx])
                smallestIdx = j;
        }
        if(smallestIdx != i)
            swap(arr[smallestIdx], arr[i]);
    }
}
```
#### A3. Insertion Sort 
- Builds the sorted array one element at a time by comparing and inserting into the correct position. Unsorted element is placed at its suitable place in each iteration.
- Stable sort & In-place algo.
- *Time Complexity*: Best case (already sorted) = **O(n)**; Worst case = **O(n^2)**

```C++
void InsertionSort(int arr[], int n)
{
    for(int i=1; i<n; i++)
    {
        int curr = arr[i];
        int prev = i-1;
        while(prev >= 0 && arr[prev] > curr)
        {
            arr[prev+1] = arr[prev];
            prev--;
        }
        arr[prev+1] = curr;
    }
}
```
##### A3.1 Shell Sort
  - Variation of insertion sort that aims to reduce the amount of shifting required and usually performs better than Insertion Sort.
  - Uses larger gap to compare elements and gap reduces after every round.
  - Unstable Sort & In-place algo.
  - *Time Complexity:* **O(n^2)**
#### A4. Heap Sort
- Heap Sort is a comparison-based sorting algorithm that uses a binary heap data structure to sort elements.
- In-place algo.
- *Time Complexity:* Building the heap = **O(n)**; Heapify operations during sorting = **O(n log n)**; Overall: **O(n log n)**.
#### A5. Quick Sort
- A divide-and-conquer algorithm that partitions the array into two halves around a pivot, then recursively sorts the subarrays.
- Unstable sort & In-place algo.
- *Time Complexity:* Best/Average Case = **O(n log⁡n)**; Worst Case = **O(n^2)** (occurs when the pivot is poorly chosen).
- - *Space Complexity*: **O(1)**
#### A6. Merge Sort
- A divide-and-conquer algorithm that *splits* the array into halves, *recursively* sorts them, and *merges* the sorted halves.
- Stable sort & Not In-place algo.
- *Time Complexity*: **O(n log⁡n)**
- *Space Complexity*: **O(n)**

```C++
void Merge(int arr[], int left, int mid, int right) 
{    
    int leftlo = left;
    int rightlo = mid + 1;
	// create a temporary array
    int len = right - left + 1;
    int temp[len];
    int i = 0;
    // sort elements from the two halves into the temp array
    while(leftlo <= mid && rightlo <= right) 
    {
        if(arr[leftlo] < arr[rightlo])
        {
            temp[i] = arr[leftlo];
            leftlo++;
        }
        else 
        {
            temp[i] = arr[rightlo];
            rightlo++;
        }
        i++;
    }
    // add remaining elements (if any)
    while(leftlo <= mid) 
    {
        temp[i] = arr[leftlo];
        leftlo++;
        i++;
    }
    while(rightlo <= right) 
    {
        temp[i] = arr[rightlo];
        rightlo++;
        i++;
    }
	// copy sorted array from temp to original
    for (int j = 0; j < len; j++) 
        arr[left + j] = temp[j];
}

void MergeSort(int arr[], int left, int right)
{
    if (left == right)
        return;
        
    int mid = (left + right)/2;
    
    MergeSort(arr, left, mid);
    MergeSort(arr, mid+1, right);
    Merge(arr, left, mid, right);
}
```
#### A7. Radix Sort
- A *non-comparison sort* that sorts numbers by their individual digits starting from the least significant to the most significant.
- Data must have same radix and width.
- *Time Complexity:* **O(n)**
#### A8. Counting Sort
- A non-comparison sort that works by counting the occurrences of each element and placing them in the correct position.
- Only works with non-negative numbers.
- Best to use when range of values is roughly equivalent to the number of values that need to be sorted.
- Not in-place algo
- *Time Complexity:* **O(n+k)**, where 'k' is the range of input values.

### B) Searching Algorithms

- Used to locate an element in a DS.

#### B1. Linear Search
- Sequentially checks each element in the array until the target is found.
- *Time Complexity*: **O(n)**

```C++
int LinearSearch(int arr[], int n, int key)
{
	for(int i=0; i<n; i++)
	{
		if(arr[i] == key)
			return i;
	}
	return -1;
}
```
#### B2. Binary Search
- Searches the array by repeatedly dividing the search range in half.
- Binary search can only be applied to:
	- Monotonic problem space (sorted arrays)
	- Data structures that provide random/direct access to elements. 
- *Time Complexity*: **O(log n)**

```C++
int BinarySearch(int arr[], int n, int key)
{    
    int start = 0;
    int end = n;
    while(start <= end)
    {
        int mid = (start + end)/2;
        if(arr[mid] == key) 
	        return mid;
        else if(arr[mid] < key) 
	        start = mid + 1;
        else
            end = mid - 1;    
    }
    return -1;
}
```

### C) Graph Traversal Algorithms

#### C1. Breadth-First Search (BFS) 
- Explores vertices *layer by layer* (level order).
- Uses a **queue** to explore nodes.
#### C2. Depth-First Search (DFS)
- Explores as far as possible along each branch before backtracking.
- Uses a **stack** (recursion or explicit stack).

### D) Shortest Path Algorithms

#### D1. Dijkstra's Algorithm
- Dijkstra's Algorithm is used to find the shortest path from a source vertex to all other vertices in a graph with **non-negative edge weights**.
- *Time Complexity:* O((V+E)log⁡ V) using a priority queue.
#### D2. Bellman Ford Algorithm
- Bellman-Ford is used to find the shortest path from a source vertex to all other vertices in a graph, **even with negative edge weights**.
- *Time Complexity:* O(V ⋅ E).

### E) Greedy Algorithms

- A greedy algorithm is a problem-solving technique where decisions are made **step by step**, choosing the **locally optimal choice** at each step in the hope that this leads to the **globally optimal solution**.

### F) Recursion

- Any function which calls itself is called recursion. **A recursive method solves a problem by calling a copy of itself to work on a smaller problem.** 
- Each time a function calls itself with a slightly simpler version of the original problem. This sequence of smaller problems must eventually converge on a base case.

- **Base case**: A terminating condition at which the recursive function will stop calling itself. In the absence of a base case, it will keep calling itself and get stuck in an infinite loop. 
- **Recursive call** (Smaller problem): The recursive function will invoke itself on a smaller version of the main problem.
- **Self-work**: Generally, we perform a calculation step in each recursive call. We can achieve this calculation step before or after the recursive call depending upon the nature of the problem.
#### F1. Divide & Conquer
- **Divide:** breaking the problem into smaller subproblems that are themselves smaller instances of the same type of problem.
- **Conquer:**  Conquer the subproblems by solving them recursively.
- **Combine:** Combine the solutions to the subproblems into the solution for the original given problem.

### G) Backtracking

- Backtracking is an algorithmic technique for solving problems by exploring all possible solutions in a systematic way. 
- It constructs solutions incrementally and abandons a solution ("backtracks") as soon as it determines that it cannot lead to a valid or optimal solution.
- There are generally three types of problems in backtracking:-
	1. **Decision Problems**: In these types of problems, we search for any feasible solution.
	2. **Optimization Problems**: In these types of problems, we search for the best possible solution.
	3. **Enumerations Problems**: In these types of problems, we find all feasible solutions.
#### G1. Recursive Exploration
- Backtracking explores all possibilities by building solutions step by step.
- It uses recursion to traverse through all potential solution paths.
#### G2. Pruning
- During the exploration, if a solution violates constraints or doesn't look promising, it is abandoned, and the algorithm backtracks to the previous step.

---
