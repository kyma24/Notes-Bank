the lifecycle of an object is made up of its **creation**, **manipulation**, and **destruction**

-   creation
    
    the first stage of the life-cycle of an object is the **definition** of the class to which it belongs.
    
    the next stage is the **instantiation** of an instance, when ****init**** is called.
    
    memory is allocated to store the instance. just before this occurs, the ****new**** method of the class is called. this is usually overridden only in special cases.
    
    after all this has happened, the object is ready to be used.
    
    note: other code can then interact with the object, by calling functions on it and accessing its attributes.
    
    eventually, it will finish being used, and can be destroyed.
    
-   destruction
    
    when an object is destroyed, the memory allocated to it is freed up, and can be used for other purposes.
    
    destruction of an object occurs when its **reference count** reaches zero.
    
    reference count is the number of variables and other elements that refer to an object.
    
    if nothing is referring to it(it has a reference count of zero) nothing can interact with it, so it can be safely deleted.
    
    in some situations, 2 or more objects can be referred to by each other only, and therefore can be deleted as well.
    
    the **del** statement reduces the reference count of an object by one, and this often leads to deletion.
    
    the magic method for the **del** statement is ****del****.
    
    the process of deleting objects when they are no longer needed is called **garbage collection**.
    
    in summary, an object's reference count increases when it is assigned a new name or placed in a container(list, tuple, or dictionary). the object's reference count decreases when it's deleted with **del**, its reference is reassigned, or its reference goes out of scope. When an object's reference count reaches zero, Python automatically deletes it.
    
    ```python
    a = 42 #Create object <42>
    b = a #Increase ref. count of <42>
    c = [a] #increase ref. count of <42>
    
    del a #decrease ref. count of <42>
    b = 100 #decrease ref. count of <42>
    c[0] = -1 #Decrease ref. count of <42>
    ```
    
    note: lower level languages like C don't have this automatic memory management
    
    ```python
    #__del__ is the magic method for
    del instance
    ```