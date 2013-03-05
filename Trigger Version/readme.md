##Detailed instructions for editing your init.sqf file (Trigger Version)

* This is what you need to edit YOUR mission init.sqf file, although you could just copy and paste the one provided in this folder...<br/>
* Comment out this line:<br/>
call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\compiles.sqf";				//Compile regular functionscall<br/>
* So it looks like ths:<br/>
//call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\compiles.sqf";  			//Compile regular functions<br/>
* Then right underneath add this line:<br/>
call compile preprocessFileLineNumbers "debug\compiles.sqf";				//Compile regular functions<br/>
* Right after this line:<br/>
"filmic" setToneMappingParams [0.153, 0.357, 0.231, 0.1573, 0.011, 3.750, 6, 4]; setToneMapping "Filmic";<br/>
* Add this line:<br/>
player_spawn_2 = compile preprocessFileLineNumbers "debug\player_spawn_2.sqf";
<br/><br/>
That's all you need to edit in your init.sqf, after you've made those changes that part of the document should look something like this:
<br/>
<br/>//Load in compiled functions
<br/>call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\variables.sqf";				//Initilize the Variables (IMPORTANT: Must happen very early)
<br/>progressLoadingScreen 0.1;
<br/>call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\publicEH.sqf";				//Initilize the publicVariable event handlers
<br/>progressLoadingScreen 0.2;
<br/>call compile preprocessFileLineNumbers "\z\addons\dayz_code\medical\setup_functions_med.sqf";	//Functions used by CLIENT for mediprogressLoadingScreen 0.4;
<br/>//call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\compiles.sqf";				//Compile regular functions
<br/>call compile preprocessFileLineNumbers "debug\compiles.sqf";				//Compile regular functions
<br/>progressLoadingScreen 1.0;
<br/>
"filmic" setToneMappingParams [0.153, 0.357, 0.231, 0.1573, 0.011, 3.750, 6, 4]; setToneMapping "Filmic";
<br/><br/>
playerstats = compile preprocessFileLineNumbers "debug\playerstats.sqf";
<br/><br/>