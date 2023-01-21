# tHotBar
tHotBar is an interface for binding and visualizing macros more easily.  It uses visual elements to display as much information as possible, and is highly customizable in appearance.

## How To Install
Download the release zip for the Ashita client version you are currently using.  Extract directly to your Ashita directory(the folder with ashita-cli.exe in it!).  Everything should fall into place.  If you feel you've messed that up, the required components are a plugin named 'tRenderer.dll' in your plugins folder, and a folder named 'tHotBar' in your addons folder.  If you need to build tRenderer yourself for a different client version, or simply don't trust foreign dlls, you can access the source at:<br>
https://github.com/ThornyFFXI/tHotBar

## How To Load
You must load the plugin tRenderer with **/load trenderer** prior to loading the addon tHotBar with **/addon load tHotBar**.  If you place these in your autoload file, you must ensure that both addons itself and trenderer are loaded prior to loading tHotBar.

## How To Use
Upon initial login, you can type **/tb** to open a configuration window and choose the layout and options that best fit your needs.  The GUI makes this very straightforward.  At present, tHotBar ships with ~500p wide, ~750p wide, and ~1000p layouts, each with a 10x2 or 10x3 macro option.  Once you are satisfied with your layout, you can hold ctrl and click any of the squares to make the binding menu appear for that square.  All bindings are automatically saved as soon as you bind them, and palette/job bindings are automatically loaded when you change to that job.

## Binding Scope
Most of the options in the binding menu are self-explanatory, but scope may need a little further explanation.  When building your active macro set, tHotBar will first look at your current palette and fill all squares it contains.  Then, if you have any empty squares, tHotBar will look at your job bindings and fill them as able.  Finally, it will look at your global bindings and fill as able.  So, if you bind something to global, that slot will show up on all jobs and palettes until you override it with a job-specific or palette-specific macro.  If you bind something to job, it will show up on all palettes for that job until you override it with a palette-specific macro.

## Palettes
If you want multiple palettes of macros for a specific job, you can use typed commands to create and change them.  By default, every job contains an undeletable palette named Base.  Every time you change to a job, you will load onto the Base palette for that job.  These commands can be used from within tHotBar macros, so you can do things like the oldschool SMN layout where your avatar summon would also swap to a palette for that avatar.  If you prefer the standard ingame ctrl-alt down/up method of changing macro palettes, you can simply use binds to recreate it:
  * /bind ^up /tb palette previous
  * /bind ^down /tb palette next
  * /bind !up /tb palette previous
  * /bind !down /tb palette next
As this may not be intended use for all users, it is not built into the addon.

**/tb palette add [required: name]**
This will add a palette on your current job.

**/tb palette remove [required: name]**
This will delete a palette from your current job.  There is no way to recover bindings after doing this.

**/tb palette list**
This will print a list of palettes for your current job.

**/tb palette change [required: name]**
This instantly swaps to a specific palette.

**/tb palette next**
Change to next palette.

**/tb palette previous**
Change to previous palette.

## Custom Icons
The binding menu allows you to enter an image path to use your own images for any ability you want.  If you want to replace existing icons, or add new icons, you should do so by adding them to the directory:<br>
**Ashita/config/addons/tHotBar/resources**<br>
You can create this directory if it does not yet exist.  All image bindings will check config prior to checking the built in folder, so this allows you to use any file structure you want without worrying about colliding with the addon's resources.  The preferred method is to use action ID as the filename, but that is not required.  For example, to add a mighty strikes icon, you would use:<br>
**Ashita/config/addons/tHotBar/resources/abilities/16.png**<br>
and you would enter the binding as:<br>
**abilities/16.png**<br>
You can also use the game's item resources directly, as tHotBar will do when binding items.  To do this, simply enter the binding as **ITEM:28540** using the item id.  This can be found on FFXIAH.com or many other places.  This example would show a warp ring.

## Custom Layouts
If you want to adjust the layouts, the same thing applies!  Copy the included layout from:<br>
**Ashita/addons/tHotBar/resources/layouts**<br>
to<br>
**Ashita/config/addons/tHotBar/resources/layouts**<br>
prior to making changes.  Even if the original remains, layouts in config will always take priority.  Make sure to click 'refresh' in the config UI to detect new or altered layouts after editing files on disk.

## Changing Bind Keys
This is done in the layout file.  Follow the instructions from the previous header to make a copy of your desired layout file, then change the DefaultMacro field in the Squares table of the layout.

## Warning About Binding
tHotBar uses ashita binds to register keyboard input.  That means if you have a luashitacast profile or anything else binding to the same keys tHotBar uses, you may have interference and suboptimal performance.  If you feel something else has interfered with your bindings, re-applying your theme from the main UI will always put the bindings back to how tHotBar expects them to be.

## FAQ
### You do know people are going to skip the caps and call this thot bar, right?<br>
Yes, that's ok.
#### More to come as common questions arise.