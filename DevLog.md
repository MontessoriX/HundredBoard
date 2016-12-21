12/8/2016, 7:28:31 PM --  Initial Commit
12/8/2016, 7:32:00 PM --  Game is Blank Game with no starter content.  Desktop 2d/3d Saleable
12/8/2016, 7:34:10 PM --  Create a Map Directory and save map named HundredMap
12/8/2016, 7:40:16 PM --  Delete SkySphere
12/8/2016, 7:42:48 PM --  File -> Editor Preferences -> Maps & Modes -> Game Editor Start Map HundredMap
12/8/2016, 7:54:47 PM --  Created a Blueprints folder and added a Game Mode Base Blueprint to it called HundredGameMode
12/8/2016, 7:55:40 PM --  Added a Player Controller Blueprint called HundredPlayerController
12/8/2016, 8:00:24 PM --  Added a new pawn blueprint called HundredPlayer
12/8/2016, 8:02:04 PM --  Added a camera to the HundredPlayer Blueprint
12/8/2016, 8:04:08 PM --  Dragged the Camera onto the Scene Root of the HundredPlayer Blueprint.  This makes it the new Scene Root for that blueprint
                          ^^^^ In the future, do not do this.  The camera should not be the scene root
12/8/2016, 8:10:49 PM --  In the HundredPlayerController -> Mouse Interface -> checked Show Mouse Cursor
12/8/2016, 8:11:34 PM --  In the HundredPlayerController -> Mouse Interface -> checked Enable Click Events
12/8/2016, 8:12:05 PM --  In the HundredPlayerController -> Mouse Interface -> checked Enable Mouse Over Events
12/8/2016, 8:15:00 PM --  In the HundredGameMode -> Classes -> Player Controller Class set to HundredPlayerController
12/8/2016, 8:17:10 PM --  In the HundredGameMode -> Classes -> Default Pawn Class set to HundredPlayer

----

12/9/2016, 6:02:23 PM	--	Since it doesn't seem like I can replace the Camera in the HundredPlayer blueprint, I am deleting the HundredPlayer blueprint and re-creating
12/9/2016, 6:03:23 PM	--	Creating a new pawn called HundredPlayer
12/9/2016, 6:04:17 PM	--	Adding a Camera to the HundredPlayer blueprint, but making sure *not* to make it the scene root
12/9/2016, 6:22:55 PM	--	In the map World Settings, Set the GameMode Override to HundredGameMode.  This makes the game use the HundredGameMode which causes the HundredPlayer to be spawned at the player start.
12/9/2016, 6:26:08 PM	--	In the HundredPlayer Blueprint, Event Graph, connected SetWorldRotation to the Event BeginPlay targeting the camera and setting the New Rotation to a hardcoded 0.0,-90.0,0  This makes the camera start looking straight downward
12/9/2016, 6:36:56 PM	--	Removed the SetWorldRotation that I just added, and replaced it with SetWorldLocationAndRotation.  Location of 0.0,575.0,1100.0 and rotation of 0.0,-90.0,0.0


----

12/10/2016, 12:19:30 PM	--	Added a comment in the HundredPlayer Blueprint to describe what we did yesterday
12/10/2016, 12:20:33 PM	--	Added a boolean variable to HundredPlayer called LMB_Down, this will be true if the left mouse button is down
12/10/2016, 12:22:01 PM	--	Deleted the nodes for BeginOverlap and Event Tick, since we don't need those now
12/10/2016, 12:23:42 PM	--	Adde a LeftMouseButton event to the HundredPlayer blueprint
12/10/2016, 12:24:06 PM	--	Set the pressed node of the LeftMouseButton event to set LMB_Down as true
12/10/2016, 12:24:50 PM	--	Set the released node of the LeftMouseButton event to set LMB_Down to false
12/10/2016, 12:30:22 PM	--	Re-Added EventTick event Converted the LMB_Down boolean to a string, and printed it out to the screen.  Just to confirm that everything was printing out correctly.  It is
12/10/2016, 12:31:06 PM	--	Deleting what I did in the line above as it was just for debug purposes

----

