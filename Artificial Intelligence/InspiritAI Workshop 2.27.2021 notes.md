-   InspiritAI Workshop 2/27/2021 notes
    
    computer vision: making computers "see" w/ **deep learning**
    
    -   intro to computer vision
        
    -   how to get from images to numbers
        
    -   neural networks
        
    -   training a neural network
        
    -   what is computer vision?
        
        broadly: applications
        
        if give self driving car an image of outside world, it won't understand unless have taught it:
        
        ability to detect certain things, i.e. stop signs, cars, people
        
        humans can look and see "a stop sign" - meaningful concept
        
        to drive a car, computer also needs to get meaning from images
        
        has to then understand what pixel data is
        
        **computer vision** is a field of AI that trains computers to **interpret and understand** the visual world.
        
        i.e. photo filters
        
        how does it work?
        
        A: Snapchat/TikTok/Instagram filters:
        
        1.  detect a face
        2.  identify landmarks(eyes, mouth, etc)
        3.  process image by adding graphics or distorting
        
        how can represent an image in color?
        
        key concept: 3D arrays: Red, Green, Blue pixel values.
        
        have each pixel value that has each corresponding red/green/blue color value.
        
        each pixel has 3 corresponding values: R, G, B. If have an 1000x1000 pixel RGB image, how many intensity values are there? - 3,000,000
        
        one way to process this is neural networks. good at identifying patterns.
        
        ideally, what want to do is pass in images, network would identify patterns in image, then output the classification it generates.
        
        neural networks loosely inspired by the brain, have revolutionized many fields, including computer vision. can recognize complex patterns. learn patterns over time, don't explicitly tell which patterns to look at.
        
        dendrites in the brain to input/output of neural network
        
        how does neuron compute?
        
        -   have to have some kind of associated **weights** between input and neuron. if don't have a strong connection, value/weight will be different
        -   has activation functions and outputs
        -   input → weights → output
        
        considering "should I eat lunch right now?"
        
        -   am I hungry?(pretty important → large weight value)
        -   is there food? (essential → very large weight value)
        -   food's tasty? (somewhat important → decent weight value)
        -   am i allergic? (essential → very large weight value)
        
        weights can be positive/negative, large or small.
        
        act like the slope in linear regression: **m** in y = mx + b
        
        i.e. allergic is negative, bc it's really important but in the opposite way.
        
        **inputs**(binary value) multiplied by **weights**(scale of -10 to 10) = weighted sum
        
        next, add the **bias term**, which is like intercept in linear regression(y = mx + **b**)
        
        bias term also determines what gets to pass thru or not, learned over time.
        
        adding a value that is learned by model over time. For this neuron, typically whatever output, not as important as it should be, so add 0.2 importance for output.
        
        have **activation function** which takes the sum from the bias term. This function responsible for signals that don't matter in neural network(rid of noise). i.e. max() function. between 0, 4.2, will give the largest value.
        
        if it were to have a negative number, it will turn into 0 because it quiets down and doesn't need to be included in the value → 0 = no lunch, bc value is negative, 4.2 = lunch, bc value is positive
        
        -   activation function/bias determines how much signal passes through
        -   different activation functions
        
        ![[Pasted image 20210323165046.png]]
        
        will get output of 0.
        
        ![[Pasted image 20210323165127.png]]
        
        deep learning = adding more layers
        
        how do we know of network has "good" weights?
        
        need to test it.
        
        when measuring network success, measure by loss.
        
        -   low loss = big difference between two classes, with correct classification
        -   medium loss = small difference between two classes, still with correct classification
        -   high loss = gets the class wrong
        
        training the network:
        
        go thru training data many times. for each piece of data:
        
        1.  calculate output
        2.  working backwards, change the weights layer by layer to improve the output(lower loss)
        
        put pixel values into the neural network diagram. Randomly initialized at start. Random values attributed to weights
        
        at first network will be very bad, and will have high loss. Then what happens is work backwards and change all weights little by little by computing **partial derivative**.
        
        doing this hundreds of thousands of times, will get pretty good model.
        
        how to choose better weights: take small steps in the right direction. computing derivatives based on weights, then adding to the weights to change little by little.
        
        general intuition: have input, have randomly initialized model, then output something.
        
    
    convolutional neural networks(CNNs) - special for identifying images/patterns
    
    training changes the weights and biases for a basic neural network.
    
    gpt3??
	
	[](https://plato.stanford.edu/entries/ethics-ai/)[https://plato.stanford.edu/entries/ethics-ai/](https://plato.stanford.edu/entries/ethics-ai/)[](https://www.frontiersin.org/articles/10.3389/fnsvs.2017.00023/full)[https://www.frontiersin.org/articles/10.3389/fnsvs.2017.00023/full](https://www.frontiersin.org/articles/10.3389/fnsvs.2017.00023/full)[](https://plato.stanford.edu/entries/ethics-ai/)[https://plato.stanford.edu/entries/ethics-ai/](https://plato.stanford.edu/entries/ethics-ai/)[](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5733340/)[https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5733340/](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5733340/)