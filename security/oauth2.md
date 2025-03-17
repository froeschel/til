# OAuth 2.0 

OAuth 2.0 is an <b>authorization</b> framework which enables third party applications to obtain limited access to an HTTP service. OAuth 2.0 uses access tokens, which represents authhorization data for the requested resource. Often a token in the JWT format is used. 
In OAuth 2.0 following roles are specified: [list from https://auth0.com/intro-to-iam/what-is-oauth-2]

* Resource Owner: The user or system that owns the protected resources and can grant access to them.

* Client: The client is the system that requires access to the protected resources. To access resources, the Client must hold the appropriate Access Token.

* Authorization Server: This server receives requests from the Client for Access Tokens and issues them upon successful authentication and consent by the Resource Owner. The authorization server exposes two endpoints: the Authorization endpoint, which handles the interactive authentication and consent of the user, and the Token endpoint, which is involved in a machine to machine interaction.

* Resource Server: A server that protects the user’s resources and receives access requests from the Client. It accepts and validates an Access Token from the Client and returns the appropriate resources to it.

