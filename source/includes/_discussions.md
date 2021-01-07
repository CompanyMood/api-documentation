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
      "id": "d26e8fb7-0290-4573-bd8f-ffd8ec39c485",
      "attributes": {
        "unseen_comments_count": 0,
        "total_comments_count": 2,
        "last_comment_created_at": "2020-09-10",
        "last_comment": "I'm sorry. 😘",
        "sorting_score": 1599733045
      },
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
      "id": "561d35fd-a97f-4270-951f-5c425393abe2",
      "attributes": {
        "unseen_comments_count": 1,
        "total_comments_count": 5,
        "last_comment_created_at": "2020-09-10",
        "last_comment": "🤩",
        "sorting_score": 1999734045
      },
      "type": "discussions"
    }
  ],
  "included": [
    {
      "id": "679c5ffb-2d81-4608-8c4d-0f373b6f1401",
      "attributes": {
        "feeling": "ok",
        "reason": "A bit rugh atm",
        "custom_tag_id": "0e7f695f-d4b1-41a3-9796-51e2c459b6db",
        "created_at": "2020-09-04",
        "user_name": "Anonymous",
        "author_image": "https://cdn.company-mood.com/users/avatars/4faebf2cc1ed879d15f325a7b0dc74a7292c03e9/mini.jpg?1583853827",
        "department_name": "Development",
        "department_hirarchy": "IT > Development"
      },
      "type": "discussable"
    },
    {
      "id": "83524eec-aa43-42c6-adba-74afa5f74b8d",
      "attributes": {
        "feeling": "satisfied",
        "reason": "Finished some nice features! ",
        "custom_tag_id": "0e7f695f-d4b1-41a3-9796-51e2c459b6db",
        "created_at": "2020-08-19",
        "user_name": "Anonymous",
        "author_image": "https://cdn.company-mood.com/users/avatars/4faebf2cc1ed879d15f325a7b0dc74a7292c03e9/mini.jpg?1583853827",
        "department_name": null,
        "department_hirarchy": null
      },
      "type": "discussable"
    }
  ]
}
```

### Response Attributes

Paramteter              | Description
------------------------|------------
id                      | id of the dicussion
relationships           | object with id and type of the discussable (the resource, the discussion is about)
unseen_comments_count   | Count of unseen comments
total_comments_count    | Count of total comments
last_comment_created_at | Date of last comment
last_comment            | Last comment on the discussion
sorting_score           | Score used for sorting (unseen comments > new seen ones > old seen ones)

#### Included Attributes

Parameter           | Description
--------------------|------------
id                  | Id of the discussed resource
feeling             | Felling key of the discussed resource
reason              | COntent of the discussed resource
custom_tag_id       | Id of the custom tags discussed resource
created_at          | Creation date of the discussed resource
user_name           | User name of the creator of the discussed resource
user_image          | User image url
department_name     | Department name (without hirarchy)
department_hirarchy | Department name (with hirarchy)



## Retrieve the data of a specific discussion including comments
Discussions are the chats a user is participating in.

```http
GET /discussions/d26e8fb7-0290-4573-bd8f-ffd8ec39c485 HTTP/1.1
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
    "relationships": {
      "comments": {
        "data": [
          {
            "id": "8419",
            "type": "comments"
          },
          {
            "id": "8437",
            "type": "comments"
          }
        ]
      }
    },
    "id": "d26e8fb7-0290-4573-bd8f-ffd8ec39c485",
    "type": "discussions"
  },
  "included": [
    {
      "id": "8419",
      "attributes": {
        "content": "😢",
        "created_at": "09.09.2020",
        "author_name": "Markus Schwed",
        "author_image": "https://cdn.company-mood.com/users/avatars/4faebf2cc1ed879d15f325a7b0dc74a7292c03e9/mini.jpg?1583853827"
      },
      "type": "comments"
    },
    {
      "id": "8437",
      "attributes": {
        "content": "I'm sorry. 😘",
        "created_at": "10.09.2020",
        "author_name": "Anonym",
        "author_image": "/assets/defaults/user/mini-avatar-287e30a2e7e10a75d7afc0731799d16a58ce47c07b14fb3e8af573b9dac8f0c4.png"
      },
      "type": "comments"
    }
  ]
}
```

### Response Attributes

Paramteter     | Description
---------------|------------
id             | id of the dicussion
relationships  | Object with the id and type of discussions comments

#### Included Attributes

Parameter      | Description
---------------|------------
id             | Id of the comment
content        | Content of the comment
created_at     | Creation date of the comment
author_name    | Name of the comments creator
author_image   | Image URL of the comments creator
