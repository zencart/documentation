---
title: HTTP response codes 
description: What do 500, 404, 200 mean? 
category: troubleshooting
weight: 10
---

HTTP Response Codes come in ranges, the and most important digit in the range is the first (leftmost).  The ranges can be read as follows:

- 1xx: Hold on
- 2xx: OK: Here you go
- 3xx: Go away
- 4xx: You messed up 
- 5xx: I messed up 

## Code 1xx: Informational
1xx series messages just tell you the server is working on it - no status can be inferred from a message like this. 

## Code 2xx: Success
A code 200 is the ideal response; it means the request was successful. 

## Code 3xx: Redirection
These responses mean you are getting sent to another page, either temporarily or permanently.  

## Code 4xx: Client Error
The server is telling the client (the browser) it doesn't know what is being asked for (eg: not found), or the request is unauthorized.

## Code 500: Server Error
The server is telling the client it can't respond, but it's not the client's fault.  
These errors mean you need to check the logs.  See [500 errors](/user/troubleshooting/500_internal_server/) for more information.


