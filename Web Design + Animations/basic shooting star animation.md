-   basic shooting star animation
    
    ```jsx
    var xPos = 350;
    var yPos = 50;
    var starRadius = 5;
    
    draw = function() {
        xPos -= 1;
        yPos += 1;
        starRadius += 0.5;
        
        background(29, 40, 115);
        fill(255, 242, 0);
        ellipse(xPos, yPos, starRadius, starRadius);
    };
    ```