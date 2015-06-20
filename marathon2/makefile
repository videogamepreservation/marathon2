### MAKEFILE (Marathon)
### Wednesday, February 9, 1994 6:27:30 PM
### (this is not your fatherÕs makefile)

# Wednesday, February 9, 1994 7:44:27 PM
#	still can't get default dependency rules for .lib or .xcoff libraries to work correctly
#	(the variable {Deps} has an extra object file at the end which doesnÕt exist)
# Thursday, February 10, 1994 9:42:16 PM
#	adapted from jason's makefile from marathon.--ajr
# Monday, March 28, 1994 2:56:12 PM
#   modified to use alain's new buildprogram
# Sunday, April 10, 1994 2:44:05 PM
#	generalized

# --------------------------------------------------------------------------------------
# CONSTANTS
# --------------------------------------------------------------------------------------

# creator type
Creator= 52.4

# every source file should depend on {UbiqDependencies}
UbiqDependencies= makefile buildprogram
Application= marathon2

# directory constants
# ObjPPC and Obj68k are now defined in the buildprogram script
Demos= :demos:
Binaries= :binaries:
Graphics= :graphics:
Source= :

# make our object directories depend on our source directory
"{ObjPPC}" Ä {Source}
"{Obj68k}" Ä {Source}

# --------------------------------------------------------------------------------------
# 68K CONSTANTS
# --------------------------------------------------------------------------------------

Environment68k= -d env68k

Standard68kLibraries= "{Libraries}Runtime.o" "{Libraries}Interface.o" "{CLibraries}StdCLib.o" ¶
	"{CLibraries}CSANELib.o" "{CLibraries}Math.o"
Standard68kLibraries881= "{CLibraries}CLib881.o" "{Libraries}Runtime.o" "{Libraries}Interface.o" ¶
	"{CLibraries}StdCLib.o" "{CLibraries}CSANELib881.o" "{CLibraries}Math881.o"

COptions881= -i "{CSeriesInterfaces}" {VersionCOptions} -opt full -b2 -r -mc68020 -k "{CSeriesLibraries}" -mc68881 -elems881
COptions= -i "{CSeriesInterfaces}" {VersionCOptions} -opt full -b2 -r -mc68020 -k "{CSeriesLibraries}"
AOptions= -i "{CSeriesInterfaces}" -case object {VersionAsmOptions}

# --------------------------------------------------------------------------------------
# 68K DEFAULT DEPENDENCY RULES
# --------------------------------------------------------------------------------------

# default dependency rule for .c.o files

.c.o Ä .c
	C {Default}.c {COptions} -o "{Obj68k}{Default}.c.o"

# default dependency rule for .a.o files
.a.o Ä .a
	Asm {Default}.a {AOptions} -o "{Obj68k}{Default}.a.o"

# default dependency rule for .lib (68k library) files (doesn't work)
#.lib Ä .c.o
#	Lib -o {TargDir}{Default}.lib {Deps}

# --------------------------------------------------------------------------------------
# PPC CONSTANTS
# --------------------------------------------------------------------------------------

EnvironmentPPC= -d envppc

StandardPPCLibraries= "{PPCLibraries}InterfaceLib.xcoff" "{PPCLibraries}MathLib.xcoff" ¶
	"{PPCLibraries}PPCCRuntime.o" "{PPCLibraries}StdCLib.xcoff" "{PPCLibraries}StdCRuntime.o" ¶
	"{PPCLibraries}QuickTimeLib.xcoff"

PPCFinalLinkOptions= -weakLib QuickTimeLib -libRename InterfaceLib.xcoff=InterfaceLib -libRename StdCLib.xcoff=StdCLib -libRename MathLib.xcoff=MathLib -libRename QuickTimeLib.xcoff=QuickTimeLib
PPCCOptions= -i "{CSeriesInterfaces}" {VersionPPCCOptions} -align mac68k -appleext on -dialect ansic -w conformance

# --------------------------------------------------------------------------------------
# PPC DEFAULT DEPENDENCY RULES
# --------------------------------------------------------------------------------------

# default dependency rule for .ppc.o files
.ppc.o Ä .c
	PPCC {Default}.c {PPCCOptions} -o "{ObjPPC}"{Default}.ppc.o 

# default dependency rule for .s.o files
.s.o Ä .s
	PPCAsm {Default}.s -o "{ObjPPC}"{Default}.s.o 

# default dependency rule for .xcoff (ppc library) files (doesn't work)
#.xcoff Ä .o
#	PPCLink -o {TargDir}{Default}.xcoff -xm library {Deps}

#---------------------------------------------------------------------------------------
# DDP Socket Listener Dependencies. (always 68K code, used in 68K and PPC versions)
#---------------------------------------------------------------------------------------
{Obj68k}network_listener.a.o Ä {UbiqDependencies}

# --------------------------------------------------------------------------------------
# 68K OBJECT DEPENDENCIES
# --------------------------------------------------------------------------------------

