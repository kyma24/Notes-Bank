```py
#list
list = ["one", "two"]

#dictionary
dict = {1: "one", 2:"two"}

#tuple
tp = ("one", "two")
```

```py
#code prints longest word in an input
txt = input()

word_list = txt.split()
word = ""
longest_word = word_list[0]

for i in range (1, len(word_list)):
    word = word_list[i]
    if len(word) > len(longest_word):
        longest_word = word

print(longest_word)
```