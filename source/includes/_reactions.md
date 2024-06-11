
# Reactions

```http
POST /reactions HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db

{
  "data": {
    "type": "reactions",
    "attributes": {
      "reactionable_id": "4123-s23awq-124fe2-1123q-4fr21",
      "reactionable_type": "Task",
      "rating": "up"
    }
  }
}
```

```http
HTTP/1.1 202 ACCEPTED
Content-Type: application/json
```

Set a reaction for a resource (Task, Comment, Statement, EventPin)


## POST attributes

Parameter         | Description
------------------|------------
reactionable_id   | ID/UUID of the resource to create the reaction for
reactionable_type | Type of the resource to create the reaction for (Comment, Task, Statement, EventPin)
rating            | The reactions rating to set (up / down)
