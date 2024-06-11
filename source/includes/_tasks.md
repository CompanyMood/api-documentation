# Tasks

## Get all tasks for current user

Get all tasks for the current user which are not archived.

```http
GET /tasks HTTP/1.1
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
       "type": "tasks",
       "attributes": {
         "name": "Implement CompanyMood",
         "description": "Implement continuous Mood monitoring",
         "percent": 100,
         "state": "implemented",
         "published": true,
         "created_at": "2018-03-11",
         "reaction_counts": {
           "up": 5,
           "down": 1
         }
       }
     },
     {
       "id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
       "type": "tasks",
       "attributes": {
         "name": "Teamevent",
         "description": "Big office party",
         "percent": 10,
         "state": "idea",
         "published": false,
         "created_at": "2018-03-15",
         "reaction_counts": {
           "up": 12,
           "down": 4
         }
       }
     }
  ]
}
```

### Response Attributes

Paramteter       | Description
-----------------|------------
id               | id of the task
name             | Name of the task
description      | Description of the task
percent          | Progress of the task in percent
state            | State of the task
published        | Did this task got published to all affected users?
created_at       | create at date of task
