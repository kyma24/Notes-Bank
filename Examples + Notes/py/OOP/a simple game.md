object-orientation is very useful when managing different objects and their relations. That is especially useful when you are developing games with different characters and features.

Let's look at an example project that shows how classes are used in game development.

The game to be developed is an old-fashioned text-based adventure game.

Below is the function handling input and simple parsing.

```python
def get_input():
	command = input(": ").split()
	verb_word = command[0]
	if verb_word in verb_dict:
		verb = verb_dict[verb_word]
	else:
		print("Unknown verb {}". format(verb_word))
		return

	if len(command) >= 2:
		noun_word = command[1]
		print(verb(noun_word))
	else:
		print(verb("nothing"))

def say(noun):
	return 'You said "{}"'.format(noun)

verb_dict = {
	"say": say,
}

while True:
	get_input()
```

the code above takes input from the user, and tries to match the first word with a command in **verb\_dict**. If a match is found, the corresponding function is called.

next set is to use classes to represent game objects.

```python
class GameObject:
	class_name = ""
	desc = ""
	objects = {}

	def __init__(self, name):
		self.name = name
		GameObject.objects[self.class_name] = self
	
	def get_desc(self):
		return self.class_name + "\\n" + self.desc

class Goblin(GameObject):
	class_name = "goblin"
	des = "A foul creature"

goblin = Goblin("Gobbly")

def examine(noun):
	if noun in GameObject.objects:
		return GameObject.objects[noun].get_desc()
	else:
		return "There is no {} here.".format(noun)
```

A **Goblin** class was created, which inherits from the **GameObjects** class.

A new function **examine** was also created, which returns the objects description.

Now a new "examine" verb can be added to the dictionary.

```python
verb_dict = {
	"say": say,
	"examine": examine,
}
```

Combining this code with the previous ones will result in:

```python
>>>
: say Hello!
You said "Hello!"

: examine goblin
goblin
A foul creature

: examine elf
There is no elf here.
:
```

the following code will add more detail to the **Goblin** class and allows you to **fight** goblins.

```python
class Goblin(GameObject):
	def __init__(self, name):
		self.class_name = "goblin"
		self.health = 3
		self._desc = "A foul creature"
		super().__init__(name)

	@property
	def desc(self):
		if self.health >= 3:
			return self.desc
		elif self.health == 2:
			health_line = "It has a wound on its knee."
		elif self.health == 1:
			health_line = "Its left arm has been cut off!"
		elif self.health <= 0:
			health_line = "It is dead."
		return self._desc + "\\n" + health_line

	@desc.setter
	#desc was turned into a property so it could be dynamically created when accessed.
	def desc(self, value):
		self._desc = value

def hit(noun):
	if noun in GameObject.objects:
		thing = GameObject.objects[noun]
		if type(thing) == Goblin:
			thing.health = thing.health - 1
			if thing.health <= 0:
				msg = "You killed the goblin!"
			else:
				msg = "You hit the {}.".format(thing.class_name)
	else:
		msg = "There is no {} here.".format(noun)
	return msg
```

this was just a simple sample; you could create different classes to fight, and to make them fight each other, so on.