12/10/2016, 12:38:51 PM	--	Creating a new Actor Blueprint called NumberPiece
12/10/2016, 12:40:49 PM	--	Adding a cube component to the NumberPiece Blueprint
12/10/2016, 12:43:46 PM	--	Scaling the cube so that it is 0.2 high along the Z axis
12/10/2016, 1:09:19 PM	--	Changing the translation of the cube so that its Z is at 10cm high.  This puts the bottom of the cube on the "floor" of the blueprint

----

12/11/2016, 12:30:51 PM	--	Added 2 instances of the NumberPiece to the game board.  These may be a little thick, and I may need to scale the cube in them down a bit in the Z axis
12/11/2016, 12:33:26 PM	--	Dragged "Get Player Controller" into the NumberPiece blueprint event graph
12/11/2016, 1:10:53 PM	--	Add Get Controlled Pawn and tie it into Get Player Controller.
12/11/2016, 1:11:35 PM	--	On the return of Get Controlled Pawn add a Cast To HundredPlayer node.  Additionally tie that into Event BeginPlay
12/11/2016, 1:12:29 PM	--	Set a new variable called PlayerControllerReference tied it into the Cast to Hundred Player.  This sets the variable when the game starts so we can use it later
12/11/2016, 1:14:04 PM	--	Created a new boolean variable called MouseOver

----
12/12/2016, 6:44:36 PM	--	Added a Boolean variable called MouseOver which will be true when the mouse is over that piece
12/12/2016, 6:45:48 PM	--	Added a new event to the NumberPiece blueprint: Event ActorBeginCursorOver is triggered when the cursor travels over this actor
12/12/2016, 6:46:24 PM	--	Set MouseOver to true when the Event ActorBeginCursorOver fires
12/12/2016, 6:47:40 PM	--	Repeated the above 2 lines, only with Event ActorEndCursorOver setting MouseOver to False when it fires
12/12/2016, 7:01:12 PM	--
12/12/2016, 7:01:51 PM	--	Created a new Event called TileAttached in the NumberPiece blueprint
12/12/2016, 7:02:49 PM	--	Added a branch node connected to the Event Tick Event.  Its condition is the MouseOver Boolean
12/12/2016, 7:04:43 PM	--	Out of the True node of the branch, I added a second branch.  In theory I could have done an AND node here, but Blueprint doesn't do any short circuiting so both would have to be evaluated when most of the time the first is not true.
12/12/2016, 7:07:19 PM	--	The condition for this second branch is created by pulling in the Player Controller Reference, and that is connected to the  LMB_Down boolean which feeds the second branch.
12/12/2016, 7:07:57 PM	--	So what these 2 branches do, is make sure that the mouse is over this blueprint, and that the button is pressed.
12/12/2016, 7:09:02 PM	--	If both of those are true, throw the TileAttached custom event
12/12/2016, 7:14:01 PM	--	Added a quick print string to the TileAttached custom event to print out that this event has been thrown.

----


12/13/2016, 7:10:24 PM	--	Spent a bit over an hour trying different methods for trying to capture the mouse location without much success.  I probably should have recorded my efforts here to not duplicate them tomorrow.

----

12/14/2016, 10:53:52 PM	--	Edit -> Project Settings.  Clicked on the collision tab.  Added a new trace channel called Cursor which has a default response of ignore


