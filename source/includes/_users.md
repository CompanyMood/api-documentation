# Users

## Get users statistics

```http
GET /users/statistics HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
X-App-Token: 27f51875-9a43-4d6c-a376-6368f09858db
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "meta": {
    "from": "2020-11-16",
    "to": "2020-12-27",
    "origin_type": "Company",
    "origin_id": "bc41eea0-1f87-4e07-8dda-6449430e7132"
  },
  "data": {
    "id": "users-statistics",
    "type": "users-statistics",
    "attributes": {
      "employees_amount": 4.0,
      "invitations_amount": 4.0,
      "terminal_users_amount": 10.0,
      "active_users_amount": 14.0,
      "users_total_amount": 18.0
    }
  }
}
```

### GET META Attributes

Paramteter   |          | Description |
-------------|----------|-------------
from         | optional | Date to limit the moods results (in ISO8601)
to           | optional | Date to limit the moods results (in ISO8601)
origin_type  | optional | Enum ["Company", "Department"]
origin_id    | optional | ID of the requested origin which stats are requested

### Response META Attributes

Paramteter   |          | Description |
-------------|----------|-------------
from         | optional | Date to limit the moods results (in ISO8601)
to           | optional | Date to limit the moods results (in ISO8601)
origin_type  | optional | Enum ["Company", "Department"]
origin_id    | optional | ID of the requested origin which stats are requested

### Response Attributes

Paramteter            | Description
----------------------|------------
employees_amount      | Amount of the invitation accepted users
invitations_amount    | Amount of the not accepted invitations
terminal_users_amount | Amount of the terminal users (set in terminals)
active_users_amount   | Amount of all participating users (employees + terminal)
users_total_amount    | Amount of all users combined

## Get current user

```http
GET /users/current HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "data": {
    "id": "1d7f7eea-b088-46dd-b29c-51ccfa4085e7",
    "type": "users",
    "attributes": {
      "firstname": "John",
      "lastname": "Doe",
      "gender": "male",
      "email": "j.doe1@example.com",
      "locale": "de",
      "image_url": "https://gravatar.com/avatar/829afce351884fcde132544bf9686221",
      "role": "admin",
      "company_id": "8f40670c-9927-4712-979f-81a2fa4c7253",
      "department_id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
      "mood_creation_notification_email_active": true,
      "mood_creation_reminder_email_active": true,
      "mood_creation_notification_push_notification_active": true,
      "mood_creation_reminder_push_notification_active": true,
      "mood_review_snoozed_until": "2019-06-14T11:15:00.000Z",
      "current_tracking_time": "2019-06-20T11:00:00.000Z",
      "weekly_status_notification_active": true,
      "auth_token": "5c3dad26-31a4-4f6d-a799-b3cd9053dc83",
      "external_uid": "AADOB-234113324-21",
      "personnel_number": "100236"
    }
  }
}
```

Returns the current user details.

### Response Attributes

Parameter                                           | Description
----------------------------------------------------|------------
firstname                                           | Firstname of the sessions user
lastname                                            | Lastname of the sessions user
gender                                              | The gender of the sessions user (`male`, `female`, `divers`)
email                                               | Email of the sessions user
locale                                              | Locale of the sessions user
image_url                                           | Url to the profile image of the sessions user
role                                                | Role of the sessions user (`admin`, `supervisor`, `department_manager` or `employee`)
company_id                                          | ID of the company, the user belongs to. `null` if the user does't belong to a company, yet.
department_id                                       | ID of the department, the user belongs to. `null` if the user doesn't belong to a department.
mood_creation_notification_email_active             | Will the user receive notifications for mood reviews per email?
mood_creation_reminder_email_active                 | Will the user receive reminder for mood reviews per email if he didn't give an answer already?
mood_creation_notification_push_notification_active | Will the user receive push notifications for mood reviews on mobile phones?
mood_creation_reminder_push_notification_active     | Will the user receive push notifications to remind him to answer the review question on mobile phone?
mood_review_snoozed_until                           | Returns a date time if the user snoozed the mood review form.
current_tracking_time                               | The next tracking time when the user should be presented with the mood tracking form.
weekly_status_notification_active                   | Will the user receive a weekly status report per mail? (Attribute is not present for users without a report role)
auth_token                                          | Auth token for users session, use this for further authorization on endpoints
external_uid                                        | External UID - After setting, it can also be used as ID in Post /users and PUT /users/:id
personnel_number                                    | The personnel number of the employee

