## Http - hypertext transfer protocol

**HTTP** stands for **H**yper **T**ext **T**ransfer **P**rotocol

**WWW** is about communication between web **clients** and **servers**

Communication between client computers and web servers is done by sending **HTTP Requests** and receiving **HTTP Responses** 

[from w3schools](https://www.w3schools.com/whatis/whatis_http.asp)

![](https://mdn.mozillademos.org/files/13827/HTTPMsgStructure2.png)

[from MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Messages)

#### Request Methods

##### GET

- requesting the server for a specific information on response
- request body is almost never sent
- for example, when looking up login ID

##### POST

- requesting the server to make something on the server side
- request body is usually sent with the header
- for example, when creating an account.

##### PUT

- requesting the server to revise something on the server side
- request body is usually sent with the header
- for example, when resetting the password

##### DELETE

- requesting the server to delete something on the server side.
- for example, when removing an account



#### Request Headers

##### Content-Type

The purpose of the Content-Type field is to describe the data contained in the body fully enough that the receiving user agent can pick an appropriate agent or mechanism to present the data to the user, or otherwise deal with the data in an appropriate manner.

[reference](https://www.w3.org/Protocols/rfc1341/4_Content-Type.html)

---

##### Accept

The **Accept** request HTTP header advertises which content types, expressed as [MIME types](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types), the client is able to understand. Using [content negotiation](https://developer.mozilla.org/en-US/docs/Web/HTTP/Content_negotiation), the server then selects one of the proposals, uses it and informs the client of its choice with the [`Content-Type`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Type) response header.

[reference](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/setRequestHeader)

---

##### MIME type

A **media type** (also known as a **Multipurpose Internet Mail Extensions or MIME type**) is a standard that indicates the nature and format of a document, file, or assortment of bytes. 

examples

| type           | subtype                                            |
| -------------- | -------------------------------------------------- |
| text           | text/plain, text/html, text/css, text/javascript   |
| application    | application/json, application/x-www-form-urlencode |
| uploading file | multipart/formed-data                              |

[reference](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types)

---

