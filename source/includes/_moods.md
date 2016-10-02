# Moods

## Retrieve moods of the logged in user

```http
GET /moods HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v1+json
Authorization: Bearer 795665b4-53da-468c-a0d7-ab2d82e58406
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db

{
  "meta": {
    "from": "2015-01-30",
    "to": "2015-04-30"
  }
}
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "meta": {
    "from": "2015-01-30",
    "to": "2015-04-30",
    "last_weeks_mood_id": "e96afc28-f27e-49b9-9f27-94dd3e2a296b"
  },
  "data": [
     {
       "id": "094822c8-d81f-4639-8197-9a586f10edcd",
       "type": "moods",
       "attributes": {
         "rating": 100,
         "calendar_week": 46,
         "year": 2015,
         "reason": "It was pretty noisy this week",
         "tag_list": [],
         "custom_tag_ids": [],
         "feeling": "happy",
         "created_at": "2015-11-21T05:59:42.517Z"
       }
     },
     {
       "id": "e96afc28-f27e-49b9-9f27-94dd3e2a296b",
       "type": "moods",
       "attributes": {
         "rating": 75,
         "calendar_week": 47,
         "year": 2015,
         "reason": "Got a new place in the basement! :)",
         "tag_list": ["Management"],
         "custom_tag_ids": ["f7559f2a-8f1c-461e-8a9b-7efea5564edb"],
         "feeling": "satisfied",
         "created_at": "2015-11-18T19:18:42.517Z"
       }
     }
  ]
}
```
Request the moods for the logged in user.

Possibility to filter the collection by `from` and `to` parameters.

### POST META Attributes

Paramteter |          | Description |
-----------|----------|-------------
from       | optional | Date to limit the moods results (in ISO8601)
to         | optional | Date to limit the moods results (in ISO8601)

### Response META Attributes

Paramteter         | Description
-------------------|------------
from               | Date to limit the moods results (in ISO8601)
to                 | Date to limit the moods results (in ISO8601)
last_weeks_mood_id | ID of the last weeks mood for given user (can be empty, means no mood given)

### Response Attributes

Paramteter         | Description
-------------------|------------
rating             | Rating as a number between 0 - 100
calendar_week      | Calendar week of the mood
year               | Year of the mood
reason             | Optional given reason
tag_list           | tag list of `CustomTag`s as Array (DEPRECATED)
custom_tag_ids     | list of `CustomTag`s IDs as Array
feeling            | Feeling of the mood (happy, satisfied, ok, unhappy, sad)
created_at         | Date of the mood creation (in ISO8601)


## Create a new mood for last week

```http
POST /moods HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v1+json
Authorization: Bearer 795665b4-53da-468c-a0d7-ab2d82e58406
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db

{
  "data" : {
    "type": "moods",
    "attributes": {
      "feeling": "happy",
      "reason": "Got a new place in the basement! :)",
      "tag_list": "Management",
      "custom_tag_ids": ["f7559f2a-8f1c-461e-8a9b-7efea5564edb"],
    }
  }
}
```

```http
HTTP/1.1 201 CREATED
Content-Type: application/json

{
  "data": {
    "id": "e96afc28-f27e-49b9-9f27-94dd3e2a296b",
    "type": "moods",
    "attributes": {
      "rating": 100,
      "calendar_week": 25,
      "year": 2015,
      "reason": "Got a new place in the basement! :)",
      "tag_list": ["Management", "Others"],
      "custom_tag_ids": ["f7559f2a-8f1c-461e-8a9b-7efea5564edb"],
      "feeling": "happy",
      "created_at": "2015-06-25T11:18:42.517Z"
    }
  }
}
```

Creates the mood for the latest calendar week.

You MUST provide a `reason` or at least one tag in the `tag_list` parameter.

### POST Attributes

Parameter |          | Description
----------|----------|------------
feeling   | required | Feeling of the mood can be ("sad", "unhappy", "ok", "satisfied", "happy") - in rating it's 0, 25, 50, 75, 100
reason    | required | Text reason for the mood
tag_list  | required | `CustomTag`s for the mood seperated by a `;` (Only tags from `/custom_tags` allowed) (DEPRECATED)
custom_tag_ids     | list of `CustomTag`s IDs as Array (Only tags from `/custom_tags` allowed)

### Response Attributes

Paramteter         | Description
-------------------|------------
rating             | Rating as a number between 0 - 100
calendar_week      | Calendar week of the mood
year               | Year of the mood
reason             | Optional given reason
tag_list           | tag list of `CustomTag`s as Array (DEPRECATED)
custom_tag_ids     | list of `CustomTag`s IDs as Array
feeling            | Feeling of the mood (happy, satisfied, ok, unhappy, sad)
created_at         | Date of the mood creation (in ISO8601)


## Update a mood

```http
PUT /moods/{mood_id} HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v1+json
Authorization: Bearer 795665b4-53da-468c-a0d7-ab2d82e58406
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db

{
  "data" : {
    "type": "moods",
    "attributes": {
      "feeling": "satisfied",
      "reason": "Got a new place in the basement! :)",
      "tag_list": "Management",
      "custom_tag_ids": ["f7559f2a-8f1c-461e-8a9b-7efea5564edb"],
    }
  }
}
```

```http
HTTP/1.1 201 CREATED
Content-Type: application/json

{
  "data": {
    "id": "e96afc28-f27e-49b9-9f27-94dd3e2a296b",
    "type": "moods",
    "attributes": {
      "rating": 75,
      "calendar_week": 25,
      "year": 2015,
      "reason": "Got a new place in the basement! :)",
      "tag_list": ["Management"],
      "custom_tag_ids": ["f7559f2a-8f1c-461e-8a9b-7efea5564edb"],
      "feeling": "satisfied",
      "created_at": "2015-06-25T11:18:42.517Z"
    }
  }
}
```

Update a specific mood (by `mood_id` in the URI)

You can only update the mood for last calendar week and if its creation
(`created_at`) is not older than 24h.

You MUST provide a `reason` or at least one tag in the `tag_list` parameter.

### POST Attributes

Parameter |          | Description
----------|----------|------------
feeling   | required | Feeling of the mood can be ("sad", "unhappy", "ok", "satisfied", "happy") - in rating it's 0, 25, 50, 75, 100
reason    | required | Text reason for the mood
tag_list  | required | `CustomTag`s for the mood seperated by a `;` (Only tags from `/custom_tags` allowed) (DEPRECATED)
custom_tag_ids     | list of `CustomTag`s IDs as Array (Only tags from `/custom_tags` allowed)

### Response Attributes

Paramteter         | Description
-------------------|------------
rating             | Rating as a number between 0 - 100
calendar_week      | Calendar week of the mood
year               | Year of the mood
reason             | Optional given reason
tag_list           | tag list of `CustomTag`s as Array (DEPRECATED)
custom_tag_ids     | list of `CustomTag`s IDs as Array
feeling            | Feeling of the mood (happy, satisfied, ok, unhappy, sad)
created_at         | Date of the mood creation (in ISO8601)


## Delete a mood

```http
DELETE /moods/{mood_id} HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v1+json
Authorization: Bearer 795665b4-53da-468c-a0d7-ab2d82e58406
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db
```

```http
HTTP/1.1 200 OK
Content-Type: application/json
```

Delete a specific mood (by `mood_id` in the URI)

You can only delete the mood for last calendar week.
