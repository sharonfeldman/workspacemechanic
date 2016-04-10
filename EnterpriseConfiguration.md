# Enterprise Configuration #

Setting up the Workspace Mechanic at your desk is one thing, but configuring it to run in an enterprise environment turns out to be easy, too.

## Useful preferences ##

One good way to push tasks to users' workstations is to set up a common set of directories where you can push tasks.

By default every user has `~/.eclipse/mechanic` as a directory where preference files, class files and any other file-based tasks may be stored. If your organization has a shared filesystem, I advise you add a line like so to `plugin_customization.ini`:

```
/instance/com.google.eclipse.mechanic/mechanicSourceDirectories=/shared/eclipse/tasks\:${user_homedir}/.eclipse/mechanic
```

This defines two directories through which tasks will be searched: `/shared/eclipse/tasks` and `~/.eclipse/mechanic`. `${user_homedir}/.eclipse/mechanic` is still included in the list, so users can set up their own tasks. If you omit it from `plugin_customization.ini` it won't be available to your enterprise users initially. But, the mechanic doesn't constrain the end-user, so there you go.

TODO: this page needs to be updated to reflect a) the JSON format and b) the inclusion of http task sources.

TODO: clarify where plugin\_customization.ini can go, though that's a standard eclipse-ism. These two references might help:
http://help.eclipse.org/help32/index.jsp?topic=/org.eclipse.platform.doc.isv/guide/product_configfeature.htm and http://www.ibm.com/developerworks/opensource/library/os-ecfeat/