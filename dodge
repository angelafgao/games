from tkinter import *
from tkinter import messagebox
import copy
import math
import random

class FallingObject(object):
    
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def draw(self, canvas): # default draw
        canvas.create_rectangle(self.x - 10, self.y - 10, self.x+ 10, 
            self.y + 10, fill = "black")

    def move(self):
        self.y += 7
        
class Fireball(FallingObject):

    def __init__(self, x, y):
        super().__init__(x, y)
        self.width = 13
        self.height = 10

    def draw(self, canvas):
        # draw flames 
        canvas.create_oval(self.x - self.width, self.y - self.height, 
            self.x + self.width, self.y + self.height, fill = "#e60000", 
            width = 0)
        canvas.create_oval(self.x - self.width, self.y - self.height, 
            self.x + self.width, self.y + self.height - 3, fill = "orange",
             width = 0)
        canvas.create_polygon(self.x - 2, self.y - 20, self.x + 4, self.y - 15,
            self.x + 4, self.y - 5, self.x - 12, self.y - 4, 
            self.x - 2, self.y - 15, fill = "yellow", width = 0)
        canvas.create_polygon(self.x + 6, self.y - 20, self.x + 12, self.y - 15,
            self.x + 12, self.y - 5, self.x - 4, self.y - 4, 
            self.x + 6, self.y - 15, fill = "orange", width = 0)
        canvas.create_polygon(self.x + 6, self.y - 18, self.x + 9, self.y - 15,
            self.x + 10, self.y - 5, self.x - 4, self.y - 4, 
            self.x + 6, self.y - 15, fill = "yellow", width = 0)
        canvas.create_polygon(self.x + 6, self.y - 15, self.x + 7, self.y - 15,
            self.x + 8, self.y - 5, self.x - 4, self.y - 4, 
            self.x + 6, self.y - 15, fill = "orange", width = 0)

class Candy(FallingObject):

    def __init__(self, x, y):
        super().__init__(x, y)
        r = 10
        self.r = r
        self.tw = 5
        self.th = 10
        self.width = r + 2*self.tw
        self.height = r
        self.color1 = "pink"
        self.color2 = "cyan"
        self.colorwrapper = "white"

    def draw(self, canvas):
        #draw candy segments
        canvas.create_arc(self.x - self.r, self.y - self.r, self.x + self.r, 
            self.y + self.r, extent = 45, fill = self.color2, 
            outline = self.color2)
        canvas.create_arc(self.x - self.r, self.y - self.r, self.x + self.r, 
            self.y + self.r, start = 45, extent = 45, fill = self.color1, 
            outline = self.color1)
        canvas.create_arc(self.x - self.r, self.y - self.r, self.x + self.r, 
            self.y + self.r, start = 90, extent = 45, fill = self.color2, 
            outline = self.color2)
        canvas.create_arc(self.x - self.r, self.y - self.r, self.x + self.r, 
            self.y + self.r, start = 135, extent = 45, fill = self.color1, 
            outline = self.color1)
        canvas.create_arc(self.x - self.r, self.y - self.r, self.x + self.r, 
            self.y + self.r, start = 180, extent = 45, fill = self.color2, 
            outline = self.color2)
        canvas.create_arc(self.x - self.r, self.y - self.r, self.x + self.r, 
            self.y + self.r, start = 225, extent = 45, fill = self.color1, 
            outline = self.color1)
        canvas.create_arc(self.x - self.r, self.y - self.r, self.x + self.r, 
            self.y + self.r, start = 270, extent = 45, fill = self.color2, 
            outline = self.color2)
        canvas.create_arc(self.x - self.r, self.y - self.r, self.x + self.r, 
            self.y + self.r, start = 315, extent = 45, fill = self.color1, 
            outline = self.color1)
        # draw outline
        canvas.create_oval(self.x - self.r, self.y - self.r, self.x + self.r, 
            self.y + self.r, fill = "")
        # draw wrapper
        canvas.create_polygon(self.x - self.r, self.y, self.x-self.r - self.tw,
            self.y + self.th, self.x - self.r - self.tw, self.y - self.th, 
            fill = self.colorwrapper, outline = "black")
        canvas.create_polygon(self.x + self.r, self.y, self.x +self.r + self.tw,
            self.y + self.th, self.x + self.r + self.tw, self.y - self.th, 
            fill = self.colorwrapper, outline = "black")

