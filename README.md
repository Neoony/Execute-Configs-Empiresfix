# Execute-Configs-Empiresfix
Execute configs on specific client count, game events, round start or timeleft.

Original plugin https://forums.alliedmods.net/showpost.php?p=590466&postcount=1
Added version 1.2.3: https://forums.alliedmods.net/showpost.php?p=2148215&postcount=155
Added empires events + readme in executeconfigs showing new commands 1.2.4: https://github.com/Neoony/Execute-Configs-Empiresfix



///////////////////////////////////////////////////////////////////////////////
////////////////////////////////Updated ReadMe////////////////////////////////
///////////////////////////////////////////////////////////////////////////////
//This plugin executes configs when there are either a certain amount of clients 
//on, a certain event occurs, a certain round starts or when there are a certain 
//amount of minutes left on the map. You can use this to disable alltalk above 
//x clients, or to change the map when the timelimit hits, etc. The configs of 
//course go into the cfg folder and the console variables are as follows:
//
//sm_executeconfigs_enabled (0/1, def 1)
//Enable/disable executing configs. The plugin will keep counting the rounds and 
//timeleft when it's disabled, but it will only actually execute the configs when 
//it's enabled.
//
//sm_executeconfigs_include_bots (0/1, def. 1)
//Enable/disable including bots when counting number of clients. This will allow 
//you to disable counting fake clients as normal clients.
//
//sm_executeconfigs_include_spec (0/1, def. 1)
//Enable/disable including spectators when counting number of clients. This will 
//allow you to disable counting spectators as normal clients.
//ADDED: Now also dont count unassigned.
//
//sm_executeconfigs_reload
//Server command to reload the configs from executeconfigs.txt.
//
//Added commands:
//
//sm_executeconfigs_file (def. "executeconfigs.txt")
//File to read the executeconfigs from.
//
//sm_executeconfigs_most_recent_only (0/1, def. 0)
//Enable/disable avoiding of execution previously scheduled configs if the new 
//schedule of the same type (client, map, ...) config appears.
//
//sm_executeconfigs_sched_min_time (def. 0.5)
//The minimal time in seconds between schedules - depends on the longest time 
//needed to execute CFG file. If next CFG execution comes sooner than current CFG 
//is executed it will be skipped. 0.5 seconds is suitable for most cases.
//
//To customize which configs get executed, put the attached executeconfigs.txt 
//in the configs folder. It contains some examples of which I'll explain one here:
//
//Example:
//
//"Configs"
//{
//   "*"
//   {
//       "clients:0"    "10:emptyserver.cfg"
//   }
//}
//
//This means that for all maps, when there are 0 clients on, emptyserver.cfg will 
//get executed after 10 seconds. The delay is for when someone joins within those 10
//seconds, it will look for a config for when there is 1 client on, and if found it 
//will execute that line. If it wasn't found it will continue to execute 
//emptyserver.cfg, so if you're changing the map in emptyserver.cfg, make sure it 
//will stop doing that by creating an empty config for clients:1.
//
//Added empires events (1.2.4)
//switching_to_new_map = Event_GameStart
//commander_elected_player = Event_RoundStart //not the best way, but no other round 
//start event seems to exist
//
