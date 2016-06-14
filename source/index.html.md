---
title: CompanyMood API Reference

language_tabs:
  - http

toc_footers:
  - <a href='https://www.company-mood.com'>Get your CompanyMood account now</a>
  - © 2016 CompanyMood

includes:
  - heartbeat
  - sessions
  - custom_tags
  - moods

search: true
---

# Introduction

This is the documentation for the API of
[CompanyMood](https://www.company-mood.com).

This API follows the [JSONAPI specification](http://jsonapi.org/format/) but without hypermedia.

There are a lot of different librabies for all kinds of languages out there to consume JSON-API APIs.

# API Request and Versions

```http
GET / HTTP/1.1
Host: api.company-mood.com
Accept: application/vnd.company-mood-v1+json
```

You need to specify the API version you want use via the `Accept`
header.

Format

`application/vnd.company-mood-v<VERSION>+json`

# Application Token

```http
GET / HTTP/1.1
Host: api.company-mood.com
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db
```

You need to send your application token with every request in the
`X-App-Token` header.

<aside class="notice">
You can get your application token by requesting it at <a href="mailto:hello@company-mood.com">hello@company-mood.com</a>.
You need an CompanyMood account.
</aside>


# Authentication

```http
GET / HTTP/1.1
Host: api.company-mood.com
Authorization: Bearer 795665b4-53da-468c-a0d7-ab2d82e58406
```

For every authenticated request (all but `/sessions`) you need to send the `auth_token` (see `/sessions` endpoint) in the `Authorization` header as a `Bearer` token.
