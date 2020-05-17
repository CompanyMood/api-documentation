# Reasonings (comments from all sources like moods, reasonings, suggestions)

## Retrieve reasonings for given meta filters

```http
GET /reasonings HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
Authorization: Bearer 795665b4-53da-468c-a0d7-ab2d82e58406
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db

{
  "meta": {
    "from": "2020-04-01",
    "to": "2020-05-31",
    "origin_type": "Company",
    "origin_id": "e96afc28-f27e-49b9-9f27-94dd3e2a296b",
    "reasonings_feeling": "happy",
    "with_reason_only": "true"
  }
}
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "meta": {
    "from": "2020-04-01",
    "to": "2020-05-31",
    "origin_type": "Company",
    "origin_id": "e96afc28-f27e-49b9-9f27-94dd3e2a296b",
    "reasonings_feeling": "happy",
    "reasonings_custom_tag_id": null,
    "with_reason_only": true
  },
  "data": [
     {
       "id": "1763109913022098",
       "type": "reasoning-1583247555",
       "attributes": {
         "username":"Anonym",
         "email":null,
         "department_link":null,
         "department_string":null,
         "discussion_path":null,
         "type":"Topics",
         "custom_tags":["Health"],
         "custom_tag_label":"Health",
         "custom_tag_id":"5c8d26ee-3a0e-3c55-8281-7fu67ed069c5",
         "feeling":"Happy",
         "feeling_key":"happy",
         "rating":100,
         "created_at":"2020-05-03T15:59:15.922+01:00",
         "created_at_as_integer":1583247555,
         "cweek":"KW 21/20",
         "period":"KW 21/20",
         "comment":"Finally great again... Cured that arrow to the knee! :)",
         "answered":false,
         "answers_count":0,
         "answers":[],
         "from_terminal":false,
         "chat_allowed":false,
         "additional_export_information":null
       }
     }
  ]
}
```
Request the reasonings for the given meta filters.

### GET META Attributes

Paramteter               |          | Description |
-------------------------|----------|-------------
origin_type              | required | Class of the reasoning origin. [Company, Department]
origin_id                | required | UUID of the requested origin.
from                     | optional | Date to limit the moods results (in ISO8601)
to                       | optional | Date to limit the moods results (in ISO8601)
reasonings_feeling       | optional | Filter reasonings for a specific feeling key [sad, unhappy, ok, satisfied, happy, positive, negative]
reasonings_custom_tag_id | optional | Filter for a specific custom_tag
with_reason_only         | optional | Return only reasonings with an existing comment

### Response META Attributes

Paramteter               |          | Description |
-------------------------|----------|-------------
origin_type              | required | Class of the reasoning origin. [Company, Department]
origin_id                | required | UUID of the requested origin.
from                     | optional | Date to limit the moods results (in ISO8601)
to                       | optional | Date to limit the moods results (in ISO8601)
reasonings_feeling       | optional | Filter reasonings for a specific feeling key [sad, unhappy, ok, satisfied, happy, positive, negative]
reasonings_custom_tag_id | optional | Filter for a specific custom_tag
with_reason_only         | optional | Return only reasonings with an existing comment

### Response Attributes

Paramteter                    | Description
------------------------------|------------
username                      | Authors name (if transparent) otherwise "Anonym"
email                         | Authors email (if transparent) otherwise null
department_link               | Link to the department, if anonymity rules allow it
department_string             | Department name, if anonymity rules allow it
discussion_path               | Path to the reasonings discussion
type                          | Translated type label
custom_tags                   | Array of translated custom tag labels
custom_tag_label              | Translated custom tag label
custom_tag_id                 | Custom tag id
feeling                       | Translated feeling label
feeling_key                   | Feeling key [sad, unhappy, ok, satisfied, happy, positive, negative]
rating                        | Rating of the feeling [0, 25, 50, 75, 100]
created_at                    | Timestamp for the creation (in ISO8601)
created_at_as_integer         | Integer representation of the created_at timestamp
cweek                         | Period string
period                        | Period string
comment                       | Given comment for the reasoning - can be null
answered                      | Have this reasoning been answered? - Boolean
answers_count                 | Count of given answers
answers                       | Answers as an array
from_terminal                 | Specifies if the reasoning was created by an terminal
chat_allowed                  | Specifies if chat/discussion is allowed
additional_export_information | Additional export informations - if applied
