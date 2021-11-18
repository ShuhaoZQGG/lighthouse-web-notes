### [Compass](https://web.compass.lighthouselabs.ca/days/w02d3)

### [Lecture](https://web.compass.lighthouselabs.ca/activities/153/lectures/4809)

### [Today's Work](https://github.com/ShuhaoZQGG/snake-client)

# **[HTTP Introduction](https://web.compass.lighthouselabs.ca/days/w02d3/activities/192)**

HTTP is a protocol used to read and write "resources" (data) in a simple text-based manner. It started off as being mostly used for HTML documents, but today it's used for all sorts of documents, like JavaScript files, CSS, and anything else that our browser is capable of downloading (PDFs, etc.).

# **HTTP Flow**

HTTP is a request-response based protocol. A client makes a request to an HTTP server, immediately also sending a message asking for a specific resource, which the server sends down as a response. A server cannot send a response to a client if the client has not first sent a request.

MDN's HTTP Overview document contains a good bit on this.

# **HTTP Requests**

As we read in the MDN article, when a client wants to communicate with a server it issues a **request**. An HTTP request is made up of many components, but there are only two parts that we need to pay attention to right now: the **PATH** and the **METHOD**. The path says what resource the client wants to act on, and the method says what action it would like to perform.

# **HTTP Methods**

There are 9 HTTP request methods, but we only need to consider 4 of them right now:

- `GET`: used to "get" some data from the server
- `POST`: usually used to create some new data
- `PUT`: generally used for editing existing data on the server
- `DELETE`: used to delete some existing data