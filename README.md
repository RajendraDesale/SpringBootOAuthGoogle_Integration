# Spring Boot OAuth2 Google Integration Example

###### Step - 1 
> Get ClientId and SecretKey from google console(Sign In with your google username and password)

###### Step - 2

> Put below extra properties in application.properties file.

> security.oauth2.client.clientId = [CLIENT_ID]

> security.oauth2.client.clientSecret = [SECRET_KEY]
> security.oauth2.client.accessTokenUri  =  https://www.googleapis.com/oauth2/v3/token
> security.oauth2.client.userAuthorizationUri  =  https://accounts.google.com/o/oauth2/auth
> security.oauth2.client.tokenName = oauth_token
> security.oauth2.client.authenticationScheme = query
> security.oauth2.client.clientAuthenticationScheme = form
> security.oauth2.client.scope = profile email

> security.oauth2.resource.userInfoUri  =  https://www.googleapis.com/userinfo/v2/me
> security.oauth2.resource.preferTokenInfo = false


##### Step - 3
   > run and hit the link http://localhost:8080/user
   > It will directly redirect to google login page, enter your google username and password and complete signIN process.
