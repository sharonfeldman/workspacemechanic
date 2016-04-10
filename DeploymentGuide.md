# Introduction #

This document assumes you've already checked out code, and are familiar with the development process.

## Bumping the Version Number ##

  * Open `/com.google.eclipse.mechanic/plugin.xml`.
  * Click on the Overview tab.
  * Update the version number.
  * **SAVE AND CLOSE THAT FILE**

  * Open `/com.google.eclipse.mechanic (feature)/feature.xml`.
  * Click on the Overview tab.
  * Update the version number.
  * In the `Exporting` section click on `Synchronize`.
  * A Version Synchronization dialog box will appear. Select "Synchronize versions on build" and click Finish.
  * **SAVE AND CLOSE THAT FILE**

  * Select both projects in the Project explorer, right-click, select Team > Commit.
  * Select one project in the Project explorer. right-click, select Team > Push.

This change [plugin/feature](http://code.google.com/a/eclipselabs.org/p/workspacemechanic/source/detail?r=b02d56dd185f4cefbe88640bba0f7b98833854cf) demonstrates a correct version number upgrade.

## Deployment ##
Deploying to an update site is pretty easy.

Clone the Update site repository. The git command is below, but the easiest way to do it is by cloning the repository itself.

> `git clone https://code.google.com/a/eclipselabs.org/p/workspacemechanic.update/`

This creates two update site projects:

> `com.google.eclipse.mechanic.update (testing)`

> `com.google.eclipse.mechanic.update (stable)`

Always push to testing prior to pushing to stable.

  * Open `site.xml` in the testing, or stable, project.
  * In the editor view, click `Synchronize...` (selected features or all features, it doesn't matter.)
  * Click `Build All`.
  * Open the `features` and `plugins` directories to see that the jars representing the latest version have been added.
  * Commit the changes with `Team > Commit`. **You must remember to add the new files to the commit.**
Next, try updating to the local filesystem that represents update site, and have it update a local instance.

This is an example of a proper upgrade on the testing update site. [update site](http://code.google.com/a/eclipselabs.org/p/workspacemechanic/source/detail?r=4ddceed4cff74bc76d3d64d5b794e582f9d85cf5&repo=update)

This verifies that the update works as advertised. Easiest way to do that is:
  * Right-click on the project resource in the project explorer, select `Properties`.
  * Select the location from the `Properties` dialog. Copy to clipboard
  * `Help > Install New Software`
  * `Work With:` (Paste from clipboard)
  * The latest version should be in the dropdown listing features. Uncheck `Show only the latest versions of software available` to view all versions.
  * Install the latest version.
  * Play with it some.
When you're happy, push the repository. The repository is now live.