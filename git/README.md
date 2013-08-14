# Understanding git

## Overview

[Git][git] is a free and open source distributed version control system (DVCS) designed to handle everything from small to very large projects with speed and efficiency.

Git was created by [Linux](http://www.linux.org/) creator, [Linus Torvalds](http://en.wikipedia.org/wiki/Linus_Torvalds) to provide a better means to support such a huge, disparate group of developers. But Git's rise in popularity is more closely tied to http://github.com. Git has been in existence in years, but the rise of GitHub has resulted in a relatively recent rise in usage of git. GitHub allows people to host open projects for free while providing simple hooks and a friendly user experience, making usage of git easier.

Other projects have invested deeply in Git, like [Mac Homebrew](https://github.com/mxcl/homebrew/wiki/Formula-Cookbook#creating-the-diff). Homebrew provides the means to install open source packages on a Mac. The tools to build and manage these formulas heavily invests in Git for things like diff tools, management of resources, and ultimately handling sending in new & updated packages through [pull requests](https://help.github.com/articles/using-pull-requests).

### Git vs. other DVCS

The two other most popular DVCS choices are [mercurial](http://mercurial.selenic.com/) and [bazaar](http://bazaar.canonical.com/en/). Mercurial has the command line tool `hg` (named after the chemical symbol for mercury) and Bazaar has the command line tool `bzr`.

Mercurial is associated with many projects. Bazaar is most famous for being used by Canonical, the company behind Ubuntu Linux. It is not unusual for a developer to need familiarity with git, mercurial, and bazaar. 

This is most often dictated by the organizations they participate in, and not by a given set of features. All three of these DVCS have the same essential features such as branching, labels, lack of requirement of a central server, and merge capabilities.

The biggest difference is learning the variance in commands and verbiage used by each tool. For example, `hg revert`  in mercurial means to back out current changes, falling back to official version. `git revert` means to add a new commit that reverses a prior edit. Git has a command to back out changes like mercurial; it simply has a different name for it.

### Git vs. non-distributed SCMs

Preceding DVCS source control management (SCM) systems, there existed several popular choices. Amongst the open source choices:
- subversion
- cvs (concurrent versions systems)

There are also many proprietary version control systems that are still in heavy use today:
- Rational ClearCase
- Perforce
- Visual SourceSafe

These aren't the only ones, but probably the most well recognized.

These proprietary products are often bundled with other software development tools and hence well entrenched in certain software development shops.

The key factor in these systems is their reliance on a central server to hold all the data tracking versioning. In essence, it is not a built-in feature for a developer to make several commits at home, disconnected from this central server, and then later add them to the server. Some of these systems have added features to support such functionality, but it simply isn't a central part of their nature.

A common metaphor used to describe the different is how two people, working independently of each, could meet somewhere remote, like on a cruise trip, and share commits. The commits would have equal authority as those found on the central server.

## Inherent benefits of a DVCS

Tools like Git come with the built in advantage that every person with a copy has EVERYTHING needed to reconstitute a project. If a central server crashed and all data was lost, any remote copy could be switched to as the official copy, because it will have enough information to proceed. The only discrepancy might be developers that don't have the latest commits.

[git]: http://gitscm.com/ 

