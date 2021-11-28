Orange Juice:
```python
# Draw the background.
### Place Your Code Here ###
Rect(0, 0, 400, 400, fill=gradient('turquoise', 'paleTurquoise'))

# Draw the glass and the orange juice.
### Place Your Code Here ###
Rect(110, 100, 180, 250, fill='azure')
Rect(120, 150, 160, 190, fill=gradient('gold', 'yellow', start='bottom'))

# Draw the ice cubes.
### Place Your Code Here ###
Rect(130, 170, 40, 40, fill=rgb(255, 255, 200))
Rect(190, 200, 30, 30, fill=rgb(255, 255, 200))

# Draw the straw.
### (HINT: The straw uses 2 rectangles that only overlap on the edges.)
### Place Your Code Here ###
Rect(240, 50, 50, 10, fill='red')
Rect(240, 60, 10, 270, fill=gradient('orange', 'orange', 'orange', 'red', start='bottom'))
```

Lantern:
```python
# This Creative Task draws a Chinese lantern! Another great place to look
# for your own Creative Task idea is by looking at other cultures.

# background
Rect(0, 0, 400, 400, fill='midnightBlue')

# light
Oval(200, 200, 340, 340, fill='darkSlateGray')

# loop
Oval(200, 100, 20, 100, fill=None, border='red', borderWidth=8)

# lantern's light
Circle(200, 200, 100, fill=gradient('yellow', 'orange', 'red'))

# decorative lantern's outline
Oval(200, 200, 200, 200, fill=None, border='darkRed', borderWidth=8)
Oval(200, 200, 140, 200, fill=None, border='darkRed', borderWidth=8)
Oval(200, 200, 80, 200, fill=None, border='darkRed', borderWidth=8)
Line(200, 100, 200, 300, fill='darkRed', lineWidth=8)

# decorative lantern strings
### (HINT: With dashes, it is only one line of code to get all of the strings!)
Line(166, 350, 234, 350, fill='red', lineWidth=100, dashes=(8, 2))

Rect(120, 100, 160, 40, fill=gradient('red', 'orangeRed', start='top'),
     border='darkRed', borderWidth=8)
Rect(120, 260, 160, 40, fill=gradient('red', 'orangeRed', start='bottom'),
     border='darkRed', borderWidth=8)
```

Android:
```python
# Draw the head.
### Place Your Code Here ###
Circle(200, 140, 80, fill=rgb(164, 198, 57))
Rect(120, 140, 160, 10, fill='white')
# Draw the eyes and then the antennas.
### Place Your Code Here ###
Circle(160, 105, 5, fill='white')
Circle(240, 105, 5, fill='white')
Line(150, 45, 200, 140, fill=rgb(164, 198, 57), lineWidth=2)
Line(250, 45, 200, 140, fill=rgb(164, 198, 57), lineWidth=2)
# Draw the main body (with rounded bottom corners).
### Place Your Code Here ###
Rect(120, 150, 160, 120, fill=rgb(164, 198, 57))
Circle(135, 270, 15, fill=rgb(164, 198, 57))
Circle(265, 270, 15, fill=rgb(164, 198, 57))
Rect(135, 270, 130, 15, fill=rgb(164, 198, 57))
# Draw the legs.
### Place Your Code Here ###
Rect(150, 285, 40, 40, fill=rgb(164, 198, 57))
Rect(210, 285, 40, 40, fill=rgb(164, 198, 57))
Circle(170, 325, 20, fill=rgb(164, 198, 57))
Circle(230, 325, 20, fill=rgb(164, 198, 57))
# Draw the arms.
### Place Your Code Here ###
Rect(70, 165, 40, 80, fill=rgb(164, 198, 57))
Circle(90, 165, 20, fill=rgb(164, 198, 57))
Circle(90, 245, 20, fill=rgb(164, 198, 57))
Rect(290, 165, 40, 80, fill=rgb(164, 198, 57))
Circle(310, 165, 20, fill=rgb(164, 198, 57))
Circle(310, 245, 20, fill=rgb(164, 198, 57))
```

