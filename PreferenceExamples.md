# Introduction #

These are just a few of the mechanic PreferenceTasks that I keep in my `~/.eclipse/mechanic` directory that I apply to all new workspaces. While they can be stored in one big `.epf` file, I like to store them individually so they can be shared among my coworkers as they see fit.

You can install these by registering the following URL as a task source: http://workspacemechanic.eclipselabs.org.codespot.com/git.wiki/uri-resources/tasks.json

### color\_mark\_occurrences.epf ###
```
# @title (demo) Darken the "Mark Occurrences" rectangles
# @description The "Mark Occurrences" feature highlights entries in the right gutter, but is too faded to see with our color scheme.
# @task_type LASTMOD
file_export_version=3.0
/instance/org.eclipse.ui.editors/occurrenceIndicationColor=136,136,136
```

### editor\_config.epf ###
```
# @title (demo) Set print margin
# @description Sets the print margin to 100 characters and show line number ruler.
# @task_type LASTMOD
file_export_version=3.0
/instance/org.eclipse.ui.editors/lineNumberRuler=true
/instance/org.eclipse.ui.editors/printMarginColumn=100
```

### no\_refresh\_workspace\_on\_startup.epf ###

```
# @title (demo) Do not refresh workspace on startup.
# @description Sets the preference that prevents workspace refresh on startup.
# @task_type LASTMOD
file_export_version=3.0
/instance/org.eclipse.ui.ide/REFRESH_WORKSPACE_ON_STARTUP=false
```

### run\_in\_background.epf ###
```
# @title (demo) Always run jobs in the background.
# @description Run jobs in the background by default.
# @task_type LASTMOD
file_export_version=3.0
/instance/org.eclipse.ui.workbench/RUN_IN_BACKGROUND=true
```