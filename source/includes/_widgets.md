# Widgets

## Get all widgets

```http
GET /widgets HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
Authorization: Bearer 795665b4-53da-468c-a0d7-ab2d82e58406
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db

{
  "meta": {
    "type": "dashboard"
  }
}
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "meta": {
    "type": "dashboard"
  },
  "data": [
    {
      "id": "company-average-mood",
      "type": "widgets"
    },
    {
      "id": "company-participation",
      "type": "widgets"
    },
    {
      "id": "company-happiness-score",
      "type": "widgets"
    },
    {
      "id": "company-custom-tags",
      "type": "widgets"
    }
    ...
  ]
}
```

This endpoint returns a set of available widgets for the current user.
The set of returned widgets depends on the role of the current user and the optional
given `type` filter.

To get a list with all widgets just request `/widgets`. If you want to get a list of widgets for the dashboard just request `/widgets`
with type filter.

You can use the returned `id`'s to request the data for specific widgets with a call to `/widgets/:id`.

### GET META Attributes

Parameter        |          | Description
-----------------|----------|-------------
type             | optional | Filter widgets by type

### Available filter types

  - dashboard

### Response META Attributes

Parameter          | Description
-------------------|------------
type               | Type of returned widgets

### Response Attributes

Parameter  | Description
-----------|------------
id         | The widget identifier

## Company Average Mood

```http
GET /widgets/company-average-mood HTTP/1.1
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
  "data": {
    "id": "company-average-mood",
    "type": "widgets",
    "attributes": {
      "data": [
        {
          "from": "2018-10-29",
          "to": "2018-11-04",
          "participation_ratio": 33,
          "happiness_score": 20
        },
        {
          "from": "2018-11-05",
          "to": "2018-11-11",
          "participation_ratio": 36,
          "happiness_score": 25
        },
        {
          "from": "2018-11-12",
          "to": "2018-11-18",
          "participation_ratio": null,
          "happiness_score": null
        },
        {
          "from": "2018-11-19",
          "to": "2018-11-25",
          "participation_ratio": 0,
          "happiness_score": 35
        }
      ]
    }
  }
}
```

This endpoint returns average mood details for the last four periods
of the current users company.

### Response Attributes

Parameter           | Description
--------------------|--------------
from                | Start date of represented week
to                  | End date of represented week
participation_ratio | Employee participation ratio in percent. `null` if anonymity settings do not allow to show data.
happiness_score     | Average happiness score for the tracking period.`null` if anonymity settings do not allow to show data.

## Department Average Mood

```http
GET /widgets/department-average-mood HTTP/1.1
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
  "data": {
    "id": "department-average-mood",
    "type": "widgets",
    "attributes": {
      "data": [
        {
          "from": "2018-10-29",
          "to": "2018-11-04",
          "participation_ratio": 33,
          "happiness_score": 20
        },
        {
          "from": "2018-11-05",
          "to": "2018-11-11",
          "participation_ratio": 36,
          "happiness_score": 25
        },
        {
          "from": "2018-11-12",
          "to": "2018-11-18",
          "participation_ratio": null,
          "happiness_score": null
        },
        {
          "from": "2018-11-19",
          "to": "2018-11-25",
          "participation_ratio": 38,
          "happiness_score": 35
        }
      ]
    }
  }
}
```

This endpoint returns average mood information for the last four periods
of the current users department.

### Response Attributes

Parameter           | Description
--------------------|--------------
from                | Start date of represented week
to                  | End date of represented week
participation_ratio | Employee participation ratio in percent. `null` if anonymity settings do not allow to show data.
happiness_score     | Average happiness score for the tracking period.`null` if anonymity settings do not allow to show data.

## Company happiness score

```http
GET /widgets/company-happiness-score HTTP/1.1
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
  "data": {
    "id": "company-happiness-score",
    "type": "widgets",
    "attributes": {
      "happiness_score": 20.3,
      "feeling": "ok"
    }
  }
}
```

This endpoint returns the happiness score widget information for the current period and current user company.

### Response Attributes

Parameter           | Description
--------------------|--------------
happiness_score     | Happiness score for the current tracking period and current user company.
feeling             | Can be 'sad', 'unhappy', 'ok', 'satisfied' or 'happy'.

## Department happiness score

```http
GET /widgets/department-happiness-score HTTP/1.1
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
  "data": {
    "id": "department-happiness-score",
    "type": "widgets",
    "attributes": {
      "happiness_score": 20.3,
      "feeling": "ok"
    }
  }
}
```

This endpoint returns the happiness score widget information for the current period
and department of the current user.

### Response Attributes

Parameter           | Description
--------------------|--------------
happiness_score     | Happiness score for the current tracking period and current user department
feeling             | Can be 'sad', 'unhappy', 'ok', 'satisfied' or 'happy'.

## Company participation

```http
GET /widgets/company-participation HTTP/1.1
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
  "data": {
    "id": "company-participation",
    "type": "widgets",
    "attributes": {
      "moods_count": 2,
      "employee_amount": 10,
      "participation_in_percent": 20,
      "moods_details": [
        { "feeling": "sad", "percent": 50, "count": 1 },
        { "feeling": "happy", "percent": 50, "count": 1 }
      ]
    }
  }
}
```

This endpoint returns participation statistics for the current users company
and the current tracking period.

### Response Attributes

Parameter                | Description
-------------------------|--------------
moods_count              | Amount of moods in current tracking period for current user company.
employee_amount          | Current user company total employee amount
participation_in_percent | Participation in percent
moods_details            | An array of objects with details for each mood group.

