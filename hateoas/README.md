# Understanding: HATEOAS

## Overview

HATEOAS stands for **Hypertext as the Engine of Application State**. It is a [constraint of the REST application achitecture](http://en.wikipedia.org/wiki/HATEOAS). There are many variations on how to pronounce this acronym, but many say "HATE-ee-os," similar to the word "hideous." A HATEOAS-based system is also referred to as a hypermedia-driven system.

A hypermedia-driven site provides the information needed to navigate the site's REST interfaces dynamically. This is different from SOA-based systems and WSDL-driven interfaces where servers and clients must access a fixed specification in advance.

## Examples

As an example, look at the following code that represents a simple `Person` object.
```java
class PersonResource {
	String firstname;
	String lastname;
}
```

A simple JSON presentation is traditionally rendered as:

```json
{ 
	"firstname" : "Dave",
	"lastname" : "Matthews"
}
```

The data is there, but nothing about it's relevant links is provides.

A HATEOAS-based response would look like:

```json
{
	"firstname" : "Dave",
	"lastname" : "Matthews",
	"links":[
		{"rel":"self","href":"http://localhost:8080/people/1"},
		{"rel":"delete","href":"http://localhost:8080/people/1"},
		{"rel":"add","href":"http://localhost:8080/people/1"}
	]
}
```

This not only has the person's name, i.e. the content of the resource, but includes the self-linking URL where that person is located. It also includes links for the other available operations: **delete** and **add**.

> **Note:** While these responses are shown in JSON, XML is also accepted as a standard response format. HATEOAS doesn't impose the requirement of either format. Instead, the hypermedia links provided along with the content is the focus of HATEOAS.

Even though this example shows **add** and **delete**, the purpose is to list hypermedia links to defined operations. A HATEOAS web service used to support shipping might have links to operations like **addItem**, **pay**, and **ship**.