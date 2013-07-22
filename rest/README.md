# Understanding: REST

## Overview

REST stands for Representationl State Transfer. It was introduced and defined in 2000 by Roy Fielding in his doctoral dissertation. REST is an architectural style for designing distributed systems. It is not a standard, but a set of constraints such as being stateless, having a client/server relationship, and a uniform interface. It is not strictly related to HTTP, but it is most commonly associated with it.

## Principles of REST

 - **Resources** - expose easily understood directory structure URIs
 - **Representations** - transfer JSON or XML to represent data objects or attributes
 - **Messages** - use HTTP methods explicitly (i.e. POST, GET, PUT, DELETE)
 - **Stateless** - state dependencies limit or restrict scalability


## HTTP Methods

HTTP Methods are used to map CRUD (create, retrieve, update, delete) operations to HTTP requests.

### GET

Use HTTP GET to retrieve information. GET requests must be safe and idempotent. They can have side effects, but the user doesn't expect them, so they cannot be critical to the operation of the system. Requests can also be partial or conditional.

Retrieves an address with an ID of 1:

```
GET /addresses/1
```

### POST

Requests that the resource at the URI do something with the provided entity. Often this is used to create a new entity, but it can also be used to update an entity.

Creates a new address:

```
POST /addresses
```

### PUT

Use an HTTP PUT to store an entity at a URI. It can be used to create a new entity or update an existing one. A PUT request is idempotent, meaning repeating it once, or a hundred times and the results are the same. This is the main difference between the expectations of PUT versus a POST request.

Modifies the address with an ID of 1:

```
PUT /addresses/1
```

### DELETE

An HTTP DELETE requests that a resource be removed, however the resource does not have to be removed immediately. It could be an asynchronous or long-running request.

Deletes an address with an ID of 1:

```
DELETE /address/1
```


## HTTP Status Codes

Status codes are an indicator of the result of the HTTP request.

 - **1XX** - informational
 - **2XX** - success
 - **3XX** - redirection
 - **4XX** - client error
 - **5XX** - server error


## Media Types

The `Accept` and `Content-Type` HTTP headers can be used to describe the content being sent or requested within an HTTP request. The client may set `Accept` to `application/json` if it is requesting a response in JSON. Conversely when sending data, setting the `Content-Type` to `application/xml` tells the client that the data being sent in the request is XML.
