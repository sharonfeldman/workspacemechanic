# Preference Tasks #

Simple preference tasks are Eclipse preference files with additional meta data included in header. Preference tasks fall into two classes: LASTMOD and RECONCILE. This is the **task type**, and specified with the `# @task_type` annotation.

Simple preference files should use the `.epf` file suffix.

Always include a line item `file_export_version=3.0` (or whatever any future version of the preference file format may be) unless you really want the older-style preference file format.

## LASTMOD ##

```
# @title Import PyDev Preferences
# @description Imports PyDev preferences.
# @task_type LASTMOD

file_export_version=3.0

# pydev settings
/instance/org.python.pydev/USE_PYLINT=true
/instance/org.python.pydev/USE_CODE_FOLDING=false
/instance/org.python.pydev/TAB_WIDTH=2
```

A `LASTMOD` task imports preferences if they have never been imported before, and when they are modified on disk. This is useful for publishing broad preferences for large groups of people. When changes are made, individuals will have a chance to import the new preferences.

A little implementation detail: The Workspace Mechanic takes different approaches when `LASTMOD` tasks are specified via disk or URL. The last modification time of file-based `LASTMOD` are used to compute difference, and MD5-hash values are used for URL-based `LASTMOD` tasks.

## RECONCILE ##

```
# @title Import PyDev Preferences
# @description Reconciles PyDev preferences.
# @task_type RECONCILE

file_export_version=3.0

# pydev settings
/instance/org.python.pydev/USE_PYLINT=true
/instance/org.python.pydev/USE_CODE_FOLDING=false
/instance/org.python.pydev/TAB_WIDTH=2
```

A `RECONCILE` task verifies that each preference in your running Eclipse instance matches the values it contains. If any values do not match the task fails and the user will be allowed to fix the mismatched preferences.

This type of task is useful for overriding global preferences specified in a `LASTMOD` preference task.

## Examples ##

See PreferenceExamples for some good examples of Preference tasks.

## Preference Recorder ##
The PreferenceRecorder is a useful tool for creating preference tasks.