#render library dependencies
{Obj68k}render.c.o Ä render.h scottish_textures.h textures.h map.h world.h lightsource.h media.h {UbiqDependencies}
{Obj68k}world.c.o Ä world.h {UbiqDependencies}
{Obj68k}textures.c.o Ä textures.h {UbiqDependencies}
{Obj68k}scottish_textures.c.o Ä render.h scottish_textures.h textures.h world.h low_level_textures.c {UbiqDependencies}
{Obj68k}scottish_textures.a.o Ä {UbiqDependencies}
{Obj68k}scottish_textures16.a.o Ä {UbiqDependencies}
{Obj68k}motion_sensor.c.o Ä render.h scottish_textures.h textures.h map.h world.h interface.h motion_sensor.h monsters.h {UbiqDependencies}
{Obj68k}overhead_map.c.o Ä overhead_map.h map.h world.h player.h overhead_map_macintosh.c {UbiqDependencies}

#wad library dependencies
{Obj68k}wad.c.o Ä wad.h tags.h crc.h find_files.h game_errors.h {UbiqDependencies}
{Obj68k}wad_macintosh.c.o Ä wad.h tags.h crc.h find_files.h game_errors.h {UbiqDependencies}
{Obj68k}wad_prefs.c.o Ä wad_prefs.h wad.h game_errors.h {UbiqDependencies}
{Obj68k}wad_prefs_macintosh.c.o Ä wad_prefs.h wad.h game_errors.h {UbiqDependencies}
{Obj68k}find_files.c.o Ä find_files.h {UbiqDependencies}
{Obj68k}crc.c.o Ä crc.h {UbiqDependencies}
{Obj68k}game_errors.c.o Ä game_errors.h {UbiqDependencies}
{Obj68k}files_macintosh.c.o Ä portable_files.h game_errors.h tags.h {UbiqDependencies}

#map library dependencies
{Obj68k}map.c.o Ä map.h world.h interface.h monsters.h projectiles.h effects.h player.h platforms.h sound.h lightsource.h media.h {UbiqDependencies}
{Obj68k}map_constructors.c.o Ä map.h world.h {UbiqDependencies}
{Obj68k}map_accessors.c.o Ä map.h world.h platforms.h {UbiqDependencies}
{Obj68k}game_wad.c.o Ä map.h world.h monsters.h network.h projectiles.h effects.h player.h ¶
	platforms.h flood_map.h scenery.h lightsource.h media.h ":editor code:editor.h" tags.h ¶
	game_wad.h interface.h shell.h game_window.h game_errors.h {UbiqDependencies}
{Obj68k}wad.c.o Ä wad.h tags.h {UbiqDependencies}
{Obj68k}flood_map.c.o Ä map.h world.h flood_map.h {UbiqDependencies}
{Obj68k}lightsource.c.o Ä map.h world.h lightsource.h {UbiqDependencies}
{Obj68k}media.c.o Ä map.h world.h media.h media_definitions.h lightsource.h {UbiqDependencies}
{Obj68k}platforms.c.o Ä map.h world.h platforms.h platform_definitions.h lightsource.h sound.h {UbiqDependencies}
{Obj68k}placement.c.o Ä map.h monsters.h {UbiqDependencies}

#shell library dependencies
{Obj68k}shell.c.o Ä map.h world.h monsters.h player.h render.h shell.h interface.h sound.h ¶
	music.h fades.h tags.h network_sound.h mouse.h screen_drawing.h computer_interface.h ¶
	game_wad.h game_window.h {UbiqDependencies}
{Obj68k}shapes.c.o Ä shell.h interface.h shapes_macintosh.c {UbiqDependencies}
{Obj68k}screen.c.o Ä interface.h map.h world.h render.h scottish_textures.h textures.h shell.h monsters.h overhead_map.h player.h valkyrie.h game_window.h {UbiqDependencies}
{Obj68k}screen.a.o Ä {UbiqDependencies}
{ObjPPC}valkyrie.c.o Ä valkyrie.h textures.h {UbiqDependencies}
{Obj68k}vbl_macintosh.c.o Ä interface.h map.h world.h shell.h player.h mouse.h key_definitions.h {UbiqDependencies}
{Obj68k}sound.c.o Ä interface.h shell.h sound.h sound_definitions.h sound_macintosh.c {UbiqDependencies}
{Obj68k}preprocess_map_mac.c.o Ä map.h world.h ":editor code:editor.h" interface.h shell.h game_wad.h ¶
	overhead_map.h player.h game_window.h tags.h wad.h {UbiqDependencies}
{Obj68k}screen_drawing.c.o Ä interface.h map.h shell.h screen_drawing.h {UbiqDependencies}
{Obj68k}game_dialogs.c.o Ä interface.h world.h shell.h music.h {UbiqDependencies}
{Obj68k}game_window_macintosh.c.o Ä map.h world.h interface.h player.h screen_drawing.h motion_sensor.h ¶
	sound.h items.h weapons.h game_window.h {UbiqDependencies}
{Obj68k}interface_macintosh.c.o Ä map.h macintosh_network.h shell.h interface.h player.h network_sound.h ¶
	screen_drawing.h sound.h fades.h game_window.h game_errors.h {UbiqDependencies}
{Obj68k}mouse.c.o Ä mouse.h world.h player.h map.h {UbiqDependencies}
{Obj68k}computer_interface.c.o Ä screen_drawing.h computer_interface.h interface.h shell.h map.h overhead_map.h {UbiqDependencies}
{Obj68k}music.c.o Ä music.h shell.h {UbiqDependencies}
{Obj68k}keyboard_dialog.c.o Ä interface.h {UbiqDependencies}
{Obj68k}images.c.o Ä images.h interface.h map.h {UbiqDependencies}
{Obj68k}preferences.c.o Ä map.h world.h shell.h interface.h sound.h preferences.h ¶
	wad.h wad_prefs.h tags.h {UbiqDependencies}

