```py
#moves n disks from fromTower to the toTower w/ assistance of aTower
#1. if base case w/ 1 disk just move fromTower to toTower - move first n-1 disks to aTower - move base disk to toTower - recursive call considers the whole of n-1 disks as another separate case from the whole thing: keeps running until only one disk is left
def main():
  n = eval(input("Enter the numer of disks: "))

  print("The moves are: ")
  moveDisks(n, 'A', 'B', 'C')
	#^calling the function: plugs in values

def moveDisks(n, fromTower, toTower, aTower):
  if n == 1:
    print("Move disk", n, "from", fromTower, "to", toTower)
		#^recursive running: accounts for when n reaches 1 after the continuous subtracting, then moves it to the toTower
  else:
    moveDisks(n-1, fromTower, aTower, toTower)
    print("Move disk", n, "from", fromTower, "to", toTower)
    moveDisks(n-1, aTower, toTower, fromTower)

main()
```