## Get all companies users

```http
GET /users HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "data": [
    {
      "id": "1d7f7eea-b088-46dd-b29c-51ccfa4085e7",
      "type": "users",
      "attributes": {
        "email": "j.doe1@example.com",
        "locale": "de",
        "role": "admin",
        "department_id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
        "disable_all_emails": false,
        "password": "kjnasdfkjnasdfkjnaaskjdfn",
        "password_confirmation": "kjnasdfkjnasdfkjnaaskjdfn",
        "external_uid": "AADOB-234113324-21",
        "personnel_number": "100236",
        "facutly": "ID Dev",
        "job_title": "Senior Software Developer",
        "manager_name": "Franka Schnabel",
        "region_name": "SW Germany",
        "location_name": "Saarlouis"
      }
    }
  ]
}
```

Returns all users of the company.

### Response Attributes

Parameter                                           | Description
----------------------------------------------------|------------
email                                               | Email of the user
locale                                              | Locale of the user
role                                                | Role of the user (`admin`, `supervisor`, `department_manager` or `employee`)
company_id                                          | ID of the company, the user belongs to. `null` if the user does't belong to a company, yet.
department_id                                       | ID of the department, the user belongs to. `null` if the user doesn't belong to a department.
disable_all_emails                                  | Are all emails disabled for this user? - Only changeable through API from ADMIN
external_uid                                        | External UID - After setting, it can also be used as ID in Post /users and PUT /users/:id
personnel_number                                    | The personnel number of the employee
faculty                                             | The users facutly
job_title                                           | The users job title
manager_name                                        | The users managers name (or email)
region_name                                         | The users region
location_name                                       | The users location

## Create a new user
This will create a user in your company which is directly able to use oauth or use
password reset to set a password.

If you want to invite a user to your company with invitation email and
invitation completion form (where the user set the password etc) you
need to use the users invite endpoint (see below)

```http
POST /users HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
Authorization: Bearer 795665b4-53da-468c-a0d7-ab2d82e58406
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db

{
  "data" : {
    "type": "users",
    "attributes": {
      "firstname": "John",
      "lastname": "Doe",
      "email": "j.doe1@example.com",
      "locale": "de",
      "role": "admin",
      "department_id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
      "mood_creation_notification_email_active": true,
      "mood_creation_reminder_email_active": true,
      "mood_creation_notification_push_notification_active": true,
      "mood_creation_reminder_push_notification_active": true,
      "weekly_status_notification_active": true,
      "disable_all_emails": false,
      "password": "kjnasdfkjnasdfkjnaaskjdfn",
      "password_confirmation": "kjnasdfkjnasdfkjnaaskjdfn",
      "external_uid": "AADOB-234113324-21",
      "personnel_number": "100236",
      "facutly": "ID Dev",
      "job_title": "Senior Software Developer",
      "manager_name": "Franka Schnabel",
      "region_name": "SW Germany",
      "location_name": "Saarlouis"
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
    "type": "users",
    "attributes": {
      "firstname": "John",
      "lastname": "Doe",
      "email": "j.doe1@example.com",
      "locale": "de",
      "role": "admin",
      "department_id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
      "mood_creation_notification_email_active": true,
      "mood_creation_reminder_email_active": true,
      "mood_creation_notification_push_notification_active": true,
      "mood_creation_reminder_push_notification_active": true,
      "weekly_status_notification_active": true,
      "disable_all_emails": false,
      "external_uid": "AADOB-234113324-21",
      "personnel_number": "100236",
      "facutly": "ID Dev",
      "job_title": "Senior Software Developer",
      "manager_name": "Franka Schnabel",
      "region_name": "SW Germany",
      "location_name": "Saarlouis"
    }
  }
}
```
### POST Attributes


