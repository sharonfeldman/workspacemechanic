# THIS FEATURE IS NOT YET RELEASED #

# Introduction #

This document walks you through how to create keyboard a binding task. A keyboard binding task allows you to add and/or remove keybindings through the Workspace Mechanic.

Start an Eclipse instance with the Workspace Mechanic installed against a clean, empty workspace. Let’s create a couple of keybindings. Go to:

> Window > Preferences > General > Keys

In the search box, type _Show Line Number_ and click on the result. It should be unbound at this point. Click on the _Binding_ text field. Type _Shift+Alt+3_.

Do likewise for:

  * Show View (Display) -> Shift+Alt+Q I
  * Show View (Markers) -> Shift+Alt+Q M

You may want to confirm that the bindings work. Try them (note that, to try the _Show Line Number_, you should be in a java file).

We’re ready to create a template of our task. To trigger that, right click the mechanic icon (it’s in the bottom right of your eclipse -- a green circle with a white checkmark or a orange circle with a !, depending) and choose _Dump keybindings_. You are presented with a dialog that should default to something like what I got here:

<pre>
Description: Keyboard bindings for zorzella<br>
Saved File Location: /tmp/workspace-mechanic-bindings.kbd<br>
</pre>

Feel free to edit the description and change the file location and/or name (either by typing or with the help of the _Browse_ button). The description will be presented later when you are prompted to apply these changes to a different workspace, but otherwise has no impact on the results. Choose _Ok_. Feel free to take a look at the created file (if you know JSON, it should be quite readable), which will contain entries for the 3 key bindings we customized above.

Now let’s apply this tasks to a different editor. Move (or copy) this file to your mechanic directory (or you might have chosen to create it there to begin with). Assuming the dialog defaults were left intact, in my case I’d do something like:

<pre>
$ mv /tmp/workspace-mechanic-bindings.kbd ~/.eclipse/mechanic/basic.kbd<br>
</pre>

Now go to a different Eclipse, where you don’t have these keybindings, but you do have the mechanic plugins installed. If that Eclipse instance is already running (and you don’t want to wait for the mechanic to trigger a scan on its own), right click the mechanic icon and choose _Check All_. If things are properly configured, the mechanic icon should change to the orange-circle-with-a-bang indicating there are tasks that need fixing. Click it, and you should see an entry saying:

<pre>
Keyboard binding fixes: Keyboard bindings for zorzella<br>
Add these bindings:<br>
<br>
Shift+Alt+3 : Show Line Number<br>
Shift+Alt+Q I : Show View (Display)<br>
Shift+Alt+Q M : Show View (Markers)<br>
</pre>

Choose _Fix Now_ and this Eclipse now has these same bindings.

Peace,

Zorzella

