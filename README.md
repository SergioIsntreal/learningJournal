# Study Log
_(Created 15/10/24)_  
Having no prior knowledge on how github works OR what I'm looking at in Visual Studio, I'll be documenting everything and anything I consider new info.

# 15/10/24
- Kiiinda learned how to assign player inputs to object movement
- Still not sure what the classes are exactly, or all the functions and variables, but I figure the more I use them, the more they'll stick

# 16/10/24
_I GOT VERTICAL INPUTS WORKING!_  
Turns out, float verticalInput = Input.GetAxis("vertical"); was the issue, the v needed to be capitalised. Otherwise, works like a charm! Now to attempt gravity-


# 22/10/24
Gonna double check my old script still works, then google what it is I even need fer the project planned. If it ends up being too complex, we're hopping ship.  

- checkpoint 1; we relearned wtf rigidbody was.

Fascinating... holding down will flip the object over lmao. Actually, might be because the cylinder is tall, would it work on a cube? ...Those. Are some fascinating physics. Turns out, you can freeze the rotation in Rigidbody, and increasing the speed fucks with the gravity.  

- checkpoint 2; we fixed an "issue" where the objects would rotate if you held a vertical input too long

Don't feel like touching boolean logic just yet, so I'm booting up a 2D scene.

- checkpoint 3; I've set it up so that jump is spacebar, but you can only do it when going right. Going left causes it to go down. Fixed, don't include player movement in that line.

Rigidbody -> Interpolate is used to get rid of the jitter when jumping, but makes the jump endless since it's just up.  
Ok, so 'AddForce' and 'transform.Translate' are different in that the former obeys gravity more. It's recommended to exert a force rather than transform objects if you're looking to have physics work correctly.

# 29/10/24
What are we doing here..?  
- UI code looks like it's applied to the main camera

# 07/01/25
Starting pretty late, but I have a clearer idea on what I want to do. Clown Control is going to be a railshooter where the camera follows a set path and the player has to shoot the enemies on screen in order to proceed. The tutorials will focus on creating waypoints for the camera to follow, the shooting controls, having the UI display the player's lives and bullets, and programming the camera to stop when a phase of enemies spawn. Depending on how much I can get done, we'll see if I need to simplify the tutorials. I'm aware there are some posted to take pointers off of, but my ideas are very specific and I want to make something more unique in playstyle- also to pay homage to House of the Dead 2, since I want to see more games like that one.

- I've encountered a bug where the Main Camera floats off when I hit play --- As it turned out, it wasn't the camera, it was the map that moved. I had to make the Mass on the Rigidbody greater than the Mass of the Player.
