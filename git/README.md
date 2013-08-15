# Understanding Git

[Git][git] is a free and open source distributed version control system (DVCS) designed to handle everything from small to very large projects with speed and efficiency.

Git was invented by [Linux](http://www.linux.org/) creator, [Linus Torvalds](http://en.wikipedia.org/wiki/Linus_Torvalds), to provide a better means to support that huge, disparate group of developers. But Git's rise in popularity is more closely tied to http://github.com. Git has been in existence for years, but only with the more recent surge in GitHub popularity has Git become so widely accepted outside the Linux community. GitHub allows people to host open projects for free while providing simple hooks and a friendly user experience, making usage of Git easier.

Other projects have invested deeply in Git, like [Mac Homebrew](https://github.com/mxcl/homebrew/wiki/Formula-Cookbook#creating-the-diff). Homebrew provides the means to install open source packages on a Mac. The tools to build and manage these formulas leverage Git for things like diff tools, crafting patches, management of resources, and submitting new & updated packages through [pull requests](https://help.github.com/articles/using-pull-requests).

### Git vs. other DVCS

The two other most popular DVCS choices are [Mercurial](http://mercurial.selenic.com/) and [Bazaar](http://bazaar.canonical.com/en/). Mercurial has the command line tool `hg` (named after the chemical symbol for mercury) and Bazaar has the command line tool `bzr`.

Mercurial is associated with many open source projects. Bazaar is most famous for being used by Canonical, the company behind Ubuntu Linux. It is not unusual for a developer to need familiarity with Git, Mercurial, and Bazaar.

The DVCS a developer must be familiar with is most often dictated by the organizations they participate in, and not by a given set of features. All three of these DVCS have the same essential features such as branching, labeling, lack of requirement of a central server, and merging. A developer might be currently using Git, but a year from now, could be working on a different project managed by Mercurial.

The biggest difference is learning the variance in commands and verbiage used by each tool. For example, `hg revert`  in Mercurial means to back out current changes, falling back to the official version. `git revert` means to add a new commit that reverses a prior edit. Git has a command to back out changes like Mercurial; it simply has a different name for it.

### Git vs. non-distributed SCMs

Preceding DVCS source control management (SCM) systems, there existed several popular choices. Amongst the open source choices:
- Subversion
- CVS (Concurrent Versions Systems)

There are also many proprietary version control systems that are still in heavy use today:
- Rational ClearCase
- Perforce
- Visual SourceSafe

These aren't the only ones, but probably the most well recognized.

These proprietary products are often bundled with other software development tools and hence well entrenched in certain software development shops.

The key factor in these systems is their reliance on a central server to hold all the critical data involved with tracking versions and branches. In essence, it is not a built-in feature for a developer to make several commits at home, disconnected from this central server, and then later add them to the server. Some of these systems have added features to support such functionality, but it simply isn't a central part of their nature.

One metaphor that can be used to describe the difference is how two people, working independently of each, could meet somewhere remote, like on a cruise trip, and share commits when using a DVCS. The shared commits would have the same authority as those found on the central server. When using a non-distributed SCM, these two people can only share code diffs, not commits. Someone must still publish the commits to the central server when they get home and have access to it in order to make them official.

## Inherent benefits of a DVCS

Tools like Git come with the built in advantage that every person with a copy has EVERYTHING needed to reconstitute a project. If a central server crashed and all data was lost, any remote copy could be switched to as the official copy, because it will have enough information to proceed. The only discrepancy might be developers that don't have the latest commits.

[git]: http://gitscm.com/ 

