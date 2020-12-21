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
      "relationships": {
        "discussable": {
          "data": {
            "id": "679c5ffb-2d81-4608-8c4d-0f373b6f1401",
            "type": "discussable"
          }
        }
      },
      "id": "d26e8fb7-0290-4573-bd8f-cfd8ec39c485",
      "type": "discussions"
    },
    {
      "relationships": {
        "discussable": {
          "data": {
            "id": "83524eec-aa43-42c6-adba-74afa5f74b8d",
            "type": "discussable"
          }
        }
      },
      "id": "561d35fd-a97f-4270-951f-6c425393abe2",
      "type": "discussions"
    }
  ],
  "included": [
    {
      "id": "679c5ffb-2d81-4608-8c4d-0f373b6f1401",
      "attributes": {
        "feeling": "ok",
        "reason": "A bit rugh atm",
        "custom_tag_id": 25540,
        "created-at": "2020-09-04",
        "last_comment": "I'm sorry. 😘",
        "user_name": "Anonymous"
      },
      "type": "discussable"
    },
    {
      "id": "83524eec-aa43-42c6-adba-74afa5f74b8d",
      "attributes": {
        "feeling": "satisfied",
        "reason": "Finished some nice features! ",
        "custom_tag_id": 25538,
        "created-at": "2020-08-19",
        "last_comment": "🤩",
        "user_name": "Anonymous"
      },
      "type": "discussable"
    }
  ]
}
```

### Response Attributes

Paramteter     | Description
---------------|------------
id             | id of the dicussion
relationships  | object with id and type of the discussable (the resource, the discussion is about)

#### Included Attributes

Parameter      | Description
---------------|------------
id             | Id of the discussed resource
feeling        | Felling key of the discussed resource
reason         | COntent of the discussed resource
custom_tag_id  | Id of the custom tags discussed resource
created_at     | Creation date of the discussed resource
last_comment   | Last comment on the discussion
user_name      | User name of the creator of the discussed resource



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
