# Introduction #

The Workspace Mechanic Preference Recorder allows you to record any changes that you make to Eclipse's preferences over a period of time, and export those changes to a task file that can be used by the Workspace Mechanic. Rather than having to track down the exact name of every preference of every plug-in you want the Mechanic to work on, you simply can use the standard dialog boxes to make your changes, and they'll be recorded for you.

# Directions #

The Preference Recorder's operations can be accessed through a drop-down menu on the Workspace Mechanic's icon at the bottom of the workbench window. Right-click on the icon to bring up the Mechanic's menu, an item of which will say "Preference Recorder".

## To Start Recording ##

In the Preference Recorder menu, select the "Start Recording" item. At this point, any changes to Eclipse's changes will be recorded.

![http://workspacemechanic.eclipselabs.org.codespot.com/git.wiki/recorder-start.jpg](http://workspacemechanic.eclipselabs.org.codespot.com/git.wiki/recorder-start.jpg)

## To Stop Recording and Export a Task ##

In the Preference Recorder menu, select "Stop Recording...".

![http://workspacemechanic.eclipselabs.org.codespot.com/git.wiki/recorder-stop.jpg](http://workspacemechanic.eclipselabs.org.codespot.com/git.wiki/recorder-stop.jpg)

A dialog box will present itself, listing a few fields you need to fill:

  * **Title**: This is the title the user will see when the the task is presented to them.
  * **Description**: Additional information the user will see attached to the task
  * **Task Type**: How the mechanic will restore the preferences. See PreferenceTasks for more information
  * **Saved File Location**: The location the task file will be written to.
  * **Saved Preferences**: A table of all of the preferences that will be exported. Any preferences that you uncheck from the table will not be exported.

Hitting OK will write export the task to the specified file, ready to be used by the Workspace Mechanic. Note that the file must be in one of the task directories [specified](Configuration.md) by the Mechanic to be picked up as a task. You aren't required to put it there, but it should eventually be put in a registered task directory.

![http://workspacemechanic.eclipselabs.org.codespot.com/git.wiki/recorder-dialog.jpg](http://workspacemechanic.eclipselabs.org.codespot.com/git.wiki/recorder-dialog.jpg)

## How it Works ##

Eclipse stores the configuration information for various plugins in its _preferences tree_, a tree of nodes, each of which contain a series of key/value pairs. In effect, each separate plugin that is installed in Eclipse has its own node in this tree. These key/value pairs typically maintain preference-like information, such as you would modify in the preferences dialog box, although individual plugins decide how to use this functionality. While recording, the preference recorder adds listeners on the global preferences tree and records any changes that occur. This means that more fundamental state changes, like modifying the workspace, or installing/removing plugins, are not recorded by the preferences recorder at the moment.