## Department participation

```http
GET /widgets/department-participation HTTP/1.1
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
  "data": {
    "id": "department-participation",
    "type": "widgets",
    "attributes": {
      "moods_count": 2,
      "employee_amount": 10,
      "participation_in_percent": 20,
      "moods_details": [
        { "feeling": "sad", "percent": 50, "count": 1 },
        { "feeling": "happy", "percent": 50, "count": 1 },
      ]
    }
  }
}
```

This endpoint returns participation statistics for the current users department
and the current tracking period.

### Response Attributes

Parameter                | Description
-------------------------|--------------
moods_count              | Amount of moods in current tracking period for current user department.
employee_amount          | Current user department total employee amount
participation_in_percent | Participation in percent
moods_details            | An array of objects with details for each mood group

## Company custom tags

```http
GET /widgets/company-custom-tags HTTP/1.1
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
  "data": {
    "id": "company-custom-tags",
    "type": "widgets",
    "attributes": {
      "total_moods_count": 2,
      "total_reasonings_count": 3,
      "custom_tag_details": [
        {
          "custom_tag_id": "7efea556-461e-8f1c-8a9b-f7559f2aedb",
          "reasonings_count": 2,
          "feeling_details": [
            { "name": "unhappy", "percent": 50.0, "reasonings_count": 1 },
            { "name": "sad", "percent": 50.0, "reasonings_count": 1 }
          ]
        },
        {
          "custom_tag_id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
          "reasonings_count": 1,
          "feeling_details": [
            { "name": "ok", "percent": 100.0, "reasonings_count": 1 },
          ]
        }
      ]
    }
  }
}
```

This endpoint returns the custom tag widget (Top X custom tags) data for the current
user company and the current tracking period. The response doesn't include custom tags or
feelings where no moods has been given in the current tracking period.
The `custom_tag_details` attribute will be an empty Array if no custom tag has any moods.

### Response Attributes

Parameter                                               | Description
--------------------------------------------------------|--------------
total_moods_count                                       | Total amount of moods in current tracking period for current user company.
total_reasonings_count                                  | Total amount of reasonings in current tracking period for current user company.
custom_tag_details                                      | An Array of objects with reasoning details for each custom tag.
custom_tag_details[custom_tag_id]                       | ID of the custom tag.
custom_tag_details[reasonings_count]                    | Amount of given reasonings for the custom tag.
custom_tag_details[feeling_details]                     | An Array of objects with details for each feeling where moods exist.
custom_tag_details[feeling_details][name]               | The identifier of the feeling.
custom_tag_details[feeling_details][percent]            | Percentage of total given moods for the current custom tag.
custom_tag_details[feeling_details][reasonings_count]   | Amount of reasonings given for the current feeling and custom tag.

## Department custom tags

```http
GET /widgets/department-custom-tags HTTP/1.1
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
  "data": {
    "id": "department-custom-tags",
    "type": "widgets",
    "attributes": {
      "total_moods_count": 5,
      "total_reasonings_count": 10,
      "custom_tag_details": [
        {
          "custom_tag_id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
          "reasonings_count": 6,
          "feeling_details": [
            { "name": "ok", "percent": 50.0, "reasonings_count": 3 },
            { "name": "happy", "percent": 50.0, "reasonings_count": 3 }
          ]
        },
        {
          "custom_tag_id": "7efea556-461e-8f1c-8a9b-f7559f2aedb",
          "reasonings_count": 4,
          "feeling_details": [
            { "name": "sad", "percent": 50.0, "reasonings_count": 2 },
            { "name": "unhappy", "percent": 50.0, "reasonings_count": 2 }
          ]
        }
      ]
    }
  }
}
```

This endpoint returns the custom tag widget (Top X custom tags) data for the current
user department and the current tracking period. The response doesn't include custom tags or
feelings where no moods has been given in the current tracking period.

### Response Attributes

Parameter                                             | Description
------------------------------------------------------|--------------
total_moods_count                                     | Total amount of moods in current tracking period for current user department.
total_reasonings_count                                | Total amount of reasonings in current tracking period for current user department.
custom_tag_details                                    | An Array of objects with mood details for each custom tag.
custom_tag_details[custom_tag_id]                     | ID of the custom tag.
custom_tag_details[reasonings_count]                  | Amount of given reasonings for the custom tag.
custom_tag_details[feeling_details]                   | An Array of objects with details for each feeling where reasonings exist.
custom_tag_details[feeling_details][name]             | The identifier of the feeling.
custom_tag_details[feeling_details][percent]          | Percentage of total given reasonings for the current custom tag.
custom_tag_details[feeling_details][reasonings_count] | Amount of reasonings given for the current feeling and custom tag.

## Rankings

```http
GET /widgets/rankings HTTP/1.1
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
  "data": {
    "id": "rankings",
    "type": "widgets",
    "attributes": {
      "company_wide_ranking": 23,
      "company_employee_amount": 120,
      "department_wide_ranking": 12,
      "department_employee_amount": 30
    }
  }
}
```

The `/widgets/rankings` endpoint returns the ranking data for the current user.

### Response Attributes

Parameter                  | Description
---------------------------|-------------
company_wide_ranking       | Current user rank of all company employees. 0 if not available.
company_employee_amount    | Employee amount of current user company.
department_wide_ranking    | Current user rank of all. 0 if not available.
department_employee_amount | Employee amount of current user department. 0 if not available.
