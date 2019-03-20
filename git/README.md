# Understanding Git

[Git][git] is a free and open source distributed version control system (DVCS). It is designed to handle projects of any size and scope with speed and efficiency.

Git was invented by [Linux](https://www.linux.org/) creator [Linus Torvalds](https://en.wikipedia.org/wiki/Linus_Torvalds) to support the huge, disparate group of Linux developers. But Git's popularity is more closely tied to https://github.com. Git has been in existence for years, but did not gain wide acceptance beyond the Linux community until the more recent surge in GitHub popularity. GitHub allows you to host open source projects at no cost. It also provides simple hooks and a friendly user experience that make Git easier to use.

Other projects such as [Mac Homebrew](https://github.com/mxcl/homebrew/wiki/Formula-Cookbook#creating-the-diff) have invested deeply in Git. Homebrew lets you install open source packages on a Mac. The tools to build and manage these formulas leverage Git for diff tools, crafting patches, management of resources, and submitting new and updated packages through [pull requests](https://help.github.com/articles/using-pull-requests).

### Git vs. other DVCSes

The two other most popular DVCS choices are [Mercurial](https://mercurial.selenic.com/) and [Bazaar](https://bazaar.canonical.com/en/). Mercurial has the command line tool `hg` (named after the chemical symbol for mercury), and Bazaar's command line tool is `bzr`.

Mercurial is associated with many open source projects. Canonical, the company behind Ubuntu Linux, uses Bazaar. It is not unusual for a developer to need familiarity with Git, Mercurial, and Bazaar.

The DVCS a developer uses is more often dictated by organizations the developer participates in than by a given set of features. Git, Mercurial, and Bazaar all have essential features such as branching, labeling, merging, and no dependency on a central server. A developer who currently uses Git could be working a year from now on a different project managed by Mercurial.

The key challenge is learning the difference in commands and verbiage for each tool. For example, `hg revert`  in Mercurial means to back out current changes, reverting to the official version. `git revert` means to add a new commit that reverses a prior edit. Git has a command to back out changes like Mercurial but has a different name for it.

### Git vs. non-distributed SCMs

Several non-distributed source control management systems (SCMs) predate DVCS and are still in use:
- Subversion
- CVS (Concurrent Versions Systems)

Many proprietary version control systems are still in heavy use today, for example:
- Rational ClearCase
- Perforce
- Visual SourceSafe

These proprietary products are often bundled with other software development tools and hence are well entrenched in certain software development shops.

The key factor in these systems, as opposed to the DVCS model, is their reliance on a central server to hold all the critical data involved with tracking versions and branches. In essence, it is not a built-in feature for a developer to make several commits at home, disconnected from this central server, and then later add them to the server. Some of these systems have added features to support such functionality, but it isn't a central part of their nature.

To illustrate the difference between DVCS and non-DVCS SCM systems, consider how two people, working independently of each, could meet somewhere remote, like on a cruise trip, and share commits when using a DVCS. The shared commits would have the same authority as those found on the central server. When using a non-distributed SCM, these two people can only share code diffs, not commits. Someone must still publish the commits to the central server when they get home and have access to it in order to make them official.

## Inherent benefits of a DVCS

The built-in advantage of tools like Git is that every person with a copy has _everything_ needed to reconstitute a project. If a central server crashes and all data is lost, any remote copy can be designated the official copy, because it will have enough information to proceed. The only discrepancy arises if developers don't have the latest commits.

[git]: https://git-scm.com 