Lighthouse:
```python
# Draw the background.
### Place Your Code Here ###
Rect(0, 0, 400, 250, fill=gradient('midnightBlue', 'steelBlue', start='top'))
Rect(0, 250, 400, 150, fill=gradient('slateBlue', 'darkSlateBlue', start='top'))
# Draw the rock behind the lighthouse and its reflection.
### (HINT: There is a point of the rock behind the lighthouse!)
### Place Your Code Here ###
Polygon(295, 210, 205, 240, 160, 280, 400, 280, 400, 230, fill=gradient('darkSlateBlue', 'darkBlue', start='top'))
Polygon(400, 280, 400, 290, 295, 300, 160, 280, fill=gradient('darkSlateBlue', 'darkBlue', start='top'), opacity=20)
# Draw the lighthouse from the top down.
### Place Your Code Here ###
Polygon(200, 120, 185, 130, 215, 130, fill=gradient('crimson', 'darkRed', start='bottom'))
Rect(190, 130, 20, 20, fill='crimson')
Rect(195, 130, 10, 20, fill='yellow')
Rect(185, 150, 30, 10, fill='fireBrick')
Polygon(190, 160, 210, 160, 215, 220, 185, 220, fill=gradient('crimson', 'darkRed', start='top'))
Polygon(203, 190, 208, 190, 208, 200, 203, 200, fill='black')
Polygon(185, 220, 215, 220, 220, 285, 180, 285, fill=gradient('snow', 'darkGray', start='top'))
# Draw the light coming from the lighthouse.
### Place Your Code Here ###
Circle(200, 140, 40, fill=gradient('yellow', 'gold', 'orange', start='top'), opacity=10)
Polygon(200, 140, 400, 260, 400, 340, fill=gradient('yellow', 'gold', 'orange', start='top'), opacity=30)
# Draw the rock in front of the lighthouse and its reflection.
### Place Your Code Here ###
Polygon(145, 240, 235, 265, 270, 290, 120, 290, fill=gradient('darkSlateBlue', 'midnightBlue', start='top'))
Polygon(120, 290, 270, 290, 235, 315, 145, 340, fill=gradient('darkSlateBlue', 'midnightBlue', start='top'), opacity=30)
```

Aurora Borealis:
```python
### Place Your Code Here ###
Rect(0, 0, 400, 400, fill=gradient('navy', 'darkCyan', start='top'))
Line(400, 0, 0, 400, fill='white', lineWidth = 600, dashes = (1, 30))
Line(0, 200, 400, 200, fill=gradient('navy', 'darkCyan', start='top'), lineWidth = 400, dashes = (25, 1))
Rect(0, 0, 400, 300, fill=gradient('whiteSmoke', 'darkMagenta', 'chartreuse', 'lightCyan', 'darkMagenta', 'royalBlue', start='bottom-right'), opacity=40)
Rect(0, 0, 400, 300, fill=gradient('black', 'darkCyan', start='top'), opacity=50)
Rect(0, 300, 400, 100, fill='midnightBlue')
Rect(0, 300, 400, 100, fill=gradient('whiteSmoke', 'darkMagenta', 'chartreuse', 'lightCyan', 'darkMagenta', 'royalBlue', start='bottom-right'), opacity=20)
Polygon(400, 150, 395, 170, 380, 158, 343, 198, 305, 228, 279, 245, 265, 265, 244, 270, 220, 260, 189, 271, 178, 280, 157, 282, 140, 269, 126, 258, 116, 277, 96, 290, 74, 283, 59, 268, 39, 284, 24, 281, 0, 290, 0, 400, 400, 400, 389, 396, 376, 392, 354, 390, 344, 385, 313, 383, 295, 380, 262, 381, 243, 381, 229, 375, 211, 363, 199, 372, 185, 375, 118, 375, 93, 361, 82, 347, 60, 330, 55, 320, 70, 325, 92, 330, 127, 324, 159, 319, 210, 324, 246, 315, 280, 303, 304, 300, 325, 304, 335, 310, 342, 310, 359, 310, 386, 304, 400, 300, fill='black')
Polygon(400, 150, 395, 170, 380, 158, 343, 198, 305, 228, 279, 245, 265, 265, 244, 270, 220, 260, 189, 271, 178, 280, 157, 282, 140, 269, 126, 258, 116, 277, 96, 290, 74, 283, 59, 268, 39, 284, 24, 281, 0, 290, 0, 400, 400, 400, 389, 396, 376, 392, 354, 390, 344, 385, 313, 383, 295, 380, 262, 381, 243, 381, 229, 375, 211, 363, 199, 372, 185, 375, 118, 375, 93, 361, 82, 347, 60, 330, 55, 320, 70, 325, 92, 330, 127, 324, 159, 319, 210, 324, 246, 315, 280, 303, 304, 300, 325, 304, 335, 310, 342, 310, 359, 310, 386, 304, 400, 300, fill=gradient('black', 'midnightBlue', 'darkBlue', start='bottom'), opacity=50)
```

