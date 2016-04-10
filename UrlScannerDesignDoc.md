# Introduction #

Alex Blewitt made a request for specifying scanners by URL. This document gets down my initial thoughts on the matter, with the hope of composing a solution.

See the [feature request](http://code.google.com/a/eclipselabs.org/p/workspacemechanic/issues/detail?id=21)

# Details #

## Problem ##

The initial public release of the Workspace Mechanic for Eclipse allowed for this notion of ‘task directories’ which contain files with which you can configure your workspace. This was ideal for its initial purpose at Google, which allowed us to push tasks to specific directories on users’ machines or to a shared filesystem location.

Outside Google, the directory mechanism mostly works well for individual engineers managing multiple workspaces on his or her computer. Sharing workspace configuration information across teams isn’t quite as easy when all you can share are plug-ins and files.

> Sidenote: some projects that share plug-ins themselves could easily add another plug-in that provides workspace-mechanic preference changes, et cetera by extending the task extension point.

## Proposal ##

Provide a task scanner that accepts URLs whose contents enumerate tasks.

We’ve just added a JSON parser to the Workspace Mechanic (to support keyboard bindings tasks, see related document) and for the purposes of this proposal will suggest JSON as the file format for the URL task scanner.

### Changes to UI ###

The existing preference dialog has the following elements:

Task scan frequency (in seconds):
Task source directories: (list of directories)
...

Propose changing this with:

Task scan frequency (in seconds):
Scan timeout (in seconds): (default 10?)
Task sources: (list of directories AND urls)

So this might be an easy solution -- to double-up on the Task source directories setting, making it a list of URLs. New... could let you specify a file or URI.

We couldn’t merely natively replace the preferences with URLs, we have to continue to maintain the old list of paths, but could also consider file:/// urls as equivalent. This however means that the storage format for the preference must change, particularly for unix implementation. Again, JSON will help here.

### Scanner Implementation ###

Scanner URLs must specify an individual resource. It cannot specify a directory because there are no reliable ways of specifying a directory via HTML. (This leaves open the possibility of directory scanning via FTP.)

Individual resources would contain, for instance, one set of preferences, e.g. http://www.projectfoo.com/mechanic/task1.epf

Also a new file type will be introduced (described here as tasks.json)

e.g. http://www.projectfoo.com/mechanic/tasks.json

```
// Scanner for project Foo
type : 'com.google.eclipse.mechanic.UriTaskProviderModel',
metadata: [
  description: "..",
  name: "...",
  contact: "...",
  rescanFrequencySeconds: "..." <-- removed
],
tasks : [
  "http://www.projectfoo.com/mechanic/task1.epf",
  "http://www.projectfoo.com/mechanic/task2.epf",
  "http://www.projectfoo.com/mechanic/subsystem.schema", <--- .schema not supported for initial release
  "relative-to-me.epf" <--- files relative to this resource ARE supported.
  "ftp://ftp.projectfoo.com/pub/othertasks", <--- FTP not supported for initial release
  ...
]
```

The proposed metadata has four columns which I hope are self-explanatory.

Also, the use of specifying tasks.json files within tasks.json files is questionable. Having the same task run multiple times is questionable.

#### File types ####
It seems risky to allow .class files to be specified in URL scanners. They will be disallowed in the initial implementation, but might be allowed in the future.

### Regarding existing file-based task scanners ###

The PreferenceFileTaskScanner, ClassFileTaskScanner and (in development) KeyboardBindingstScanner) all extend DirectoryIteratingTaskScanner. All four of these rely on files, and should be retooled to accept an appropriate abstraction.

### Content cache ###
The current code (0.0.6) has one content cache that ensures files aren't read multiple times in a single scan.

Older implementations of this code had another cache that kept files from being read from the internet once every 12 hours, but it was pulled. The code (currently) still exists in the repository, but commented out.

# Questions #

  * Should URL sites be whitelisted inside enterprise environments?
  * How to take network connectivity timeouts into account?