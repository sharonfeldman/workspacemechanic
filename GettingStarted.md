**1. Install the plug-in.**

Update site can be found at http://workspacemechanic.eclipselabs.org.codespot.com/git.update/mechanic

**2. Install a task**

Open up a terminal window. From your home directory, run:
```
$ mkdir -p ~/.eclipse/mechanic
```

On Windows run
```
$ mkdir %HOME%\.eclipse\mechanic
```

**3. Create a sample Workspace Mechanic task.**

Create a new file called `~/.eclipse/mechanic/editor_config.epf` (or `%HOME%\.eclipse\mechanic\editor_config.epf`) with the following content:

```
# @title Set print margin
# @description Sets the print margin to 100 characters and show line number ruler.
# @task_type RECONCILE
file_export_version=3.0
/instance/org.eclipse.ui.editors/lineNumberRuler=true
/instance/org.eclipse.ui.editors/printMarginColumn=100
```

**4. Run.**

Find the Mechanic icon on the lower trim. Double-click it. It will perform a system scan, and, unless you already have a line number and print margin set to 100, the mechanic trim widget will turn into an exclamation mark!

![http://workspacemechanic.eclipselabs.org.codespot.com/git.wiki/trimwidget.jpg](http://workspacemechanic.eclipselabs.org.codespot.com/git.wiki/trimwidget.jpg)

**4. Fix**

Click the trim widget again. A dialog box should appear showing you the failed mechanic task.

![http://workspacemechanic.eclipselabs.org.codespot.com/git.wiki/suggestions.jpg](http://workspacemechanic.eclipselabs.org.codespot.com/git.wiki/suggestions.jpg)

Click OK to accept the mechanic task.