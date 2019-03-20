# Understanding OAuth

OAuth (Open Authorization), as stated on [oauth.net](https://oauth.net), is "an open protocol to allow secure authorization in a simple and standard method from web, mobile and desktop applications." In other words, OAuth is an authorization protocol that allows users to approve a third-party application to act on their behalf without revealing their login credentials to that third party. 

In contrast, OAuth is not an authentication protocol for signing in with a username and password. Authentication is handled independently from the OAuth process. 


## Why use OAuth?

OAuth has become a standard for third-party applications to communicate with the APIs of popular web sites, such as Facebook, Twitter, and Foursquare, to name a few. 


## Versions
Currently, the two major versions of OAuth are 1.0(a) and 2.0.

### OAuth 1.0(a)

OAuth 1.0 is the original OAuth specification. It defines a single authorization flow for use by all clients. OAuth 1.0a corrected a security issue in the original 1.0 specification. Although you may still see web sites using 1.0, it has largely been replaced by 1.0a or 2.0.

#### Authorization steps

The following steps are considered the "three-legged OAuth flow". They are a high-level description of the process to authorize a third-party `Consumer` to access `User` resources at a `Provider`.

 1. The Consumer obtains an unauthorized Request Token.
 2. The User authorizes the Request Token.
 3. The Consumer exchanges the Request Token for an Access Token.


### OAuth 2.0

The next version of OAuth is not backwards compatible with previous versions. OAuth 2.0 is meant to replace and make obsolete OAuth 1.0. The complexity of the original OAuth specification was simplified to allow for easier developer integration, while also establishing specific authorization flows for web applications, desktop applications, mobile phones, and living room devices.

#### Authorization grants

The [RFC 6749](https://tools.ietf.org/html/rfc6749#section-1.3) specification defines four grant types. These grant types provide developers with alternative methods for obtaining the user's permission to access the resources on a provider. 

 - Authorization Code Grant. The authorization code is obtained by using an authorization server as an intermediary between the client and resource owner.
 - Implicit grant. This grant is a simplified authorization code flow optimized
   for clients implemented in a browser that uses a scripting language such as JavaScript.
 - Resource Owner Password Credentials grant. The resource owner password credentials) username and password) can be used directly as an authorization grant to obtain an access
   token.
 - Client Credentials grant. The client credentials (or other forms of client authentication) can be used as an authorization grant when the authorization scope is limited to the protected resources under the control of the client, or limited to protected resources previously arranged with the authorization server.
