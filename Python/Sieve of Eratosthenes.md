```py
import time

def SieveOfEratosthene(n):
	start = time.clock()
	prime =[True for i in range(n+1)]
	p = 2
		while (p * p <= n ):
			if (prime[p] == True):
				for i in range(p * 2, n + 1, p):
					prime[i] = False
					p += 1

# print or count primes
c = 0
for p in range(2, n):
if prime[p]:
#print (p, end = " ")
c += 1
# print ("The number of primes smaller or euqal to ", n)
# print (" is ", c)
```