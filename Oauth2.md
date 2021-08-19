# Oauth2

https://darutk.medium.com/oauth-access-token-implementation-30c2e8b90ff0



- A user makes a request to my token endpoint, passing in a username/password with a grant_type of password. If the credentials are valid, then I create a JWT.
- The user gets back a JWT, and then the client uses that token going forward for all requests
- Any requests that require authorization I use the token's claims to ensure the user is allowed to make this request.
