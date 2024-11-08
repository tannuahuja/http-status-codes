## why we need http codes and what is the need
HTTP status codes are three-digit numbers returned by a web server in response to an HTTP request.

#### Why Do We Need HTTP Codes?
1. Feedback: They tell the client (browser, app, etc.) whether the request was successful or failed, and the nature of the issue.
2.Error Handling: They help diagnose and troubleshoot problems, whether on the client or server side.
3.Efficiency: They streamline interactions by summarizing the result of requests in a concise, standardized format.
4. Standardization: They provide a consistent way for clients and servers to communicate.


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
                  1. Server misconfigurations (e.g., faulty server-side code or server software).
                  2. Database connection failures.
                  3. Unhandled exceptions or errors in server-side application logic.
                  4 . Insufficient server resources (e.g., memory, CPU).
                  5.  Errors in third-party services or APIs the server relies on.


               example : A web application runs a piece of server-side code that attempts to access a database, but the database is down or unreachable. The server returns a 500 Internal                          Server Error to the client because it couldn't complete the request due to the underlying issue.


        501 : The server does not support the functionality required to fulfill the request. This typically means that the server either does not recognize the request method (e.g., PUT,                   DELETE, etc.) or lacks the necessary capabilities to process it.       

              Comman causes :
                   1. The server doesn't support the HTTP method requested (e.g., the client tries to use PUT on a server that only supports GET or POST).
                   2. The server is out of date or lacks the required software to handle the specific request type (e.g., a feature hasn't been implemented yet)

               example : A client sends a DELETE request to a server that doesn’t support this HTTP method for the given resource. The server responds with 501 Not Implemented because it                       cannot process the DELETE request.

        502 : Bad Gateway
              example : we are using frontend -> backend -> Database
                 here frontend and backend is working fine but database is not sending the response on time in this case there is the 502 error.
                 the databse server is taking too much time to respond 

               Comman issues : 
                  1. Upstream server issues: The server you're trying to access (the "upstream server") is down or not responding correctly.
                  2. Timeouts: The gateway server waited too long for a response from the upstream server, leading to a timeout.
                  3. Network issues: There might be network connectivity problems between the gateway server and the upstream server.
                  4. Invalid response: The upstream server might send a malformed or invalid response that the gateway server can't process.

              ex: Imagine a website using a load balancer (acting as a reverse proxy) to distribute traffic between multiple backend servers. If one of the backend servers is down or                        responds incorrectly, the load balancer may respond with 502 Bad Gateway, indicating that it couldn’t get a valid response from the backend server.    
              Client's Perspective: The client may be accessing a service through a proxy or load balancer and may not know exactly which server in the chain is having the issue.
              Like the 500 error, the client only knows that something went wrong on the server side.



### Key Differences Between 500 and 502:
   500 - Internal Server Error: This error indicates a general issue on the server itself. It could be any internal problem, such as misconfiguration, faulty code, or resource exhaustion. The server fails to process the request, but it is not dependent on communication with another server.
   502 - Bad Gateway: This error occurs when the server, acting as a gateway or proxy, receives an invalid or unexpected response from an upstream server. The problem usually involves communication between multiple servers or services.

### Quick Summary:
500: Something is wrong with the server, but the exact cause isn’t clear or specified. It can happen for a variety of reasons, such as bugs in the application or database failures.
502: The server is acting as a middleman (e.g., reverse proxy, API gateway) and couldn’t get a valid response from an upstream server, like another server or service.
Both errors are server-side issues, meaning they’re not something the client can fix, but they indicate different types of server failures.





for demo we use :

             httpbin.org
             
            
