# Spring Boot OAuth2 Google Integration Example

###### Step - 1 
> Get authorization grant code from user
first step is to get authorizarion grant from resource 
owner from URL : http://localhost:8080/oauth/authorize?client_id=clientapp&response_type=code&scope=read_profile_info

It will bring a login page. Provide username and password. For this demo, use “RajendraDesale” and.
After login, you will be redirected to grant access page where you choose to grant access to third party application.

It will redirect to a URL like : http://localhost:8081/login?code=NgTFY2. 
Here 'NgTFY2' is authorization code for the third party application

###### Step - 2

> Get access token from authorization server.
Now application will use authorization grant to get the access token. 
Here we need to make following request.

*Access token request from postman

http://localhost:8080/oauth/token
@ Headers Parameters -
Content-Type: application/x-www-form-urlencoded
authorization: Basic Y2xpZW50YXBwOjEyMzQ1Ng==
 
@ Body Parameters -
Form data - application/x-www-form-urlencoded: 
grant_type=authorization_code
code=NgTFY2
redirect_uri=http://localhost:8081/login

It will ask for client app credentials in separate window.
  Search in OAuth2AuthorizationServer.java file in Project.
  user - clientapp 
  pass - 123456.
  
###### Or 
> make similar request from cURL.
Access token request from cURL
cmd - curl -X POST --user clientapp:123456 http://localhost:8081/oauth/token 
        -H "content-type: application/x-www-form-urlencoded"
        -d "code=NgTFY2&grant_type=authorization_code&redirect_uri=http%3A%2F%2Flocalhost%3A8082%2Flogin&scope=read_user_info"
		
Once we have access token, we can go to resource server to fetch protected user data.		

###### Get resource request

> curl -X GET http://localhost:8080/api/users/me 
     -H "authorization: Bearer 59ddb16b-6943-42f5-8e2f-3acb23f8e3c1"		
1. [Spring boot oauth2 auth server](https://howtodoinjava.com/spring5/security5/oauth2-auth-server/)
