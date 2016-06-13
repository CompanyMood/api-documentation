# CustomTags

## Retrieve the tags pool for logged in user
Custom tags specify the tags you can use to describe your mood.  It's `id` and `name` is the same value.

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
       "id": "Workload",
       "type": "custom_tags",
       "attributes": {
         "name": "Workload"
       }
     },
     {
       "id": "Private",
       "type": "custom_tags",
       "attributes": {
         "name": "Private"
       }
     },
     {
       "id": "Management",
       "type": "custom_tags",
       "attributes": {
         "name": "Management"
       }
     }
  ]
}
```

### Response Attributes

Paramteter | Description
-----------|------------
name       | Same as `id` (used for `tag_list` in mood creation)
