# Password reset

```http
POST /password-resets HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db

{
  "data": {
    "type": "password-resets",
    "attributes": {
      "email": "valid@example.com"
    }
  }
}
```

```http
HTTP/1.1 202 ACCEPTED
Content-Type: application/json
```

To start a reset password process you have to send a POST request with the user email
address to this endpoint. If the request was successful, you'll receive an email
with a password reset link.

This endpoint does not require authentication with auth_token.

## POST attributes

Parameter | Description
-----------|------------
email      | User email for whom the process will be started
