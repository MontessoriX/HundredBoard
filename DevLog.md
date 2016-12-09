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
