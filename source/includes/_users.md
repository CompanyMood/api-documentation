# Users

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
      "auth_token": "5c3dad26-31a4-4f6d-a799-b3cd9053dc83"
    }
  }
}
```

Returns the current user details.

### Response Attributes

Parameter | Description
-----------|------------
firstname                                           | Firstname of the sessions user
lastname                                            | Lastname of the sessions user
gender                                              | The gender of the sessions user (`male`, `female`, `divers`)
email                                               | Email of the sessions user
locale                                              | Locale of the sessions user
image_url                                           | Url to the profile image of the sessions user
role                                                | Role of the sessions user (`admin`, `department_manager` or `employee`)
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
