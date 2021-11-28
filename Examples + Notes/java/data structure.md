-   data structure
    
    -   **big O notation** describes performance of algorithm
    -   O(1) - whenever runs line of code, takes a constant time: doesn't matter how many elements in array code that is running.
        -   if duplicates same line of code, it becomes O(2): double run time. but since it is always a constant time, it becomes O(1) always, w/o variation(size of array doesn't matter
    -   however, during loops, size of input matters. the larger, the slower & the more time it takes: big O notation of O(n), where n is the number of iterations.
    -   if add statements around, like adding a print statement bfore and after for loop, big O notation is O(1) + O(n) + O(1) = O(n), because the print statements don't contribute much.
        -   meanwhile, when you double the for loop, it's O(2n) which simplifies to O(n) because it increases linearly.
    -   if add a different for loop after other for loop, it becomes O(n) and O(m) separately, but added together, since the relationship is linear, it is still O(n).
    -   nested for loops: big O value of n SQUARED. in short, try not to use nested loops if you can help it.
        -   same as O(n), if there is a loop before the nested loops, the big O notation is O(n + n^2), which is equal to O(n^2) → drop the extra n
        -   runtime complexity for 2 loops nested in 1 is O(n^3)
    -   **linear search** of an array: takes a long time, has a linear relationship: O(n)
    -   **binary search** of an array: reduces work by half every step. 1M items only uses MAX of 19 comparisons: O(log n) - more scalable than linear!
    
    CONSTANT - O(1)
    
    LOGARITHMIC - O(log n)
    
    LINEAR - O(n)
    
    QUADRATIC - O(n^2)
    
    EXPONENTIAL - O(2^n)
    
    -   **space complexity**: limited space; optimize space in the memory... use big O notation to express how much space the code needs to run
        
    -   O(1) space: reserves one space for the memorization of variables
        
    -   O(n) space: allocates space for the size of array w/ size n
        
        -   for a for loop: keeps saving the value each iteration
    -   **arrays**:
        
        -   integers in Java take 4 bytes of memory: looking up items in an array by index is fast bc the calculation of memory address is very simple
        -   PROS: very useful in general
        -   CONS: **1.** arrays are static in Java; when they are allocated, it specifies size and can't be changed later on(have to guess how many spaces: if guess too little, then there are blank spaces which wastes space). when/if resizing, copies old array into larger array, thus leaving some spaces blank and wasting memory. By moving, need for loop that takes # of items in array number of iterations, it is O(n), much more than O(1)← best case. **Worst case scenario**: get rid of first item, need to move all of the other values over; the more values, the more costly. Big O value of O(n). Address of array in memory is printed in shell after running the code, expressed in base 16.
            -   will find double the space of the first array if have to add another item
        
        ```java
        import java.util.Arrays;
        
        public class Main
        {
        	public static void main(String[] args)
        	{
        		int{} numbers = {10, 20, 30};
        		System.out.println(numbers.length);
        		System.out.println(Arrays.toString(numbers));
        
        //^^toString is a static method; can be called w/ the class(in this case, Arrays)
        	}
        }
        ```
        
        -   **dynamic array**: as you add items, it will auto-grow; as you remove items, it will auto-shrink
        
        ```java
        import java.util.Arrays;
        public class Main
        {
        	public static void main(String[] args)
        	{
        		Array numbers = new Array(3);
        		numbers.insert(10);
        		numbers.insert(20);
        		numbers.insert(30);
        		numbers.print();
        	}
        }
        ```
        
        -   linked lists
            
            can be really scrambled
            
            -   to store list of objects in sequence
                -   unlike arrays, can grow/shrink automatically
            -   first node = head, last node = tail
                -   linkage btwn first one & second one, etc.
                -   each node has 2 attributes: 1 is value, another is address of next node on the linked list
                -   if there are people aligned together. first is head. only needs to remember who is the next one/behind them, middle only need to know who is behind them to keep list going(doesn't need to know front one, since head knows where second is.)
            
            to find out if a value is in the list, have to traverse from head to tail. O(n). By index, node keeps reference to next node; worst case will also be O(n) bc may be the object at the end of the list. have to traverse until find item.
            
            to insert list. add the end, just have to add to the end and make the original tail reference new node. thus, O(1)
            
            at beginning, create new node, link to first node, change head to reference new node, so O(1) simply update links/references
            
            in the middle, first have to find node(O(1)), create another node, have to update links(O(1)) by breaking/adding, so is O(n)
            
            basically same for deleting. If need to remove tail, have to traverse to find the node before the tail, so is O(n) if get rid of beginning, end, and middle item then it would be respectively O(1), O(n), O(n)