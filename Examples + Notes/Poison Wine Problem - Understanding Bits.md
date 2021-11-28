Question:
You have 1,000 bottles of wine, and exactly one bottle is poisoned. You need to find the poisoned wine before your party starts in an hour. You have 10 rats to test on to find out which bottle is deadly. The poison takes effect after an hour of consumption, so you only have one chance to run your rat poison experiment, meaning you can't feed some rats wine and wait an hour before feeding them more wine. Assume each rat can drink as much wine as you feed it. How do you find the poisoned wine?

Answer:
Tactic #1: How not to do it.
Feed each rat a different wine, and whichever one dies has drunk the poisoned wine.
Can only test 10 wines, so it doesn't work.

Tactic #2: Try something random.
Feed each rat a different combination of wines.
- In this case, you can use a pattern of rats to determine which wine is poisonous, but the pattern of rats has to be unique to each wine, so it will be tough.

To answer this, we need to determine how many patterns can we make with 10 rats?

Each rat can either drink a wine, or not drink a wine; thus, there are two choices per rat( to drink or not to drink)

Two decisions per rat with 10 rats would be ${2^{10}}$ combinations, or ${1024}$ different wines can be tested.

To finish the problem, you could not give any of the rats the first wine, so if none of the rats die you know that the first wine is poisonous.
 You could have only the last rat drink the second wine, the third could be only the second to last rat drink it, the fourth could be both the second to last and the last rats drinking it, so on, so forth.
 
Relation to CS:
The rats are essentially bits. Bits are entities that can store a zero or a one. Bits make up the memory, and can store a lot because 10 bits have the potential to store 1024 items.

To solve this programmatically:
1)  We should feed each wine to the rats in a unique combination, so that it is possible to identify the wine by seeing which combination of rats died. For example if you fed the  wine numbered 10 to the 1st, 4th, 7th, 10th rats it results the string "1001001001" representing which rats were fed the wine based on the rat's position. This combination should never be used for feeding any other wine.
2) We need a Hash-map to store the relation of feeding combination string and the wine number. So in the previous example after feeding a wine we store the feeding combination string in the HashMap called feedingCombinationWineMap in the form like {"1001001001" : 10}.
3) After the feeding of all the wines is done and one hour passed we get to know which rats died. We construct a string called diedRatsString based on ,if a rat died it is 1 if not 0. So for example if  1st, 4th, 7th, 10th rats died it gives the string "1001001001". We query this diedRatsString string in the feedingCombinationWineMap to get which is poisoned wine. In this case it is 10th wine.

Step 2 can be skipped, since we can calculate the index of the wine from just the pattern, i.e.
$$
1001001001 = 2^{0} + 2^{3} + 2^{6} + 2^{9} = 585
$$