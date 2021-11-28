-   Hackathon ML Workshop 2/26/2021 notes
    
    gan - generative adversarial networks
    
    [](https://thispersondoesnotexist.com/)[https://thispersondoesnotexist.com/](https://thispersondoesnotexist.com/)
    
    tend to have a lot of similar layers and often have components of CNNs in them or have their own neural networks
    
    [](https://deepai.org/machine-learning-glossary-and-terms/transformer-neural-network)[https://deepai.org/machine-learning-glossary-and-terms/transformer-neural-network](https://deepai.org/machine-learning-glossary-and-terms/transformer-neural-network)
    
    runs through neural network
    
    creates space in high dimensional vector space for a class. As gets more used and refined, trained, it gets better at recognizing.
    
    when seeing an image never seen before, it turns into a high dimensional vector and compare its closeness in vector space to the classes, and then figure out which is the best one.
    
    training data representative of the type of image want to do. Training environment should match what want to analyze in real world. Think abt training data, not in number, but in density of data. High res or low res, color or no color, higher res and more color will result in a higher density of data. If training data is not related to real world data, will not produce good res pictures when applying. Models good at pattern recognition.
    
    classes = different groups of objects to recognize.
    
    in zendo, take lots of pictures and upload and then compile all pictures, highlight things to upload to each class to train model in some ways, can be applicable to some other things.
    
    train machine and then when see picture, know that this is a certain class.
    
    training the neural network in a supervised environment at the same time going through unlabeled images and predicting. After user labels/corrects, will keep training itself and innovate.
    
    still need some supervised environment to correct unsupervised.
    
    classification task: classifies image
    
    true positives/number of true positives predicted + number of false positives
    
    precision = 1/2 or 50%. Precision for the model would be 50%, therefore. If give 50 random images, would probably get 25 of the
    
    recall = true positive / true positives + false negatives
    
    classification model
    
    tensorflow pytorch
    
    Tensforflow keras