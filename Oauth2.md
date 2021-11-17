# Oauth2

https://darutk.medium.com/oauth-access-token-implementation-30c2e8b90ff0



- A user makes a request to my token endpoint, passing in a username/password with a grant_type of password. If the credentials are valid, then I create a JWT.
- The user gets back a JWT, and then the client uses that token going forward for all requests
- Any requests that require authorization I use the token's claims to ensure the user is allowed to make this request.


# Note:

- Apache CXF, Spring Security are the different open source provide the Outh.
- 


#
- In JWT Oauth, there are two things
    - Authentication -> Using username/password or secret-id to validate whether it is valid user or not.
    - Authorization -> It means what all access can be provided to user if they are valid from authentication if ok then provide a JWT token with refresh time

First it validate the username/password from LDAP and then if ok then route it for Authorization.
