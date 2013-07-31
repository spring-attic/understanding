# Understanding OAuth

## Overview

OAuth stands for Open Authorization. As stated on [ouath.net](http://oauth.net), OAuth is "An open protocol to allow secure authorization in a simple and standard method from web, mobile and desktop applications". In other words, it is an authorization protocol that allows users to approve a third-party application to act on their behalf without revealing their login credentials to that third-party. In contrast, OAuth is not an authentication protocol for signing in with a username and password. Authentication is handled independently from the OAuth process. Currently, there are two major versions of OAuth being used, 1.0(a) and 2.0.


## Why use OAuth?

OAuth has become a standard for third-party applications to communicate with the APIs of popular web sites, such as Facebook, Twitter, and Foursquare, to name a few. 


## Versions

### OAuth 1.0(a)

OAuth 1.0 is the original OAuth specification. It defines a single authorization flow for use by all clients. OAuth 1.0a corrected a security issue present in the original 1.0 specification. While you may still see web sites using 1.0, it has largely been replaced by 1.0a or 2.0.

#### Authorization steps

The following steps are often labeled as the "three-legged OAuth flow". They are a high level description of the process to authorize a third-party `Consumer` to access `User` resources at a `Provider`.

 1. The Consumer obtains an unauthorized Request Token.
 2. The User authorizes the Request Token.
 3. The Consumer exchanges the Request Token for an Access Token.


### OAuth 2.0

The next version of OAuth is not backwards compatible with previous versions. OAuth 2.0 is meant to replace and obsolete OAuth 1.0. The complexity of the original OAuth specification was simplified to allow for easier developer integration, while also establishing specific authorization flows for web applications, desktop applications, mobile phones, and living room devices.

#### Authorization Grant

The [RFC 6749](http://tools.ietf.org/html/rfc6749#section-1.3) specification defines four grant types. These different grant types provide developers with alternative methods for obtaining the user's permission to access the resources on a provider. 

 - Authorization Code Grant - The authorization code is obtained by using an authorization server
   as an intermediary between the client and resource owner.
 - Implicit Grant - The implicit grant is a simplified authorization code flow optimized
   for clients implemented in a browser using a scripting language such
   as JavaScript.
 - Resource Owner Password Credentials Grant - The resource owner password credentials (i.e., username and password)
   can be used directly as an authorization grant to obtain an access
   token.
 - Client Credentials Grant - The client credentials (or other forms of client authentication) can
   be used as an authorization grant when the authorization scope is
   limited to the protected resources under the control of the client,
   or to protected resources previously arranged with the authorization
   server.
