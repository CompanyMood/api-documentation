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

Paramteter       |          | Description
-----------------|----------|-------------
type             | optional | Filter widgets by type

### Available filter types

  - dashboard

### Response META Attributes

Paramteter         | Description
-------------------|------------
type               | Type of returned widgets

### Response Attributes

Paramteter | Description
-----------|------------
id         | The widget identifier


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
  "data": [
    {
      "id": "ranking",
      "type": "widgets",
      "attributes": {
        "company_wide_ranking": 23,
        "company_employee_amount": 120,
        "department_wide_ranking": 12,
        "department_employee_amount": 30
      }
    }
  ]
}
```

The `/widgets/rankings` endpoint returns the ranking data for the current user.

### Response Attributes

Paramteter                 | Description
---------------------------|-------------
company_wide_ranking       | Current user rank of all company employees. 0 if not available.
company_employee_amount    | Employee amount of current user company.
department_wide_ranking    | Current user rank of all. 0 if not available.
department_employee_amount | Employee amount of current user department. 0 if not available.
