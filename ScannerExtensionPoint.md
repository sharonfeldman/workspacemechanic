# Task Scanners #

Task Scanners let you define an entire new task type through an extension point.

```
<extension point="com.google.eclipse.mechanic.scanners">
    <scanner class="com.google.eclipse.mechanic.internal.PreferenceFileTaskScanner">
    </scanner>
</extension>
```

The `class` attribute declares a scanner which must implement `com.google.eclipse.mechanic.TaskScanner`. For scanners that are called one per registered directory, extend `com.google.eclipse.mechanic.DirectoryIteratingTaskScanner`