# Departments

## Retrieve the departments of the users company
Returns with an 401 if the user does not belong to a company or isn't an
admin of the company.

```http
GET /departments HTTP/1.1
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
       "type": "departments",
       "attributes": {
         "name": "Services"
       }
     },
     {
       "id": "a9767fd1-a187-40e2-954c-872cebff5e70",
       "type": "departments",
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
id         | id of the department
name       | name