----
12/15/2016, 5:04:33 PM	--	In the NumberPiece blueprint a new function called Attach_And_Move
12/15/2016, 5:06:57 PM	--	Adding an input for the Attach_And_Move function.  This is a boolean variable called Attached
12/15/2016, 5:09:13 PM	--	Off of the Set_Attached function start node, adding a Set Simulate Physics component.  This automatically set the Cube's static mesh as the target
12/15/2016, 5:24:12 PM	--	Wired up Attached from the node start to the Simulate in point on Set Simulate Physics with a boolean Not node in between.  So that if the piece is attached physics are not simulated.  And if the piece is not attached, physics are simulated
12/15/2016, 6:19:12 PM	--	Added a branch node after Set Simulate Physics.  The boolean input goes back to the Attached boolean from the start of the Attach_And_Move function.  
12/15/2016, 6:29:38 PM	--	Back in the Event Graph, we used to have the event tick eventually calling a TileAttached custom event.  I'm deleting that entire custom event an the reference to it
12/15/2016, 6:30:47 PM	--	Wiring up a call to the new Attach_And_Move function we wrote.  If the second branch statement is true, we know that the mouse is over the piece and the left mouse button is down.  So we want to wire that True to the Attach_And_Move function and set attached to true.
12/15/2016, 6:31:37 PM	--	We also want to wire BOTH of the false connections from both branches to a call to the Attach_And_Move function where the attached node is false
12/15/2016, 6:36:53 PM	--	Back in the Attach_And_Move function, adding a Print String to the True branch.  The string is just "Piece is attached" to let us know things are getting there at the appropriate time.

----

12/16/2016, 7:37:10 PM	--	Added a Get Player Controller node to the Attach_And_Move function of the NumberPiece Blueprint
12/16/2016, 7:37:42 PM	--	Added a ConvertMouseLocationToWorldSpcae node and wired its target to the return value of Get Player Controller
12/16/2016, 7:39:09 PM	1481935149000
--I need to finish documenting this when I get it all working


----

12/17/2016, 6:05:25 PM	--	Feeling under the weather today, and no brain power for coding, but still want to do something to work on the game.  I started up a new project, this time WITH sample content, and mobile settings, and found some of the samples I wanted to bring over to this project.  I selected the M_Wood_Oak, M_Wood_Pine and M_Wood_Walnut materials right clicked on them and selected Asset Actions -> Migrate
12/17/2016, 6:06:57 PM	--	I then selected my HundredBoard game and exported the files there.
12/17/2016, 6:07:12 PM	--	Closing that started project, I returned to the HundredBoard game and the materials were in there


----

12/18/2016, 9:53:03 PM	--	In the NumberPiece blueprint, I added the M_Wood_Pine to be the material for the cube.



----

12/19/2016, 10:42:04 PM	--	in the NumberPiece blueprint, selected the Cube, and in the Details, under physics properties enabled "Simulate Physics"
12/19/2016, 11:11:03 PM	--	Back in the level, I added a blocking volume, and set its location to 0,0,-80cm and scale to 5,5,1
12/19/2016, 11:12:16 PM	--	On this blocking volume, set the collision presets to Custom, Collison Enabled to Query only (No Physics Collision)
12/19/2016, 11:12:41 PM	--	Set every collision response to ignore, with the exception of Cursor, which is set to Block


----

12/20/2016, 10:24:52 PM	1482290692000	Completed the attach_and_move function.  The entire function now works like this:
12/20/2016, 10:27:21 PM	1482290841000	Returning to the branch node that we used on 12/15/2016, 6:36:53 PM I replaced the true output and connected it to a line trace by channel node.
12/20/2016, 10:29:54 PM	1482290994000	The start for this LineTraceByChannel is fed by GetPlayer Controler for player index 0, which feeds into the ConvertMouseLocationToWorldSpace and that World Location.  So in short, the Start is the world location of the mouse cursor.
12/20/2016, 10:32:13 PM	1482291133000	The End of the LineTraceByChannel is the worldDirection from the ConvertMouseLocationToWorldSpace we referenced before vector multiplied by the cursor trace distance, and vector added to the world location.  So in short, the end is the cursor trace distance straight into the screen.
12/20/2016, 10:32:48 PM	1482291168000	The Trace Channel of the LineTraceByChannel is "Cursor"
12/20/2016, 10:34:09 PM	1482291249000	The Out Hit of the LineTraceByChannel feeds a Break Hit Result
12/20/2016, 10:35:11 PM	1482291311000	The execution out of the LineTraceByChannel and the return channel feed a branch.  The True output of which goes to a SetActorLocation node.
12/20/2016, 10:36:44 PM	1482291404000	The SetActorLocation's new location is fed by the Location from the Break Hit Result and then vector added 0,0,30.0 to.  This moves the item to 30cm high, and moves it to wherever the mouse is.


----