#network library dependencies
{Obj68k}network_games.c.o Ä map.h items.h player.h monsters.h network_games.h {UbiqDependencies}
{Obj68k}network.c.o Ä map.h interface.h network.h macintosh_network.h game_errors.h {UbiqDependencies}
{Obj68k}network_stream.c.o Ä network.h macintosh_network.h network_stream.h {UbiqDependencies}
{Obj68k}network_dialogs.c.o Ä network.h macintosh_network.h player.h map.h shell.h interface.h screen_drawing.h {UbiqDependencies}
{Obj68k}network_names.c.o Ä network.h macintosh_network.h {UbiqDependencies}
{Obj68k}network_adsp.c.o Ä network.h macintosh_network.h {UbiqDependencies}
{Obj68k}network_ddp.c.o Ä network.h macintosh_network.h {UbiqDependencies}
{Obj68k}network_lookup.c.o Ä network.h macintosh_network.h {UbiqDependencies}
{Obj68k}network_microphone.c.o Ä shell.h network.h network_sound.h {UbiqDependencies}
{Obj68k}network_speaker.c.o Ä network_sound.h {UbiqDependencies}
{Obj68k}network_modem.c.o Ä network.h macintosh_network.h network_modem.h {UbiqDependencies}
{Obj68k}network_modem_protocol.c.o Ä network_modem.h game_errors.h map.h interface.h {UbiqDependencies}
{Obj68k}progress.c.o Ä progress.h {UbiqDependencies}

#game library dependencies
{Obj68k}{Application}.c.o Ä map.h world.h render.h interface.h flood_map.h effects.h monsters.h projectiles.h player.h ¶
	scottish_textures.h textures.h monsters.h projectiles.h effects.h flood_map.h player.h ¶
	network.h scenery.h platforms.h lightsource.h media.h music.h fades.h items.h weapons.h game_window.h {UbiqDependencies}
{Obj68k}player.c.o Ä map.h world.h player.h monsters.h interface.h sound.h fades.h media.h items.h ¶
	weapons.h game_window.h {UbiqDependencies}
{Obj68k}pathfinding.c.o Ä map.h world.h flood_map.h {UbiqDependencies}
{Obj68k}monsters.c.o Ä monster_definitions.h render.h scottish_textures.h textures.h map.h world.h interface.h monsters.h projectiles.h effects.h player.h platforms.h sound.h {UbiqDependencies}
{Obj68k}scenery.c.o Ä scenery_definitions.h scenery.h map.h world.h {UbiqDependencies}
{Obj68k}projectiles.c.o Ä projectile_definitions.h render.h scottish_textures.h textures.h map.h world.h interface.h monsters.h projectiles.h effects.h media.h {UbiqDependencies}
{Obj68k}effects.c.o Ä effect_definitions.h render.h scottish_textures.h textures.h map.h world.h interface.h effects.h {UbiqDependencies}
{Obj68k}devices.c.o Ä map.h world.h monsters.h interface.h player.h platforms.h sound.h ¶
	computer_interface.h music.h lightsource.h game_window.h {UbiqDependencies}
{Obj68k}weapons.c.o Ä map.h world.h projectiles.h player.h weapons.h sound.h interface.h ¶
	items.h monsters.h game_window.h weapon_definitions.h {UbiqDependencies}
{Obj68k}items.c.o Ä map.h world.h interface.h monsters.h player.h sound.h platforms.h ¶
	fades.h items.h flood_map.h effects.h game_window.h item_definitions.h weapons.h {UbiqDependencies}
{Obj68k}physics.c.o Ä physics_models.h render.h scottish_textures.h textures.h map.h world.h monsters.h player.h {UbiqDependencies}
{Obj68k}vbl.c.o Ä interface.h map.h world.h shell.h player.h mouse.h key_definitions.h {UbiqDependencies}
{Obj68k}interface.c.o Ä map.h macintosh_network.h shell.h interface.h player.h network_sound.h ¶
	screen_drawing.h sound.h fades.h game_window.h game_errors.h {UbiqDependencies}
{Obj68k}game_window.c.o Ä map.h world.h interface.h player.h screen_drawing.h motion_sensor.h ¶
	sound.h items.h weapons.h game_window.h {UbiqDependencies}
{Obj68k}fades.c.o Ä interface.h shell.h {UbiqDependencies}
{Obj68k}import_definitions.c.o Ä wad.h extensions.h shell.h {UbiqDependencies}

# --------------------------------------------------------------------------------------
# 68K LIBRARY DEPENDENCIES
# --------------------------------------------------------------------------------------

RenderLibObjects68k= {Obj68k}render.c.o {Obj68k}world.c.o {Obj68k}textures.c.o ¶
	{Obj68k}scottish_textures.c.o {Obj68k}overhead_map.c.o {Obj68k}motion_sensor.c.o ¶
	{Obj68k}scottish_textures.a.o {Obj68k}scottish_textures16.a.o
