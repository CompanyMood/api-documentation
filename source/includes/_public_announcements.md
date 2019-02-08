# Public Announcements

## Get all public announcements

```http
GET /public_announcements HTTP/1.1
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
      "type": "public-announcements",
      "attributes": {
        "creator_name": "Jovanni Williamson",
        "content": "Awesome public announcement",
        "task_id": "a9767fd1-a187-40e2-954c-872cebff5e70",
        "own_reaction": "up",
        "reaction_counts": {
          "up": 15,
          "down": 2
        },
        "created_at": "2018-06-25T11:18:42.517Z"
      }
    },
    {
      "id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
      "type": "public-announcements",
      "attributes": {
        "creator_name": "Sammy Nonetti",
        "content": "We created a survey for our upcoming team event. Please participate.",
        "task_id": "e96afc28-f27e-49b9-9f27-94dd3e2a296b",
        "own_reaction": null,
        "reaction_counts": {
          "up": 8,
          "down": 1
        },
        "created_at": "2018-05-25T19:12:32.212Z"
      }
    }
  ]
}

```

Get all public announcements which are accessible by the current user.

### Response Attributes

Paramteter            | Description
----------------------|------------
id                    | ID of the public announcement.
creator_name          | Name of announcement creator.
content               | Content of the public announcement.
task_id               | ID of the associated Task.
own_reaction          | The reaction of the current user. Can be "up", "down" or null.
reaction_counts       | An Object with details for "up" and "down" reactions.
reaction_counts[up]   | Amount of up votes.
reaction_counts[down] | Amount of down votes.
created_at            | Date of the public announcement creation (in ISO8601)

## Create announcement reaction

```http
POST /public_announcements/f7559f2a-8f1c-461e-8a9b-7efea5564edb/reactions HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
Authorization: Bearer 795665b4-53da-468c-a0d7-ab2d82e58406
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db

{
  "data" : {
    "type": "public-announcements",
    "attributes": {
      "reaction": "down"
    }
  }
}
```

```http
HTTP/1.1 201 CREATED
Content-Type: application/json

{
  "data": {
    "id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
    "type": "public-announcements",
    "attributes": {
      "creator_name": "Jovanni Williamson",
      "content": "Awesome public announcement",
      "task_id": "a9767fd1-a187-40e2-954c-872cebff5e70",
      "own_reaction": "down",
      "reaction_counts": {
        "up": 14,
        "down": 3
      },
      "created_at": "2018-06-25T11:18:42.517Z"
    }
  }
}
```

React on public announcements with an "up" or "down" vote.

### POST attributes

Paramteter       | Description |
-----------------|-------------
reaction         | The reaction key. Can be "up" or "down".

### Response Attributes

Paramteter            | Description
----------------------|------------
id                    | ID of the public announcement.
creator_name          | Name of announcement creator.
content               | Content of the public announcement.
task_id               | ID of the associated Task.
own_reaction          | The reaction of the current user. Can be "up", "down" or null.
reaction_counts       | An Object with details for "up" and "down" reactions.
reaction_counts[up]   | Amount of up votes.
reaction_counts[down] | Amount of down votes.
created_at            | Date of the public announcement creation (in ISO8601)
