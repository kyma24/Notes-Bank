this is an example project, showing a program that analyzes a sample file to find what percentage of txt each character occupies

this section shows how a file could be open/read.

```python
filename = input("Enter a filename: ")

with open(filename) as f:
	text = f.read()

print(text)
```

```python
>>>
Enter a filename: test.txt
Ornhgvshy vf orggre guna htyl.
Rkcyvpvg vf orggre guna vzcyvpvg.
Fvzcyr vf orggre guna pbzcyvpngrq.
Syng vf orggre guna arfgrq.
Fcenfr fv orggre guna qrafr.
Ernqnovyvgl pbhagf.
Fcrpvny pnfrf nera'g fcrpvny rabthu gb oernx gur ehyrf.
Nygubhtu cenpgvpnyvgl orgnf chevgl.
Reebef fubhyq arire cnff fvyragyl.
Hayrff rkcyvpvgyl fvyraprq.
Va gur snpr bs nzovthvgl, ershfr gur grzcgngvba bg thrff.
Gurer fubhyq or bar-- naq cersrenoylbayl bar --boivbhf jnl gb qb vg.
Nygubhtu gung jnl znl abg or boivbhf ng svefg hayrff lbh'er Qhgpu.
Abj vf orggre guna arrire.
Nygubhtu arire vf bsgra orggre guna *evtug* abj.
Vs gur vzcyrzragngvba vf uneq gb rkcynva, vg'f n onq vqrn.
Vs gur vzcyrzragngvba vf rnfl gb rkcynva, vg znl or n tbbq vqrn.
Anzrfcnprf ner bar ubaxvat terng vqrn -- yrg'f qb zber bs gubfr!
```

This part of the program shows a function that counts how many times a character occurs in a string.

```python
def count_char(text, char):
	count = 0
	for c in text:
		if c == char:
			count += 1
	return count
```

this function takes as its arguments the text of the file and one character, returning the number of times that character appears in the text.

now we can call it for our file.

```python
filename = input("Enter a filename: ")
with open (filename) as f:
	text = f.read()

print(count_char(text, "r"))

>>>
Enter a filename: test.txt
83
>>>
#the character "r" appears 83 times in the file
```

the next part of the program finds what percentage of the text each character of the alphabet occupies

```python
for char in "abcdefghijklmnopqrstuvwxyz":
	perc = 100 * count_char(text, char) / len(text)
	print("{0} - {1}%".format(char, round(perc, 2)))
```

putting it all together:

```python
def count_char(text, char):
	count = 0
	for c in text:
		if c == char:
			count += 1
	return count

filename = input("Enter a filename: ")
with open(filename) as f:
	text = f.read()

for char in "abcdefghijklmnopqrstuvwxyz":
	perc = 100 * count_char(text, char) / len(text)
	print("{0} - {1}%".format(char, round(perc, 2)))

>>>
Enter a filename: test.txt
a - 4.68%
b - 4.94%
c - 2.28%
...
>>>
```