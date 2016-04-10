# What is a task #

For the Workspace Mechanic, a _task_ is a unit of work the mechanic performs during a scan. Tasks contain a description of the behavior they analyze, and can both evaluate the environment for compliance as well as repair the environment to bring it into compliance.

## On the outside ##

On the outside, tasks can be `.class` files or `.epf` files with some special metadata. The mechanic will scan all registered directories for those files, and operate accordingly.

But tasks aren't just manifested as files. You can create individual tasks through the `tasks` extension point, or define a whole new class of tasks with the `scanners` extension point.

## On the inside ##

Tasks implement the `com.google.eclipse.mechanic.CompositeTaskInterface` interface. Most implementations can just extend `com.google.eclipse.mechanic.CompositeTask`.

Concrete subclasses of `CompositeTask` require these four methods:

  * `String getDescription()`: Returns a string suitable for display to the user describing what action will be taken when the `run` method is called.
  * `String getTitle()`: Returns a string suitable for display to the user providing a title for this Task. This is used in contexts where a short description is needed.
  * `boolean evaluate()`: Evaluates the environment and returns true if the environment adheres to this test. If it returns false, the user will be informed of the failure.
  * `void run()`: Brings the environment into compliance such that `evaluate` would return true on subsequent scans.