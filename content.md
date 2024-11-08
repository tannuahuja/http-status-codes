## why we need http codes and what is the need


#### there are many codes but we need to learn only 11 most impt ones

## 2XX : means success (200, 201, 204)

      200 : success (OK)
      
      201 : something is created (an API has uploaded a picture, github created a user, branch using API ) [POST ] request 
      
      204: when there is no content from server to the cleint

 we can use 200 for every case also 

 
## 3XX : means success with some redirection

     300 : (multiple choices) he server offers several options for the resource, and the client must choose one. For example, a page could offer the user options for different languages               (English, Spanish, etc.)
     
           HTTP/1.1 300 Multiple Choices
           Location: /en, /es, /fr

     301 : means The resource has been permanently moved to a new URL. Future requests should use the new URL. Example: http://example.com redirects to http://newdomain.com
          like moving from /old-page to /new-page 

     302 : means he resource is temporarily located at a different URL. The client should use the original URL for future requests. Example: A temporary redirection from http://example.com            to http://temp.com 
            A temporary redirect, like during maintenance or when you’re redirecting to a login page
     
          HTTP/1.1 302 Found
          Location: http://example.com/login


    300: Multiple options (e.g., language or format choices).
    301: Permanent redirection to a new URL.
    302: Temporary redirection to a new URL.


## 4XX : means request is a failture are the issue with the cleint itself
(red flag)

        400 : means bad request, The server cannot process the request because the syntax is incorrect or malformed. This could happen if the client sends invalid or incomplete data
              Common Causes:
              1.   Invalid query parameters.
              2.   Incorrect URL formatting.
              3.   Missing or malformed headers.
              4.   Badly structured JSON, XML, or form data.
            eg: a POST request for an api api.github.com/user/name in which we have to give name but instaed of name we passed username so it is a BAD REQUEST     


        401: means unautherised/ unauthenticated
             request requires authentication, but the client has not provided valid credentials. It is commonly used in situations where a user needs to log in or supply an API key to                    access the resource.
             Common Causes:
              1.  Missing or incorrect credentials (e.g., username/password, API keys).
              2.   The client has not logged in or provided authentication information.

        403: means forbidden/ unautherised
             The server understands the request but refuses to authorize it. This is different from a 401 Unauthorized error, where the issue is lack of authentication. A 403 indicates                  that, even with the correct credentials, the client is not allowed to access the resource due to permissions.
                eg: you have access to the college website but not to the placecemt of student details so u can access only other data but that resource u want to access it gives 403 error                 from the server simply permission issues


        404 :(resource not found) 
             A 404 error is commonly displayed when a user tries to access a non-existent page on a website, The URL was typed incorrectly (typos, incorrect path)
             The page or resource was deleted or moved without proper redirection, A broken link or outdated bookmark
               eg : If you try to visit a page that doesn't exist:  GET /blog/my-nonexistent-post
               The server will respond with 404 Not Found, indicating that the page doesn't exist or is no longer available.

## 5XX : means the issue with the application and the server 

         500: means there is some issue in the server or in the application
            This is a general-purpose error message, which doesn't specify the exact nature of the issue but indicates that something went wrong on the server.

            Common Causes:

Server misconfigurations (e.g., faulty server-side code or server software).
Database connection failures.
Unhandled exceptions or errors in server-side application logic.
Insufficient server resources (e.g., memory, CPU).
Errors in third-party services or APIs the server relies on.
