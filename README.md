![Logo](http://i45.tinypic.com/30rp5qx.jpg)<br />

##DayZ Duel Admin Debug Monitor
=============================
* V1.1

The DayZ Duel Admin Debug Monitor (remember you saw it here first) gives admins a special extended debug monitor while giving normal players 
the regular version (non-admin), It is kept up to date by Nomadic Hayward (aka UrbanSkaters).  When a regular
NON-admin user logs in they will see the debug monitor on the left (see screenshot above) and when an Admin
logs in (assuming you've put their UID in the list as explained below), they will see the extended debug monitor.

There are two versions: 

* The Always on version will stay on ALL the time. 
* The Trigger version will only come on when you press your Debug Monitor hotkey, and fades after about 30 seconds.

Both versions are for Chernarus but should also work with other maps (back up your original files before testing).

I accept no responsibility for any damage or downtime this script may cuase to your server. (please backup first)  
The script has been tested and confirmed to be working by both admins and regular users on my server.
If you do not understand any of my instructions below, then please contact me: urbanskaters@gmail.com

##Version requirements

This debug monitor has been tested with Chernarus using DayzCode V1.7.6.1 <br/>
I cannot gaurantee that it will work with any other version, though it should work with other maps.

##Instructions

NB: These instructions assume you already know how to unpack your mission.pbo, if not please Google for more information.

First things first, merge the included init.sqf with your own mission init.sqf file (remember to do the Instance Number). 

You DO NOT need the mission.sqm or description.ext files, these are just to complete the mission folder structure.
You should have your own, but if you haven't then use these instead (they only work with Chernarus though)

Copy the debug folder and contents to your mission folder, along with the merged init.sqf (if you haven't done so already)

You will need to make changes to the following file, depending on which version you're using:

* For the Trigger Version: debug\playerstats.sqf (near line 13)
* For the Always On Version: debug\player_spawn_2.sqf (near line 279)

Look for this code on those lines: <i>if ((getPlayerUID vehicle player) in ["11111","222222"])</i>

And change the UIDs to those of yours and your admin(s). 
To add more UIDS simply put a comma at the end of the last UID and add a UID in brackets..
So adding a new UID to the above example would look like this ["11111","22222","33333"]

##Detailed instructions for editing your init.sqf (Always on Version)

*This is what you need to edit YOUR mission init.sqf file, although you could just copy and paste the one provided in this folder...<br/>
*Locate the //Load in Compiled functions and comment out the following line:
call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\variables.sqf";  			//Initilize the Variables (IMPORTANT: Must happen very early)
*and comment it out so it looks like this:
// call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\variables.sqf";				//Initilize the Variables (IMPORTANT: Must happen very early)
*then right underneath it on the next line, add this:
call compile preprocessFileLineNumbers "debug\variables.sqf";				//Initilize the Variables (IMPORTANT: Must happen very early)
Comment out this line:
call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\compiles.sqf";				//Compile regular functions
*Then right underneath add this line:
call compile preprocessFileLineNumbers "debug\compiles.sqf";				//Compile regular functions
*Right after this line:
"filmic" setToneMappingParams [0.153, 0.357, 0.231, 0.1573, 0.011, 3.750, 6, 4]; setToneMapping "Filmic";
*Add this line:
player_spawn_2 = compile preprocessFileLineNumbers "debug\player_spawn_2.sqf";

That's all you need to edit in your init.sqf, after you've made those changes that part of the document should look something like this:

<code>//Load in compiled functions
//call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\variables.sqf";				//Initilize the Variables (IMPORTANT: Must happen very early)
call compile preprocessFileLineNumbers "debug\variables.sqf";				//Initilize the Variables (IMPORTANT: Must happen very early)
progressLoadingScreen 0.1;
call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\publicEH.sqf";				//Initilize the publicVariable event handlers
progressLoadingScreen 0.2;
call compile preprocessFileLineNumbers "\z\addons\dayz_code\medical\setup_functions_med.sqf";	//Functions used by CLIENT for medical
progressLoadingScreen 0.4;
//call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\compiles.sqf";				//Compile regular functions
call compile preprocessFileLineNumbers "debug\compiles.sqf";				//Compile regular functions
progressLoadingScreen 1.0;

"filmic" setToneMappingParams [0.153, 0.357, 0.231, 0.1573, 0.011, 3.750, 6, 4]; setToneMapping "Filmic";


player_spawn_2 = compile preprocessFileLineNumbers "debug\player_spawn_2.sqf";</code>

##Detailed instructions for editing your init.sqf file (Trigger Version)

*This is what you need to edit YOUR mission init.sqf file, although you could just copy and paste the one provided in this folder...<br/>
*Locate the //Load in Compiled functions and comment out the following line:
call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\variables.sqf";  			//Initilize the Variables (IMPORTANT: Must happen very early)
*and comment it out so it looks like this:
// call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\variables.sqf";				//Initilize the Variables (IMPORTANT: Must happen very early)
*then right underneath it on the next line, add this:
call compile preprocessFileLineNumbers "debug\variables.sqf";				//Initilize the Variables (IMPORTANT: Must happen very early)
Comment out this line:
call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\compiles.sqf";				//Compile regular functions
*Then right underneath add this line:
call compile preprocessFileLineNumbers "debug\compiles.sqf";				//Compile regular functions
*Right after this line:
"filmic" setToneMappingParams [0.153, 0.357, 0.231, 0.1573, 0.011, 3.750, 6, 4]; setToneMapping "Filmic";
*Add this line:
player_spawn_2 = compile preprocessFileLineNumbers "debug\player_spawn_2.sqf";

That's all you need to edit in your init.sqf, after you've made those changes that part of the document should look something like this:

<code>//Load in compiled functions
call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\variables.sqf";				//Initilize the Variables (IMPORTANT: Must happen very early)
progressLoadingScreen 0.1;
call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\publicEH.sqf";				//Initilize the publicVariable event handlers
progressLoadingScreen 0.2;
call compile preprocessFileLineNumbers "\z\addons\dayz_code\medical\setup_functions_med.sqf";	//Functions used by CLIENT for medical
progressLoadingScreen 0.4;
//call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\compiles.sqf";				//Compile regular functions
call compile preprocessFileLineNumbers "debug\compiles.sqf";				//Compile regular functions
progressLoadingScreen 1.0;

"filmic" setToneMappingParams [0.153, 0.357, 0.231, 0.1573, 0.011, 3.750, 6, 4]; setToneMapping "Filmic";

playerstats = compile preprocessFileLineNumbers "debug\playerstats.sqf";</code>




##More Info:

If you want to see what the non-admin debug monitor looks like, then simply ommit your UID from the list.  
Only UID's listed will get the Admin debug monitor. Either SCRL+LCK or the H key should bring it up. 

Any questions or comments about this version to: urbanskaters at gmail dot com

If you feel brave and want to try new variables, then visit (for a list of useful commands): 
http://community.bistudio.com/wiki/Category:Scripting_Commands_ArmA2 <br/>
Unfortunately I can't provide support for any changes you make to this script.  

##Credits:

Credit to P1-Kashwak for letting me modify and republish his original project :)<br/>
The original Project page by P1-Kashwak can be found here: <br/>
http://opendayz.net/index.php?threads/dayz-debug-monitor.8256/

##About Nomadic Hayward:

Hayward is a WordPress consultant, IT Lecturer and Charity Worker living in London.  He calls himself Nomadic
Hayward because that's where his life is heading, he has long since given up doing anything just for the money 
and now focuses on charity work, teaching people how to set up websites for free, tinkering with code and planning 
his escape in 2015 when his Nomadic lifestyle should be well underway.  He believes in open source projects with a 
real passion and feels that people shouldn't need to charge for doing the things they love doing, as this takes away 
from the pleasure of doing it.  He accepts his own faults but dislikes others who can't do the same! 
