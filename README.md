# Study Log
_(Created 15/10/24)_  
Having no prior knowledge on how github works OR what I'm looking at in Visual Studio, I'll be documenting everything and anything I consider new info.

# 15/10/24
- Kiiinda learned how to assign player inputs to object movement
- Still not sure what the classes are exactly, or all the functions and variables, but I figure the more I use them, the more they'll stick

# 16/10/24
_I GOT VERTICAL INPUTS WORKING!_  
Turns out, `float verticalInput = Input.GetAxis("vertical");` was the issue, the v needed to be capitalised. Otherwise, works like a charm! Now to attempt gravity-


# 22/10/24
Gonna double check my old script still works, then google what it is I even need for the project planned. If it ends up being too complex, we're hopping ship.  

- checkpoint 1; we relearned what rigidbody is.

Fascinating... holding down will flip the object over lmao. Actually, might be because the cylinder is tall, would it work on a cube? ...Those. Are some fascinating physics. Turns out, you can freeze the rotation in Rigidbody, and increasing the speed messes with the gravity.  

- checkpoint 2; we fixed an "issue" where the objects would rotate if you held a vertical input too long

Don't feel like touching boolean logic just yet, so I'm booting up a 2D scene.

- checkpoint 3; I've set it up so that jump is spacebar, but you can only do it when going right. Going left causes it to go down.
- Fixed, don't include `player movement` in that line.

`Rigidbody -> Interpolate` is used to get rid of the jitter when jumping, but makes the jump endless since it's just up.  
Ok, so `AddForce` and `transform.Translate` are different in that the former obeys gravity more. It's recommended to exert a force rather than transform objects if you're looking to have physics work correctly.

# 29/10/24
What are we doing here..?  
- UI code looks like it's applied to the main camera

# 07/01/25
Starting pretty late, but I have a clearer idea on what I want to do. Clown Control is going to be a railshooter where the camera follows a set path and the player has to shoot the enemies on screen in order to proceed. The tutorials will focus on creating waypoints for the camera to follow, the shooting controls, having the UI display the player's lives and bullets, and programming the camera to stop when a phase of enemies spawn. Depending on how much I can get done, we'll see if I need to simplify the tutorials. I'm aware there are some posted to take pointers off of, but my ideas are very specific and I want to make something more unique in playstyle- also to pay homage to House of the Dead 2, since I want to see more games like that one.

- I've encountered a bug where the Main Camera floats off when I hit play --- As it turned out, it wasn't the camera, it was the map that moved. I had to make the Mass on the Rigidbody greater than the Mass of the Player.
- RigidBody was removed from the objects due to a lack of understanding on how to freeze transformations based on uneven mass. Technically the game doesn't need it anyway, the physics would only overcomplicate the camera movements.
- The Player Object is able to travel from waypoint to waypoint, but the camera does not turn to face the direction of them. I am considering either applying the code to the camera itself (and doing away with the 3D object) or finding a way to have the camera face the direction it is travelling in.

Leaving it off here. As it stands, there seems to be an issue where the camera will teleport further forward when the GameObj reaches certain Waypoints. I suspect the moveCamera and followWP scripts were clashing with each other, so it may need to be simplified. If I cant get it to smoothly traverse between points, I can move onto refinement, but there isn't much time to linger on this starting tutorial.

# 10/01/25
We're trying a new method; I'm going to mess with code first to ensure it works, THEN I'll make the tutorials. Making the tutorial as I work only means I'll be spending too long editing it when I run into a bug and have to scrap certain steps.

- Can confirm, applying the 'follow waypoints' script directly to the camera works perfectly
- Initially wanted to lock the crosshair to the screen, but now I'm thinking it'd be better to allow the cursor to point off-screen, as that's how the reloading system worked for the original HotD games.
- I'm not too sure how enemies would work here. Either I could add scripted events at each waypoint (or in between them), or I give them proximity, but the former seems more in line with how the enemy ai used to work.
- I hesitate to use any code I don't fully understand the purpose of. Some of the tutorials I'm looking for are blown through quickly or coded for a specific purpose, and my attempts to mix n match what I need for my own script haven't been very successful.

- Ran into an issue where it wouldn't let me drag and drop sprites for the bullet display, but it seems to be an issue with 2D sprites on a 3D engine. To resolve this, I had to view the image in `Inspector` and change the Texture to Sprite (2D and UI). It's not working with the array, but worked with the public sprites. Linking the ammo displaye to the actual ammo count is a bit tricky to wrap my head around, so I may end up simplifying the UI visuals.

# 11/01/25
I reviewed the first few lines of code I was using for the ammo display. The tutorial I'm following is for 2D rather than 3D, and it's for heart contrainers rather than bullets, but a lot of the same principles apply. I've changed the array to Sprite instead of Image to see if it works. It didn't.

- I got some help from the original poster of the tutorial I was following. The issue was that my gameobjects were set to raw images instead of images, hence it wouldn't let me drag and drop them. Now that the display is up and running, I just need to figure out how to link it to the reload and playerAmmo scripts.
- As I'm tinkering around with the code, I ended up doing away with playerAmmo and just directly applying its code to ammoDisplay.

The game project now runs as intended. I just need to work backwards and simplify/streamline how I got to this point.

# 12/01/25
Just finished the last tutorial. Went through them all a few times just to make sure the spelling and syntax was correct. To source screenshots for the tutorials, I made a duplicate project as I was typing them out and would follow the steps. My only mistake was renaming some of the variables, as I would copy and paste code from my original script and it didn't always line up. Either way, everything seems to be in order. I'm quite happy with how much I was able to pick up in a short timespan, though I wish I'd been able to implement the enemy clowns. I fear the ammoDisplay script would need a ton more lines to do with damage and registering hits, which I'm none too familiar with.
