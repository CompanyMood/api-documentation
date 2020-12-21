# Comments (for chat)

## Create a new comment for a discussion

```http
POST /comments HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
Authorization: Bearer 795665b4-53da-468c-a0d7-ab2d82e58406
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db

{
  "data" : {
    "type": "comments",
    "attributes": {
      "discussion_id": "679c5ffb-2d81-4608-8c4d-0f373b6f1401",
      "comment": {
        "content": "Happy to hear from you."
      }
    }
  }
}
```

```http
HTTP/1.1 201 CREATED
Content-Type: application/json

{
  "data": {
    "id": "8437",
    "attributes": {
      "content": "Happy to hear from you.",
      "created_at": "10.09.2020",
      "author_name": "Anonym",
      "author_image": "/assets/defaults/user/mini-avatar-287e30a2e7e10a75d7afc0731799d16a58ce47c07b14fb3e8af573b9dac8f0c4.png"
    },
    "type": "comments"
  }
}
```

### POST Attributes

Parameter                   |          | Description
----------------------------|----------|------------
discussion_id               | required | Id of the discussion you want to post to
comment[content]            | required | Comment you want to post

### Response Attributes

Paramteter     | Description
---------------|------------
id             | Id of the comment
content        | Content of the comment
created_at     | Creation date of the comment
author_name    | Name of the comments creator
author_image   | Image URL of the comments creator
