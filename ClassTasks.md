# Classes #

Tasks can be implemented as classes most easily by extending the `com.google.eclipse.mechanic.CompositeTask` class, then implementing a few methods. In order to compile tasks you'll need to have the workspace mechanic jar on your classpath.

```
package com.google.eclipse.mechanic.ext;

import com.google.eclipse.mechanic.CompositeTask;

/**
 * Hello world task implemented as a Java class.
 */
public class ClassHelloWorldTask extends CompositeTask {

  public String getTitle() {
    return "Hello World";
  }

  public String getDescription() {
    return "Does do anything. This is an task implemented as" +
        " a plain old class file.";
  }

  public boolean evaluate() {
    return false;
  }

  public void run() {
    System.out.println("You've got class!");
  }
}
```

The class task scanner only looks for classes in the `com.google.eclipse.mechanic.ext` package, so the package definition above is not superfluous.

## Installation ##
The class file needs to be installed in one of the registered task directories, and it needs to respect the directory structure.

For instance, if one of your registered task directories is `/enterprise/eclipse/mechanic` then `ClassHelloWorldTask.class` must be installed at `/enterprise/eclipse/mechanic/com/google/eclipse/mechanic/ext/ClassHelloWorldTask.class`.

### Supporting classes ###
Of course, if your task requires additional classes, they must also be copied to the registered task directories. For instance:



```
package com.google.eclipse.mechanic.ext;

import com.google.eclipse.mechanic.CompositeTask;
import com.google.myproject.Util;

public class ClassHelloWorldTask extends CompositeTask {

  ...

  public boolean evaluate() {
    return Util.evaluate();
  }

  public void run() {
    Util.repair();
  }
}

---

package com.google.myproject;

public class Util {
  public static boolean evaluate() { ... }
  public static void run() { ... }
}
```

In this case, `com.google.myproject.Util.class` must also be copied to `/enterprise/eclipse/mechanic/com/google/myproject/Util.class`.