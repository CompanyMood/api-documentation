# Suggestions

## Create suggestion

```http
POST /suggestions HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
Authorization: Bearer 795665b4-53da-468c-a0d7-ab2d82e58406
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db

{
  "data" : {
    "type": "suggestions",
    "attributes": {
      "content": "Free coffee plz!",
      "feeling": "happy",
      "custom_tag_id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
      "not_anonymous": false
    }
  }
}
```

```http
HTTP/1.1 201 CREATED
Content-Type: application/json

{
  "data": {
    "id": "e23sed23-f27e-49b9-9f27-94dd3e2a296b",
    "type": "suggestions",
    "attributes": {
      "content": "Free coffee plz!",
      "feeling": "happy",
      "custom_tag_id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
      "not_anonymous": false,
      "created_at": "2018-06-25T11:18:42.517Z"
  }
}
```

Creates a suggestion for the current user with the given details.

You MUST provide a `feeling`, `content` and a `custom_tag`.
The suggestion will be anonymous by default if you don't provide
a `not_anonymous` parameter.

### POST Attributes

Paramteter       |          | Description
-----------------|----------|-------------
content          | required | The suggestion content.
feeling          | required | Feeling of the suggestion can be ("sad", "unhappy", "ok", "satisfied", "happy").
custom_tag_id    | required | ID of the custom tag for the suggestion.
not_anonymous    | optional | Create not anonymous suggestion. True or false. False if not given.

### Response Attributes

Paramteter         | Description
-------------------|------------
content            | The suggestion content
feeling            | Feeling of the suggestion can be ("sad", "unhappy", "ok", "satisfied", "happy")
custom_tag_id      | ID of the custom tag for the suggestion
not_anonymous      | Boolean value. Displays if suggestion is anonymous or not
created_at         | Date of the suggestion creation (in ISO8601)
