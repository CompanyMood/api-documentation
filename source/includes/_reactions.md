
# Reactions

```http
POST /response_requests HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db

{
  "data": {
    "type": "response_requests",
    "attributes": {
      "commentable_id": "4123-s23awq-124fe2-1123q-4fr21",
      "commentable_type": "Reasoning",
      "user_id": "4312-s23awq-124fe2-1123q-4fr21"
    }
  }
}
```

```http
HTTP/1.1 202 ACCEPTED
Content-Type: application/json
```

Create a response requests for a feedback (Reasoning, Suggestion)


## POST attributes

Parameter         | Description
------------------|------------
commentable_id    | ID/UUID of the resource to create the request for
reactionable_type | Type of the resource to create the reaction for (Reasoning, Suggestion)
user_id           | The users UID you want to request a response from
