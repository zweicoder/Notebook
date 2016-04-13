# How RESTful client side auth is done

### **TL;DR - Save credentials / token in client side and send with every request to the REST API**

> Let's look at how plain old authentication works first.

>- The user connects to `https://example.com`
- The server serves a rich Javascript application which renders the initial page. Somehwere in the page there is a login form.
- Many of the sections of this single page app haven't been populated with data due to the user not being logged in. All these sections have an event listener on a "login" event. All this is client side stuff, the server does not know of these events.
- User enters his/her login and password and hits the submit button, which triggers a Javascript handler to record the username and password in client side variables. Then this handler triggers the "login" event. Again, this is all client side action, **credentials were not sent to the server yet**.
- The listeners of the "login" event are invoked. Each of these now needs to send one or more requests to the RESTful API at `https://example.com/api` to obtain the user specific data to render on the page. Every single request they send to the web service will include the username and password, possibly in the form of HTTP [Basic](http://en.wikipedia.org/wiki/Basic_access_authentication) authentication, since the service being RESTful isn't allowed to maintain client state from one request to the next. Since the web service is on secure HTTP the password is safely encrypted during transit.
- The web service at `https://example.com/api` receives a bunch of individual requests, each with authentication information. The username and password in each request is checked against the user database and if found correct the requested function executes and data is returned to the client in JSON format. If username and password do not match an error is sent to the client in the form of a 401 HTTP error code.
- Instead of forcing clients to send username and password with every request you can have a "get_access_token" function in your RESTful service that takes the username and password and responds with a token, which is some sort of cryptographic hash that is unique and has some expiration date associated with it. These tokens are stored in the database with each user. Then the client sends the access token in subsequent requests. The access token will then be validated against the database instead of the username and password.
- Non browser client applications like phone apps do the same as above, they ask user to enter his/her credentials, then send them (or an access token generated from them) with every request to the web service.

The important take away point from this example is that **RESTful web services require authentication with every request**.