Parameter                                           | Description
----------------------------------------------------|------------
firstname                                           | Firstname of the user
lastname                                            | Lastname of the user
email                                               | Email of the user
locale                                              | Locale of the user
role                                                | Role of the user (`admin`, `supervisor`, `department_manager` or `employee`)
department_id                                       | ID of the department, the user belongs to. `null` if the user doesn't belong to a department.
mood_creation_notification_email_active             | Will the user receive notifications for mood reviews per email?
mood_creation_reminder_email_active                 | Will the user receive reminder for mood reviews per email if he didn't give an answer already?
mood_creation_notification_push_notification_active | Will the user receive push notifications for mood reviews on mobile phones?
mood_creation_reminder_push_notification_active     | Will the user receive push notifications to remind him to answer the review question on mobile phone?
weekly_status_notification_active                   | Will the user receive a weekly status report per mail? (Attribute is not present for users without a report role) password | Password for the user (the user can change it later)
disable_all_emails                                  | Are all emails disabled for this user? - Only changeable through API from ADMIN
password_confirmation                               | Password confirmation
external_uid                                        | External UID - After setting, it can also be used as ID in Post /users and PUT /users/:id
personnel_number                                    | The personnel number of the employee
faculty                                             | The users facutly
job_title                                           | The users job title
manager_name                                        | The users managers name (or email)
region_name                                         | The users region
location_name                                       | The users location


### Response Attributes

Parameter                                           | Description
----------------------------------------------------|------------
firstname                                           | Firstname of the user
lastname                                            | Lastname of the user
email                                               | Email of the user
locale                                              | Locale of the user
role                                                | Role of the user (`admin`, `supervisor`, `department_manager` or `employee`)
company_id                                          | ID of the company, the user belongs to. `null` if the user does't belong to a company, yet.
department_id                                       | ID of the department, the user belongs to. `null` if the user doesn't belong to a department.
mood_creation_notification_email_active             | Will the user receive notifications for mood reviews per email?
mood_creation_reminder_email_active                 | Will the user receive reminder for mood reviews per email if he didn't give an answer already?
mood_creation_notification_push_notification_active | Will the user receive push notifications for mood reviews on mobile phones?
mood_creation_reminder_push_notification_active     | Will the user receive push notifications to remind him to answer the review question on mobile phone?
weekly_status_notification_active                   | Will the user receive a weekly status report per mail? (Attribute is not present for users without a report role)
disable_all_emails                                  | Are all emails disabled for this user? - Only changeable through API from ADMIN
external_uid                                        | External UID - After setting, it can also be used as ID in Post /users and PUT /users/:id
personnel_number                                    | The personnel number of the employee
faculty                                             | The users facutly
job_title                                           | The users job title
manager_name                                        | The users managers name (or email)
region_name                                         | The users region
location_name                                       | The users location

## Invite a user
This will invite a user to your company account.
The user will receive an email and can complete the registration with firstname, lastname and password setting there.

If you want to create direct usable user accounts with fix passwords, name, email etc please use the users create endpoint (see above)

```http
POST /users/invitations HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
Authorization: Bearer 795665b4-53da-468c-a0d7-ab2d82e58406
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db

{
  "data" : {
    "type": "users",
    "attributes": {
      "firstname": "John",
      "lastname": "Doe",
      "email": "j.doe1@example.com",
      "locale": "de",
      "role": "admin",
      "department_id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
      "external_uid": "AADOB-234113324-21",
      "personnel_number": "100236",
      "facutly": "ID Dev",
      "job_title": "Senior Software Developer",
      "manager_name": "Franka Schnabel",
      "region_name": "SW Germany",
      "location_name": "Saarlouis"
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
    "type": "users",
    "attributes": {
      "firstname": "John",
      "lastname": "Doe",
      "email": "j.doe1@example.com",
      "locale": "de",
      "role": "admin",
      "department_id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
      "mood_creation_notification_email_active": true,
      "mood_creation_reminder_email_active": true,
      "mood_creation_notification_push_notification_active": true,
      "mood_creation_reminder_push_notification_active": true,
      "weekly_status_notification_active": true,
      "external_uid": "AADOB-234113324-21",
      "personnel_number": "100236",
      "facutly": "ID Dev",
      "job_title": "Senior Software Developer",
      "manager_name": "Franka Schnabel",
      "region_name": "SW Germany",
      "location_name": "Saarlouis"
    }
  }
}
```
### POST Attributes


Parameter        | Description
-----------------|------------
firstname        | Firstname of the user
lastname         | Lastname of the user
email            | Email of the user
locale           | Locale of the user
role             | Role of the user (`admin`, `supervisor`, `department_manager` or `employee`)
department_id    | ID of the department, the user belongs to. `null` if the user doesn't belong to a department.
external_uid     | External UID - After setting, it can also be used as ID in Post /users and PUT /users/:id
personnel_number | The personnel number of the employee
faculty          | The users facutly
job_title        | The users job title
manager_name     | The users managers name (or email)
region_name      | The users region
location_name    | The users location


