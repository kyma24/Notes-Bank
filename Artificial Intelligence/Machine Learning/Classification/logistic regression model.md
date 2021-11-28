-   logistic regression model
    -   probability of surviving
        
        in order to determine the best possible line to split the data, need to have a way of scoring the line. First, look at a single datapoint.
        
        Ideally, if the **datapoint** is a passenger who survived, it would be on the right side of the line and far from the line. If it's a datapoint for a passenger who didn't survive, it would be far from the line to the left. The further it is from the line, the more confident the user is that it's on the correct side of the line.
		
		for each datapoint, have a score that's a value between 0 and 1. can think of it as the **probability** that the passenger survives. If the value is close to 0 that point would be far to the left of the line and that means that the user is confident that the passenger didn't survive. If the value is close to 1 that point would be far to the right of the line and that means that the user is confident the passenger did survive. A value of 0.5 means the point falls directly on the line and the user is uncertain if the passenger survives.
		
		the equation for calculating this score is below, though the intuition for it is far more important than the actual equation.
		
		recall that the equation for the line is in the form 0 = ax + by + c(x is the Fare, y is the Age, and a, b & c are the coefficients that are controlled). The number **e** is the mathematical constant, approx 2.71828.
		
		![contentImage](https://api.sololearn.com/DownloadFile?id=4076)
		
		this function is called the sigmoid.
		
		Logistic Regression gives not just a prediction(survived or not), but also a probability(i.e. 80% chance this person survived).
		
		### Likelihood
		to calculate how good the line is, need to score whether the predictions are correct. Ideally if predict w/ a high probability that a passenger survives(meaning the datapoint is far to the right of the line), then that passenger actually survives.
		
		so will get rewarded when predict something correctly and penalized if predict something incorrectly.
		here's the **likelihood** equation. Though again, the intuition is more important than the equation.
		
		![contentImage](https://api.sololearn.com/DownloadFile?id=4077)
		
		here p is the predicted probability of surviving from the previous part.
		
		the likelihood will be a value between 0 and 1. The higher the value, the better the line is.
		
		look at a couple of possibilities:
		- If the predicted probability p is 0.25 and the passenger didn't survive, get a score of 0.75(good).
		- If the predicted probability is 0.25 and the passenger survived, get a score of 0.25(bad)
		
		multiply all the individual scores for each datapoint together to get a score for the line. Thus can compare different lines to determine the best one.
		
		say for ease of computation that have 4 datapoints.
		
		![contentImage](https://api.sololearn.com/DownloadFile?id=4074)
		
		get the total score by multiplying the four scores together:
		
		```
		0.25 * 0.75 * 0.6 * 0.8 = 0.09
		```
		
		the value is always going to be really small since it is the likelihood that the model predicts everything perfectly. A perfect model would have predicted probability of 1 for all positive cases and 0 for all negative cases.
		
		note that the likelihood is how the user scores and compares possible choices of a best fit line.