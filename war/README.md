# Understanding WAR

[WAR (Web application ARchive) files][war] are used to distribute Java-based web applications. They have the same file structure as JAR files, which is a single compressed file, containing multiple files bundled inside it.

WAR files are used to combine [JSPs][u-jsp], servlets, Java class files, XML files, javascript libraries, JAR libraries, static web pages, and any other resources needed to run the application.

WAR files are usually deployed in servlet containers, but may also be deployed to Java EE application servers. When a WAR file is deployed to a container, the container usually unpacks it to access the files and then proceeds to launch the application. With servlet containers being the most prolific platform for Java web apps, WAR files are not only a Java spec standard, but a 

WAR files cannot be edited while the application is running. Any changes require rebuilding the file.

[war]: http://en.wikipedia.org/wiki/WAR_file_format_(Sun)
[u-jsp]: /u/jsp