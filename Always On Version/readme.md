##Detailed instructions for editing your init.sqf (Always on Version)

* This is what you need to edit in YOUR mission init.sqf file, although you could just copy and paste the one provided in this folder...<br/>
* Locate the //Load in Compiled functions and just below comment out the following line:<br/>
<code> call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\variables.sqf";  			//Initilize the Variables (IMPORTANT: Must happen very early)</code>
* so it looks like this:<br/>
<code> // call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\variables.sqf";				//Initilize the Variables (IMPORTANT: Must happen very early)</code>
* then right underneath it on the next line, add this:<br/>
<code> call compile preprocessFileLineNumbers "debug\variables.sqf";				//Initilize the Variables (IMPORTANT: Must happen very early)</code>
* Now comment out this line:<br/>
<code> call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\compiles.sqf";				//Compile regular functions</code>
* Then right underneath add this line:<br/>
<code> call compile preprocessFileLineNumbers "debug\compiles.sqf";				//Compile regular functions</code>
* Right after this line:<br/>
<code> "filmic" setToneMappingParams [0.153, 0.357, 0.231, 0.1573, 0.011, 3.750, 6, 4]; setToneMapping "Filmic";</code>
* Add this line:<br/>
<code> player_spawn_2 = compile preprocessFileLineNumbers "debug\player_spawn_2.sqf";</code>
<br/><br/>
That's all you need to edit in your init.sqf, after you've made those changes<br/>
that part of the document should look something like this:
<br/><br/>
<pre><code> //Load in compiled functions
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
  player_spawn_2 = compile preprocessFileLineNumbers "debug\player_spawn_2.sqf";</code></pre>

<br/><br/>
Don't forget to change your Instance number (at the top of your init file).
<br/><br/>