WadLibObjects68k= {Obj68k}wad.c.o {Obj68k}wad_macintosh.c.o {Obj68k}crc.c.o {Obj68k}find_files.c.o ¶
	{Obj68k}wad_prefs.c.o {Obj68k}wad_prefs_macintosh.c.o {Obj68k}game_errors.c.o {Obj68k}files_macintosh.c.o
MapLibObjects68k= {Obj68k}map.c.o {Obj68k}lightsource.c.o {Obj68k}flood_map.c.o {Obj68k}media.c.o ¶
	{Obj68k}platforms.c.o {Obj68k}map_accessors.c.o {Obj68k}map_constructors.c.o {Obj68k}game_wad.c.o {Obj68k}wad.c.o ¶
	{Obj68k}placement.c.o
ShellLibObjects68k= {Obj68k}shell.c.o {Obj68k}screen.c.o {Obj68k}valkyrie.c.o {Obj68k}screen.a.o ¶
	{Obj68k}shapes.c.o {Obj68k}sound.c.o {Obj68k}preprocess_map_mac.c.o {Obj68k}game_dialogs.c.o ¶
	{Obj68k}game_window_macintosh.c.o {Obj68k}interface_macintosh.c.o {Obj68k}vbl_macintosh.c.o ¶
	{Obj68k}screen_drawing.c.o {Obj68k}mouse.c.o {Obj68k}computer_interface.c.o ¶
	{Obj68k}music.c.o {Obj68k}preferences.c.o {Obj68k}keyboard_dialog.c.o {Obj68k}images.c.o
GameLibObjects68k= {Obj68k}{Application}.c.o {Obj68k}devices.c.o {Obj68k}monsters.c.o ¶
	{Obj68k}player.c.o {Obj68k}pathfinding.c.o {Obj68k}weapons.c.o {Obj68k}items.c.o ¶
	{Obj68k}physics.c.o {Obj68k}projectiles.c.o {Obj68k}effects.c.o {Obj68k}scenery.c.o ¶
	{Obj68k}fades.c.o {Obj68k}game_window.c.o {Obj68k}interface.c.o {Obj68k}vbl.c.o ¶
	{Obj68k}import_definitions.c.o
NetworkLibObjects68k= {Obj68k}network_dialogs.c.o {Obj68k}network_names.c.o {Obj68k}network_adsp.c.o ¶
	{Obj68k}network_ddp.c.o {Obj68k}network_lookup.c.o {Obj68k}network.c.o ¶
	{Obj68k}network_microphone.c.o {Obj68k}network_speaker.c.o {Obj68k}network_games.c.o ¶
	{Obj68k}network_stream.c.o {Obj68k}network_modem.c.o {Obj68k}network_modem_protocol.c.o ¶
	{Obj68k}progress.c.o

"{Obj68k}"render.lib Ä {RenderLibObjects68k}
	Lib -o "{Obj68k}"render.lib {Deps}
"{Obj68k}"wad.lib Ä {WadLibObjects68k}
	Lib -o "{Obj68k}"wad.lib {Deps}
"{Obj68k}"map.lib Ä {MapLibObjects68k}
	Lib -o "{Obj68k}"map.lib {Deps}
"{Obj68k}"shell.lib Ä {ShellLibObjects68k}
	Lib -o "{Obj68k}"shell.lib {Deps}
"{Obj68k}"game.lib Ä {GameLibObjects68k}
	Lib -o "{Obj68k}"game.lib {Deps}
"{Obj68k}"network.lib Ä {NetworkLibObjects68k}
	Lib -o "{Obj68k}"network.lib {Deps}

# --------------------------------------------------------------------------------------
# 68K APPLICATION DEPENDENCIES AND BUILD COMMANDS
# --------------------------------------------------------------------------------------

ApplicationLibraries68k = "{Obj68k}"shell.lib "{Obj68k}"map.lib "{Obj68k}"render.lib ¶
	"{Obj68k}"game.lib "{Obj68k}"wad.lib "{Obj68k}"network.lib {CSeriesLibraries68k}
RezDependencies68k= {Application}.r "{Binaries}"{Application}.resource {UbiqDependencies} ¶
	"{Demos}"demos.resource "{Graphics}demo.screens" ¶
	"{Graphics}game.screens"
LinkDependencies68k= {ApplicationLibraries68k}

{Targ68k} ÄÄ {RezDependencies68k}
	Rez {Application}.r {Environment68k} {VerRezOptions} -append -o {Targ68k}
{Targ68k} ÄÄ {LinkDependencies68k}
	Link {Link68kOptions} -w -t APPL -c "{Creator}" {ApplicationLibraries68k} {Standard68kLibraries} -o {Targ68k} > link.out
{Targ68k} ÄÄ {Obj68k}network_listener.a.o
	Link  -rt SOCK=128 -m TheSocketListener -sg "socket_listener" ¶
		"{Obj68k}"network_listener.a.o -o {Targ68k}
	SetFile -a iB {Targ68k}
{Application} ÄÄ {RezDependencies68k} {LinkDependencies68k}
	noresnames {Application}
{Application}.gamma ÄÄ {RezDependencies68k} {LinkDependencies68k}
	noresnames {Application}.gamma

# --------------------------------------------------------------------------------------
# 68K DEMO APPLICATION DEPENDENCIES AND BUILD COMMANDS
# --------------------------------------------------------------------------------------