class Player(object):

    def __init__(self, x, y):
        self.x = x
        self.y = y
        self.width = 40
        self.height = 50
        self.direction = 1

    def draw(self, canvas):
        # draw legs
        canvas.create_rectangle(self.x-self.width/4, self.y - self.height, 
            self.x + self.width/4, self.y, fill = "black")
        # draw paper bag 
        canvas.create_rectangle(self.x-self.width/2, self.y - self.height, 
            self.x + self.width/2, self.y - 10, fill = "#994d00")
        # draw eyes and mouth
        canvas.create_oval(self.x - 12, self.y - self.height*2/3 - 4, 
            self.x - 2, self.y - self.height*2/3+ 4, fill = "white")
        canvas.create_oval(self.x + 2, self.y - self.height*2/3 - 4, 
            self.x + 12, self.y - self.height*2/3+ 4, fill = "white")
        canvas.create_oval(self.x - 8, self.y - self.height*2/3 - 2, 
            self.x - 6, self.y - self.height*2/3+ 2, fill = "black")
        canvas.create_oval(self.x + 6, self.y - self.height*2/3 - 2, 
            self.x + 8, self.y - self.height*2/3+ 2, fill = "black")
        canvas.create_arc(self.x - 4, self.y - self.height/2- 4, self.x + 4, 
            self.y  - self.height/2 + 4, start = 180, extent = 180, fill = "white")

    # changes direction
    def changedir(self): 
        self.direction = (-1)*self.direction

    # moves the player in the direction it's going in
    def move(self, data):
        self.x += 10*self.direction
        if self.x >= data.width:
            self.x = 0
        elif self.x <= 0:
            self.x = data.width

    # tests for intersections between player and falling objects
    def hitObject(self, other):
        (selfX0, selfY0) = (self.x - self.width, self.y - self.height)
        (selfX1, selfY1) = (self.x + self.width, self.y + self.height)
        (otherX0, otherY0) = (other.x - other.width, other.y - other.height)
        (otherX1, otherY1) = (other.x + other.width, other.y + other.height)
        return ((selfX1 >= otherX0) and (otherX1 >= selfX0) and 
            (selfY1 >= otherY0) and (otherY1 >= selfY0))

def init(data):
    data.gameOver = False
    data.score = 0
    data.groundh = data.height - 30
    data.player = Player(data.width/2, data.groundh)
    data.fallingobjects = []
    data.timersection = 0
    data.objmargin = 10

def timerFired(data):
    # move player
    data.player.move(data)
    testHit(data)
    # moves falling objects and pops them when out of range
    for i in range(len(data.fallingobjects)): 
        currobject = data.fallingobjects[i]
        if currobject.y >= data.height:
            data.fallingobjects.pop(i)
            break
        currobject.move()
    data.timersection += 1
    randsection = random.randint(7, 20)
    # sends a random object down at a random time and random location
    if (data.timersection >= randsection and random.random() > 0.7):
        x = random.randint(data.objmargin, data.width - data.objmargin)
        obj = random.random()
        if obj > 0.3:
            data.fallingobjects.append(Fireball(x, 0))
        else:
            data.fallingobjects.append(Candy(x, 0))
        data.timersection = 0

def mousePressed(event, data):
    if int(event.type) == 4: # changes direction of player with each mouse press
        data.player.changedir()
    
def keyPressed(event, data):
    if event.keysym == "r": # restarts game
        init(data)

def redrawAll(canvas, data):
    drawbackground(canvas, data)
    # game over
    if data.gameOver == True:
        canvas.create_text(data.width/2, data.height/2, text = "Game Over", 
            fill = "white", anchor = S)
        canvas.create_text(data.width/2, data.height/2, 
            text = "Press r to restart", fill = "white", anchor = N)
    else:
         #draw player
         data.player.draw(canvas)
         #draw falling objects
         for i in range(len(data.fallingobjects)):
            currobject = data.fallingobjects[i]
            currobject.draw(canvas)


####################################
# other functions
####################################

