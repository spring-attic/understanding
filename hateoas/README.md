# Understanding HATEOAS

## Overview

HATEOAS (Hypertext as the Engine of Application State) is a [constraint of the REST application achitecture](http://en.wikipedia.org/wiki/HATEOAS).

A hypermedia-driven site provides information to navigate the site's REST interfaces dynamically by including hypermedia links. This capability differs from that of SOA-based systems and WSDL-driven interfaces where servers and clients usually must access a fixed specification elsewhere.

> **Note:** Pronunciations of HATEOS vary. Some people pronounce it as "hate-ee-os," similar to "hideous," or  as "hate O-A-S". People also refer to it as a hypermedia-driven system.


## Examples

The following code represents a `Customer` object.

```java
class Customer {
	String name;
}
```

A simple JSON presentation is traditionally rendered as:

```json
{ 
	"name" : "Alice"
}
```

The customer data is there, but the data contains nothing about its relevant links.

A HATEOAS-based response would look like this:

```json
{
	"name": "Alice",
	"links": [ {
		"rel": "self",
		"href": "http://localhost:8080/customer/1"
	} ]
}
```
This response not only has the person's name, but includes the self-linking URL where that person is located.

- **rel** denotes a relationship. In this case, it's a reference to itself.
- **href** is a complete URL that uniquely defines the resource.

> **Note:** Although these responses are shown in JSON, XML is also accepted as a standard response format. HATEOAS doesn't impose the requirement of either format. The hypermedia links are the focus of HATEOAS.

It's possible to build more complex relationships. With HATEOAS, the output makes it easy to glean how to interact with the service without looking up a specification or other external document.

Look at the following catalog, courtesy of the sample application shown in the [Spring Data Book](https://github.com/SpringSource/spring-data-book):

```json
{
	"content": [ {
		"price": 499.00,
		"description": "Apple tablet device",
		"name": "iPad",
		"links": [ {
			"rel": "self",
			"href": "http://localhost:8080/product/1"
		} ],
		"attributes": {
			"connector": "socket"
		}
	}, {
		"price": 49.00,
		"description": "Dock for iPhone/iPad",
		"name": "Dock",
		"links": [ {
			"rel": "self",
			"href": "http://localhost:8080/product/3"
		} ],
		"attributes": {
			"connector": "plug"
		}
	} ],
	"links": [ {
		"rel": "product.search",
		"href": "http://localhost:8080/product/search"
	} ]
}	
```
Not only are the items and their prices shown, but the URL for each resource is shown, providing illumination to the interfaces of this site. Because HATEOAS is the final level of REST interfaces, each link is presumed to implement the standard GET/POST/PUT/DELETE verbs of REST (or a subset).