{DemoTarg68k} ÄÄ {RezDependencies68k}
	Rez "{Application}.r" {Environment68k} {VerRezOptions} -append -o {DemoTarg68k}
{DemoTarg68k} ÄÄ {LinkDependencies68k}
	Link -w -t APPL -c "{Creator}" {ApplicationLibraries68k} {Standard68kLibraries} -o {DemoTarg68k}
{DemoTarg68k} ÄÄ {Obj68k}network_listener.a.o
	Link  -rt SOCK=128 -m TheSocketListener -sg "socket_listener" ¶
		"{Obj68k}"network_listener.a.o -o {DemoTarg68k}
	SetFile -a iB {DemoTarg68k}
{Application}.demo ÄÄ {RezDependencies68k} {LinkDependencies68k}
	noresnames {Application}.demo

# --------------------------------------------------------------------------------------
# PPC OBJECT DEPENDENCIES
# --------------------------------------------------------------------------------------

#render library dependencies
{ObjPPC}render.ppc.o Ä render.h scottish_textures.h textures.h map.h world.h lightsource.h media.h {UbiqDependencies}
{ObjPPC}world.ppc.o Ä world.h {UbiqDependencies}
{ObjPPC}textures.ppc.o Ä textures.h {UbiqDependencies}
{ObjPPC}scottish_textures.ppc.o Ä render.h scottish_textures.h textures.h world.h {UbiqDependencies}
{ObjPPC}motion_sensor.ppc.o Ä render.h scottish_textures.h textures.h map.h world.h interface.h motion_sensor.h monsters.h screen_drawing.h {UbiqDependencies}
{ObjPPC}overhead_map.ppc.o Ä overhead_map.h map.h world.h player.h overhead_map_macintosh.c {UbiqDependencies}

#wad library dependencies
{ObjPPC}wad.ppc.o Ä find_files.h crc.h wad.h tags.h game_errors.h {UbiqDependencies}
{ObjPPC}wad_macintosh.ppc.o Ä find_files.h crc.h wad.h tags.h game_errors.h {UbiqDependencies}
{ObjPPC}wad_prefs.ppc.o Ä wad_prefs.h wad.h game_errors.h {UbiqDependencies}
{ObjPPC}wad_prefs_macintosh.ppc.o Ä wad_prefs.h wad.h game_errors.h {UbiqDependencies}
{ObjPPC}crc.ppc.o Ä crc.h {UbiqDependencies}
{ObjPPC}find_files.ppc.o Ä find_files.h {UbiqDependencies}
{ObjPPC}game_errors.ppc.o Ä game_errors.h {UbiqDependencies}
{ObjPPC}files_macintosh.ppc.o Ä portable_files.h game_errors.h tags.h {UbiqDependencies}

#map library dependencies
{ObjPPC}map.ppc.o Ä map.h world.h interface.h monsters.h projectiles.h effects.h player.h platforms.h sound.h lightsource.h media.h {UbiqDependencies}
{ObjPPC}map_constructors.ppc.o Ä map.h world.h {UbiqDependencies}
{ObjPPC}map_accessors.ppc.o Ä map.h world.h platforms.h {UbiqDependencies}
{ObjPPC}game_wad.ppc.o Ä map.h world.h monsters.h network.h projectiles.h effects.h player.h ¶
	platforms.h flood_map.h scenery.h lightsource.h media.h ":editor code:editor.h" tags.h ¶
	game_wad.h interface.h shell.h game_window.h game_errors.h {UbiqDependencies}
{ObjPPC}flood_map.ppc.o Ä map.h world.h flood_map.h {UbiqDependencies}
{ObjPPC}lightsource.ppc.o Ä map.h world.h lightsource.h {UbiqDependencies}
{ObjPPC}media.ppc.o Ä map.h world.h media.h media_definitions.h lightsource.h {UbiqDependencies}
{ObjPPC}platforms.ppc.o Ä map.h world.h platforms.h platform_definitions.h lightsource.h sound.h {UbiqDependencies}
{ObjPPC}placement.ppc.o Ä map.h monsters.h {UbiqDependencies}

