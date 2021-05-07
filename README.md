# Web Information

## What is Http and how it works

It comes from their initials "Hypertext Transfer Protocol" and it allows us to make requests of data and resources as, for example, HTML documents. Http is the base of any swap of data on Web between the client and the server where the info is allowed. So, a full Web page is made of multiple sub-documents received, as for example, the texts, colors, videos, scripts, among others.

![ilustracion](https://camo.githubusercontent.com/d395ba9e0b382f76bf840162c1e4b2c95abcc2d99e18f0edb0c6d3810a9bcb97/687474703a2f2f626c6f67732e696e6e6f766174696f6e6d2e636f6d2f77702d636f6e74656e742f75706c6f6164732f323031362f31302f485454502d50726f746f636f6c2d363234783234382e706e67)

Clients and servers can comunicate changing individual messages called "requests" and the messages sent by the server are called "response". 

### Architecture of systems based on HTTP

Http is based on client-server principle. Most of the time the client uses a Web browser to send the different requests to a server. Every request are managed by the server and It sends a response. Normally, there are some intermediaries between client and server, for example, proxies, routers and modems. But, Http is designed by the concept of layers, which let the client-server to browse without any trouble.

![Ejemplo](https://www.w3.org/TR/mmi-arch/Images/HTTP_lifecycle_transport_2.png)

### What is an API 

API is the initials of "Application Programming Interface" and is a set of definitios and protocols used to develop and integrate applications. on other words, APIs allow two applications to interface or interact with each other. An API a set of programming instructions and functions used to access a website or web-based software application


## What is Rest API

REST is any interface between systems which use Http to obtain data or generate operations on any data on any format, like XML or JSON

 
### Characteristics of API REST

- The request are defined by messages
- One direction for any process instance
- Low resources cosumption
- The instances of the process are created explicitly
- The client does not need enrutment info of the initial URI
- Easy to config
- It is simpliest than SOAP


## Htttp requests and responses

On Web, clients-server comunication with the protocol Http, which rule the way the client make his requests and how the server give the different responses. For requests and responses there are some methods which are "universal" in most of APIs

**Note:** an **Stateless Http protocol** means that the Http protocol is not retaining the identity of every client on its memory. In other words, server are not capable of identifying every client, and therefore treats every request from client like a new request and maybe, it requieres an authentication for every one.


## HTTP status codes

The HTTP status codes let us to know the status of a specific request made by the Client. The posible answer are grouped in five (5) different classes:

- **1xx:** These are informational responses, which let us to know that the request was received and it is still processing the answer
- **2xx:** These are succesfull responses, which let us to know that the request was successfully received, understood and accepted
- **3xx:** These are redirection responses, which let us to know that further actions need to be taken in order to complete the request
- **4xx:** These are client error responses, which let us to know that the request contains bad syntax or cannot be fulfilled
- **5xx:** These are server error responses, which let us to know if the server had failed to fulfil an aparently valid request


## Http Methods

Http define a set of "requests methods" to clarify the action the client needs a resource to do. It is often called *Http verbs* Every methods has a different semantic but the y share some characteristics as safety, idempotency and cacheable.

### Characteristics of Http Methods

- **Safe:** An Http method is safe if it does not alter the state of the server. In other words, a method is safe if it leads to a read-only operation. `GET`, `HEAD`, or `OPTIONS` are safe methods. We can say that **All safe methods are idempotent, but not all idempotent methods are safe**. For example, `PUT` and `DELETE` are both idempotent but unsafe.


- **Idempotent:** An Http method is idempotent if an identical request can be made once or several times in a row with the same effect while leaving the server in the same state. In other words, an idempotent method should not have any side-effects.`GET`, `HEAD`, `PUT` and `DELETE` are considered idempotent methods if these are implemented correctly. `POST` is not consedered an idempotent method. 

    `GET /pageX HTTP/1.1` repeatedly is considered an idempotent method because client always gets the same result.

- **Cacheable:** A cacheable response is an Http response that can be cached, that is stored to be retrieved later, saving a new request to the server. Not all Http responses can be cached. `GET` and `HEAD` are cacheable methods. A response to `POST` or `PATCH`request cal also be cached if freshness is indicated and the `Content-Location` header is set, but this is not common. `PUT` and `DELETE` are **NOT** cacheable. On the other hand, some status code of the response are cacheable, for example `200`,`203`,`204`,`206`,`300`,`301`,`404`,`405`,`410`,`414` and `501`.

    There are specific headers in the response, like `Cache-Control` that prevents caching.
    
### Methods

![Ilustracion](https://yosoy.dev/wp-content/uploads/2017/12/HTTP.jpg)

- **`GET`:** This method requests a representation of the specified resource. This is the primary method of information retrieval and the focus od almost all performance optimizations. Requests using `GET` should only be used to request data (they should not include data).

    **Characteristics:**

    - Request does not have body
    - Succesfull response has body
    - Is Safe, Idempotent and Cacheable
    - Allowed in Html forms
    - Compatible with Chrome, Firefox, Edge (12), Internet Explorer, Opera, Safari
    - Mobile compatible with WebView Android, Chrome Android, Firefox Android, Opera Android, Safari iOS, Samsung Internet
    
    **Syntax:** 
    
    `GET /index.html`
    


- **`HEAD`:** This method requests the headers that would be returned if the `HEAD` request's URL was instead requested with the Http `GET` method. For example, if a URL might produce a large download, a `HEAD` request could read its `Content-Lenght`header to check the filesize without downloading the file. It is identical to `GET` method except that the server MUST NOT send a message body in the response

    **Characteristics:**

    - Request does not have body
    - Succesfull response does not have body
    - Is Safe, Idempotent and Cacheable
    - Not Allowed in Html forms
    - Compatible with Chrome, Firefox, Edge (12), Internet Explorer, Opera, Safari
    - Mobile compatible with WebView Android, Chrome Android, Firefox Android, Opera Android, Safari iOS, Samsung Internet
  
    **Syntax:**
    
    `HEAD /index.html`


- **`POST`:** This method sends data to the server. The type of the body of the requests is indicated by the `Content-Type` header. The difference between `POST` and `PUT` is that `PUT` is idempotent, I mean, calling this method several times has the same efect on the server. where successive identical `POST` request may have additional effects, like passing an order several times.

    A `POST` request is tipically sent via an HTML form and resultss in a change on the server. This method is used for the following functions:
    
    - Providing a block of data, such as the fields entered into an HTML form, to a data handling process
    - Posting a message to a bulletin board, newsgroup, mailing list, blog or similars
    - Creating a new resource that has yet to be identified by the origin server
    - Appending data to a resource exisiting representations
    
    **Characteristics:**
    
    - Request has body
    - Succesfull response has body
    - Not Safe, Not Idempotent and only Cacheable if freshness information is included
    - Allowed in Html forms
    - Compatible with Chrome, Firefox, Edge (12), Internet Explorer, Opera, Safari
    - Mobile compatible with WebView Android, Chrome Android, Firefox Android, Opera Android, Safari iOS, Samsung Internet    
    
    **Syntax:**
    
    `Post /test`
    
    Using the default `application/x-www-form-unlencoded`
    
    ``` 
    POST /test HTTP/1.1
    User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT
    Host: foo.example
    Content-Type: application/x-www-form-unlencoded
    Content-Length: 27
    Accept-Language: es-mx
    Accept-Encoding: gzip, deflate
    Connection: Keep-Alive
    
    field=value1&field2=value2 
    
    ```
    
    A form using `multipart/form-data`
    
    ```
    POST /test HTTP/1.1
    Host: foo.example
    Content-Type: multipart/form-data;boundary="boundary"
    
    --boundary
    Content-Disposition: form-data; name="field1"
    
    value1
    --boundary
    Content-Disposition: form-data; name="field2"; filename="example.txt"
    
    value2
    --boundary--
    ```
    
- **`PUT`:** this method creates a new resource or replaces a representation of the targer resource with the request playload. 

    **Characteristics:**
    
    - Request has body
    - Succesfull response does not have body
    - Not Safe, Not Cacheable
    - Idempotent
    - Not Allowed in Html forms
    - Compatible with Chrome, Firefox, Edge (12), Internet Explorer, Opera, Safari
    - Mobile compatible with WebView Android, Chrome Android, Firefox Android, Opera Android, Safari iOS, Samsung Internet 

    **Syntax:**
    
    `PUT /new.html HTPP/1.1`
    
    Example
    
    The client request the `PUT` method shown bellow
    
    ```
    PUT /index.htm HTTP/1.1
    User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT
    Host: www.sdlsjdskdj.com
    Accept-Language: es-mx
    Connection: Keep-Alive
    Content-Type: text/html
    Content-Length: 182
    ```
    
    The server gives the next answer:
    
    ```
    HTTP/1.1 201 Created
    Date: Wed, 07 Apr 2021 10:32:45 GMT
    Server: Apache/2.2.12 (Win32)
    Content-Type: text.html
    Content-Length: 30
    Connection: Closed
    ```
    
- **`DELETE`:** this method deletes the specified resource

    **Characteristics:**
    
    - Request may have body
    - Succesfull response may have body
    - Not Safe, Not Cacheable
    - Idempotent
    - Not Allowed in Html forms
    - Compatible with Chrome, Firefox, Edge (12), Internet Explorer, Opera, Safari
    - Mobile compatible with WebView Android, Chrome Android, Firefox Android, Opera Android, Safari iOS, Samsung Internet 
    
    **Syntax:**
    
    `DELETE /file.html HTPP/1.1`
    
    Example
    
    The client request the `DELETE` method shown bellow
    
    ```
    DELETE /hello.htm HTTP/1.1
    User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT
    Host: www.sdlsjdskdj.com
    Accept-Language: es-mx
    Connection: Keep-Alive 
    ```
    
    The server gives the next answer:
    
    ```
    HTTP/1.1 200 Ok
    Date: Wed, 07 Apr 2021 10:32:45 GMT
    Server: Apache/2.2.12 (Win32)
    Content-Type: text.html
    Content-Length: 30
    Connection: Closed
    ```
    
- **`PATCH`:** this method applies partial modifications to a resource. A `PATCH`request is considered s aset of instructions on how to modify a resource. This method conrast with `PUT` method, which is a complete representation of a source. For example, if an auto-incrementing counter field is an integral part of the resource, then a `PUT` will naturally overwrite it (since it overwrites everything), but not necessarily so fo `PATCH`

    **Characteristics:**
    
    - Request has body
    - Succesfull response has body
    - Not Safe, Not Cacheable, Not Idempotent
    - Not Allowed in Html forms
    - Compatible with Chrome, Firefox, Edge (12), Internet Explorer, Opera, Safari
    - Mobile compatible with WebView Android, Chrome Android, Firefox Android, Opera Android, Safari iOS, Samsung Internet 
    
    **Syntax:**
    
    `PATCH /file.txt HTTP/1.1
    
    Example
    
    The client request the `PATCH` method shown bellow
    
    ```
    PATCH /file.txt HTTP/1.1
    User-Agent: Mozilla/4.0 (compatible; MSIE5.01; Windows NT
    Host: www.sdlsjdskdj.com
    Content-Type: application/example
    If-Match: "e0023aa4e
    Content-Length: 100
    
    [description of changes]
    ```
    
    The server gives the next answer:
    
    ```
    HTTP/1.1 204 No Content
    Content-Location: /file.txt
    ETag: "e0023aa4f
    ```

## Maturity Model (Richardson Model)


It was developed by Leonard Richardson and he analized how different web services were designed. He divided every WS into four categories based on how much they are REST compliant. 

This model used three (3) different factors to decide the maturity of a service:

- URI: is a unique sequence of characters that identifies a logical or physical resource used by Web technologies. For example

    `https://jhon.doe@www.example.com:123/forum/questions/?tag=networking&order=newest#top`
    
    Where
    
    - scheme: `https`
    - userinfo: `jhon.doe`
    - host: `@www.example.com`
    - port: `123`
    - path: `forum/questions`
    - query: `tag=networking&order=newest`
    - fragment: `top`
    
    Note that authority es equivalent to userinfo plus host plus port

- HTTP methods: which are described before.
- Hypermedia: often called HATEOAS, which is letting the client a easy way to connect to the application. The relation between client-server is made dinamically and client have not to code the URI structures for various resources.

The level of Richardson model are:

1. Level Zero: on this level of maturity does not make use of any URI, Http methods and HATEOAS capabilities.
2. Level One: on this level of maturity makes use of URIs out of URI, Http methods and HATEOAS capabilities. This service employ many URIs but only a single HTTP verb - generally `POST`.
3. Level Two: on this level of maturity makes use of URIs and HTTP out of URI, Http methods and HATEOAS capabilities. This level host numerous URI-adressable resources.  Such services support several of HTTP verbs on each exposed resource - (CRUD) `CREATE`, `READ`, `UPDATE`, `DELETE`, which analogues are `POST`, `GET`, `PATCH` or `PUT`,`DELETE`.
4. Level Three: on this level of maturity makes use of all three factors . In this level it is easy for the responses to be self-explanatory by using HATEOAS


## How to build APIs

![ilustracion](https://www.mindk.com/blog/wp-content/uploads/2019/07/Continuous-integration-min.png)

APIs are everywhere, They help us integrate third-party features, connect enterprise systems, and exchange data between apps. Knowing how to create an API can give us a number of advantages like higher develpoment speed, streamlined architecture, better scalability with microservices, simpler integrations, easier testing, better security, among others.

To build an API it's necessary to follow the new steps:

1. Gather requirements: Defining objectives let you to know who are going to benefit from the API, how can incorporate their need to the API, what tools I am going to need to provide along with the API, among other questions.

2. Design an API: Before writing the first line of code, it is necessary to define the requirements and reflects that API will consume, as setting the architecture of the API, for example: security, testabilitty, scalability, reliability, usability.

    It is also important to separate API design into several layer, like Client, Validation Layer, Caching Layer, Orchestration Layer and Business Logic.  

3. Implement: Build API endpoints that are URLs that return different responses depending the method used in the request. Also it is important to handle exceptions and errors as the Http status code shown before. Use throttling, because sudden increases in traffic can disrupt the API; to prevent this, it is common to use **traffic cuotas** which are a rate or a maximun of requests per time. 

4. Test: Is too important to test validation, functionability, reliability, load, security, among others

5. Monitor and iterate: Monitor the success metrics as API uptime, requests per month, monthly unique users, response times, among others.


## SOAP

As REST, SOAP is a Web communication protocol. It is commonly used to expose web services and transmit data over HTTP/HTTPS. Soap works only with XML, I mean, JSON files are not allowed on this architecture.

|Simple Object Access Protocol (SOAP)|Representational State Transfer (REST)|
-------------------------------------------------|---------------------------
|Provides data as services (i.e. verbs + nouns).|Provides data as representations of resources (i.e. nouns).|
|Uses a verbose XML data format for communication that consumes more bandwidth.|	Uses a variety of data formats including JSON, XML, HTML, and plain text.|
|An official protocol with strict guidelines.|	A flexible architectural style with a number of loose guidelines.|
|Works with application layer protocols like HTTP, UDP, and SMTP.|	Works only with HTTP.|
|Requests can’t be cached.|	Requests can be cached.|
|Requires detailed API contracts.|	No detailed contracts needed.|
|Has built-in security, error handling, and authorization.|	Developers have to take care of security, error handling, and authorization themselves.|
|Benefits: higher security and extensibility.|	Benefits: higher performance, scalability, and flexibility.|
