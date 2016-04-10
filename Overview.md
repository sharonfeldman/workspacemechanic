# Overview #

The Workspace Mechanic automates maintenance of your Eclipse environment by tweaking preferences, adding extension locations, and so on. You can use it to:

  * Create a consistent environment among groups as large as the entire company, your local team, or even among your own many workspaces
  * Save time setting up new workspaces
  * Create tasks that ensure your favorite new preferences are applied to all your current and future workspaces. (This is one of our favorite features!)

The key to the Workspace Mechanic's behavior is the [Task](WhatIsATask.md). A task describes a simple test and an action that, when run, changes the environment so the test will subsequently pass. Tasks can come in many forms: preference files, Java classes, Groovy scripts and Eclipse extensions. You can easily define your own Tasks.

On a periodic basis, the mechanic will scan your workspace's environment, executing all the registered Tasks. If all Tasks pass, nothing happens. If some Tasks fail you are presented with the failed tasks, and may choose which of those to fix, or skip, or entirely ignore. This should be familiar to anyone who has run tools like virus and spyware scanners, or software updaters.

The Workspace Mechanic is capable of loading tasks in a variety of forms (compiled classes, preference files and through an extension point mechanism), and can do so from defined locations on disk.