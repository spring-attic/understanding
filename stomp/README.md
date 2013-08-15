# Understanding STOMP

STOMP (Simple/Streaming Text Oriented Protocol) is a text-based, interoperable wire format for asynchronous messaging. Being language agnostic, STOMP enables messaging between applications, regardless of the language they are developed in.

Frame Format

When a client communicates with a message broker supporting STOMP, it sends a "frame". A frame is roughly analogous to an HTTP request, in that it is defined by a command, zero or more headers, a blank line, and then the content payload of the frame.

For example, when a client wants to connect with a STOMP broker, it will send a `CONNECT` frame:

```
CONNECT
accept-version:1.1,1.0
heart-beat:10000,10000
```

Once connected, the client can subscribe to a message destination by sending a `SUBSCRIBE` frame:

```
SUBSCRIBE
id:sub-0
destination:/queue/greetings
```

In this example, the client is subscribing to the "/queue/greetings" destination.

The client may also publish content to a destination for other clients that are subscribed to that destination to consume:

```
SEND
destination:/app/hello
content-length:15

{\"name\":\"Fred\"}
```

Here, the client is publishing a simple [JSON][u-json] structure to the "/app/hello" destination.

If the client is subscribed to a destination, they may receive a `MESSAGE` frame from the STOMP broker:

```
MESSAGE
subscription:sub-0
message-id:qeof1yi4-1
destination:/queue/greetings

{\"content\":\"Hello, Fred!\"}
```

Again, this frame contains a simple JSON structure as its payload.



[u-json]: /understanding/json
