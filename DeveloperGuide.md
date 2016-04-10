# Introduction #

Anyone can contribute to the Workspace Mechanic project using your own Git clone of our source repository. Everyone, including contributors should use this technique to contribute changes.

# Details #

## CLA ##

We welcome your contribution. Please sign one of the [Contributor License Agreements](ContributorLicenseAgreements.md); we can't accept contributions without it.

## Git ##

This project uses [Git](http://git-scm.com/) as its version control system, and we also recommend using the [Egit](http://eclipse.org/egit/) plug-in. [Egit Getting-Started Tutorial](http://wiki.eclipse.org/EGit/Git_For_Eclipse_Users)

If you need to learn git, there are several [good](http://www.vogella.de/articles/Git/article.html) [references](http://book.git-scm.com/) available.

## Create a Personal Clone ##

[Create a new personal clone](http://code.google.com/a/eclipselabs.org/p/workspacemechanic/source/createClone). We suggest you use a name in the form of `USERNAME-devel`.

Before you move away from this page, be sure that you enable the `Allow non-members to review code` on your personal clone. If you already moved away from the page, you can do this by going to your repository home, clicking on `Administer`, then `Source`. The option appears under the `Code Reviews` section. By enabling this option you'll be allowing Workspace Mechanic project members (and anyone else) to comment on your changes before we merge the changes into the main branch.

## How we use Guava ##

This project uses Guava as part of its internal implementation. Guava cannot be used as any part of the public API. Otherwise it will interfere with other plug-ins that interoperate with the Workspace Mechanic and use the Guava-OSGI plug-in.

## Contributing Code ##

Once you've created a local clone of your development clone you can get started writing code.

  1. Make changes to the code.
  1. Commit changes to your local clone by selecting the Eclipse project and selecting Team > Commit.
  1. Push your changes to your development clone with Team > Push to Upstream.
  1. Once you've pushed your changes up to you development clone you should [request a code review](http://code.google.com/a/eclipselabs.org/p/workspacemechanic/issues/entry?template=Review%20request). Be sure to provide a link to the revision you want reviewed (since the Request a Review link [is broken](http://code.google.com/p/support/issues/detail?id=3173)).

You should discuss any changes you're making with the team on the [Workspace Mechanic Google Group](http://groups.google.com/group/workspace-mechanic).

### Tests ###

Be prepared to be asked to provide tests. Code with tests will be looked at much faster than code without tests. Tests that run as JUnit tests (and are annotated with @RunAsJUnit) are preferred to tests that have to run as plug-in tests. Mockito is your friend.

To run all the tests:

Right click on the project `com.google.eclipse.mechanic.tests`, select Run as > JUnit Plug-in Tests. Note that some of the tests can be run with JUnit without all the plug-in dressing, but you'll need to run all the tests anyway.

### About @author tags ###
Historically, the code has had @author tags, and there are still plenty of them today. However, I'm casually removing them, and will discourage new @author tags. While this project isn't nearly as complex as Subversion, Ben and Fitz' excellent talk [How Open Source Projects Survive Poisonous People](http://www.youtube.com/watch?v=ZSFDm3UYkeE) makes a compelling argument. (Watch the whole thing, but the relevant section is at the 17:30 point.)

Authors will be acknowledged on the [Attribution](Attribution.md) wiki page.