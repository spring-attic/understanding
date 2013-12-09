# Understanding JavaScript Package Managers

There are several JavaScript package managers: [npm](http://npmjs.org/),
[bower](http://bower.io/), [volo](http://volojs.org/),
[ringojs](http://packages.ringojs.org/), [component](http://component.io/).
Currently, npm and bower have the most registered packages and enjoy the
broadest third-party support.

Npm deals mainly in node-compatible JavaScript modules.  However, bower focuses
on the entire web platform, offering packages that could contain modules,
scripts, CSS stylesheets, HTML templates, images, or fonts.  For these reasons,
npm tends to be used primarily for node.js development, and bower tends to be
the favorite for client-side work.

While npm and bower use incompatible organizational patterns, both may
be used in a single project since they use different configuration files
(`package.json` and `bower.json`), and they install packages into
different subdirectories.  It's not uncommon to use npm to manage
server-side packages and bower to manage client-side packages.

Unlike Java's Maven, JavaScript package managers concentrate mainly
on finding packages, installing packages, and managing package versions.
Npm also offers the ability to run simple build-related and test-related
tasks.

## Using JavaScript package managers

Getting started with package managers is straightforward.  The following
examples are for bower and npm, but similar concepts exist for the others.

After installing bower or npm, type `bower init` or `npm init` at the root
directory of your project.  The package manager will ask several questions.
Your answers will be used to create a `bower.json` or `package.json`
config file.

To search for packages, type `bower search <keywords>` or `npm search <keywords>`.
A list of matching packages will be displayed.

To install a package and save its information to the config file, type
`bower install --save <package-name>` or `npm install --save <package-name>`.
The `--save` option is not required.  However, the package manager, as well
as other third-party tools, can use the extra configuration data to automate
or simplify certain tasks.
