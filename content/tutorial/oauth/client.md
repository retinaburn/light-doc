---
title: "Client"
date: 2017-11-10T14:50:54-05:00
description: ""
categories: []
keywords: []
slug: ""
aliases: []
toc: false
draft: false
---

Every client that accesses service(s) must register itself in order to get
access token during runtime from OAuth 2.0 provider. If it happens that the client is
an service and some other client is calling it. This particular API need to register
itself twice. One as a client and one as a service. 

The client service provide endpoint to create a new client, update an existing client and
delete a client. Here we have the services accessed by curl command for demo purpose. In
reality, these APIs will be accessed from light-portal UI. 


To add a new client.

```
curl -k -H "Content-Type: application/json" -X POST -d '{"clientType":"public","clientProfile":"mobile","clientName":"AccountViewer","clientDesc":"Retail Online Banking Account Viewer","scope":"act.r act.w","redirectUri": "http://localhost:8080/authorization","ownerId":"admin"}' https://localhost:6884/oauth2/client
```

And here is the result with client_id and client_secret.

```
{"clientDesc":"Retail Online Banking Account Viewer","clientType":"public","clientProfile":"mobile","redirectUri":"http://localhost:8080/authorization","clientId":"e24e7110-c39f-49f1-85eb-8434cb577482","clientName":"AccountViewer","scope":"act.r act.w","clientSecret":"YDJLse8SQRapHyoMsdPUig","ownerId":"admin","createDt":"2016-12-31"}
```

To query all clients.

```
curl -k https://localhost:6884/oauth2/client?page=1

```
And here is the result.

```
[{"clientDesc":"PetStore Web Server that calls PetStore API","clientId":"f7d42348-c647-4efb-a52d-4c5787421e72","clientType":"public","clientProfile":"mobile","redirectUri":"http://localhost:8080/authorization","clientName":"PetStore Web Server","scope":"petstore.r petstore.w","ownerId":"admin","updateDt":null,"createDt":"2016-12-31","authenticateClass":null},{"clientDesc":"Retail Online Banking Account Viewer","clientId":"9ef89c7b-f17b-4a64-a24b-ce539ed80641","clientType":"public","clientProfile":"mobile","redirectUri":"http://localhost:8080/authorization","clientName":"AccountViewer","scope":"act.r act.w","ownerId":"admin","updateDt":null,"createDt":"2016-12-31","authenticateClass":null}]
```

To query a client by id.

```
curl -k https://localhost:6884/oauth2/client/f7d42348-c647-4efb-a52d-4c5787421e72
```

And here is the result.

```
{"clientDesc":"PetStore Web Server that calls PetStore API","clientId":"f7d42348-c647-4efb-a52d-4c5787421e72","clientType":"public","clientProfile":"mobile","redirectUri":"http://localhost:8080/authorization","clientName":"PetStore Web Server","scope":"petstore.r petstore.w","clientSecret":"f6h1FTI8Q3-7UScPZDzfXA","ownerId":"admin","updateDt":null,"createDt":"2016-12-31","authenticateClass":null}
```

To update a client with a shorter clientDesc.

```
curl -k -H "Content-Type: application/json" -X PUT -d '{"clientDesc":"PetStore Web Server","clientId":"f7d42348-c647-4efb-a52d-4c5787421e72","clientType":"public","clientProfile":"mobile","redirectUri":"http://localhost:8080/authorization","clientName":"PetStore Web Server","scope":"petstore.r petstore.w","clientSecret":"f6h1FTI8Q3-7UScPZDzfXA","ownerId":"admin","updateDt":null,"createDt":"2016-12-31","authenticateClass":null}' https://localhost:6884/oauth2/client
```

To delete a client with client id.

```
curl -k -X DELETE https://localhost:6884/oauth2/client/9ef89c7b-f17b-4a64-a24b-ce539ed80641

```

