# Understanding WAR

[WAR (Web application ARchive) files][war] are used to distribute Java-based web applications. A WAR has the same file structure as a JAR file, which is a single compressed file that contains multiple files bundled inside it.

WAR files are used to combine [JSPs][u-jsp], servlets, Java class files, XML files, javascript libraries, JAR libraries, static web pages, and any other resources needed to run the application.

WAR files are usually deployed in servlet containers, but can also be deployed to Java EE application servers. When a WAR file is deployed to a container, the container usually unpacks it to access the files and then launches the application.

WAR files cannot be edited while the application is running. Any changes require rebuilding the file.

[war]: http://en.wikipedia.org/wiki/WAR_file_format_(Sun)
[u-jsp]: /understanding/view-templates