#shell library dependencies
{ObjPPC}shell.ppc.o Ä map.h world.h monsters.h player.h render.h shell.h interface.h sound.h ¶
	music.h fades.h tags.h network_sound.h mouse.h screen_drawing.h computer_interface.h ¶
	game_wad.h game_window.h {UbiqDependencies}
{ObjPPC}shapes.ppc.o Ä shell.h interface.h shapes_macintosh.c {UbiqDependencies}
{ObjPPC}screen.ppc.o Ä interface.h map.h world.h render.h scottish_textures.h textures.h shell.h monsters.h overhead_map.h player.h valkyrie.h game_window.h {UbiqDependencies}
{ObjPPC}quadruple.s.o Ä {UbiqDependencies}
{ObjPPC}valkyrie.ppc.o Ä valkyrie.h textures.h {UbiqDependencies}
{ObjPPC}sound.ppc.o Ä interface.h shell.h sound.h sound_definitions.h sound_macintosh.c {UbiqDependencies}
{ObjPPC}preprocess_map_mac.ppc.o Ä map.h world.h ":editor code:editor.h" interface.h shell.h game_wad.h ¶
	overhead_map.h player.h game_window.h tags.h wad.h {UbiqDependencies}
{ObjPPC}game_dialogs.ppc.o Ä interface.h world.h shell.h music.h {UbiqDependencies}
{ObjPPC}screen_drawing.ppc.o Ä interface.h map.h shell.h screen_drawing.h {UbiqDependencies}
{ObjPPC}game_window_macintosh.ppc.o Ä map.h world.h interface.h player.h screen_drawing.h motion_sensor.h ¶
	sound.h items.h weapons.h game_window.h {UbiqDependencies}
{ObjPPC}images.ppc.o Ä images.h interface.h map.h {UbiqDependencies}
{ObjPPC}mouse.ppc.o Ä mouse.h world.h player.h map.h {UbiqDependencies}
{ObjPPC}computer_interface.ppc.o Ä screen_drawing.h computer_interface.h interface.h shell.h map.h overhead_map.h {UbiqDependencies}
{ObjPPC}music.ppc.o Ä music.h shell.h {UbiqDependencies}
{ObjPPC}keyboard_dialog.ppc.o Ä interface.h {UbiqDependencies}
{ObjPPC}preferences.ppc.o Ä map.h world.h shell.h interface.h sound.h preferences.h ¶
	wad.h wad_prefs.h tags.h {UbiqDependencies}
{ObjPPC}vbl_macintosh.ppc.o Ä interface.h map.h world.h shell.h player.h mouse.h key_definitions.h {UbiqDependencies}
{ObjPPC}interface_macintosh.ppc.o Ä map.h macintosh_network.h shell.h interface.h player.h network_sound.h ¶
	screen_drawing.h sound.h fades.h game_window.h game_errors.h {UbiqDependencies}

#network library dependencies
{ObjPPC}network_games.ppc.o Ä map.h items.h player.h monsters.h network_games.h {UbiqDependencies}
{ObjPPC}network.ppc.o Ä network.h macintosh_network.h game_errors.h {UbiqDependencies}
{ObjPPC}network_stream.ppc.o Ä network.h macintosh_network.h network_stream.h {UbiqDependencies}
{ObjPPC}network_dialogs.ppc.o Ä network.h macintosh_network.h shell.h map.h player.h interface.h screen_drawing.h {UbiqDependencies}
{ObjPPC}network_names.ppc.o Ä network.h macintosh_network.h {UbiqDependencies}
{ObjPPC}network_adsp.ppc.o Ä network.h macintosh_network.h {UbiqDependencies}
{ObjPPC}network_ddp.ppc.o Ä network.h macintosh_network.h {UbiqDependencies}
{ObjPPC}network_lookup.ppc.o Ä network.h macintosh_network.h {UbiqDependencies}
{ObjPPC}network_microphone.ppc.o Ä shell.h network.h network_sound.h {UbiqDependencies}
{ObjPPC}network_speaker.ppc.o Ä network_sound.h {UbiqDependencies}
{ObjPPC}network_modem.ppc.o Ä network.h macintosh_network.h network_modem.h {UbiqDependencies}
{ObjPPC}network_modem_protocol.ppc.o Ä network_modem.h game_errors.h map.h interface.h {UbiqDependencies}
{ObjPPC}progress.ppc.o Ä progress.h {UbiqDependencies}

#game library dependencies
{ObjPPC}{Application}.ppc.o Ä map.h world.h render.h interface.h flood_map.h effects.h monsters.h projectiles.h player.h ¶
	scottish_textures.h textures.h monsters.h projectiles.h effects.h flood_map.h player.h ¶
	network.h scenery.h platforms.h lightsource.h media.h music.h fades.h items.h weapons.h game_window.h {UbiqDependencies}
{ObjPPC}player.ppc.o Ä map.h world.h player.h monsters.h interface.h sound.h fades.h media.h items.h ¶
	weapons.h game_window.h {UbiqDependencies}
{ObjPPC}pathfinding.ppc.o Ä map.h world.h flood_map.h {UbiqDependencies}
{ObjPPC}monsters.ppc.o Ä monster_definitions.h render.h scottish_textures.h textures.h map.h world.h interface.h monsters.h projectiles.h effects.h player.h platforms.h sound.h {UbiqDependencies}
{ObjPPC}scenery.ppc.o Ä scenery_definitions.h scenery.h map.h world.h {UbiqDependencies}
{ObjPPC}projectiles.ppc.o Ä projectile_definitions.h render.h scottish_textures.h textures.h map.h world.h interface.h monsters.h projectiles.h effects.h media.h {UbiqDependencies}
{ObjPPC}effects.ppc.o Ä effect_definitions.h render.h scottish_textures.h textures.h map.h world.h interface.h effects.h {UbiqDependencies}
{ObjPPC}devices.ppc.o Ä map.h world.h monsters.h interface.h player.h platforms.h sound.h ¶
	computer_interface.h music.h lightsource.h game_window.h {UbiqDependencies}
{ObjPPC}weapons.ppc.o Ä map.h world.h projectiles.h player.h weapons.h sound.h interface.h ¶
	items.h monsters.h game_window.h weapon_definitions.h {UbiqDependencies}
{ObjPPC}items.ppc.o Ä map.h world.h interface.h monsters.h player.h sound.h platforms.h ¶
	fades.h items.h flood_map.h effects.h game_window.h item_definitions.h weapons.h {UbiqDependencies}
{ObjPPC}physics.ppc.o Ä physics_models.h render.h scottish_textures.h textures.h map.h world.h player.h {UbiqDependencies}
{ObjPPC}vbl.ppc.o Ä interface.h map.h world.h shell.h player.h mouse.h key_definitions.h {UbiqDependencies}
{ObjPPC}interface.ppc.o Ä map.h shell.h interface.h player.h ¶
	screen_drawing.h sound.h fades.h game_window.h game_errors.h {UbiqDependencies}
{ObjPPC}game_window.ppc.o Ä map.h world.h interface.h player.h screen_drawing.h motion_sensor.h ¶
	sound.h items.h weapons.h game_window.h {UbiqDependencies}
{ObjPPC}fades.ppc.o Ä interface.h shell.h {UbiqDependencies}
{ObjPPC}import_definitions.ppc.o Ä extensions.h wad.h {UbiqDependencies}