Weird Computer Click Thing
```python
# Background
Rect(0, 0, 400, 400, fill='ivory')

#Table
Polygon(0, 100, 0, 270, 522, 480, 522, 310, fill=gradient('saddleBrown', 'burlyWood', start='left'))
Polygon(0, 270, 0, 300, 522, 510, 522, 480)

#Computer
Polygon(120, 136, 120, 200, 207, 235, 207, 170, fill=gradient('antiqueWhite', 'linen', 'antiqueWhite', start='left'))
screen = Polygon(125, 145, 125, 195, 200, 225, 200, 175, fill='black')
Polygon(120, 136, 207, 170, 262, 150, 175, 111, fill=gradient('linen', 'floralWhite', start='bottom-right'))
Polygon(207, 170, 262, 150, 262, 215, 207, 235, fill='oldLace')
Polygon(120, 200, 207, 235, 187, 260, 100, 225, fill=gradient('papayaWhip', 'linen', start='top-left'))
Polygon(100, 225, 100, 250, 187, 285, 187, 260, fill=gradient('antiqueWhite', 'linen', start='bottom-right'))
Polygon(207, 235, 187, 260, 187, 285, 262, 230, 262, 215, fill=gradient('antiqueWhite', 'antiqueWhite', 'seashell', start='bottom-left'))

def onMousePress(mouseX, mouseY):
    colors = ['black', 'crimson', 'tomato', 'darkOrange', 'orange', 'gold', 'yellowGreen', 'forestGreen', 'lightSkyBlue', 'cornflowerBlue', 'royalBlue', 'plum', 'mediumPurple', 'indigo']
    c = abs(pythonRound(mouseX/20)-250%14)
    if c >= len(colors):
        screen.fill=colors[abs(pythonRound(mouseY/20)-250%14)]
    else:
        screen.fill = colors[c]
```

Pikachu:
```python
app.background = 'gold'

# eyes
Circle(90, 150, 40)
Circle(310, 150, 40)
Circle(100, 140, 20, fill='white')
Circle(300, 140, 20, fill='white')

# nose and cheek
Oval(200, 180, 30, 15)
leftCheek = Circle(50, 250, 40, fill='crimson')
rightCheek = Circle(350, 250, 40, fill='crimson')

# mouth
mouth = Oval(200, 250, 60, 100, visible=False)
Oval(165, 220, 80, 40, rotateAngle=-15)
Oval(235, 220, 80, 40, rotateAngle=15)
leftMouth = Oval(165, 215, 80, 40, fill='gold', rotateAngle=-15)
rightMouth = Oval(235, 215, 80, 40, fill='gold', rotateAngle=15)

def onMousePress(mouseX, mouseY):
    # Change the background color, show the mouth, and change the fill of the
    # mouth covers.
    ### Place Your Code Here ###
    app.background = gradient('white', 'white', 'gold')
    mouth.visible = True
    leftMouth.fill, rightMouth.fill = 'white', 'white'
    leftCheek.radius, rightCheek.radius = 50, 50

def onMouseRelease(mouseX, mouseY):
    # Change the background color, the mouth, and the fill of the mouth covers
    # back.
    ### Place Your Code Here ###
    app.background = 'gold'
    mouth.visible = False
    leftMouth.fill, rightMouth.fill = 'gold', 'gold'
    leftCheek.radius, rightCheek.radius = 40, 40
```

