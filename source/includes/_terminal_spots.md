# TerminalSpots

## Retrieve the terminal spots of the users company
Returns with an 401 if the user does not belong to a company

You'll need the terminal_spot_id and its associated department_id if you
want to track a terminal mood. More under /moods

### Note
In this endpoint you'll get all dependend `departments` and `terminal_spot_department_settings` as sideloaded relationships and includes.

```http
GET /terminal_spots HTTP/1.1
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
  "data": [{
     "id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
     "type": "terminal_spot",
     "attributes": {
       "name": "Production exit terminal",
       "description": "This terminal gets placed at the facility A.1-5s exits",
       "soft_cap_rate": 10,
       "hard_cap_rate": 25,
       "mood_barometer_active": true,
       "suggestions_active": true,
       "surveys_active": true
     },
     "relationships": {
       "terminal_spot_department_settings": {
         "data": [
           {
             "id": "0cc30da9-ffc7-40ff-9c88-ef03aa692b98",
             "type": "terminal_spot_department_settings"
           }
         ]
       }
     }
   }],
   "included": [{
    "id": "0cc30da9-ffc7-40ff-9c88-ef03aa692b98",
    "type": "terminal_spot_department_settings",
    "attributes": {
      "users_count": 9,
      "department_id": "ea985df4-2c38-4c44-bda9-5bbe031f6755"
    },
    "relationships": {
      "department": {
        "data": {
          "id": "ea985df4-2c38-4c44-bda9-5bbe031f6755",
          "type": "departments"
        }
      }
    }
  },{
    "id": "ea985df4-2c38-4c44-bda9-5bbe031f6755",
    "type": "departments",
    "attributes": {
      "name": "Design",
      "breadcrumb": "German HQ > Development > Design"
    }
  }]
}
```

### Response Attributes

#### terminal_spot

Paramteter            | Description
----------------------|------------
id                    | id of the terminal spot
name                  | name of the terminal spot
description           | description of the terminal spot
soft_cap_rate         | Soft cap rate defines at what rate (not amount) of overtracked moods, a warning should get shown fir a terminals department
hard_cap_rate         | Hard cap rate defines at what rate (not amount) of overtracked moods, a terminal should not allow the tracking for a terminals department
mood_barometer_active | A boolean value which indicates if the mood review feature is active for this terminal spot.
suggestions_active    | A boolean value which indicates if the suggestion box feature is activated for this terminal spot.
surveys_active        | A boolean value which indicates if the survey feature is activated for this terminal spot.

#### side loaded department

Paramteter | Description
-----------|------------
id         | id of the terminal spot
name       | name of the terminal spot
breadcrumb | All names in path to the department incl. it's own

#### side loaded terminal_spot_department_settings

Paramteter    | Description
--------------|------------
id            | id of the terminal spot
users_count   | how much users are supposed to track via this terminal_spot_department_setting
department_id | department id for this terminal_spot_department_setting (needed for tracking terminal mood)
