# **What is CORS?**

> *Have you ever thought of what actualluy happens when you add a link to an unsplash image to your website. Or when you try to use a google font in your website by adding the generated link to the head tag? Its all possible by a mechanism called **CORS** What is this thing, and how does it work and why is it important?*

CORS stands for Cross Origin Resource Sharing. It's a mechanism that enables resources to be shared between different urls (or "origins"). By default, every browser use what called the Same Origin Policy (SOP) which allows a client to access data from a server with the same origin and blocks every request that is from a client with from a different origin. This is one of the reasons why we sometimes get a broken image from a url instead of the real image. The reason for this is that the images server, for instance doesn't have the url of your client on its list of valid clients who can access their images.

  Trying to access information from a server who doesn't have CORS enabled
or, does have your url in their list of valid clients will show the      `Cross-Origin Request Blocked`  error to the server.

## How does CORS work under the hood?

It works by "preflighting" the request before the request even gets to the server. What is this "preflighting"? It is when the browser of the client asks the server if it has the client's url in its list of valid clients. If the url is found, the server adds a particular header known as the `Access-Control-Allow-Origin` header to the request from the client through the client's browser. Then the request will be made. If the url is not found, the request will not be made.

## How can you enable CORS for your server

Below is how to add CORS to your express server.

To make a particular url a allowed client for your server;

``` javaScript
const cors = require ('cors');

app.use(cors({
    origin:['https://allowed-client1.com', 'https://allowed-client2.com', ...]
}))
```

You can also allow every client to access your server by replacing the array with `"*"`. This is not reccomended for reasons that will be stated in the later parts of this article.

## Why is CORS so cool?

The main reason why cors is important is because of its security measures. The way its preflights a request before it accepts it makes it nearly impossible to invade a server for malicious reasons. Also if it was not because of CORS, all our webpages would be in the primitive Times New Roman.


The End.

Written by [Kwabena Boakye](https://twitter.com/PapaYiadom)