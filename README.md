
# Data Structure Review (in Java) :relaxed:

### Table of Contents
- :see_no_evil:  List < E >
- [ArrayList](#arraylist)  
- [LinkedList](#linkedlist)
- [Stack](#stack)
- [Vector](#vector)
- :hear_no_evil:  Set < E > (NO duplicate values, Objects unordered)
- [HashSet](#hashset)  
- [LinkedHashSet](#linkedhashset)  
- [TreeSet](#treeset) 
- :speak_no_evil: Queue < E >
- [Array Deque](#arraydeque)  
- [LinkedList DeQue](#linkedlist-deque)  
- :baby:  Map < K, V >
- [HashMap](#hashmap)  
- [HashLinkedMap](#hashlinkedmap)  
- [HashTable](#hashtable)  
- [TreeMap](#treemap)  
- :clown_face: Trees
- [Binary Search Tree](#binary-search-tree)
- [Heap](#heap)
- [Min Heap](#min-heap)
- [Max Heap](#max-heap)
-  [Priority Queue](#priority-queue)  
- :angel: Other
- [String and Char](#string--char)  
- [Basic Operators](#basic-operators)  
- [Math Operators](#math-operators)  
- [Balls into Bins problem](#balls-into-bins-problem)

<img src="https://cdncontribute.geeksforgeeks.org/wp-content/uploads/java-collection.jpg" width="800" />

___ 
###  ArrayList           
    //the size can increase if collection grows or shrunk if objects are removed from the collection.
Example:

    public static void main(String[] args) 
                        throws IOException 
    { 
        int n = 5; 
        ArrayList<Integer> arrli = new ArrayList<Integer>(n); 
 
        for (int i=1; i<=n; i++) 
            arrli.add(i); // Appending the new element at the end of the list 
  
        System.out.println(arrli); 
        
        arrli.remove(3); // Remove element at index 3 

        System.out.println(arrli); 

        for (int i=0; i<arrli.size(); i++) 
            System.out.print(arrli.get(i)+" "); 
    } 
    
output:

    [1, 2, 3, 4, 5]
    [1, 2, 3, 5]
    1 2 3 5 

___
### LinkedList
<img src="https://www.geeksforgeeks.org/wp-content/uploads/gq/2013/03/Linkedlist.png" width="600" />

    //Like arrays, Linked List is a linear data structure. Unlike arrays, linked list elements are not stored at the contiguous location 
    //LinkedList can be represented as a class and a Node as a separate class. 
    class LinkedList { 
	Node head; // head of list 

	/* Linked list Node*/
	class Node { 
		int data; 
		Node next; 

		// Constructor to create a new node 
		// Next is by default initialized 
		// as null 
		Node(int d) { data = d; next = null;} 
	} 
___
### Stack

    // last-in-first-out
    // Stack is a subclass of Vector.
    
    Object push(Object element) : Pushes an element on the top of the stack.
	Object pop() : Removes and returns the top element of the stack. An ‘EmptyStackException’ exception is thrown if we call pop() when the invoking stack is empty.
	Object peek() : Returns the element on the top of the stack, but does not remove it.
	boolean empty() : It returns true if nothing is on the top of the stack. Else, returns false.
	int search(Object element) : It determines whether an object exists in the stack. If the element is found, it returns the position of the element from the top of the stack. Else, it returns -1.


    // Pushing element on the top of the stack 
    static void stack_push(Stack<Integer> stack){ 
        for(int i = 0; i < 5; i++){ 
            stack.push(i); 
        } 
    } 
      
    // Popping element from the top of the stack 
    static void stack_pop(Stack<Integer> stack){ 
        System.out.println("Pop :"); 
        for(int i = 0; i < 5; i++) { 
            Integer y = (Integer) stack.pop(); 
            System.out.println(y); 
        } 
    } 
  
    // Displaying element on the top of the stack 
    static void stack_peek(Stack<Integer> stack) { 
        Integer element = (Integer) stack.peek(); 
        System.out.println("Element on stack top : " + element); 
    } 
      
    // Searching element in the stack 
    static void stack_search(Stack<Integer> stack, int element) { 
        Integer pos = (Integer) stack.search(element); 
        if(pos == -1) 
		System.out.println("Element not found"); 
        else
		System.out.println("Element is found at position " + pos);
	}
	
	public static void main (String[] args){ 
		Stack<Integer> stack = new Stack<Integer>(); 

		stack_push(stack); 
		stack_pop(stack); 
		stack_push(stack); 
		stack_peek(stack); 
		stack_search(stack, 2); 
		stack_search(stack, 6); 
	} 

___
### Vector
[vector](https://www.geeksforgeeks.org/java-util-vector-class-java/)
	
	
	Vector implements a dynamic array that means it can grow or shrink as required. 
	Like an array, it contains components that can be accessed using an integer index
	They are very similar to ArrayList but Vector is synchronised and have some legacy method 
	which collection framework does not contain.
	
	Constructor:

	Vector(): Creates a default vector of initial capacity is 10.
	Vector(int size): Creates a vector whose initial capacity is specified by size.
	Vector(int size, int incr): Creates a vector whose initial capacity is specified by size 
		and increment is specified by incr. It specifies the number of elements to allocate 
		each time that a vector is resized upward. (If increment is specified, Vector will 
		expand according to it in each allocation cycle but if increment is not specified 
		then vector’s capacity get doubled in each allocation cycle.)
	Vector(Collection c): Creates a vector that contains the elements of collection c.

Example:

	class Vector_demo { 
	    public static void main(String[] arg) 
	    { 

		// create default vector 
		Vector v = new Vector(); 

		v.add(1); 
		v.add(2); 
		v.add("geeks"); 
		v.add("forGeeks"); 
		v.add(3); 

		System.out.println("Vector is " + v); 
	    } 
	}

Output:
	
	Vector is: [1, 2, geeks, forGeeks, 3]

___      
### HashSet
[hashset](https://www.geeksforgeeks.org/hashset-in-java/)   
	
    Java HashSet class is used to create a collection that uses a hash table for storage. 
    It inherits the AbstractSet class and implements Set interface.  
    
    The important points about Java HashSet class are:  
    1. HashSet is implemented using a hash table 
    2. HashSet contains unique elements only.  
	3. Elements are not ordered.    
	4. NULL elements are allowed in HashSet.  
	5. The add, remove, and contains method have constant time complexity O(1).
	
    Constructors:
	HashSet h = new HashSet();  // HashSet<Integer> h = new HashSet<Integer>();  //Default initial capacity is 16 and default load factor is 0.75.
	HashSet h = new HashSet(int initialCapacity); //default loadFactor of 0.75
	HashSet h = new HashSet(int initialCapacity, float loadFactor);
	HashSet h = new HashSet(Collection C);

Example:

     public static void main(String[]args) 
    { 
        HashSet<String> h = new HashSet<String>(); 
  
        // Adding elements into HashSet usind add() 
        h.add("India"); 
        h.add("Australia"); 
        h.add("South Africa"); 
        h.add("India");// adding duplicate elements 
  
        // Displaying the HashSet 
        System.out.println(h); 
        System.out.println("List contains India or not:" + 
                           h.contains("India")); 
  
        // Removing items from HashSet using remove() 
        h.remove("Australia"); 
        System.out.println("List after removing Australia:"+h); 
  
        // Iterating over hash set items 
        System.out.println("Iterating over list:"); 
        Iterator<String> i = h.iterator(); 
        while (i.hasNext()) 
            System.out.println(i.next()); 
    } 
    
Output:

   	[South Africa, Australia, India]
	List contains India or not:true
	List after removing Australia:[South Africa, India]
	Iterating over list:
	South Africa
	India
	
Methods:

	boolean add(E e) //Used to add the specified element if it is not present, if it is present then return false.
	void clear() //Used to remove all the elements from set.
	boolean contains(Object o) //Used to return true if an element is present in set.
	boolean remove(Object o) //Used to remove the element if it is present in set.
	Iterator iterator() //Used to return an iterator over the element in the set.
	boolean isEmpty() //Used to check whether the set is empty or not. Returns true for empty and false for non-empty condition for set.
	int size() //Used to return the size of the set.
	Object clone() //Used to create a shallow copy of the set.

___
### LinkedHashSet
[linkedhashset](https://www.geeksforgeeks.org/linkedhashset-in-java-with-examples/)
	
	A LinkedHashSet is an ordered version of HashSet that maintains a doubly-linked List across all elements.
	LinkedHashSet lets us iterate through the elements in the order in which they were inserted.
	1. Contains unique elements only like HashSet. 
	2. Maintains insertion order.
Example:

	public static void main(String[] args)  
	{   
		LinkedHashSet<String> linkedset = new LinkedHashSet<String>();   

		// Adding element to LinkedHashSet   
		linkedset.add("A");   
		linkedset.add("B");   
		linkedset.add("C");   
		linkedset.add("D");  

		// This will not add new element as A already exists  
		linkedset.add("A");  
		linkedset.add("E");   

		System.out.println("Size of LinkedHashSet = " + 
					    linkedset.size());   
		System.out.println("Original LinkedHashSet:" + linkedset);   
		System.out.println("Removing D from LinkedHashSet: " + 
				    linkedset.remove("D"));   
		System.out.println("Trying to Remove Z which is not "+ 
				    "present: " + linkedset.remove("Z"));   
		System.out.println("Checking if A is present=" +  
				    linkedset.contains("A")); 
		System.out.println("Updated LinkedHashSet: " + linkedset);   
	}   
	
Output:

	Size of LinkedHashSet=5
	Original LinkedHashSet:[A, B, C, D, E]
	Removing D from LinkedHashSet: true
	Trying to Remove Z which is not present: false
	Checking if A is present=true
	Updated LinkedHashSet: [A, B, C, E]

___
### TreeSet
[treeset](https://www.geeksforgeeks.org/treeset-in-java-with-examples/)	
	
	The ordering of the elements is maintained by a set using their natural ordering.
	1. No duplicate values
	2. Objects in a TreeSet are stored in a sorted and ascending order.
	3. TreeSet does not allow to insert Heterogeneous objects. It will throw classCastException at Runtime if trying to add hetrogeneous objects.
	4. TreeSet serves as an excellent choice for storing large amounts of sorted information which are supposed to be accessed quickly because of its faster access and retrieval time.
	5. operations like add, remove and search take O(Log n) time. And operations like printing n elements in sorted order takes O(n) time.
	6. Java TreeSet class doesn't allow null element.
	7. Java TreeSet class is non synchronized.
Example:

	public static void main(String[] args) 
	{ 
	TreeSet<String> ts1 = new TreeSet<String>(); 

	// Elements are added using add() method 
	ts1.add("A"); 
	ts1.add("B"); 
	ts1.add("C"); 

	// Duplicates will not get insert 
	ts1.add("C"); 

	// Elements get stored in default natural 
	// Sorting Order(Ascending) 
	System.out.println(ts1); 
	} 
Output:

	[A, B, C]
	
Iterate:

	public static void main(String args[]){  
		//Creating and adding elements  
		TreeSet<String> al=new TreeSet<String>();  
		al.add("Ravi");  
		al.add("Vijay");  
		al.add("Ravi");  
		al.add("Ajay");  
		//Traversing elements  
		Iterator<String> itr=al.iterator();  
		while(itr.hasNext()){  
		System.out.println(itr.next());  
		}  
	}
Output:

	Ajay
	Ravi
	Vijay


___
### ArrayDeque
[arraydeque](https://www.geeksforgeeks.org/arraydeque-in-java/)
	
	ArrayDeque in Java provides a way to apply resizable-array in addition to the implementation of the Deque interface.
	It is also known as Array Double Ended Queue or Array Deck. 
	This is a special kind of array that grows and allows users to add or remove an element from both the sides of the queue.
	
	1. no capacity restrictions and they grow as necessary to support usage.
	2. Null elements are prohibited in the ArrayDeque.
	3. ArrayDeque class is likely to be faster than Stack when used as a stack.
	4. ArrayDeque class is likely to be faster than LinkedList when used as a queue.
Example:

   	public static void main(String[] args) 
    	{ 
		// Intializing an deque 
		Deque<Integer> de_que = new ArrayDeque<Integer>(10); 

		// add() method to insert 
		de_que.add(10); 
		de_que.add(20); 
		de_que.add(30); 
		de_que.add(40); 
		de_que.add(50); 
		for (Integer element : de_que) 
		{ 
		    System.out.println("Element : " + element); 
		} 

		System.out.println("Using clear() "); 

		// clear() method 
		de_que.clear(); 

		// addFirst() method to insert at start 
		de_que.addFirst(564); 
		de_que.addFirst(291); 

		// addLast() method to insert at end 
		de_que.addLast(24); 
		de_que.addLast(14); 

		System.out.println("Above elements are removed now"); 

		// Iterator() : 
		System.out.println("Elements of deque using Iterator :"); 
		for(Iterator itr = de_que.iterator(); itr.hasNext();) 
		{ 
		    System.out.println(itr.next()); 
		} 

		// descendingIterator() : to reverse the deque order 
		System.out.println("Elements of deque in reverse order :"); 
		for(Iterator dItr = de_que.descendingIterator();  
						       dItr.hasNext();) 
		{ 
		    System.out.println(dItr.next()); 
		} 

		// element() method : to get Head element 
		System.out.println("\nHead Element using element(): " + 
						     de_que.element()); 

		// getFirst() method : to get Head element 
		System.out.println("Head Element using getFirst(): " +  
						       de_que.getFirst()); 

		// getLast() method : to get last element 
		System.out.println("Last Element using getLast(): " +  
							de_que.getLast()); 

		// toArray() method : 
		Object[] arr = de_que.toArray(); 
		System.out.println("\nArray Size : " + arr.length); 

		System.out.print("Array elements : "); 
		for(int i=0; i<arr.length ; i++) 
		    System.out.print(" " + arr[i]); 

		// peek() method : to get head 
		System.out.println("\nHead element : " + de_que.peek()); 

		// poll() method : to get head 
		System.out.println("Head element poll : " + de_que.poll()); 

		// push() method : 
		de_que.push(265); 
		de_que.push(984); 
		de_que.push(2365); 

		// remove() method : to get head 
		System.out.println("Head element remove : " + de_que.remove()); 

		System.out.println("The final array is: "+de_que); 
    	} 	
	
Output:

	Element : 10
	Element : 20
	Element : 30
	Element : 40
	Element : 50
	Using clear() 
	Above elements are removed now
	Elements of deque using Iterator :
	291
	564
	24
	14
	Elements of deque in reverse order :
	14
	24
	564
	291

	Head Element using element(): 291
	Head Element using getFirst(): 291
	Last Element using getLast(): 14

	Array Size : 4
	Array elements :  291 564 24 14
	Head element : 291
	Head element poll : 291
	Head element remove : 2365
	The final array is: [984, 265, 564, 24, 14]
___
### LinkedList Deque
	TBD
    
___ 
### HashMap
[hashmap](https://www.geeksforgeeks.org/java-util-hashmap-in-java/)

    A HashMap store items in "key/value" pairs, and you can access them by a key (e.g. a String). 
    (有点像python的dictionary)
    
    1. To access a value, must know its key
    2. No duplicate keys, but allows duplicate values
    3. HashMap allows null key also but only once and multiple null values.
    4. This class makes no guarantees as to the order of the map

    Create HashMap Obj:
        import java.util.HashMap; // import the HashMap class
        HashMap<String, String> xxx = new HashMap<String, String>();
        HashMap<String, Integer> xxx= new HashMap<String, Integer>();

    Add keys and values:
        xxx.put("England", "London");

    Access an Item:
        xxx.get("England");

    Remove an Item:
        xxx.remove("England");

    Remove all items:
        xxx.clear();

    Hashmap Size:
        xxx.size();

    Loop through a HashMap:
        for (String i : xxx.keySet()) {
          System.out.println(i);
        }
        for (String i : xxx.values()) {
          System.out.println(i);
        }
        for (String i : xxx.keySet()) {
          System.out.println("key: " + i + " value: " + xxx.get(i));
        }
    
    An example:
        Map<Integer, Integer> map = new HashMap<Integer, Integer>();
        if (map.containsKey(target - nums[i])) { 
            result[0] = map.get(target - nums[i]);
        }

___
### HashLinkedMap
[linkedhashmap](https://www.geeksforgeeks.org/linkedhashmap-class-java-examples/)
    
    LinkedHashMap is just like HashMap with an additional feature of maintaining an order of elements inserted into it.
Example:

	public static void main(String a[]) 
	{ 
		LinkedHashMap<String, String> lhm = new LinkedHashMap<String, String>(); 
		lhm.put("one", "practice.geeksforgeeks.org"); 
		lhm.put("two", "code.geeksforgeeks.org"); 
		lhm.put("four", "quiz.geeksforgeeks.org"); 

		// It prints the elements in same order  
		// as they were inserted     
		System.out.println(lhm); 

		System.out.println("Getting value for key 'one': " 
					       + lhm.get("one")); 
		System.out.println("Size of the map: " + lhm.size()); 
		System.out.println("Is map empty? " + lhm.isEmpty()); 
		System.out.println("Contains key 'two'? "+  
					  lhm.containsKey("two")); 
		System.out.println("Contains value 'practice.geeks"
		+"forgeeks.org'? "+ lhm.containsValue("practice"+ 
		".geeksforgeeks.org")); 
		System.out.println("delete element 'one': " +  
				   lhm.remove("one")); 
		System.out.println(lhm); 
	} 
Output:

	{one=practice.geeksforgeeks.org, two=code.geeksforgeeks.org, four=quiz.geeksforgeeks.org}
	Getting value for key 'one': practice.geeksforgeeks.org
	Size of the map: 3
	Is map empty? false
	Contains key 'two'? true
	Contains value 'practice.geeksforgeeks.org'? true
	delete element 'one': practice.geeksforgeeks.org
	{two=code.geeksforgeeks.org, four=quiz.geeksforgeeks.org}
___
### HashTable
[hashtable](https://www.geeksforgeeks.org/hashtable-in-java/)

	1. key or value cannot be null
	2. it is similar to HashMap, but is synchronised.
Example:

    public static void main(String[] arg) 
    { 
        // creating a hash table 
        Hashtable<Integer, String> h = 
                      new Hashtable<Integer, String>(); 
  
        Hashtable<Integer, String> h1 = 
                      new Hashtable<Integer, String>(); 
  
        h.put(3, "Geeks"); 
        h.put(2, "forGeeks"); 
        h.put(1, "isBest"); 
  
        // create a clone or shallow copy of hash table h 
        h1 = (Hashtable<Integer, String>)h.clone(); 
  
        // checking clone h1 
        System.out.println("values in clone: " + h1); 
  
        // clear hash table h 
        h.clear(); 
  
        // checking hash table h 
        System.out.println("after clearing: " + h); 
    } 
Output:

	values in clone: {3=Geeks, 2=forGeeks, 1=isBest}
	after clearing: {}
___
### TreeMap
[treemap](https://www.geeksforgeeks.org/treemap-in-java/)

	TreeMap is Red-Black tree based NavigableMap implementation. 
	It is sorted according to the natural ordering of its keys.
	TreeMap class implements Map interface similar to HashMap class. 
	The main difference between them is that HashMap is an unordered collection while 
		TreeMap is sorted in the ascending order of its keys.
	
	1. does not allow null keys (like Map)
Example:

	public static void main(String args[]) {
		/* This is how to declare TreeMap */
		TreeMap<Integer, String> tmap = new TreeMap<Integer, String>();

		/*Adding elements to TreeMap*/
		tmap.put(1, "Data1");
		tmap.put(23, "Data2");
		tmap.put(70, "Data3");
		tmap.put(4, "Data4");
		tmap.put(2, "Data5");

		/* Display content using Iterator*/
		Set set = tmap.entrySet();
		Iterator iterator = set.iterator();
		while(iterator.hasNext()) {
		Map.Entry mentry = (Map.Entry)iterator.next();
		System.out.print("key is: "+ mentry.getKey() + " & Value is: ");
		System.out.println(mentry.getValue());
		}
	}
Output:

	key is: 1 & Value is: Data1
	key is: 2 & Value is: Data5
	key is: 4 & Value is: Data4
	key is: 23 & Value is: Data2
	key is: 70 & Value is: Data3

___ 
### Binary Search Tree

	1. The left subtree of a node contains only nodes with keys lesser than the node’s key.
	2. The right subtree of a node contains only nodes with keys greater than the node’s key.
	3. The left and right subtree each must also be a binary search tree.
	4. There must be no duplicate nodes.

<img src = "https://cdncontribute.geeksforgeeks.org/wp-content/uploads/BSTSearch.png" width = 250>

Search:

	public Node search(Node root, int key) 
	{
	    if (root==null || root.key==key) 
		return root; 
		
	    if (root.key > key) 
		return search(root.left, key); 

	    return search(root.right, key); 
	} 


Node Class and Constructors:

	class BinarySearchTree { 
		class Node { 
			int key; 
			Node left, right; 

			public Node(int item) { 
				key = item; 
				left = right = null; 
			} 
		} 

		// Root of BST 
		Node root; 

		// Constructor 
		BinarySearchTree() { 
			root = null; 
		} 

		// This method mainly calls insertRec() 
		void insert(int key) { 
			root = insertRec(root, key); 
		} 

		/* A recursive function to insert a new key in BST */
		Node insertRec(Node root, int key) { 

			/* If the tree is empty, return a new node */
			if (root == null) { 
				root = new Node(key); 
				return root; 
			} 

			/* Otherwise, recur down the tree */
			if (key < root.key) 
				root.left = insertRec(root.left, key); 
			else if (key > root.key) 
				root.right = insertRec(root.right, key); 

			/* return the (unchanged) node pointer */
			return root; 
		} 

		// This method mainly calls InorderRec() 
		void inorder() { 
			inorderRec(root); 
		} 

		// A utility function to do inorder traversal of BST 
		void inorderRec(Node root) { 
			if (root != null) { 
				inorderRec(root.left); 
				System.out.println(root.key); 
				inorderRec(root.right); 
			} 
		} 

		// Driver Program to test above functions 
		public static void main(String[] args) { 
			BinarySearchTree tree = new BinarySearchTree(); 

			/* Let us create following BST 
				     50 
				   /	\ 
				 30	 70 
				/ \ 	 / \ 
			       20 40    60 80 */
			tree.insert(50); 
			tree.insert(30); 
			tree.insert(20); 
			tree.insert(40); 
			tree.insert(70); 
			tree.insert(60); 
			tree.insert(80); 

			// print inorder traversal of the BST 
			tree.inorder(); 
		} 
	} 



### Heap
What is a Heap?
A heap is a binary tree-based data structure that satisfies the heap property, which is a specialized order property that helps maintain efficient access to the root element.

There are two types of heaps:

	Min-Heap (great for priority queues)
	Max-Heap (great for heapsort)

___ 
### Min Heap
In a min-heap, the root node has the smallest value in the entire tree. This means that every parent node is less than or equal to its children.

Properties:
	
	- The smallest element is at the root.
	- The tree is complete (1. levels filled except the lowest; 2. lowest level filled to a certain point starting from the left).

Operations:

	Insert: Insert a new element at the bottom and then "bubble up" to maintain the heap property.
	Extract Min: Remove the root element (smallest) and replace it with the last element, then "bubble down" to maintain the heap property.

	Mapping the elements of a heap into an array is trivial: 
		Current Node	arr[i]
		Parent Node	arr[(i-1)/2]
		Left Child	arr[(2*i) + 1]
		Right Child	arr[(2*i )+ 2]
  		The root of the whole tree is at arr[0].
e.g.

		    5                      13
		 /      \               /       \  
	       10        15           16         31 
	      /                      /  \        /  \
	    30                     41    51    100   41

___ 
### Max Heap

In a max-heap, the root node has the largest value in the entire tree. This means that every parent node is greater than or equal to its children.

Properties:

	- The largest element is at the root.
	- The tree is complete (every level of the tree is filled from left to right).

 e.g.

	         9
	       /   \
	      7     5
	     / \
	    6   3
Operations:

	Insert: Insert a new element at the bottom and then "bubble up" to maintain the heap property.
	Extract Max: Remove the root element (largest) and replace it with the last element, then "bubble down" to maintain the heap property.

___ 
### Priority Queue
[priorityqueue](https://www.javatpoint.com/java-priorityqueue)

	PriorityQueue:
	- Not a normal FIFO queue
	- Removes elements by priority, not insertion order
	- In Java, default is a min heap
	- peek()/poll() return the smallest element by default
	- To make a max heap, provide a custom comparator	
	
	1. PriorityQueue doesn’t permit NULL pointers.
	2. We can’t create PriorityQueue of Objects that are non-comparable
	3. PriorityQueue are unbound queues.
	
Example:

	PriorityQueue<Integer> minHeap = new PriorityQueue<>();
	PriorityQueue<Integer> maxHeap = new PriorityQueue<>((a, b) -> Integer.compare(b, a));
	 
	maxHeap.offer(num);
	int top = maxHeap.peek();
	int first = maxHeap.poll();


___ 
### String && Char
    String.valueOf(i)
    String[] keyboard = {"QWERTYUIOP","ASDFGHJKL","ZXCVBNM"};
    
    String s
    String[] parts = s.split(" ");
    
    char[] arr = s.toCharArray();
    
    System.out.println(Character.isUpperCase('c'));
    false
        
    String s;    
    int index=s.indexOf('a');
    
    //delete a char in a string
    String s;
    s = s.substring(0, index) + s.substring(index + 1);
___ 
### basic operators
    https://www.tutorialspoint.com/java/java_basic_operators.htm

    **Assume integer variable A holds 10 and variable B holds 20

    +(addition)         A+B gives 30
    -(subtraction)      A-B gives -10
    *(multiplication)   A*B gives 200
    /(division)         B/A gives 2
    %(modulus)          B%A gives 0
    ++(increment)       B++ gives 21
    --(decrement)       B-- gives 19


    ==(equal to)        A==B is not true
    !=(not equal to)    A!=B is true
    >(greater than)     A>B is not true
    <(less than)        A<B is true
    >=(greater than or equal to)
    <=(less than or equal to)

    =====================================================================
    the bitwise operators
    =====================================================================
    **assume a=60 and b=13
    a = 0011 1100
    b = 0000 1101

    a&b = 0000 1100
    a|b = 0011 1101
    a^b = 0011 0001             0 ^ N = N        N ^ N = 0
    ~a  = 1100 0011
    <<(left shift)               a<<2 will give 1111 0000
    >>(right shift)              a>>2 will give      1111
    >>>(zero fill right shift)   a>>>2 will give 0000 1111    


    ======================================================================
    logical operators
    ======================================================================
    assume A holds true and B holds false
    &&(logical and)  A&&B is false
    ||(logical or)   A||B is true
    ! (logical not)  !(A&&B) is true
___     
### math operators

    http://tutorials.jenkov.com/java/math-operators-and-math-class.html
    int abs1 =  Math.abs(10);  // abs1 = 10 (absolute value)
                Math.abs(int)
                Math.abs(long)
                Math.abs(float)
                Math.abs(double)
    int min = Math.min(10, 20);
    int max = Math.max(10, 20);
    double random = Math.random();
___ 
### Balls into Bins problem

        Give m balls and n bins. Find out how many ways to assign balls to bins. Notice the buckets has no order. Like (1,2,3) and (3,2,1) are considered the same. 
        eg, m = 3, n = 2, return 2. (1, 2) and (3, 0)


        int assignBalls(int m, int n) {
                if (m == 0 || n == 1) {
                    return 1;
                }
                if (n > m) {
                    return assignBalls(m, m);
                } else {
                    return assignBalls(m, n - 1) + assignBalls(m - n, n);
                }
            }
