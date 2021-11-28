```py
#queueClass.py
class Queue:
    def __init__(self):
        self.queue = []
    
    def isEmpty(self):
        return not self.queue
    
    def enqueue(self, object):
        return self.queue.insert(0, object)
    
    def dequeue(self):
        if not self.queue:
            return None
        else:
            return self.queue.pop()
    
    def size(self):
        return len(self.queue)
```
```py
#hotPotato.py
from queueClass import Queue

raw_names = input("participants' names(in order): ")
rounds = int(input("number of rounds: "))
names = raw_names.split()

def simulator(names, rounds):
    originalQueue = Queue()
    
    for i in range (len(names)):
        originalQueue.enqueue(names[i])
    
    while True:
        for i in range (rounds):
            originalQueue.enqueue(originalQueue.dequeue())
        originalQueue.dequeue()
        if originalQueue.size() == 1:
            return originalQueue.dequeue()
            break
    
print(simulator(names, rounds))
```