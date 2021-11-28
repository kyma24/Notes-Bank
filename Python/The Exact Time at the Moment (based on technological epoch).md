```py
#Import the tools
import time
currentTime = time.time()
#Set the times
epochHours = int(currentTime/3600) % 24 - 5
epochMinutes = int(currentTime/60) % 60
epochSeconds = int(currentTime) % 60
#Output the results
print("The time right now is", epochHours, ":", epochMinutes, ":", epochSeconds, ".")
```