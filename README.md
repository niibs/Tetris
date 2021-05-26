
# Prison Tetris 
A CMSC 21 Final Project 

> By: Lungay, Mariane Faye | Miranda, Ericka Monique | Nogra, Nibay


## OVERVIEW
Our game is called “Prison Tetris,” it is based on the 1980s arcade classic game of Tetris. The object of the game is to score as many points as possible by clearing horizontal lines of Blocks. And similar to the classic game of tetris, lines are cleared when they are filled with Blocks and have no empty spaces. But to make things interesting, this will be a story-based game.

One day, Prisoner A finds themself trapped in a prison cell with tetriminos falling from above. In order to get Prisoner A out of the cell, the player must first keep the prisoner alive within the 2-minute interval. To do this, the player must make sure that the tetriminos do not fall directly on the prisoner, and that the piling blocks do not reach the top of the playing field. If the player
manages to complete the level, the time bomb will explode and create an opening on one side of the playing field and the prisoner gets to successfully escape.


## GAMEPLAY

The player controls the tetriminos by using the **left and right arrow keys** (to turn), the **up arrow key** (to rotate clockwise), and the **down arrow key** (to drop: soft). But for a hard drop, the **space bar** will be used. And to hold and change pieces, we use the **Shift key**. The prisoner is represented by an emoji. The player controls the prisoner by using the **A and D keys** (to turn), and the **W key** (to jump one unit/block up). The prisoner cannot jump higher than 1 unit/block up. In the case that the prisoner gets trapped and has no way to escape, the player can choose from the following options:

- Clear the blocks on top without crushing the prisoner 
- Opt to exit from the game 
- Intentionally exit by either crushing the prisoner with a block or have the piling blocks reach the top of the playing field

The player wins if they manage to have the prisoner survive within the 2-minute time limit. But with each level, the tetriminos’ drop speed will increase. And the player loses if:

- The tetriminos or blocks fall directly on the prisoner (crushed) 
- The piling blocks reach the top of the playing field

Each line cleared is equivalent to one hundred points, and the scores will be recorded on a leaderboard or scoreboard.

## MAIN MENU
Before the game starts, the game menu will appear. The menu list will include the following:
- “HOW TO PLAY” button, where the game rules and controls, in one txt file, will be read by the program and accessed by the user. 
- “STORY” button, where the story of the game, in a txt file, will be read by the program and accessed by the user. 
- “START” button, where the user will be prompted to type in their name while a file, players.txt, will be opened for reading and writing. If the username does not exist in the file, this string will be written in the file. If the username already exists however, the program will inform the user about this and prompt them to answer the question, “Do you wish to continue with the name provided?” The purpose of which is to verify the player’s identity. If the answer to the question is a yes, then the game starts. Else, the program will ask the user for another username. 
- “LEADERBOARD” button, which shows the top 10 highest scores filtered by the level of difficulty. This is where scores.txt will be opened to read the records that belong to the level's top 10 scores.

> **Note:** When the game ends, the score together with the player's name, the level of difficulty, and the time consumed will be stored in a file called scores.txt. scores.txt will be utilized to check whether the player has set a new high score by knowing whether the score belongs to the top 10 scores provided the level of difficulty.

## FEATURES

The features of the game include:
- The player can rotate the block in a clockwise direction and move the current horizontally and vertically. 
- The player is able to move the prisoner. The prisoner can jump as long as the adjacent block is just at most a unit higher than its position (see image below). The prisoner can also fall. 
- The next block must be visible to the player. 
- The player can store a block in a “holding area”. However, the swapping between the current block and the stored block can only be done once for every new block introduced to the playing area. 
- The current block drops at a constant speed which varies with the game’s level of difficulty. 
- A ticking time bomb will indicate the time needed for the blocks to disintegrate and the wall to open up provided that the prisoner has not died.

## OBJECTS

### Blocks
Comes in 7 shapes, **I, L, J, T, O, S, and Z,** all of which can be rotated, moved to the right and to the left, and dropped. The player can “hold” the block if they do not have a good spot to put it for the time being. Only one block can be stored in the **“holding area”** at a time. The colors for each block will vary.

> **Variables:**
> - x-coordinate 
> - y-coordinate 
> - rotation
> 
> **Functions**
> - rotate(): rotates the block 90 clockwise every time the ↑ key is pressed  
> - moveBlock(): moves the block a unit to the left every time the ← key is pressed, a unit to the right when the → key is pressed, and a unit downwards when the ↓key is pressed 
> - speed(): moves the block x units per second in a downwards direction (x relies on the round’s level of difficulty) 
> - drop(): the block takes the position of its ghost piece as soon as the space bar is hit 
> - exceed(): detects whether the block has touched the ceiling of the playing field once dropped 
> - wholeDrop(): decrease the y-coordinate of all blocks above the cleared lines through clear() by the number of lines cleared

### Ghost Piece
A faint outline which appears below the current block and gives the player a general idea of where it will settle once the block reaches the bottom.

> **Variables:**
> - x-coordinate 
> - y-coordinate 
> 
> **Functions**
> - copy(): copies the configuration of the current block but places the ghost piece at the lowest possible position such that it is above the ground or above the surface of a block.

### Prisoner
The prisoner is trapped inside the prison cell and is maneuvered by the player to avoid the falling blocks. The prisoner can move left and right, and jump at the adjacent block only a unit higher than the prisoner’s current position.

> **Variables:**
> - x-coordinate 
> - y-coordinate 
> 
> **Functions**
> - movePrisoner(): moves the prisoner a unit to the left every time the A key is pressed, a unit to the right when the D key is pressed, and a unit upward when the W key is pressed 
> - fall(): if the prisoner is not on a surface, it falls at a certain rate until it lands on a surface 
> - crushed(): detects whether the current block lands on the prisoner

### Playing Field
The grid into which the blocks fall and the prisoner moves around. It consists of cells which are either occupied or not. The Tetris Guideline specifies a playfield 10 blocks wide by 40 blocks tall, where the tetrominoes are started in rows 21 and 22.

> **Variables:**
> - row size 
> - column size
>
>**Functions**
> - clear(): counts the instances wherein a horizontal line is formed when a block is dropped and clears these lines 
> - score(): accumulates the score in the whole round such that a line cleared is equivalent to 100 points.

### Time Bomb
The Time Bomb displays a clock counting down how much time left is needed for the blocks to disintegrate and the wall to open up.
> **Variables:**
> - minute 
> - second
>
>**Functions**
> - checkTime(): stops the game once minute == 0 and second == 0.



### ScoreBoard
The scoreboard keeps track of and displays the score, and level for the player.
> **Variables:**
> - score 
> - level

