# Understanding SOAP

**SOAP** or **Simple Object Access Protocol** is a protocol designed to exchange information in the form of Web Services. It is primarily based on XML documents exchanged over HTTP, but it's possible to transmit messages through other mediums like email and JMS.

SOAP was initially designed in 1998 during the height of [CORBA](https://en.wikipedia.org/wiki/Common_Object_Request_Broker_Architecture) to provide a simpler way to transfer information. Since then, multiple versions of the SOAP spec have been released.

SOAP web services are generally based on a a [Web Services Description Language](https://en.wikipedia.org/wiki/Web_Services_Description_Language) or WSDL, which is an XML contract that defines all the data and services offered by a given web service. The client and the server both use this contract as a basis for exchanging information and making [remote procedural calls](https://en.wikipedia.org/wiki/Remote_procedure_call).
