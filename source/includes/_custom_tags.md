# CustomTags

## Retrieve the tags pool for logged in user
Custom tags specify the tags you can use to describe your mood.
Returns with an 401 if the user does not belong to a company.

```http
GET /custom_tags HTTP/1.1
Host: api.company-mood.com
Content-Type: application/json
Accept: application/vnd.company-mood-v2+json
Authorization: Bearer 795665b4-53da-468c-a0d7-ab2d82e58406
X-App-Token: 27f50875-9a43-4d6c-a376-6968f09858db

{
  "meta": {
    "include_archived": true
  }
}
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "data": [
     {
       "id": "f7559f2a-8f1c-461e-8a9b-7efea5564edb",
       "type": "custom_tags",
       "attributes": {
         "name": "Workload",
         "archived": "false",
         "labels": {
           "de": "Auslastung",
           "en": "Workload",
           "fr": "Charge de travail",
           "es": "Carga de trabajo",
           "it": "Carico di lavoro",
           "nl": "Werkbelasting",
           "pl": "Obciążenie pracą",
           "pt": "Carga de trabalho",
           "ru": "Рабочая нагрузка"
         },
         "descriptions": {
           "de": "Auslastung",
           "en": "Workload",
           "fr": "Charge de travail",
           "es": "Carga de trabajo",
           "it": "Carico di lavoro",
           "nl": "Werkbelasting",
           "pl": "Obciążenie pracą",
           "pt": "Carga de trabalho",
           "ru": "Рабочая нагрузка"
         },
         "de_translation": "Auslastung",
         "en_translation": "Workload",
         "fr_translation": "Charge de travail"
       }
     },
     {
       "id": "c23e5e7d-162f-4fdc-9243-5e6349ce2bd1",
       "type": "custom_tags",
       "attributes": {
         "name": "Privat",
         "labels": {
           "de": "Privat",
           "en": "Private",
           "fr": "Privé",
           "es": null,
           "it": null,
           "nl": null,
           "pl": null,
           "pt": null,
           "ru": null
         },
         "descriptions": {
           "de": "Privat",
           "en": "Private",
           "fr": "Privé",
           "es": null,
           "it": null,
           "nl": null,
           "pl": null,
           "pt": null,
           "ru": null
         },
         "de_translation": "Privat",
         "en_translation": "Private",
         "fr_translation": "Privé"
       }
     },
     {
       "id": "a9767fd1-a187-40e2-954c-872cebff5e70",
       "type": "custom_tags",
       "attributes": {
         "name": "Management",
         "archived": "true",
         "labels": {
           "de": "Führungskräfte",
           "en": "Managers",
           "fr": "Managers / Responsables",
           "es": "personal directivo",
           "it": "Personale direttivo",
           "nl": "Leidinggevenden",
           "pl": "Menedżerowie",
           "pt": "Gerentes",
           "ru": "Менеджеры"
         },
         "descriptions": {
           "de": "Führungskräfte",
           "en": "Managers",
           "fr": "Managers / Responsables",
           "es": "personal directivo",
           "it": "Personale direttivo",
           "nl": "Leidinggevenden",
           "pl": "Menedżerowie",
           "pt": "Gerentes",
           "ru": "Менеджеры"
         },
         "de_translation": "Vorgesetzte",
         "en_translation": "Management",
         "fr_translation": "Responsables"
       }
     }
  ]
}
```

### GET META Attributes

Paramteter       |          | Description |
-----------------|----------|-------------
include_archived | optional | Should response include archived custom tags as well? (default: false)

### Response Attributes

Paramteter     | Description
---------------|------------
id             | id of the tag (used for `custom_tag_ids` in mood creation)
name           | name (DEPRECATED)
archived       | Is this custom tag available for usage or already archived
labels         | An object of translations of the custom tag name.
descriptions   | An object of translations of the custom tag description.
de_translation | German translation of the tag (DEPRECATED)
en_translation | English translation of the tag (DEPRECATED)
fr_translation | English translation of the tag (DEPRECATED)
