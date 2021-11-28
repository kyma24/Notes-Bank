**Inheritance**: ability for one class to be related to another class in much the same way that people can be related to one another. i.e. Children inherit characteristics from their parents; similarly, Python child classes can inherit charactersitic data and behavior from a parent class. These classes are often referred to as **subclasses** and **superclasses**.

Below: built-in Python collections & their relationships to one another. We call a relationship structure such as this an **inheritance hierarchy**. For example, this list is a child of the sequential collection. In this case, we call the list the child and the sequence the parent(or subclass and superclass sequence). This is often referred to as an `IS-A Relationship`(the list **IS-A** sequential collection). This implies that lists inherit important characteristics from sequences, namely the order of the underlying data and operations such as concatenation, repitition, and indexing.
![../_images/inheritance1.png](https://runestone.academy/runestone/books/published/pythonds/_images/inheritance1.png)

Sequential collections: Lists, tuples, dictionaries, strings, etc. They all inherit common data organization and operations. However, each of them is distinct based on whether the data is homogenous and whether the collection is immutable. The children all gain from their parents but distinguish themselves by adding additional characteristics.

By organizing classes in hierarchical fashion, OOP languages allow previously written code to be extended to meet the needs of a new situation. In addition, by organizing data in this hierarchical matter, we can better understand the relationships that exist & be more efficient in building abstract representations.

Constructing simulation to explore idea further: application to simulate digital circuits. The basic building block for simulation will be logic gate. 
![../_images/truthtable.png](https://runestone.academy/runestone/books/published/pythonds/_images/truthtable.png)

In order to implement a circuit, will first build a representation for logic gates. Logic gates are easily organized into a class inheritange hierarchy as shown below. At the top of the hierarchy, the `LogicGate` class represents the most general characteristics of logic gates: namely, a label for the gate and an output line. The next level of subclasses breaks the logic gates into two families, those that have one input line and those that have two. Below that, the specific logic functions of each appear.
![../_images/gates.png](https://runestone.academy/runestone/books/published/pythonds/_images/gates.png)

We can now start to implement the classes by starting w/ the most general, `LogicGate`. As noted earlier, each gate has an id label and a single output line. In addition, we need methods to allow a user of a gate to ask the gate for its label.

The other behavior that every logic gate needs is the ability to know its output value. This will require that the gate perform the appropriate logic based on the current input. In order to produce output, the gate needs to know specifically what that logic is. This means calling a method to perform the logical computation. The complete class is shown:
```python
class LogicGate:
	def __init__(self, n):
		self.label = n
		self.output = None
	def getLabel(self):
		return self.label
	def getOutput(self):
		self.output = self.performGateLogic()
		return self.output
```

At this point, we won't implement the `performGateLogic` function. The reason for this is that we don't know how each gate will perform its own logical operation. Those details will be included by each indvl gate that is added to the hierarchy. This is a very powerful idea in OOP. We are writing a method that will use code that doesn't exist yet. The parameter `self` is a reference to the actual gate object invoking the method. Any new logic gate that gets added to the hierarchy will simply need to implement the `performGateLogic` function and it will be used at the appropriate time. Once done, the gate can provide its output value. This ability to extend a hierarchy that currently exists and provide the specific functions that the hierarchy needs to use the new class is extremely important for reusing existing code.

We categorized the logic gates based on the number of input lines. The AND and OR gates both have 2 input lines. NOT gates have 1 input line. The `BinaryGate` class will be a subclass of `LogicGate` and will add two input lines. The `UnaryGate` class will also subclass `LogicGate` but will have only a single input line. In computer circuit design, these lines are sometimes called "pins" so we will use that terminology in the implementation.
```python
class BinaryGate(LogicGate):
	def __init__(self, n):
		LogicGate.__init__(self, n)
		self.pinA = None
		self.pinB = None
	def getPinA(self):
		return int(input("Enter Pin A input for gate " + self.getLabel() + "-->"))
	def getPinB(self):
		return int(input("Enter Pin B input for gate " + self.getLabel() + "-->"))
```

```python
class UnaryGate(LogicGate):
	def __init__(self, n):
		LogicGate.__init__(self, n)
		self.pin = None
	def getPin(self):
		return int(input("Enter Pin input for gate " + self.getLabel() + "-->"))
```

The constructors of both of these classes start w/ an explicit call to the constructor of the parent class using the parent's `__init__` method. When creating an instance of the `BinaryGate` class, we first want to initialize any data items that are inherited from `LogicGate`. In this case, that means the label for the gate. The constructor then goes on to add the two input lines (`pinA` and `pinB`). This is a very common pattern that you should always use when building class hierarchies. Child class constructors need to call parent class constructors and then move on to their own distinguishing data.

Python also has a func called `super` which can be used in place of explicitly naming the parent class. This is a more general mechanism, and is widely used, especialy when a class has more than one parent. For example, in the example abv, `LogicGate.__init__(self,n)` could be replaced with `super(UnaryGate,self).__init__(n)`.

The only behavior that the `BinaryGate` class adds is the ability to get the values from the two input lines. Since these values come from some external place, we will simply ask the user via an input statement to provide them. The same implementation occurs for the `UnaryGate` class except that there is only one input line.

Now that we have a general class for gates depending on the number of input lines, we can build specific gates that have unique behavior. For example, the `AndGate` class will be a subclass of `BinaryGate` since AND gates have 2 input lines. As before, the first line of the constructor calls upon the parent class constructor (`BinaryGate`), which in turn calls its parent class constructor (`LogicGate`). Note that the `AndGate` class doesn't provide any new data since it inherits two input lines, one output line, and a label.
```python
class AndGate(BinaryGate):
	def __init__(self, n):
		super(AndGate, self).__init__(n)
	def performGateLogic(self):
		a = self.getPinA()
		b = self.getPinB()
		if a==1 and b==1:
			return 1
		else:
			 return 0
```

The only thing `AndGate` needs to add is the specific behavior that performs the `performGateLogic` method. For an AND gate, this method first must get the two input values and then only return 1 if both input values are 1. The complete class is shown above.

We can show the `AndGate` class in action by creating an instance and asking it to compute its output. The following session shows an `AndGate` object, `g1`, that has an internal label `"G1"`. When we invoke the `getOutput` method, the object must first call its `performGateLogic` method which in turn queries the two input lines. Once the values are provided, the correct output is shown.
```python
>>> g1 = AndGate("G1")
>>> g1.getOutput()
Enter Pin A input for gate G1 -->1
Enter Pin B input for gate G1 -->0
0
```

The same development can be done for OR gates and NOT gates. The `OrGate` class will also be a subclass of `BinaryGate` and the `NotGate` class will extend the `UnaryGate` class. Both of these classes will need to provide their own `performGateLogic` functions, as this is their special behavior.

We can use a single gate by first constructing an instance of one of the gate classes and then asking the gate for its output(which in turn needs inputs to be provided). For example:
```python
>>> g2 = OrGate("G2")
>>> g2.getOutput()
Enter Pin A input for gate G2 -->1
Enter Pin B input for gate G2 -->1
1
>>> g2.getOutput()
Enter Pin A input for gate G2 -->0
Enter Pin B input for gate G2 -->0
0
>>> g3 = NotGate("G3")
>>> g3.getOutput()
Enter Pin input for gate G3 -->0
1
```

Now that we have the basic gates working, we can turn our attention to building circuits. In order to create a circuit, we need to connect gates together, the output of one flowing into the input of another. To do this, we will implement a new class called `Connector`.

The `Connector` class will not reside in the gate hierarchy. It will, however, ues the gate hierarchy in that each connector will have two gates, one on either end. This relationship is very important in OOP. It is called the **HAS-A Relationship**. Recall earlier that the phrase "IS-A Relationship" was used to say that a child class is related to a parent class, for example `UnaryGate` IS-A `LogicGate`.
![../_images/connector.png](https://runestone.academy/runestone/books/published/pythonds/_images/connector.png)

Now, with the `Connector` class, we say that a `Connector` HAS-A `LogicGate` meaning that connectors will have instances of the `LogicGate` class within them but are not part of the hierarchy. When designing classes, it is very important to distinguish between those that have the IS-A relationship(which requires inheritance) and those that have HAS-A relationships(with no inheritance).

Below shows the `Connector` class. The two gate instances within each connector object will be referred to as the `fromgate` and the `togate`, recognizing that data values will "flow" from the output of one gate into an input line of the next. The call to `setNextPin` is very important for making connections. We need to add this method to the gate classes so that each `togate` can choose the proper input line for the connection.
```python
class Connector:
	def __init__(self, fgate, tgate):
		self.fromgate = fgate
		self.togate = tgate
		tgate.setNextPin(self)
	def getFrom(self):
		return self.fromgate
	def getTo(self):
		return self.togate
```

In the `BinaryGate` class, for gates with two possible input lines, the connector must be connected to only one line. If both of them are available, we will choose `pinA` by default. If `pinA` is already connected, then we will choose `pinB`. It is not possible to connect to a gate with no available input lines.
```python
def setNextPin(self,source):
	if self.pinA == None:
		self.pinA = source
	else:
		if self.pinB == None:
			self.pinB = source
		else:
			raise RuntimeError("Error: NO EMPTY PINS")
```

Now it's possible to get input from two places: externally, as before, and from the output of a gate that is connected to that input line. This requires a change to the `getPinA` and `getPinB` methods. If the input lines isn't connected to anything(`None`), then ask the user externally as before. However, if there is a connection, the connection is accessed and `fromgate`'s output value is retrieved. This in turn causes that gate to process its logic. This continues until all input is available and the final output value becomes the required input for the gate in question. In a sense, the circuit works backwards to find the input necessary to finally produce output.
```python
def getPinA(self):
	if self.pinA == None:
		return input("Enter Pin A input for gate " + self.getLabel() + "-->")
	else:
		return self.pinA.getFrom().getOutput()
```

The following fragment constructs the circuit shown earlier:
```python
>>> g1 = AndGate("G1")
>>> g2 = AndGate("G2")
>>> g3 = OrGate("G3")
>>> g4 = NotGate("G4")
>>> c1 = Connector(g1,g3)
>>> c2 = Connector(g2, g3)
>>> c3 = Connector(g3, g4)
```

The outputs from the two AND gates(`g1` and `g2`) are connected to the Or gate(`g3`) and that output is connected to the NOT gate(`g4`). The output from the NOT gate is the output of the entire circuit. For example:
```python
>>> g4.getOutput()
Pin A input for gate G1-->0
Pin B input for gate G1-->1
Pin A input for gate G2-->1
Pin B input for gate G2-->1
0
```

Full code:
```python
class LogicGate:

    def __init__(self,n):
        self.name = n
        self.output = None

    def getLabel(self):
        return self.name

    def getOutput(self):
        self.output = self.performGateLogic()
        return self.output


class BinaryGate(LogicGate):

    def __init__(self,n):
        super(BinaryGate, self).__init__(n)

        self.pinA = None
        self.pinB = None

    def getPinA(self):
        if self.pinA == None:
            return int(input("Enter Pin A input for gate "+self.getLabel()+"-->"))
        else:
            return self.pinA.getFrom().getOutput()

    def getPinB(self):
        if self.pinB == None:
            return int(input("Enter Pin B input for gate "+self.getLabel()+"-->"))
        else:
            return self.pinB.getFrom().getOutput()

    def setNextPin(self,source):
        if self.pinA == None:
            self.pinA = source
        else:
            if self.pinB == None:
                self.pinB = source
            else:
                print("Cannot Connect: NO EMPTY PINS on this gate")


class AndGate(BinaryGate):

    def __init__(self,n):
        BinaryGate.__init__(self,n)

    def performGateLogic(self):

        a = self.getPinA()
        b = self.getPinB()
        if a==1 and b==1:
            return 1
        else:
            return 0
			
class NandGate(BinaryGate):
	def __init__(self,n):
		BinaryGate.__init__(self,n)
	
	def performGateLogic(self):
		a = self.getPinA()
		b = self.getPinB()
		if a==1 and b==1:
			return 0
		else:
			return 1

class OrGate(BinaryGate):

    def __init__(self,n):
        BinaryGate.__init__(self,n)

    def performGateLogic(self):

        a = self.getPinA()
        b = self.getPinB()
        if a ==1 or b==1:
            return 1
        else:
            return 0
			
class NorGate(BinaryGate):
	def __init__(self,n):
		BinaryGate.__init__(self,n)
	
	def performGateLogic(self):
		a = self.getPinA()
		b = self.getPinB()
		if a==1 or b==1:
			return 0
		else:
			return 1

class UnaryGate(LogicGate):

    def __init__(self,n):
        LogicGate.__init__(self,n)

        self.pin = None

    def getPin(self):
        if self.pin == None:
            return int(input("Enter Pin input for gate "+self.getLabel()+"-->"))
        else:
            return self.pin.getFrom().getOutput()

    def setNextPin(self,source):
        if self.pin == None:
            self.pin = source
        else:
            print("Cannot Connect: NO EMPTY PINS on this gate")


class NotGate(UnaryGate):

    def __init__(self,n):
        UnaryGate.__init__(self,n)

    def performGateLogic(self):
        if self.getPin():
            return 0
        else:
            return 1


class Connector:

    def __init__(self, fgate, tgate):
        self.fromgate = fgate
        self.togate = tgate

        tgate.setNextPin(self)

    def getFrom(self):
        return self.fromgate

    def getTo(self):
        return self.togate


def main():
   g1 = AndGate("G1")
   g2 = AndGate("G2")
   g3 = OrGate("G3")
   g4 = NotGate("G4")
   c1 = Connector(g1,g3)
   c2 = Connector(g2,g3)
   c3 = Connector(g3,g4)
   print(g4.getOutput())

main()
```