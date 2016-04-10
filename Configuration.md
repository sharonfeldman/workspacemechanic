# System preferences for the Workspace Mechanic #

Preferences can be found at `Window > Preferences > Workspace Mechanic`.

The mechanic supports several preferences.
  * `Task scan frequency`: How long the mechanic sleeps between scans (default is 1 hour).
  * `Task source directories`: Disk locations the Mechanic will scan for Mechanic tasks.
  * `Blocked Tasks`: List of items previously blocked. You can also block items by adding them directly to this list, or remove them as well.
  * `Show popup when tasks fail`: By default a popup dialog appears. This checkbox allows you to hide or show the popup.

![http://workspacemechanic.eclipselabs.org.codespot.com/git.wiki/preferences.jpg](http://workspacemechanic.eclipselabs.org.codespot.com/git.wiki/preferences.jpg)

When the Workspace Mechanic runs it checks the _Task Source Directories_ defined in the above dialog, loads the tasks it finds, and evaluates them to see if any settings are out of date.