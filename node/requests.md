# Requests in Node.js

When you create a server in Node.js, the callback function (which is often abstracted into a separate file called `app.ts` or `app.js`) handles each incoming request to that server.

```javascript
const http = require("node:http");

const server = http.createServer((request, response) => {
  // This function handles each incoming request
});
```

## Request Object Structure

The `request` parameter is an instance of `http.IncomingMessage`. This object is created by the `http.Server` when it receives an HTTP request.

### Key Properties and Methods

- `req.method`: The HTTP method (GET, POST, PUT, DELETE, etc.)
- `req.url`: The request URL string
- `req.headers`: Object containing all request headers
- `req.httpVersion`: HTTP version of the request

### Headers

Headers can be accessed via `req.headers`, which returns an object with lowercase header names:

```javascript
console.log(req.headers);
// Prints something like:
// {
//   'user-agent': 'curl/7.22.0',
//   'host': '127.0.0.1:8000',
//   'accept': '*/*',
//   'authorization': 'Bearer eyJhbGciOiJIUzI1...'
// }
```

For authentication, the `Authorization` header is particularly important:

```javascript
const authHeader = req.headers.authorization || req.headers["authorization"];
// For Bearer token: 'Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6...'
```

### Request Body Handling

For handling request bodies (in POST/PUT requests):

```javascript
// Using event-based approach in native Node.js
let body = "";
request.on("data", (chunk) => {
  body += chunk.toString();
});

request.on("end", () => {
  const data = JSON.parse(body);
  // Process the data
});
```

## Express vs. Native HTTP

Express.js extends the native Node.js request object with additional functionality:

```javascript
// Express middleware for parsing JSON bodies
app.use(express.json());

// Then in your route handler:
app.post("/api/users", (req, res) => {
  // req.body is already parsed
  const { username, password } = req.body;
});
```

Express adds these helpful properties:

- `req.body`: Contains parsed request body (requires middleware)
- `req.params`: Contains route parameters
- `req.query`: Contains URL query parameters
- `req.cookies`: Contains cookies (requires cookie-parser middleware)

## Example HTTP Request

A typical HTTP request looks like this:

```
GET /home.html HTTP/1.1
Host: developer.mozilla.org
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:50.0)
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Referer: https://developer.mozilla.org/testpage.html
Connection: keep-alive
Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...
```

For authenticated requests, the Authorization header must contain the JWT token using the Bearer scheme.

### Sources

- [Anatomy of an http transaction](https://nodejs.org/en/learn/modules/anatomy-of-an-http-transaction)
- [http request headers](https://nodejs.org/api/http.html#http_request_headers)
- [express: and properties of request](https://expressjs.com/en/api.html#req.app)
