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
    "id": "70d17931-a3f0-4aa3-b432-c46f4b763d4f",
    "type": "settings",
    "attributes": {
      "mood_creation_notification_email_active": true,
      "mood_creation_reminder_email_active": true,
      "mood_creation_notification_push_notification_active": true,
      "mood_creation_reminder_push_notification_active": true,
      "weekly_status_notification_active": true,
      "new_discussion_comment_email_notification_active": false,
      "locale": "de"
    }
  }
}
```

### Response Attributes

Parameter                                           | Description
----------------------------------------------------|--------------
id                                                  | Current user ID
mood_creation_notification_email_active             | Will the user receive notifications for mood reviews per email?
mood_creation_reminder_email_active                 | Will the user receive reminder for mood reviews per email if he didn't give an answer already?
mood_creation_notification_push_notification_active | Will the user receive push notifications for mood reviews on mobile phones?
mood_creation_reminder_push_notification_active     | Will the user receive push notifications to remind him to answer the review question on mobile phone?
weekly_status_notification_active                   | Will the user receive a weekly status report per mail? (Attribute is not present for users without a report role)
new_discussion_comment_email_notification_active    | Will the user receive an email notification for new discussion comments
locale                                              | A string with the locale of the current user


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
      "new_discussion_comment_email_notification_active": false
      "locale": "en"
    }
  }
}
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "data": {
    "id": "70d17931-a3f0-4aa3-b432-c46f4b763d4f",
    "type": "settings",
    "attributes": {
      "mood_creation_notification_email_active": false,
      "mood_creation_reminder_email_active": false,
      "mood_creation_notification_push_notification_active": false,
      "mood_creation_reminder_push_notification_active": false,
      "weekly_status_notification_active": false,
      "new_discussion_comment_email_notification_active": false,
      "locale": "en"
    }
  }
}
```

### PUT Attributes

Parameter                                           | Description
----------------------------------------------------|------------
mood_creation_notification_email_active             | Will the user receive notifications for mood reviews per email?
mood_creation_reminder_email_active                 | Will the user receive reminder for mood reviews per email if he didn't give an answer already?
mood_creation_notification_push_notification_active | Will the user receive push notifications for mood reviews on mobile phones?
mood_creation_reminder_push_notification_active     | Will the user receive push notifications to remind him to answer the review question on mobile phone?
weekly_status_notification_active                   | Will the user receive a weekly status report per mail? (Attribute is not present for users without a report role)
new_discussion_comment_email_notification_active    | Will the user receive an email notification for new discussion comments
locale                                              | A string with the new locale for the current user

### Response Attributes

Parameter                                           | Description
----------------------------------------------------|------------
mood_creation_notification_email_active             | Will the user receive notifications for mood reviews per email?
mood_creation_reminder_email_active                 | Will the user receive reminder for mood reviews per email if he didn't give an answer already?
mood_creation_notification_push_notification_active | Will the user receive push notifications for mood reviews on mobile phones?
mood_creation_reminder_push_notification_active     | Will the user receive push notifications to remind him to answer the review question on mobile phone?
weekly_status_notification_active                   | Will the user receive a weekly status report per mail? (Attribute is not present for users without a report role)
new_discussion_comment_email_notification_active    | Will the user receive an email notification for new discussion comments
locale                                              | A string with the locale of the current user
