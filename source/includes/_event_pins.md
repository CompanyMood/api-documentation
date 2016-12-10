# EventPins

## Retrieve the event_pins of the users company
Returns with an 401 if the user does not belong to a company.

```http
GET /event_pins HTTP/1.1
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
       "type": "event_pins",
       "attributes": {
         "name": "New office manager",
         "description": "The new office manager got employed.",
         "date": "2016-03-11",
         "visible_for_role": "employee",
         "department_ids": [
           "094822c8-d81f-4639-8197-9a586f10edcd"
         ]
       }
     },
     {
       "id": "a9767fd1-a187-40e2-954c-872cebff5e70",
       "type": "event_pins",
       "attributes": {
         "name": "Off-Site in Berlin",
         "description": "We spend a week in Berlin together.",
         "date": "2016-05-27",
         "visible_for_role": "department_manager",
         "department_ids": []
       }
     }
  ]
}
```

### Response Attributes

Paramteter       | Description
-----------------|------------
id               | id of the department
name             | Name of the event pin
description      | Description of the event pin
department_ids   | Department ids for departments the event pin belong. Belongs to whole company if empty
date             | Date of the event pin
visible_for_role | Shows what users should be able to see it.
