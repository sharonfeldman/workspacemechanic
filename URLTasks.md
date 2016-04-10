# Summary #

File-based tasks are specified by directories. Since there's no way to specify directories via HTTP, we must use an additional file to represent a manifest. The manifest is a file in JSON format:

```
{
    "type": "com.google.eclipse.mechanic.UriTaskProviderModel",
    "metadata": {
        "description": "my set of tasks",
        "name": "Jane Programmer",
        "contact": "jane@projectfoo.com"
    },
    "tasks": [
        "http://www.projectfoo.com/mechanic/task1.epf",
        "http://www.projectfoo.com/mechanic/task2.epf",
        "relative-to-me.epf"
    ]
}
```

As a standard, the extension of the manifest is =.manifest=

The metadata fields are by and large not used, and serve as documentation.

Note also that tasks can be specified absolutely and relatively.

**Security note:** =.class= files are not supported in URL manifests.

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

### Content cache ###
Older implementations of this code had another cache that kept files from being read from the internet once every 12 hours, but it was pulled. The code (currently) still exists in the repository, but commented out.