# --------------------------------------------------------------------------------------
# PPC LIBRARY DEPENDENCIES
# --------------------------------------------------------------------------------------

RenderLibObjectsPPC= {ObjPPC}render.ppc.o {ObjPPC}world.ppc.o {ObjPPC}textures.ppc.o ¶
	{ObjPPC}scottish_textures.ppc.o {ObjPPC}overhead_map.ppc.o {ObjPPC}motion_sensor.ppc.o
WadLibObjectsPPC= {ObjPPC}wad.ppc.o {ObjPPC}wad_macintosh.ppc.o {ObjPPC}find_files.ppc.o {ObjPPC}crc.ppc.o ¶
	{ObjPPC}wad_prefs.ppc.o {ObjPPC}wad_prefs_macintosh.ppc.o {ObjPPC}game_errors.ppc.o ¶
	{ObjPPC}files_macintosh.ppc.o
MapLibObjectsPPC= {ObjPPC}map.ppc.o {ObjPPC}lightsource.ppc.o {ObjPPC}flood_map.ppc.o {ObjPPC}media.ppc.o ¶
	{ObjPPC}platforms.ppc.o {ObjPPC}map_accessors.ppc.o {ObjPPC}map_constructors.ppc.o {ObjPPC}game_wad.ppc.o ¶
	{ObjPPC}placement.ppc.o
ShellLibObjectsPPC= {ObjPPC}shell.ppc.o {ObjPPC}screen.ppc.o {ObjPPC}quadruple.s.o ¶
	{ObjPPC}valkyrie.ppc.o {ObjPPC}shapes.ppc.o ¶
	{ObjPPC}sound.ppc.o {ObjPPC}preprocess_map_mac.ppc.o {ObjPPC}game_dialogs.ppc.o ¶
	{ObjPPC}game_window_macintosh.ppc.o {ObjPPC}interface_macintosh.ppc.o {ObjPPC}vbl_macintosh.ppc.o ¶
	{ObjPPC}screen_drawing.ppc.o {ObjPPC}mouse.ppc.o {ObjPPC}computer_interface.ppc.o ¶
	{ObjPPC}music.ppc.o {ObjPPC}preferences.ppc.o {ObjPPC}keyboard_dialog.ppc.o {ObjPPC}images.ppc.o
GameLibObjectsPPC= {ObjPPC}{Application}.ppc.o {ObjPPC}devices.ppc.o {ObjPPC}monsters.ppc.o ¶
	{ObjPPC}player.ppc.o {ObjPPC}pathfinding.ppc.o {ObjPPC}weapons.ppc.o {ObjPPC}items.ppc.o ¶
	{ObjPPC}physics.ppc.o {ObjPPC}projectiles.ppc.o {ObjPPC}effects.ppc.o {ObjPPC}scenery.ppc.o ¶
	{ObjPPC}fades.ppc.o {ObjPPC}game_window.ppc.o {ObjPPC}interface.ppc.o {ObjPPC}vbl.ppc.o ¶
	{ObjPPC}import_definitions.ppc.o
NetworkLibObjectsPPC= {ObjPPC}network_dialogs.ppc.o {ObjPPC}network_names.ppc.o {ObjPPC}network_adsp.ppc.o ¶
	{ObjPPC}network_ddp.ppc.o {ObjPPC}network_lookup.ppc.o {ObjPPC}network.ppc.o ¶
	{ObjPPC}network_microphone.ppc.o {ObjPPC}network_speaker.ppc.o {ObjPPC}network_games.ppc.o ¶
	{ObjPPC}network_stream.ppc.o {ObjPPC}network_modem.ppc.o {ObjPPC}network_modem_protocol.ppc.o ¶
	{ObjPPC}progress.ppc.o

"{ObjPPC}"render.xcoff Ä {RenderLibObjectsPPC}
	PPCLink -o "{ObjPPC}"render.xcoff {SymbolsPPC} -xm library {Deps}
"{ObjPPC}"wad.xcoff Ä {WadLibObjectsPPC}
	PPCLink -o "{ObjPPC}"wad.xcoff {SymbolsPPC} -xm library {Deps}
"{ObjPPC}"map.xcoff Ä {MapLibObjectsPPC}
	PPCLink -o "{ObjPPC}"map.xcoff {SymbolsPPC} -xm library {Deps}
"{ObjPPC}"shell.xcoff Ä {ShellLibObjectsPPC}
	PPCLink -o "{ObjPPC}"shell.xcoff {SymbolsPPC} -xm library {Deps}
