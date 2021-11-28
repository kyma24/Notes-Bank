-   AcWing #29: eliminating repeated numbers (Java)
    
    i.e.
    
    input: 1->2->3->3->4->4->5
    
    output: 1->2->5
    
    input: 1->1->1->2->3
    
    output: 2->3
    
    ```java
    /**
     * Definition for singly-linked list.
     * public class ListNode {
     *     int val;
     *     ListNode next;
     *     ListNode(int x) { val = x; }
     * }
     */
    class Solution {
        public ListNode deleteDuplication(ListNode head) 
        {
            ListNode ln = new ListNode(0);
            ln.next = head;
            
            ListNode p = ln;
    
            while (p.next != null)
            {
                ListNode q = p.next;
                boolean hasDup = false;
                while (q.next != null && q.val == q.next.val)
                {  
                    q.val = q.next.val;
                    q.next = q.next.next;
                   
                    hasDup = true;
                }
                
                if (hasDup && q.next != null)
                {
                    q.val = q.next.val;
                    q.next = q.next.next;
                    p.next = q;
                }
                else if (hasDup && q.next == null)
                {
                    p.next = null;
                    break;
                }
                else
                {
                    p = q;
                }
            }
            return ln.next;
        }
    }
    ```