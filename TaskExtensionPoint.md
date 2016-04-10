# Task Extension Points #

You can write tasks as OSGi extension points by implementing the `com.google.eclipse.mechanic.tasks` extension point.

```
<extension point="com.google.eclipse.mechanic.tasks"> 
    <task class="com.google.eclipse.myteam.tasks.MyTask">
    </task>
</extension> 
```

the `<task>` element defines a new task using the `class` attribute.

## forcePluginActivation ##
You can additionally define the `forcePluginActivation` attribute, which controls whether the instantiation of the task is delayed until the declaring plug-in is active.

When `forcePluginActivation` is true, the hosting bundle will be started as soon as the mechanic requests the task.

When `forcePluginActivation` is false this task will not be evaluated until the declaring plug-in has been started. This is used to keep plug-ins from instantiating too early, defeating the value of the OSGi lazy loading architecture.

In cases where eager bundle instantiation becomes a barrier to effectively deploying tasks, consider adding a new bundle with much fewer dependencies that only contain tasks.