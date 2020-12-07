# Discussions

## Retrieve the logged in users discussions
Discussions are the chats a user is participating in.

```http
GET /discussions HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
Authorization: Bearer 795665b4-53da-468c-a0d7-ab2d82e58406
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "data": [
     {
       "id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
       "type": "discussions",
       "attributes": {
         "name": "Workload"
       }
     }
  ]
}
```

### Response Attributes

Paramteter     | Description
---------------|------------
id             | id of the dicussion
TBD            | TBD


## Retrieve the data of a specific discussion including comments
Discussions are the chats a user is participating in.

```http
GET /discussions/f7559f2a-8f1c-461e-8a9b-7efea5564edb HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
Authorization: Bearer 795665b4-53da-468c-a0d7-ab2d82e58406
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "data": {
    "id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
    "type": "discussions",
    "attributes": {
      "name": "Workload"
    }
  }
}
```

### Response Attributes

Paramteter     | Description
---------------|------------
id             | id of the dicussion
TBD            | TBD