# draws background of game
def drawbackground(canvas, data):
    # draws sky and grass
    canvas.create_rectangle(0, 0, data.width, data.height, fill = "light blue")
    canvas.create_rectangle(0, data.height/3, data.width, data.height, fill = "green", width = 0)
    canvas.create_rectangle(0, data.height/2, data.width, data.height, fill = "dark green", width = 0)
    canvas.create_text(5, 5, text = "Score = %d" %data.score, fill = "black", anchor = NW)
    canvas.create_rectangle(0, data.groundh, data.width, data.height, fill = "#5f4630")
    # draw cloud shadows
    canvas.create_oval(10, 30, 70, 55, fill = "#d9d9d9", width = 0)
    canvas.create_oval(30, 20, 80, 40, fill = "#d9d9d9", width = 0)
    canvas.create_oval(60, 20, 100, 40, fill = "#d9d9d9", width = 0)
    canvas.create_oval(25, 45, 70, 75, fill = "#d9d9d9", width = 0)
    canvas.create_oval(55, 45, 100, 75, fill = "#d9d9d9", width = 0)
    canvas.create_oval(35, 30, 120, 60, fill = "#d9d9d9", width = 0)
    canvas.create_oval(20, 30, 100, 40, fill = "#d9d9d9", width = 0)
    # draw cloud
    canvas.create_oval(10, 30, 70, 50, fill = "white", width = 0)
    canvas.create_oval(30, 20, 80, 35, fill = "white", width = 0)
    canvas.create_oval(60, 20, 100, 35, fill = "white", width = 0)
    canvas.create_oval(25, 45, 70, 70, fill = "white", width = 0)
    canvas.create_oval(55, 45, 100, 70, fill = "white", width = 0)
    canvas.create_oval(35, 30, 120, 55, fill = "white", width = 0)
    canvas.create_oval(20, 30, 100, 45, fill = "white", width = 0)
    # second cloud
    canvas.create_oval(210, 130, 270, 155, fill = "#d9d9d9", width = 0)
    canvas.create_oval(230, 120, 280, 140, fill = "#d9d9d9", width = 0)
    canvas.create_oval(260, 120, 300, 140, fill = "#d9d9d9", width = 0)
    canvas.create_oval(225, 145, 270, 175, fill = "#d9d9d9", width = 0)
    canvas.create_oval(255, 145, 300, 175, fill = "#d9d9d9", width = 0)
    canvas.create_oval(235, 130, 320, 160, fill = "#d9d9d9", width = 0)
    canvas.create_oval(220, 130, 300, 140, fill = "#d9d9d9", width = 0)
    # draw cloud
    canvas.create_oval(210, 130, 270, 150, fill = "white", width = 0)
    canvas.create_oval(230, 120, 280, 135, fill = "white", width = 0)
    canvas.create_oval(260, 120, 300, 135, fill = "white", width = 0)
    canvas.create_oval(225, 145, 270, 170, fill = "white", width = 0)
    canvas.create_oval(255, 145, 300, 170, fill = "white", width = 0)
    canvas.create_oval(235, 130, 320, 155, fill = "white", width = 0)
    canvas.create_oval(220, 130, 300, 145, fill = "white", width = 0)
    

# if hit, game over
def testHit(data):
    for i in range(len(data.fallingobjects)):
        currobject = data.fallingobjects[i]
        player = data.player
        hit = player.hitObject(currobject) 
        if hit == True and type(currobject) == Candy:
            data.score += 1
            data.fallingobjects.pop(i)
            break
        elif hit == True and type(currobject) == Fireball:
            data.gameOver = True
            data.fallingobjects.pop(i)
            break

####################################
# use the run function as-is
####################################

# from CMU 15-112 framework
def run(width=300, height=300):
    # Set up data and call init
    class Struct(object): pass
    data = Struct()
    data.width = width
    data.height = height
    data.timerDelay = 100 # milliseconds
    init(data)
    def redrawAllWrapper(canvas, data):
        canvas.delete(ALL)
        redrawAll(canvas, data)
        canvas.update()    

    def mousePressedWrapper(event, canvas, data):
        mousePressed(event, data)
        redrawAllWrapper(canvas, data)

    def keyPressedWrapper(event, canvas, data):
        keyPressed(event, data)
        redrawAllWrapper(canvas, data)

    def timerFiredWrapper(canvas, data):
        timerFired(data)
        redrawAllWrapper(canvas, data)
        # pause, then call timerFired again
        canvas.after(data.timerDelay, timerFiredWrapper, canvas, data)
    # create the root and the canvas
    root = Tk()
    canvas = Canvas(root, width=data.width, height=data.height)
    canvas.pack()
    # set up events
    root.bind("<Button-1>", lambda event:
                            mousePressedWrapper(event, canvas, data))
    root.bind("<Key>", lambda event:
                            keyPressedWrapper(event, canvas, data))
    timerFiredWrapper(canvas, data)
    # and launch the app
    root.mainloop()  # blocks until window is closed
    print("bye!")
    
run(350, 500)

