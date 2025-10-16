# 🌿 API Quick Reference

---

## <span style = "color:hotpink">✨ HTTP Verbs </span>

!!! info "GET"
    🟠 **GET:** Retrieve data from the server.

!!! success "POST"
    🟢 **POST:** Send data to the server to create a resource.

!!! warning "PUT"
    🔵 **PUT:** Send data to the server to update a resource.

!!! danger "DELETE"
    🔴 **DELETE:** Delete a resource from the server.

!!! info "PATCH"
    🟠 **PATCH:** Send data to the server to update a resource partially.

!!! info "TRACE"
    🟠 **TRACE:** Returns the full HTTP Request received by the server for debugging.

!!! info "OPTIONS"
    🟠 **OPTIONS:** Returns the HTTP methods supported by the server for the request URL.

!!! info "CONNECT"
    🟠 **CONNECT:** Converts the request connection to a transparent TCP/IP tunnel for secure communication.

!!! warning "PURGE"
    🟡 **PURGE:** Invalidates a cached resource.

!!! warning "LOCK"
    🟡 **LOCK:** Locks the resource for exclusive use by the client.

!!! warning "UNLOCK"
    🟡 **UNLOCK:** Unlocks the resource previously locked by the client.

!!! info "MKCOL"
    🟠 **MKCOL:** Creates a new collection resource.

!!! info "COPY"
    🟠 **COPY:** Copies the resource identified by the request-URI to the destination URI.

---

## ✨ HTTP Status Codes

!!! info "Informational"
    - **100:** Informational.

!!! success "Success"
    - **200:** Success.

!!! warning "Redirection"
    - **300:** Redirection.

!!! danger "Client Errors"
    - **400:** Client errors.

!!! danger "Server Errors"
    - **500:** Server errors.

---

## ✨ Response Headers

!!! info "Content-type"
    🟠 **Content-type:** Specifies the MIME type of the data in the response body.

!!! info "Content-length"
    🟠 **Content-length:** Specifies the length of the response body in bytes.

!!! info "Cache-control"
    🟠 **Cache-control:** Specifies the caching behavior of the response.

!!! info "Location"
    🟠 **Location:** Specifies the URI of a resource to retrieve the request resource.

!!! info "Server"
    🟠 **Server:** Name and version of the server software generating the response.

!!! info "Access-control-allow-origin"
    🟠 **Access-control-allow-origin:** Which origins are allowed to access the resource.

!!! info "Set-cookie"
    🟠 **Set-cookie:** Specifies a cookie to be stored by the client and sent back with future requests.

!!! info "Expires"
    🟠 **Expires:** Date/time after which the response is considered stale.

!!! info "Last-modified"
    🟠 **Last-modified:** Date/time that the resource was last modified.

---

## ✨ API Design

!!! info "REST"
    🟠 **REST:** Representational State Transfer, a design pattern for building web services.

!!! info "SOAP"
    🟠 **SOAP:** Simple Object Access Protocol, a messaging protocol for exchanging structured data.

!!! info "GraphQL"
    🟠 **GraphQL:** A query language and runtime for building APIs.

!!! info "API Gateway"
    🟠 **API Gateway:** A service that manages, protects, and scales APIs.

---

## ✨ API Architectures

!!! info "SOA"
    🟠 **SOA:** Service-Oriented Architecture, a style for building distributed systems.

!!! info "Microservices"
    🟠 **Microservices:** An architectural style for building applications as a suite of small independent services.

!!! info "Serverless"
    🟠 **Serverless:** Cloud execution model where the provider manages infrastructure and resources automatically.

!!! info "Event-Driven"
    🟠 **Event-Driven:** Flow of data between components is triggered by events.

!!! info "RESTful API"
    🟠 **RESTful API:** Uses HTTP requests to GET, POST, PUT, and DELETE data.

---

## ✨ API Design Patterns

!!! info "Adapter Pattern"
    🟠 **Adapter Pattern:** Converts the interface of a class into another interface that clients expect.

!!! info "Decorator Pattern"
    🟠 **Decorator Pattern:** Adds behaviors to an individual object dynamically.

!!! info "Proxy Pattern"
    🟠 **Proxy Pattern:** Provides a surrogate or placeholder to control access to another object.

!!! info "Chain of Responsibility"
    🟠 **Chain of Responsibility Pattern:** Delegates commands to a chain of processing objects.

!!! info "Observer Pattern"
    🟠 **Observer Pattern:** Defines a one-to-many dependency between objects; dependents update automatically when the object changes.

---

## ✨ API Security

!!! info "OAuth"
    🟠 **OAuth:** Open standard for authorization used for protecting APIs.

!!! info "JWT"
    🟠 **JWT:** JSON Web Tokens, a standard for securely transmitting information between parties.

!!! info "SSL/TLS"
    🟠 **SSL/TLS:** Protocol for establishing a secure connection between client and server.

!!! info "API Key"
    🟠 **API Key:** Secret token limiting requests to an API over a period.

!!! info "OpenID Connect"
    🟠 **OpenID Connect:** Authentication layer on top of OAuth for multi-domain user auth.

!!! info "CORS"
    🟠 **Cross-Origin Resource Sharing (CORS):** Allows resources on a webpage to be requested from another domain.

---

## ✨ API Testing

!!! info "Postman"
    🟠 **Postman:** Popular tool for testing and debugging APIs.

!!! info "SoapUI"
    🟠 **SoapUI:** Tool for testing SOAP and REST web services.

!!! info "Swagger"
    🟠 **Swagger:** Tool for designing, building, and testing APIs.

!!! info "JMeter"
    🟠 **JMeter:** Tool for testing API performance.

!!! info "TestRail"
    🟠 **TestRail:** Test management tool for planning, executing, and tracking API tests.

!!! info "Dredd"
    🟠 **Dredd:** Command-line tool for testing API documentation against backend implementation.

!!! info "REST Assured"
    🟠 **REST Assured:** Java-based library for testing RESTful APIs.

!!! info "Karate DSL"
    🟠 **Karate DSL:** Testing framework for APIs using Gherkin syntax.

!!! info "HttpMaster"
    🟠 **HttpMaster:** Tool for testing and debugging APIs.

!!! info "Assertible"
    🟠 **Assertible:** Tool for testing and monitoring APIs with automated tests.
