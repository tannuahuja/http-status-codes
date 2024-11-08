## why we need http codes and what is the need


#### there are many codes but we need to learn only 11 most impt ones

## 2XX : means success (200, 201, 204)

      200 : success (OK)
      
      201 : something is created (an API has uploaded a picture, github created a user, branch using API ) [POST ] request 
      
      204: when there is no content from server to the cleint

 we can use 200 for every case also 

 
## 3XX : means success with some redirection

     300 : (multiple choices) he server offers several options for the resource, and the client must choose one. For example, a page could offer the user options for different languages (English, Spanish, etc.)
     HTTP/1.1 300 Multiple Choices
    Location: /en, /es, /fr

     301 : means The resource has been permanently moved to a new URL. Future requests should use the new URL. Example: http://example.com redirects to http://newdomain.com
       like moving from /old-page to /new-page 

     302 : means he resource is temporarily located at a different URL. The client should use the original URL for future requests. Example: A temporary redirection from http://example.com to http://temp.com 
     A temporary redirect, like during maintenance or when you’re redirecting to a login page
     HTTP/1.1 302 Found
    Location: http://example.com/login


    300: Multiple options (e.g., language or format choices).
    301: Permanent redirection to a new URL.
    302: Temporary redirection to a new URL.


## 4XX : means request is a failture are the issue with the cleint itself
## 5XX : means the issue with the application and the server 
