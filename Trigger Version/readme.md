##Detailed instructions for editing your init.sqf file (Trigger Version)

* This is what you need to edit YOUR mission init.sqf file, although you could just copy and paste the one provided in this folder...<br/>
* Locate the //Load in Compiled functions line and just below comment out the following line:<br/>
 <code> call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\compiles.sqf";				//Compile regular functionscall</code>
* So it looks like ths:<br/>
 <code> // call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\compiles.sqf";  			//Compile regular functions</code>
* Then right underneath add this line:<br/>
  <code> call compile preprocessFileLineNumbers "debug\compiles.sqf";				//Compile regular functions</code>
* Right after this line:<br/>
  <code> "filmic" setToneMappingParams [0.153, 0.357, 0.231, 0.1573, 0.011, 3.750, 6, 4]; setToneMapping "Filmic";</code>
* Add this line:<br/>
  <code> playerstats = compile preprocessFileLineNumbers "debug\playerstats.sqf";</code>
<br/><br/>
  That's all you need to edit in your init.sqf, after you've made those changes<br/>that part of the document should look something like this:
<br/><pre><code>  //Load in compiled functions
  call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\variables.sqf";				//Initilize the Variables (IMPORTANT: Must happen very early)
  progressLoadingScreen 0.1;
  call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\publicEH.sqf";				//Initilize the publicVariable event handlers
  progressLoadingScreen 0.2;
  call compile preprocessFileLineNumbers "\z\addons\dayz_code\medical\setup_functions_med.sqf";	//Functions used by CLIENT for mediprogressLoadingScreen 0.4;
  //call compile preprocessFileLineNumbers "\z\addons\dayz_code\init\compiles.sqf";				//Compile regular functions
  call compile preprocessFileLineNumbers "debug\compiles.sqf";				//Compile regular functions
   progressLoadingScreen 1.0;
  "filmic" setToneMappingParams [0.153, 0.357, 0.231, 0.1573, 0.011, 3.750, 6, 4]; setToneMapping "Filmic";  
  playerstats = compile preprocessFileLineNumbers "debug\playerstats.sqf";
</code></pre>

<br/><br/>
Don't forget to change your Instance number (at the top of your init file).
<br/><br/>
