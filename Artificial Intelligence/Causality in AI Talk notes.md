-   Causality in AI Talk notes
    -   causes and effects(what's causality abt)
        
        X → Y
        
        x causes y
        
        -   plays significant role in the calculation of probability
        -   underlying web of causes of a behavior or event and furnishes critical insights that predictive models fail to provide.
        
        however, y is not always perfectly predictable, i.e. medicine might not always cure, studying might not always ace test, even light switches occasionally fail.
        
        maybe need to add more nodes & possibilities:
        
        -   maybe didn't ace test bc don't like subject, or were in bad mood, or even small things like anxiety/run out of time.
        
        add Z node: if X is studying, and Y is acing test, then Z is any other possibilities(i.e. mood, sleep, time):
        
        Z can influence Y, or even X and Y.
        
        No Z causes X, X causes Y and Y causes Z.
        
        DAGS = Directed Acrylic Graphs
        
    -   determinism vs probabilistic natures of things
        
        -   determinism
            
            Baruch Spinoza, Jewish Dutch philosopher, was expelled & shunned by Jewish society at 23 yrs old, bc claimed that causal knowledge determines everything.
            
            bayesian networks?
            
            imagine have all nodes in causal diagrams for person, for every atom/subatomic particle, etc.
            
            -   encapsulates characteristics and desires,
            -   every atom accounted for,
            -   everything could be determined
                -   even whether you would be cured from the medicine
                -   or even what next thought will be
            
            heisenberg's uncertainty principle: doesn't allow to measure anything w/ 100% accuracy
            
        -   probability
            
            "Nothing is impossible. Some things are just less likely than others."
            
            -   likelihood that events will occur
                -   number of **desired outcomes** / number of **total outcomes**
            
            on quantum level, everything is probabilistic
            
            probabilities overcome limitations of knowledge
            
            -   can never have enough nodes
            
            much of science is discovering and substantiating the discovery.
            
            -   effects of causes
                
                -   i.e. light turning on from flipping switch
                    -   probability of defective bulb,
                    -   probability that wires break,
                    -   probability that power goes out,
                    -   probability of defective switch(much smaller than bulb), etc.
            -   causes of effects
                
                -   probability of having flipped switch when seeing light
                -   probability of planet passing by when star's light dims
    -   experimentation(applies to scientific discoveries)
        
        -   as humans, instinctively infer causes during some phenomenon & effects
            -   how can be sure?
                
            -   how can start to imagine?
                
            -   when to start thinking?
                
                start less then 1 sometimes
                
                -   playful manipulation - manipulate the scenario and then try to understand what's going on
        
        can test hypotheses through experimentation
        
        -   much more sophisticated academically/as mature
            
        -   testing medicine: clinical trials
            
        -   Randomized Controlled Trials(RCT)
            
            -   separate people into control and treatment groups
        -   look at difference in outcomes, assuming completely randomized, as the participant, don't know whether control or treatment. will be able to get causal knowledge in perfect instance.
            
        -   proportion cured when given medicine - proportion cured with placebo/without medicine
            
        -   don't know if 75% cure rate for given medicine is bad until know the proportion cured with placebo. If greater, the medicine isn't good.
            
        -   when proportion cured when given medicine = 100%, no medicine = 0%, that is most effective generally.
            
        -   beneficial if positive, harmful if negative, is it no effect if 0?(if difference between real and placebo is 0)
            
            -   no, there is still some bad & good if it's 0; def would have some sort of effect. If anything, it could even be amazing, and no one would know.
    -   counterfactuals(part of causality)
        
        -   "If i had taken the freeway, I would've gotten home earlier"
            -   if had not taken freeway or that decision has not yet been made: counterfactual
        
        counterfactual statements are counter to the facts
        
        -   X is decision w/ x = take freeway, x' = take side roads
        -   Y is outcome with y = home earlier, y' = home later
        -   P(y sub x) = probability of home earlier had freeway been taken
        -   P(y sub x | x') = probability of y sub x given you chose side roads
        
        necessity and sufficiency
        
        -   drug not only necessary, but also sufficient for curing disease
        -   often core question to get to in life/science: probability of necessity and sufficiency
        -   when say "thank you", yes, that is a counterfactual statement.
        -   why say thank you? to be polite abt how they did a service for you
            -   person did or said something that you had a good outcome, but had they not said/did that, then would've had a bad outcome.
            -   if prob high enough, you say thank you, but otherwise don't mean it
    -   how all related to AI