"{ObjPPC}"game.xcoff Ä {GameLibObjectsPPC}
	PPCLink -o "{ObjPPC}"game.xcoff {SymbolsPPC} -xm library {Deps}
"{ObjPPC}"network.xcoff Ä {NetworkLibObjectsPPC}
	PPCLink -o "{ObjPPC}"network.xcoff {SymbolsPPC} -xm library {Deps}

# --------------------------------------------------------------------------------------
# PPC APPLICATION DEPENDENCIES AND BUILD COMMANDS
# --------------------------------------------------------------------------------------

ApplicationLibrariesPPC= "{ObjPPC}"render.xcoff "{ObjPPC}"map.xcoff "{ObjPPC}"wad.xcoff ¶
	"{ObjPPC}"shell.xcoff "{ObjPPC}"game.xcoff "{ObjPPC}"network.xcoff {CSeriesLibrariesPPC}
RezDependenciesPPC= {Application}.r "{Binaries}{Application}.resource" {UbiqDependencies} ¶
	"{Demos}"demos.resource "{Graphics}demo.screens" ¶
	"{Graphics}game.screens"
LinkDependenciesPPC= {ApplicationLibrariesPPC}

{TargPPC} ÄÄ {RezDependenciesPPC}
	Rez {Application}.r {EnvironmentPPC} {VerRezOptions} -append -o {TargPPC}
{TargPPC} ÄÄ {LinkDependenciesPPC}
	PPCLink {ApplicationLibrariesPPC} {StandardPPCLibraries} {SymbolsPPC} {PPCFinalLinkOptions} -o "{TargPPC}"
	MergeFragment {CSeriesLibraries}DisplayLib.runtime "{TargPPC}"
#	MakePef "{ObjPPC}"{TargPPC}.xcoff -o {TargPPC} {MakePefOptions}
	SetFile -t APPL -c "{Creator}" -a iB {TargPPC}
{TargPPC} ÄÄ {Obj68k}network_listener.a.o
	Link  -rt SOCK=128 -m TheSocketListener -sg "socket_listener" ¶
		"{Obj68k}"network_listener.a.o -o {TargPPC}
{Application}.alpha.ppc ÄÄ {LinkDependenciesPPC}
	MakeSym -i ::cseries.lib {SymbolsPPC} -o "{TargPPC}.xSYM" "{ObjPPC}{TargPPC}.xcoff"
{Application}.ppc ÄÄ {RezDependenciesPPC} {LinkDependenciesPPC}
	noresnames {Application}.ppc
{Application}.gamma.ppc ÄÄ {RezDependencies68k} {LinkDependencies68k}
	noresnames {Application}.gamma.ppc

# --------------------------------------------------------------------------------------
# PPC DEMO APPLICATION DEPENDENCIES AND BUILD COMMANDS
# --------------------------------------------------------------------------------------

{DemoTargPPC} ÄÄ {RezDependenciesPPC}
	Rez {Application}.r {EnvironmentPPC} {VerRezOptions} -append -o {DemoTargPPC}
{DemoTargPPC} ÄÄ {LinkDependenciesPPC}
	PPCLink {ApplicationLibrariesPPC} {StandardPPCLibraries} {SymbolsPPC} {PPCFinalLinkOptions} -o "{DemoTargPPC}"
	MergeFragment {CSeriesLibraries}DisplayLib.runtime "{DemoTargPPC}"
#	MakePef "{ObjPPC}{DemoTargPPC}.xcoff" -o {DemoTargPPC} {MakePefOptions}
	SetFile -t APPL -c "{Creator}" -a iB {DemoTargPPC}
{DemoTargPPC} ÄÄ {Obj68k}network_listener.a.o
	Link  -rt SOCK=128 -m TheSocketListener -sg "socket_listener" ¶
		"{Obj68k}"network_listener.a.o -o {DemoTargPPC}
{Application}.demo.alpha.ppc ÄÄ {LinkDependenciesPPC}
	MakeSym -i ::cseries.lib {SymbolsPPC} -o {DemoTargPPC}.xSYM "{ObjPPC}{DemoTargPPC}.xcoff"
{Application}.demo.ppc ÄÄ {RezDependenciesPPC} {LinkDependenciesPPC}
	noresnames {Application}.demo.ppc

# --------------------------------------------------------------------------------------
# FAT APPLICATION DEPENDENCIES AND BUILD COMMANDS
# --------------------------------------------------------------------------------------

{FatTarg} Ä {TargPPC} {Targ68k}
	Duplicate -y {TargPPC} {FatTarg}
	Rez {Application}.r {EnvironmentPPC} -d fat -d CODE_FILE=¶"{Targ68k}¶" {VerRezOptions} -append -o {FatTarg}

# --------------------------------------------------------------------------------------
# FAT DEMO APPLICATION DEPENDENCIES AND BUILD COMMANDS
# --------------------------------------------------------------------------------------

{DemoFatTarg} Ä {DemoTargPPC} {DemoTarg68k}
	Duplicate -y {DemoTargPPC} {DemoFatTarg}
	Rez {Application}.r {EnvironmentPPC} -d fat -d CODE_FILE=¶"{DemoTarg68k}¶" {VerRezOptions} -append -o {DemoFatTarg}
