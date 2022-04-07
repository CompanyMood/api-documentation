# Oauth

## Sign in via google oauth2

```http
POST /oauth/google_oauth2 HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db

{
  "data": {
    "type": "oauth",
    "attributes": {
      "id_token": "INSERT ID TOKEN HERE"
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
      "department_id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
      "mood_creation_notification_email_active": true,
      "mood_creation_reminder_email_active": true,
      "mood_creation_notification_push_notification_active": true,
      "mood_creation_reminder_push_notification_active": true,
      "weekly_status_notification_active": true
    }
  }
}
```

You can create a new oauth session and get the `auth_token` and other important informations
about the just logged in user by sending a `id_token` to this endpoint.

The returned role can be "admin", "supervisor", "employee" or "department_manager".

### POST Attributes

Paramteter     | Description
---------------|------------
id_token       | Request this token from google auth api (see <https://developers.google.com/identity/sign-in/web/sign-in>)

### Response Attributes

Paramteter                                          | Description
----------------------------------------------------|------------
firstname                                           | Firstname of the sessions user.
lastname                                            | Lastname of the sessions user.
email                                               | Email of the sessions user.
locale                                              | Locale of the sessions user.
image_url                                           | Url to the profile image of the sessions user.
role                                                | Role of the sessions user (`admin`, `supervisor`, `department_manager` or `employee`).
auth_token                                          | Auth token for users session, use this for further authorization on endpoints.
company_id                                          | ID of the company, the user belongs to. Empty if the user does't belong to a company, yet.
department_id                                       | ID of the department, the user belongs to. `null` if the user doesn't belong to a department.
mood_creation_notification_email_active             | Will the user receive notifications for mood reviews per email?
mood_creation_reminder_email_active                 | Will the user receive reminder for mood reviews per email if he didn't give an answer already?
mood_creation_notification_push_notification_active | Will the user receive push notifications for mood reviews on mobile phones?
mood_creation_reminder_push_notification_active     | Will the user receive push notifications to remind him to answer the review question on mobile phone?
weekly_status_notification_active                   | Will the user receive a weekly status report per mail? (Attribute is not present for users without a report role)


## Sign in via Microsoft Azure oauth2

```http
POST /oauth/azure_oauth2 HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db

{
  "data": {
    "type": "oauth",
    "attributes": {
      "id_token": "INSERT ID TOKEN HERE"
      // OR
      "access_token": "INSERT ACCESS TOKEN HERE"
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
      "department_id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
      "mood_creation_notification_email_active": true,
      "mood_creation_reminder_email_active": true,
      "mood_creation_notification_push_notification_active": true,
      "mood_creation_reminder_push_notification_active": true,
      "weekly_status_notification_active": true
    }
  }
}
```

You can create a new oauth session and get the `auth_token` and other important informations
about the just logged in user by sending a `id_token` to this endpoint.

The returned role can be "admin", "supervisor", "employee" or "department_manager".

### POST Attributes
We support those 2 token types for azure authentication via oauth2.
Make sure to only send one of them rather than both in the same request.

Paramteter     | Description
---------------|------------
id_token       | Request this token from azure auth api (see <https://docs.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-auth-code-flow#request-an-access-token>)
access_token   | Request this token from google auth api (see <https://developers.google.com/identity/sign-in/web/sign-in>)

### Response Attributes

Paramteter                                          | Description
----------------------------------------------------|------------
firstname                                           | Firstname of the sessions user.
lastname                                            | Lastname of the sessions user.
email                                               | Email of the sessions user.
locale                                              | Locale of the sessions user.
image_url                                           | Url to the profile image of the sessions user.
role                                                | Role of the sessions user (`admin`, `supervisor`, `department_manager` or `employee`).
auth_token                                          | Auth token for users session, use this for further authorization on endpoints.
company_id                                          | ID of the company, the user belongs to. Empty if the user does't belong to a company, yet.
department_id                                       | ID of the department, the user belongs to. `null` if the user doesn't belong to a department.
mood_creation_notification_email_active             | Will the user receive notifications for mood reviews per email?
mood_creation_reminder_email_active                 | Will the user receive reminder for mood reviews per email if he didn't give an answer already?
mood_creation_notification_push_notification_active | Will the user receive push notifications for mood reviews on mobile phones?
mood_creation_reminder_push_notification_active     | Will the user receive push notifications to remind him to answer the review question on mobile phone?
weekly_status_notification_active                   | Will the user receive a weekly status report per mail? (Attribute is not present for users without a report role)


## Sign in via apple

```http
POST /oauth/apple HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db

{
  "data": {
    "type": "oauth",
    "attributes": {
      "authorization_code": "authorizationCode from apple-service",
      "authorized_scopes":  "authorizedScopes from apple-service",
      "email":              "email from apple-service",
      "full_name":          "fullName from apple-service",
      "identity_token":     "identityToken from apple-service",
      "real_user_status":   "realUserStatus from apple-service",
      "state":              "state from apple-service",
      "user":               "user from apple-service"
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
      "department_id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
      "mood_creation_notification_email_active": true,
      "mood_creation_reminder_email_active": true,
      "mood_creation_notification_push_notification_active": true,
      "mood_creation_reminder_push_notification_active": true,
      "weekly_status_notification_active": true
    }
  }
}
```

The returned role can be "admin", "supervisor", "employee" or "department_manager".

### POST Attributes

Paramteter        | Description
------------------|------------
authorizationCode | Get this from login with apples (using AppleAuthRequestResponse interface)
authorizedScopes  | Get this from login with apples (using AppleAuthRequestResponse interface)
email             | Get this from login with apples (using AppleAuthRequestResponse interface)
fullName          | Get this from login with apples (using AppleAuthRequestResponse interface)
identityToken     | Get this from login with apples (using AppleAuthRequestResponse interface)
realUserStatus    | Get this from login with apples (using AppleAuthRequestResponse interface)
state             | Get this from login with apples (using AppleAuthRequestResponse interface)
user              | Get this from login with apples (using AppleAuthRequestResponse interface)

### Response Attributes

Paramteter                                          | Description
----------------------------------------------------|------------
firstname                                           | Firstname of the sessions user.
lastname                                            | Lastname of the sessions user.
email                                               | Email of the sessions user.
locale                                              | Locale of the sessions user.
image_url                                           | Url to the profile image of the sessions user.
role                                                | Role of the sessions user (`admin`, `supervisor`, `department_manager` or `employee`).
auth_token                                          | Auth token for users session, use this for further authorization on endpoints.
company_id                                          | ID of the company, the user belongs to. Empty if the user does't belong to a company, yet.
department_id                                       | ID of the department, the user belongs to. `null` if the user doesn't belong to a department.
mood_creation_notification_email_active             | Will the user receive notifications for mood reviews per email?
mood_creation_reminder_email_active                 | Will the user receive reminder for mood reviews per email if he didn't give an answer already?
mood_creation_notification_push_notification_active | Will the user receive push notifications for mood reviews on mobile phones?
mood_creation_reminder_push_notification_active     | Will the user receive push notifications to remind him to answer the review question on mobile phone?
weekly_status_notification_active                   | Will the user receive a weekly status report per mail? (Attribute is not present for users without a report role)

