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
