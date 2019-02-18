# Settings

## Retrieve the current user settings


```http
GET /settings HTTP/1.1
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
    "id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
    "type": "settings",
    "attributes": {
      "mood_creation_notification_email_active": true,
      "mood_creation_reminder_email_active": true,
      "mood_creation_notification_push_notification_active": true,
      "mood_creation_reminder_push_notification_active": true,
      "weekly_status_notification_active": true,
      "locale": true
    }
  }
}
```

### Response Attributes

Parameter                           | Description
------------------------------------|------------
id                                  | id of the company


## Update current user settings

```http
PUT /settings HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
Authorization: Bearer 795665b4-53da-468c-a0d7-ab2d82e58406
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db

{
  "data": {
    "type": "settings",
    "attributes": {
      "mood_creation_notification_email_active": false,
      "mood_creation_reminder_email_active": false,
      "mood_creation_notification_push_notification_active": false,
      "mood_creation_reminder_push_notification_active": false,
      "weekly_status_notification_active": false,
      "locale": false
    }
  }
}
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "data": {
    "type": "settings",
    "attributes": {
      "mood_creation_notification_email_active": false,
      "mood_creation_reminder_email_active": false,
      "mood_creation_notification_push_notification_active": false,
      "mood_creation_reminder_push_notification_active": false,
      "weekly_status_notification_active": false,
      "locale": false
    }
  }
}
```

### PUT Attributes

Parameter                           | Description
------------------------------------|------------

### Response Attributes

Parameter                           | Description
------------------------------------|------------
