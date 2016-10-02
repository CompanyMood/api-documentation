# CustomTags

## Retrieve the tags pool for logged in user
Custom tags specify the tags you can use to describe your mood.  It's `id` and `name` is the same value.
Returns with an 401 if the user does not belong to a company.

```http
GET /custom_tags HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v1+json
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
       "type": "custom_tags",
       "attributes": {
         "name": "Workload",
         "de_translation": "Arbeitspensum",
         "en_translation": "Workload"
       }
     },
     {
       "id": "c23e5e7d-162f-4fdc-9243-5e6349ce2bd1",
       "type": "custom_tags",
       "attributes": {
         "name": "Private",
         "de_translation": "Privat",
         "en_translation": "Private"
       }
     },
     {
       "id": "a9767fd1-a187-40e2-954c-872cebff5e70",
       "type": "custom_tags",
       "attributes": {
         "name": "Management",
         "de_translation": "Vorgesetzte",
         "en_translation": "Management"
       }
     }
  ]
}
```

### Response Attributes

Paramteter     | Description
---------------|------------
id             | id of the tag (used for `custom_tag_ids` in mood creation)
name           | name (DEPRECATED)
de_translation | German translation of the tag
en_translation | English translation of the tag
