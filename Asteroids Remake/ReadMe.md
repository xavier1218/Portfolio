Here is a link to play our game on the TIC-80 website: [TIC-80 Link](https://tic80.com/play?cart=3253).

The following is a direct copy of Xavier Serrano and Alyssa Zhang's submission for our Swarthmore Computer Science class, CPSC 091s - Game Systems, taught by [Keith O'Hara](https://drablab.org/keithohara/).



# Remake
## Downloads
Our TIC-80 remake of the original Atari Asteroids has been attached to this GitHub repository. To play the game, install TIC-80 and run the following commands in your machine's terminal.
```
$ tic80
```
This will open up the TIC-80 command line. Open the TIC-80 folder, move the asteroids.tic file into the TIC-80 folder, load the .tic file, and run the game.
```
$ folder
$ load asteroids.tic
$ run
```
## About Asteroids
The Atari 2600 version of Asteroids is a space-themed multi-directional shooter game released by Atari in 1981. The game consists of the player's ship anchored in the middle of the screen and asteroids and UFOs floating around the player's ship at varying speeds and sizes. To increase the player's score, they must shoot at the asteroids as they drift by, breaking those asteroids into smaller asteroids that they can shoot at again to destroy. The smaller the asteroids, the faster they travel and as the game progresses, the asteroid danger zone encroaches farther into the player's ship's zone. The UFOs were added to keep the player from just sitting and dodging the asteroids. The game is based on the 1979 arcade game Asteroids, which was a slightly more complex version of the game where the player's rocket ship could move around the screen while destroying asteroids.

## Pros and Cons of Asteroids
The original arcade version of Asteroids was widely considered to be a success and was played in arcades around the country. 2 years later, Atari released a ported version of the game for the Atari 2600 gaming console. Because the game was ported to a less powerful system, it had some limitations compared to the arcade version.  In the Atari 2600 version, there was no ability for the rocket to move around as in the arcade original. To adjust, the asteroids were also limited to only vertical motion outside of the rocket's space. The asteroids were also rainbow colored instead of the original black and white, which could be seen as a bit of an upgrade between the two versions, but outer space isn't very colorful, so this is debatable.


## Building Asteroids
In order to make the game less predictable, the asteroids are generated and built in a random way.  There are 6 asteroid sprites, one of which is chosen at random. The asteroid is then given a random starting point somewhere on the edge of the screen. A velocity of .25,.5,.75,1 is then randomly selected and appropriately given direction based on its starting position.  Finally, the scale (size) of the asteroids is chosen to be a value from 1-5.  All of this generated information is passed into a function that tracks all of the asteroids on the screen, draws them, and updates their location based on their velocity. Asteroids which are no longer on the screen are deleted.

### Sprites
We have 7 asteroid sprites of varying colors and shapes that we use.
We have 2 rocket sprites, one facing upward and one facing 45 degrees. These sprites are rotated to face all 8 directions in gameplay.
We have a rocket tile to indicate the number of lives left.
We have 5 tiles that spell out the word "score" to have the score displayed on the screen.
We have a bullet sprite to represent the bullet fired from the rocket at the asteroids.
We have 3 tiles of stars to form the space background of the map.

### Map
Our map is an outer space scene that is black with 3 star tile spread throughout the map to give the illusion of being in outer space.  The map is updated based on the number of lives left, which is displayed by a number of rocket ships in the bottom left corner to represent the lives. Finally, the word score is printed on the map, and the score is printed separately as it changes through gameplay.

There is a separate map screen for the when the player dies, which has the words "you died". It appears for 2 seconds between lives.
There is a final map screen for when the game is over, which prints "game over" and the score. 

### Physics & Motion
The asteroid velocity is determined based on the asteroid's randomly-generated starting position. It is generated such that the asteroid moves through the field of play. The velocity is .25, .5, .75, or 1.0 unit per cycle.
The rocket can move in 8 directions at a speed of 1 per cycle.
The bullet is fired from the rocket, and travels at a speed of 1 unit per cycle in both the x and y direction. The bullet travels in the same direction the rocket was facing when it was fired.  
The rocket is able to go through the edge of the screen and reappear at the opposite side. 
Collisions are detected between the rocket and the asteroids. If the rocket is within a certain distance of the asteroid, depending on the asteroid's size, this counts as a collision. The game is reset, and the lives are adjusted appropriately.
Collisons are also detected between the rocket bullets and the asteroids in the same way. If a collision is detected, the score is incremented and the asteroid is removed from the screen.

### Game Conditions
The score is incremented by 10 each time a bullet hits an asteroid. 
The lives of the player are decremented each time the player is hit by an asteroid.
When the player dies, a screen appears that says "you died" for 2 seconds.
If the player has no lives left, the game over screen appears with their score. The game over screen is another map element that is a black screen with the words "game over" and their score.