### Response Attributes

Parameter                                           | Description
----------------------------------------------------|------------
firstname                                           | Firstname of the user
lastname                                            | Lastname of the user
email                                               | Email of the user
locale                                              | Locale of the user
role                                                | Role of the user (`admin`, `supervisor`, `department_manager` or `employee`)
department_id                                       | ID of the department, the user belongs to. `null` if the user doesn't belong to a department.
mood_creation_notification_email_active             | Will the user receive notifications for mood reviews per email?
mood_creation_reminder_email_active                 | Will the user receive reminder for mood reviews per email if he didn't give an answer already?
mood_creation_notification_push_notification_active | Will the user receive push notifications for mood reviews on mobile phones?
mood_creation_reminder_push_notification_active     | Will the user receive push notifications to remind him to answer the review question on mobile phone?
weekly_status_notification_active                   | Will the user receive a weekly status report per mail? (Attribute is not present for users without a report role)
external_uid                                        | External UID - After setting, it can also be used as ID in Post /users and PUT /users/:id
personnel_number                                    | The personnel number of the employee
faculty                                             | The users facutly
job_title                                           | The users job title
manager_name                                        | The users managers name (or email)
region_name                                         | The users region
location_name                                       | The users location

## Update a user

```http
PUT /users/<user-uid> HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
Authorization: Bearer 795665b4-53da-468c-a0d7-ab2d82e58406
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db

{
  "data" : {
    "type": "users",
    "attributes": {
      "id": "e96afc28-f27e-49b9-9f27-94dd3e2a296b",
      "firstname": "John",
      "lastname": "Doe",
      "email": "j.doe1@example.com",
      "locale": "de",
      "role": "admin",
      "department_id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
      "external_uid": "AADOB-234113324-21",
      "personnel_number": "100236",
      "disable_all_emails": false,
      "facutly": "ID Dev",
      "job_title": "Senior Software Developer",
      "manager_name": "Franka Schnabel",
      "region_name": "SW Germany",
      "location_name": "Saarlouis"
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
    "type": "users",
    "attributes": {
      "firstname": "John",
      "lastname": "Doe",
      "email": "j.doe1@example.com",
      "locale": "de",
      "role": "admin",
      "department_id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
      "external_uid": "AADOB-234113324-21",
      "personnel_number": "100236",
      "disable_all_emails": false,
      "facutly": "ID Dev",
      "job_title": "Senior Software Developer",
      "manager_name": "Franka Schnabel",
      "region_name": "SW Germany",
      "location_name": "Saarlouis"
    }
  }
}
```
### Update Attributes


Parameter                                           | Description
----------------------------------------------------|------------
firstname                                           | Firstname of the user
lastname                                            | Lastname of the user
email                                               | Email of the user
locale                                              | Locale of the user
role                                                | Role of the user (`admin`, `supervisor`, `department_manager` or `employee`)
department_id                                       | ID of the department, the user belongs to. `null` if the user doesn't belong to a department.
external_uid                                        | External UID - After setting, it can also be used as ID in Post /users and PUT /users/:id
personnel_number                                    | The personnel number of the employee
disable_all_emails                                  | Are all emails disabled for this user? - Only changeable through API from ADMIN
faculty                                             | The users facutly
job_title                                           | The users job title
manager_name                                        | The users managers name (or email)
region_name                                         | The users region
location_name                                       | The users location


### Response Attributes

Parameter                                           | Description
----------------------------------------------------|------------
firstname                                           | Firstname of the user
lastname                                            | Lastname of the user
email                                               | Email of the user
locale                                              | Locale of the user
role                                                | Role of the user (`admin`, `supervisor`, `department_manager` or `employee`)
department_id                                       | ID of the department, the user belongs to. `null` if the user doesn't belong to a department.
external_uid                                        | External UID - After setting, it can also be used as ID in Post /users and PUT /users/:id
personnel_number                                    | The personnel number of the employee
disable_all_emails                                  | Are all emails disabled for this user? - Only changeable through API from ADMIN
faculty                                             | The users facutly
job_title                                           | The users job title
manager_name                                        | The users managers name (or email)
region_name                                         | The users region
location_name                                       | The users location

## Delete a user

```http
DELETE /users/{user_id} HTTP/1.1
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

Delete a specific user (by `user_id` in the URI)
