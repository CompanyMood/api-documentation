# Departments

## Retrieve the departments of the users company
Returns with an 401 if the user does not belong to a company or isn't an
admin of the company.

```http
GET /departments HTTP/1.1
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
       "id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
       "type": "departments",
       "attributes": {
         "name": "Services",
         "breadcrumb": "Development > In House > Services"
       }
     },
     {
       "id": "a9767fd1-a187-40e2-954c-872cebff5e70",
       "type": "departments",
       "attributes": {
         "name": "Management",
         "breadcrumb": "Management"
       }
     }
  ]
}
```

### Response Attributes

Paramteter | Description
-----------|------------
id         | id of the department
name       | name
breadcrumb | All names in path to the department incl. it's own

## Create a new department

```http
POST /departments HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
Authorization: Bearer 795665b4-53da-468c-a0d7-ab2d82e58406
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db

{
  "data" : {
    "type": "departments",
    "attributes": {
      "name": "Management",
      "description": "All managers",
      "parent_id": "a9767fd1-a187-40e2-954c-872cebff5e70"
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
    "type": "departments",
    "attributes": {
      "name": "Management",
      "desciption": "All managers",
      "breadcrumb": "Management",
      "parent_id": "a9767fd1-a187-40e2-954c-872cebff5e70"
    }
  }
}
```
### POST Attributes

Paramteter  |          | Description
------------|----------|--------------------
name        | required | Name of the department
description | optional | Description of the department
parent_id   | optional | UUID of the parent department

### Response Attributes

Paramteter  | Description
------------|------------
name        | Name of the department
description | Description of the department
parent_id   | UUID of the parent department
breadcrumb  | All names in path to the department incl. it's own

## Update an existing department

```http
PUT /departments/{department_id} HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
Authorization: Bearer 795665b4-53da-468c-a0d7-ab2d82e58406
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db

{
  "data" : {
    "id": "e96afc28-f27e-49b9-9f27-94dd3e2a296b",
    "type": "departments",
    "attributes": {
      "name": "Management",
      "description": "All managers",
      "parent_id": "a9767fd1-a187-40e2-954c-872cebff5e70"
    }
  }
}
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "data": {
    "id": "e96afc28-f27e-49b9-9f27-94dd3e2a296b",
    "type": "departments",
    "attributes": {
      "name": "Management",
      "desciption": "All managers",
      "breadcrumb": "Management",
      "parent_id": "a9767fd1-a187-40e2-954c-872cebff5e70"
    }
  }
}
```
### PUT Attributes

Paramteter  |          | Description
------------|----------|--------------------
name        | required | Name of the department
description | optional | Description of the department
parent_id   | optional | UUID of the parent department

### Response Attributes

Paramteter  | Description
------------|------------
name        | Name of the department
description | Description of the department
parent_id   | UUID of the parent department
breadcrumb  | All names in path to the department incl. it's own

## Delete a department

```http
DELETE /departments/{department_id} HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
Authorization: Bearer 795665b4-53da-468c-a0d7-ab2d82e58406
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db
```

```http
HTTP/1.1 200 OK
Content-Type: application/json
```

Delete a specific department (by `department_id` in the URI)

### Important!
The subdepartment children get added to the parent of this deleted department.
If the deleted department is root, then rootify the orphan subdepartments.