Feed The Kitty:
```python
# background
app.background = rgb(170, 185, 55)
Circle(200, 200, 150, fill='white')

# ears
Polygon(261, 158, 305, 132, 280, 195, fill=rgb(145, 170, 110),
        border=rgb(53, 31, 22), borderWidth=6)
Polygon(139, 158, 95, 132, 120, 195, fill=rgb(145, 170, 110),
        border=rgb(53, 31, 22), borderWidth=6),
Polygon(227, 129, 305, 133, 264, 160, border=rgb(55, 30, 20), borderWidth=6)
Polygon(173, 129, 95, 133, 136, 160, border=rgb(55, 30, 20), borderWidth=6)

# face and body
Oval(200, 276, 120, 130, border=rgb(55, 30, 20), borderWidth=6)
Circle(200, 200, 80, border=rgb(55, 30, 20), borderWidth=8)

# plate
Oval(200, 323, 140, 45, fill='beige', border=rgb(55, 30, 20), borderWidth=3)
Oval(200, 312, 200, 50, fill='white', border=rgb(55, 30, 20), borderWidth=4)
Oval(200, 317, 150, 30, fill=None, border=rgb(170, 185, 55), borderWidth=3)

# hands
Oval(165, 285, 30, 35, border=rgb(55, 30, 20), borderWidth=5, rotateAngle=-20)
Oval(235, 285, 30, 35, border=rgb(55, 30, 20), borderWidth=5, rotateAngle=20)

# eyes and tears
Oval(163, 193, 75, 100, fill='beige', border=rgb(55, 30, 20), borderWidth=4,
     rotateAngle=5)
Oval(237, 193, 75, 100, fill='beige', border=rgb(55, 30, 20), borderWidth=4,
     rotateAngle=-5)
leftEye = Oval(165, 185, 45, 55, border=rgb(55, 30, 20), borderWidth=4)
rightEye = Oval(235, 185, 45, 55, border=rgb(55, 30, 20), borderWidth=4)
leftTear = Oval(150, 240, 25, 15, fill='lightCyan', border=rgb(85, 130, 125))
rightTear = Oval(250, 240, 25, 15, fill='lightCyan', border=rgb(85, 130, 125))

# message
message = Label('pleeeease', 200, 90, fill=rgb(170, 185, 55), size=25, bold=True)

# food
foodPile = Oval(200, 320, 10, 5, fill='lightSalmon')
food = Circle(200, 30, 10, fill='lightSalmon', border='black', borderWidth=4)

def onMousePress(mouseX, mouseY):
    # The cat is not happy until the pile of food has a height of 30 pixels.
    # Until then, increase the width and height of the pile.
    ### (HINT: Make sure to set the bottom of the foodPile to 325!)
    ### Place Your Code Here ###
    if foodPile.height < 30:
        foodPile.height += 2
        foodPile.width += 5
        foodPile.bottom = 325
    # When the food has a height of at least 30 pixels, change the message
    # text and hide the tears.
    ### Place Your Code Here ###
    if foodPile.height >= 30:
        leftTear.visible, rightTear.visible = False, False
        message.value = "meow"

def onMouseMove(mouseX, mouseY):
    # Moves the food as the mouse moves.
    food.centerX = mouseX
    food.centerY = mouseY

    # Makes the eyes follow the food.
    leftEye.centerX = 155 + (mouseX / 20)
    leftEye.centerY = 180 + (mouseY / 20)
    rightEye.centerX = 225 + (mouseX / 20)
    rightEye.centerY = 180 + (mouseY / 20)
```

https://github.com/ErikRHanson/Problem-Solving-with-Algorithms-and-Data-Structures-Using-Python