# Understanding JSON

## Overview

JSON (JavaScript Object Notation) is a lightweight syntax for exchanging data that is designed to be understood easily by humans, and parsed easily by machines. As the name implies, JSON is based on the JavaScript scripting language; however, JSON itself is completely language independent.

JSON is a popular notation for transmitting data through RESTful web services. Numerous libraries for most programming languages allow easy parsing of JSON data, and many web frameworks now support producing JSON as response data. And because JSON has a smaller footprint than XML, it is ideal for conditions where network speeds are limited. For example, mobile devices often have slower connections and so benefit from a smaller download.

The official internet media type for JSON is `application/json`, and JSON files typically have a `.json` extension.


## Structure

JSON is defined by two basic structures. 

 - Name/value pairs
 - Ordered list of values

A value can be any one of the following types, and these structures can be nested:

 - String (Unicode)
 - Number
 - Boolean (true or false)
 - Array
 - Object
 - null (empty)


## Examples

This object has three fields, where "name" is a string, "age" is a number, and "member" is a boolean.

```javascript
{
    "name": "John",
    "age":  35
    "member": false
}
```

Arrays contain a list of values, which can be of any type. This object has two arrays; the "indexes" array contains numbers, and the "names" array contains strings.

```javascript
{
    "indexes": [5, 10, 15, 20],
    "names": ["John", "Elizabeth", "Mary"]
}
```

A contact card for an address book is a more complex example. This example combines many elements, including nested objects and arrays.

```javascript
{
    "firstName": "John",
    "lastName": "Smith",
    "birthday": "1975-01-31",
    "spouse": {
        "firstName": "Mary",
        "lastName": "Smith"
    },
    "addresses": [
        {
            "description": "home",
            "street": "123 Peachtree Ln",
            "city": "Atlanta",
            "state": "GA",
            "postalCode": 30305
        },
        {
            "description": "work",
            "street": "456 Peachtree St",
            "city": "Atlanta",
            "state": "GA",
            "postalCode": 30305
        }
    ],
    "phoneNumbers": [
        {
            "description": "home",
            "number": "404-555-1234"
        },
        {
            "description": "mobile",
            "number": "678-555-1234"
        }
    ]
}
```