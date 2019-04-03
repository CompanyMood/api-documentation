# Sessions

## Create a new session

```http
POST /sessions HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
Authorization: Bearer 795665b4-53da-468c-a0d7-ab2d82e58406
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db

{
  "data": {
    "type": "sessions",
    "attributes": {
      "email": "valid@example.com",
      "password": "secret"
    }
  }
}
```

```http
HTTP/1.1 201 CREATED
Content-Type: application/json

{
  "data": {
    "id": "1d7f7eea-b088-46dd-b29c-51ccfa4085e7",
    "type": "users",
    "attributes": {
      "firstname": "John",
      "lastname": "Doe",
      "email": "j.doe1@example.com",
      "locale": "de",
      "image_url": "https://gravatar.com/avatar/829afce351884fcde132544bf9686221",
      "role": "admin",
      "auth_token": "5c3dad26-31a4-4f6d-a799-b3cd9053dc83",
      "company_id": "8f40670c-9927-4712-979f-81a2fa4c7253",
      "mood_creation_notification_email_active": true,
      "mood_creation_reminder_email_active": true,
      "mood_creation_notification_push_notification_active": true,
      "mood_creation_reminder_push_notification_active": true,
      "weekly_status_notification_active": true
    }
  }
}
```

You can create a new session and get the `auth_token` and other important informations about the just logged in user by sending the `email` and `password` to this endpoint.

The returned role can be "admin", "supervisor", "employee" or "department_manager".

### POST Attributes

Parameter | Description
-----------|------------
email      | Email for session
password   | Password for session

### Response Attributes

Parameter | Description
-----------|------------
firstname                                           | Firstname of the sessions user
lastname                                            | Lastname of the sessions user
email                                               | Email of the sessions user
locale                                              | Locale of the sessions user
image_url                                           | Url to the profile image of the sessions user
role                                                | Role of the sessions user (`admin`, `department_manager` or `employee`)
auth_token                                          | Auth token for users session, use this for further authorization on endpoints
company_id                                          | ID of the company, the user belongs to. Empty if the user does't belong to a company, yet.
mood_creation_notification_email_active             | Will the user receive notifications for mood reviews per email?
mood_creation_reminder_email_active                 | Will the user receive reminder for mood reviews per email if he didn't give an answer already?
mood_creation_notification_push_notification_active | Will the user receive push notifications for mood reviews on mobile phones?
mood_creation_reminder_push_notification_active     | Will the user receive push notifications to remind him to answer the review question on mobile phone?
weekly_status_notification_active                   | Will the user receive a weekly status report per mail? (Attribute is not present for users without a report role)
