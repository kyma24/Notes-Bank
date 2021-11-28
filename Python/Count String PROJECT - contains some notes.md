```py
text = input("Enter a text: ")

print("\n" + text)

vowels_count = 0
upper_count = 0
longest_word = ""

#initialize a list with size 26 and default value 0. Basically making a list of 26 elements, all of which are 0. Essentially an array.
char_count = [0] * 26

#split text into words
list_words = text.split()
print(list_words)

#process word by word for outputs
for i in range (len(list_words)):

  word = list_words[i]
  #skip is not a word?
  if word.isdigit():
    continue

  special_char_index = -1

  #process char by char in each word for outputs
  for j in range (len(word)):
    char = word [j]

    #count for upper case letters for output
    if char.isupper():
      upper_count += 1
      
      #change to lower case for tracking letter count
      char = char.lower()
    
    if (char >= "a" and char <= "z"):
      #use ASCII code as index:
      char_count [ord(char) - ord('a')] += 1
    else:
      #special character to be removed
      special_char_index = j
  
  #remove special char
  if special_char_index > -1:
    print(word)
    if special_char_index >= len(word) - 1:
      #special char at end of a word
      word = word[:special_char_index]
      # : is slicing. If in set of 5 nums(0-4) and do [:3], only returns first 3 elements. If [3:], returns characters after third position inclusive. If [1:3], then returns a slice of the list, the start to the end - 1
    else:
      #special char in the middle of a word
      word = word[:special_char_index] + word[special_char_index + 1:]
    print(word)
  
  #check the longest word
  if len(word) > len(longest_word):
    longest_word = word
  #must update/handle tie

#add vowel count
vowels_count = char_count[0]
vowels_count += char_count[ord('e') - ord('a')]
vowels_count += char_count[ord('i') - ord('a')]
vowels_count += char_count[ord('o') - ord('a')]
vowels_count += char_count[ord('u') - ord('a')]

#print result
print(26 - char_count.count(0))
#gives count of how many 0s in list
print(vowels_count)
print(upper_count)
print(max(char_count))
print(longest_word)
```