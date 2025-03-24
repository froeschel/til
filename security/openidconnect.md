# OpenID Connect

OIDC authentication works by allowing users to sign in to one application and receive access to another. For example, if a user wants to create an account at a news site, they may have an option to use Facebook to create their account rather than creating a new account. If they choose Facebook, they are using OIDC authentication. Facebook, which is referred to as the OpenID provider, handles the authentication process and obtains the user’s consent to provide specific information, such as a user profile, to the news site, which is the relying party. 

## ID tokens 
The OpenID provider uses ID tokens to transmit authentication results and any pertinent information to the relying party. Examples of the type of data that are sent include an ID, email address, and name.

## Scopes
Scopes define what the user can do with their access. OIDC provides standard scopes, which define things such as which relying party the token was generated for, when the token was generated, when the token will expire, and the encryption strength used to authenticate the user. 

## A typical OIDC authentication process includes the following steps:

1) A user goes to the application they wish to access (the relying party).
2) The user types in their username and password.
3) The relying party sends a request to the OpenID provider.
4) The OpenID provider validates the user’s credentials and obtains authorization.
5) The OpenID provider sends an identity token and often an access token to the relying party.
6) The relying party sends the access token to the user’s device.
7) The user is given access based on the information provided in the access token and relying party. 


[source]("https://www.microsoft.com/en-us/security/business/security-101/what-is-openid-connect-oidc")

A [link](https://learn.microsoft.com/en-us/aspnet/core/security/authentication/configure-oidc-web-authentication?view=aspnetcore-9.0) to an example of how to configure OpenID Connect in ASP.NET Core.