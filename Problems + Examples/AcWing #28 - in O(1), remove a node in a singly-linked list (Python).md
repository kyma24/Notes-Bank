-   AcWing #28: in O(1), remove a node in a singly-linked list (Python)
    
    ```python
    # Definition for singly-linked list.
    # class ListNode(object):
    #     def __init__(self, x):
    #         self.val = x
    #         self.next = None
    
    class Solution(object):
        def deleteNode(self, node):
            """
            :type node: ListNode
            :rtype: void 
            """
            if node.next:
                node.val = node.next.val
                node.next = node.next.next
                return node
            else:
                return null
    ```