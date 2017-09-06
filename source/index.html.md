---
title: CRM API
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - javascript--nodejs: Node.JS
  - python: Python
  - ruby: Ruby
  - java: Java
toc_footers: []
includes: []
search: true
highlight_theme: darkula
---

# CRM API

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

This is the unified CRM API from Apideck.  You can find 
out more about Apideck at 
[https://apideck.com](https://apideck.com) or on 
[apideck-io.slack.com, #crm](https://apideck-io.slack.com).

Base URLs:

* <a href="https://api.apideck.com/crm">https://api.apideck.com/crm</a>


<a href="https://apideck.com/terms/">Terms of service</a>
Email: <a href="mailto:hello@apideck.com">Support</a> 
License: <a href="http://www.apache.org/licenses/LICENSE-2.0.html">Apache 2.0</a>

# Authentication



- oAuth2 authentication. 

    - Flow: authorizationCode
    - Authorization URL = [https://api.apideck.com/oauth2/authorize](https://api.apideck.com/oauth2/authorize)
    - Token URL = [https://api.apideck.com/oauth2/token](https://api.apideck.com/oauth2/token)

|Scope|Scope Description|
|---|---|
|write:activities|modify activities|
|read:activities|read activities|
|write:calls|modify calls|
|read:calls|read calls|
|write:companies|modify companies|
|read:companies|read companies|
|write:contacts|modify contacts|
|read:contacts|read contacts|
|write:opportunities|modify opportunities|
|read:opportunities|read opportunities|
|write:leads|modify leads|
|read:leads|read leads|
|write:tasks|modify tasks|
|read:tasks|read tasks|
|write:campaigns|modify campaigns|
|read:campaigns|read campaigns|
|write:products|modify products|
|read:products|read products|
|write:emails|modify emails|
|read:emails|read emails|
|write:notes|modify notes|
|read:notes|read notes|
|write:files|modify files|
|read:files|read files|
|write:users|modify users|
|read:users|read users|
|write:webhooks|modify webhooks|
|read:webhooks|read webhooks|




# Activities

Everything about your activities

## allActivities

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/activities \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/activities HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/activities',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/activities',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/activities',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/activities', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/activities");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /activities`

*Get all activities*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
page|query|integer|false|Page number to start from. Omitting the page parameter will return page 1
per_page|query|integer|false|Number of records to return per page. Default = 100.


> Example responses

```json
[
  {
    "id": "124",
    "owner_id": "349",
    "title": "Meeting Marc Benioff",
    "description": "Do a background check before meeting",
    "location": "22 Main street, NY, US",
    "type": "Meeting",
    "visibility": "Busy",
    "is_private": false,
    "start_date": "2017-08-12T14:00:00.001Z",
    "end_date": "2017-08-12T16:00:00.001Z",
    "duration": 120,
    "all_day": false,
    "reminder_date": "2017-08-10T16:00:00.001Z",
    "linked_resources": [
      {
        "id": 2,
        "type": "Opportunity"
      }
    ],
    "creator_id": 456,
    "updated_at": "2017-08-12T20:43:21.291Z",
    "created_at": "2017-08-12T20:43:21.291Z"
  }
]
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|Inline

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[Activity](#schemaactivity)]|false|No description
» id|string|false|No description
» owner_id|string|false|No description
» title|string|true|No description
» description|string|false|No description
» location|string|false|No description
» type|string|true|No description
» visibility|string|false|No description
» is_private|boolean|false|No description
» start_date|string|false|No description
» end_date|string|false|No description
» duration|integer|false|No description
» all_day|boolean|false|No description
» reminder_date|string|false|No description
» creator_id|integer|false|No description
» updated_at|string|false|No description
» created_at|string|false|No description
» linked_resources|[[LinkedResource](#schemalinkedresource)]|false|No description
»» id|integer|false|No description
»» type|string|false|No description



<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:activities )
</aside>

## addActivity

> Code samples

```shell
# You can also use wget
curl -X POST https://api.apideck.com/crm/activities \
  -H 'Content-Type: application/json'

```

```http
POST https://api.apideck.com/crm/activities HTTP/1.1
Host: api.apideck.com
Content-Type: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/activities',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "id": "124",
  "owner_id": "349",
  "title": "Meeting Marc Benioff",
  "description": "Do a background check before meeting",
  "location": "22 Main street, NY, US",
  "type": "Meeting",
  "visibility": "Busy",
  "is_private": false,
  "start_date": "2017-08-12T14:00:00.001Z",
  "end_date": "2017-08-12T16:00:00.001Z",
  "all_day": false,
  "reminder_date": "2017-08-10T16:00:00.001Z",
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json'

};

fetch('https://api.apideck.com/crm/activities',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.post 'https://api.apideck.com/crm/activities',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.post('https://api.apideck.com/crm/activities', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/activities");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /activities`

*Add a new activity*

> Body parameter

```json
{
  "id": "124",
  "owner_id": "349",
  "title": "Meeting Marc Benioff",
  "description": "Do a background check before meeting",
  "location": "22 Main street, NY, US",
  "type": "Meeting",
  "visibility": "Busy",
  "is_private": false,
  "start_date": "2017-08-12T14:00:00.001Z",
  "end_date": "2017-08-12T16:00:00.001Z",
  "all_day": false,
  "reminder_date": "2017-08-10T16:00:00.001Z",
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
body|body|[Activity](#schemaactivity)|true|Activity object that needs to be added
» id|body|string|false|No description
» owner_id|body|string|false|No description
» title|body|string|true|No description
» description|body|string|false|No description
» location|body|string|false|No description
» type|body|string|true|No description
» visibility|body|string|false|No description
» is_private|body|boolean|false|No description
» start_date|body|string|false|No description
» end_date|body|string|false|No description
» duration|body|integer|false|No description
» all_day|body|boolean|false|No description
» reminder_date|body|string|false|No description
» creator_id|body|integer|false|No description
» updated_at|body|string|false|No description
» created_at|body|string|false|No description
» linked_resources|body|[[LinkedResource](#schemalinkedresource)]|false|No description
»» id|body|integer|false|No description
»» type|body|string|false|No description


#### Enumerated Values

|Parameter|Value|
|---|---|
» type|Meeting/Call/Task|
» visibility|Busy/OutOfOffice/Free|
»» type|Lead/Opportunity/Person/Company|

### Responses

Status|Meaning|Description|Schema
---|---|---|---|
201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:activities )
</aside>

## getActivity

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/activities/{id} \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/activities/{id} HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/activities/{id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/activities/{id}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/activities/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/activities/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/activities/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /activities/{id}`

*Find activity by ID*

Returns a single activity

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


> Example responses

```json
{
  "id": "124",
  "owner_id": "349",
  "title": "Meeting Marc Benioff",
  "description": "Do a background check before meeting",
  "location": "22 Main street, NY, US",
  "type": "Meeting",
  "visibility": "Busy",
  "is_private": false,
  "start_date": "2017-08-12T14:00:00.001Z",
  "end_date": "2017-08-12T16:00:00.001Z",
  "all_day": false,
  "reminder_date": "2017-08-10T16:00:00.001Z",
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[Activity](#schemaactivity)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:activities )
</aside>

## updateActivity

> Code samples

```shell
# You can also use wget
curl -X PATCH https://api.apideck.com/crm/activities/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PATCH https://api.apideck.com/crm/activities/{id} HTTP/1.1
Host: api.apideck.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/activities/{id}',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "id": "124",
  "owner_id": "349",
  "title": "Meeting Marc Benioff",
  "description": "Do a background check before meeting",
  "location": "22 Main street, NY, US",
  "type": "Meeting",
  "visibility": "Busy",
  "is_private": false,
  "start_date": "2017-08-12T14:00:00.001Z",
  "end_date": "2017-08-12T16:00:00.001Z",
  "all_day": false,
  "reminder_date": "2017-08-10T16:00:00.001Z",
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/activities/{id}',
{
  method: 'PATCH',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.patch 'https://api.apideck.com/crm/activities/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.patch('https://api.apideck.com/crm/activities/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/activities/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`PATCH /activities/{id}`

*Update an existing activity*

> Body parameter

```json
{
  "id": "124",
  "owner_id": "349",
  "title": "Meeting Marc Benioff",
  "description": "Do a background check before meeting",
  "location": "22 Main street, NY, US",
  "type": "Meeting",
  "visibility": "Busy",
  "is_private": false,
  "start_date": "2017-08-12T14:00:00.001Z",
  "end_date": "2017-08-12T16:00:00.001Z",
  "all_day": false,
  "reminder_date": "2017-08-10T16:00:00.001Z",
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return
body|body|[Activity](#schemaactivity)|true|Fields that need to be updated on the resource
» id|body|string|false|No description
» owner_id|body|string|false|No description
» title|body|string|true|No description
» description|body|string|false|No description
» location|body|string|false|No description
» type|body|string|true|No description
» visibility|body|string|false|No description
» is_private|body|boolean|false|No description
» start_date|body|string|false|No description
» end_date|body|string|false|No description
» duration|body|integer|false|No description
» all_day|body|boolean|false|No description
» reminder_date|body|string|false|No description
» creator_id|body|integer|false|No description
» updated_at|body|string|false|No description
» created_at|body|string|false|No description
» linked_resources|body|[[LinkedResource](#schemalinkedresource)]|false|No description
»» id|body|integer|false|No description
»» type|body|string|false|No description


#### Enumerated Values

|Parameter|Value|
|---|---|
» type|Meeting/Call/Task|
» visibility|Busy/OutOfOffice/Free|
»» type|Lead/Opportunity/Person/Company|

> Example responses

```json
{
  "id": "124",
  "owner_id": "349",
  "title": "Meeting Marc Benioff",
  "description": "Do a background check before meeting",
  "location": "22 Main street, NY, US",
  "type": "Meeting",
  "visibility": "Busy",
  "is_private": false,
  "start_date": "2017-08-12T14:00:00.001Z",
  "end_date": "2017-08-12T16:00:00.001Z",
  "all_day": false,
  "reminder_date": "2017-08-10T16:00:00.001Z",
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[Activity](#schemaactivity)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:activities )
</aside>

## deleteActivity

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.apideck.com/crm/activities/{id}

```

```http
DELETE https://api.apideck.com/crm/activities/{id} HTTP/1.1
Host: api.apideck.com


```

```javascript

$.ajax({
  url: 'https://api.apideck.com/crm/activities/{id}',
  method: 'delete',

  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

fetch('https://api.apideck.com/crm/activities/{id}',
{
  method: 'DELETE'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'


result = RestClient.delete 'https://api.apideck.com/crm/activities/{id}',
  params: {
  }

p JSON.parse(result)
```

```python
import requests

r = requests.delete('https://api.apideck.com/crm/activities/{id}', params={

)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/activities/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`DELETE /activities/{id}`

*Deletes a activity*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No description|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:activities )
</aside>

# Calls

Everything about your calls

## allCalls

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/calls \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/calls HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/calls',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/calls',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/calls',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/calls', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/calls");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /calls`

*Get all calls*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
page|query|integer|false|Page number to start from. Omitting the page parameter will return page 1
per_page|query|integer|false|Number of records to return per page. Default = 100.


> Example responses

```json
[
  {
    "id": "124",
    "owner_id": "349",
    "subject": "Call Marc Benioff",
    "description": "Go over the details of the contract",
    "start": "2017-08-12T14:00:00.001Z",
    "end": "2017-08-12T16:00:00.001Z",
    "duration": 120,
    "actual_start": "2017-08-12T14:00:00.001Z",
    "actual_end": "2017-08-12T16:00:00.001Z",
    "actual_duration": 120,
    "recording_url": "https://api.apideck.com/files/1350945",
    "voicemail_url": "https://api.apideck.com/files/139045945",
    "direction": "incoming",
    "missed": false,
    "linked_resources": [
      {
        "id": 2,
        "type": "Opportunity"
      }
    ],
    "creator_id": "456",
    "updated_at": "2017-08-12T20:43:21.291Z",
    "created_at": "2017-08-12T20:43:21.291Z"
  }
]
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|Inline

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[Call](#schemacall)]|false|No description
» id|string|false|No description
» owner_id|string|false|No description
» subject|string|false|No description
» description|string|false|No description
» start|string|false|No description
» end|string|false|No description
» duration|integer|false|No description
» actual_start|string|false|No description
» actual_end|string|false|No description
» actual_duration|integer|false|No description
» recording_url|string|false|No description
» voicemail_url|string|false|No description
» direction|string|false|No description
» missed|boolean|false|No description
» creator_id|string|false|No description
» updated_at|string|false|No description
» created_at|string|false|No description
» linked_resources|[[LinkedResource](#schemalinkedresource)]|false|No description
»» id|integer|false|No description
»» type|string|false|No description



<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:calls )
</aside>

## addCall

> Code samples

```shell
# You can also use wget
curl -X POST https://api.apideck.com/crm/calls \
  -H 'Content-Type: application/json'

```

```http
POST https://api.apideck.com/crm/calls HTTP/1.1
Host: api.apideck.com
Content-Type: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/calls',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "id": "124",
  "owner_id": "349",
  "subject": "Call Marc Benioff",
  "description": "Go over the details of the contract",
  "start": "2017-08-12T14:00:00.001Z",
  "end": "2017-08-12T16:00:00.001Z",
  "actual_start": "2017-08-12T14:00:00.001Z",
  "actual_end": "2017-08-12T16:00:00.001Z",
  "recording_url": "https://api.apideck.com/files/1350945",
  "voicemail_url": "https://api.apideck.com/files/139045945",
  "direction": "incoming",
  "missed": false,
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json'

};

fetch('https://api.apideck.com/crm/calls',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.post 'https://api.apideck.com/crm/calls',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.post('https://api.apideck.com/crm/calls', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/calls");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /calls`

*Add a new call*

> Body parameter

```json
{
  "id": "124",
  "owner_id": "349",
  "subject": "Call Marc Benioff",
  "description": "Go over the details of the contract",
  "start": "2017-08-12T14:00:00.001Z",
  "end": "2017-08-12T16:00:00.001Z",
  "actual_start": "2017-08-12T14:00:00.001Z",
  "actual_end": "2017-08-12T16:00:00.001Z",
  "recording_url": "https://api.apideck.com/files/1350945",
  "voicemail_url": "https://api.apideck.com/files/139045945",
  "direction": "incoming",
  "missed": false,
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
body|body|[Call](#schemacall)|true|Call object that needs to be added
» id|body|string|false|No description
» owner_id|body|string|false|No description
» subject|body|string|false|No description
» description|body|string|false|No description
» start|body|string|false|No description
» end|body|string|false|No description
» duration|body|integer|false|No description
» actual_start|body|string|false|No description
» actual_end|body|string|false|No description
» actual_duration|body|integer|false|No description
» recording_url|body|string|false|No description
» voicemail_url|body|string|false|No description
» direction|body|string|false|No description
» missed|body|boolean|false|No description
» creator_id|body|string|false|No description
» updated_at|body|string|false|No description
» created_at|body|string|false|No description
» linked_resources|body|[[LinkedResource](#schemalinkedresource)]|false|No description
»» id|body|integer|false|No description
»» type|body|string|false|No description


#### Enumerated Values

|Parameter|Value|
|---|---|
» direction|incoming/outgoing|
»» type|Lead/Opportunity/Person/Company|

### Responses

Status|Meaning|Description|Schema
---|---|---|---|
201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:calls )
</aside>

## getCall

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/calls/{id} \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/calls/{id} HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/calls/{id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/calls/{id}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/calls/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/calls/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/calls/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /calls/{id}`

*Find call by ID*

Returns a single call

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


> Example responses

```json
{
  "id": "124",
  "owner_id": "349",
  "subject": "Call Marc Benioff",
  "description": "Go over the details of the contract",
  "start": "2017-08-12T14:00:00.001Z",
  "end": "2017-08-12T16:00:00.001Z",
  "actual_start": "2017-08-12T14:00:00.001Z",
  "actual_end": "2017-08-12T16:00:00.001Z",
  "recording_url": "https://api.apideck.com/files/1350945",
  "voicemail_url": "https://api.apideck.com/files/139045945",
  "direction": "incoming",
  "missed": false,
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[Call](#schemacall)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:calls )
</aside>

## updateCall

> Code samples

```shell
# You can also use wget
curl -X PATCH https://api.apideck.com/crm/calls/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PATCH https://api.apideck.com/crm/calls/{id} HTTP/1.1
Host: api.apideck.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/calls/{id}',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "id": "124",
  "owner_id": "349",
  "subject": "Call Marc Benioff",
  "description": "Go over the details of the contract",
  "start": "2017-08-12T14:00:00.001Z",
  "end": "2017-08-12T16:00:00.001Z",
  "actual_start": "2017-08-12T14:00:00.001Z",
  "actual_end": "2017-08-12T16:00:00.001Z",
  "recording_url": "https://api.apideck.com/files/1350945",
  "voicemail_url": "https://api.apideck.com/files/139045945",
  "direction": "incoming",
  "missed": false,
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/calls/{id}',
{
  method: 'PATCH',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.patch 'https://api.apideck.com/crm/calls/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.patch('https://api.apideck.com/crm/calls/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/calls/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`PATCH /calls/{id}`

*Update an existing call*

> Body parameter

```json
{
  "id": "124",
  "owner_id": "349",
  "subject": "Call Marc Benioff",
  "description": "Go over the details of the contract",
  "start": "2017-08-12T14:00:00.001Z",
  "end": "2017-08-12T16:00:00.001Z",
  "actual_start": "2017-08-12T14:00:00.001Z",
  "actual_end": "2017-08-12T16:00:00.001Z",
  "recording_url": "https://api.apideck.com/files/1350945",
  "voicemail_url": "https://api.apideck.com/files/139045945",
  "direction": "incoming",
  "missed": false,
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return
body|body|[Call](#schemacall)|true|Fields that need to be updated on the resource
» id|body|string|false|No description
» owner_id|body|string|false|No description
» subject|body|string|false|No description
» description|body|string|false|No description
» start|body|string|false|No description
» end|body|string|false|No description
» duration|body|integer|false|No description
» actual_start|body|string|false|No description
» actual_end|body|string|false|No description
» actual_duration|body|integer|false|No description
» recording_url|body|string|false|No description
» voicemail_url|body|string|false|No description
» direction|body|string|false|No description
» missed|body|boolean|false|No description
» creator_id|body|string|false|No description
» updated_at|body|string|false|No description
» created_at|body|string|false|No description
» linked_resources|body|[[LinkedResource](#schemalinkedresource)]|false|No description
»» id|body|integer|false|No description
»» type|body|string|false|No description


#### Enumerated Values

|Parameter|Value|
|---|---|
» direction|incoming/outgoing|
»» type|Lead/Opportunity/Person/Company|

> Example responses

```json
{
  "id": "124",
  "owner_id": "349",
  "subject": "Call Marc Benioff",
  "description": "Go over the details of the contract",
  "start": "2017-08-12T14:00:00.001Z",
  "end": "2017-08-12T16:00:00.001Z",
  "actual_start": "2017-08-12T14:00:00.001Z",
  "actual_end": "2017-08-12T16:00:00.001Z",
  "recording_url": "https://api.apideck.com/files/1350945",
  "voicemail_url": "https://api.apideck.com/files/139045945",
  "direction": "incoming",
  "missed": false,
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[Call](#schemacall)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:calls )
</aside>

## deleteCall

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.apideck.com/crm/calls/{id}

```

```http
DELETE https://api.apideck.com/crm/calls/{id} HTTP/1.1
Host: api.apideck.com


```

```javascript

$.ajax({
  url: 'https://api.apideck.com/crm/calls/{id}',
  method: 'delete',

  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

fetch('https://api.apideck.com/crm/calls/{id}',
{
  method: 'DELETE'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'


result = RestClient.delete 'https://api.apideck.com/crm/calls/{id}',
  params: {
  }

p JSON.parse(result)
```

```python
import requests

r = requests.delete('https://api.apideck.com/crm/calls/{id}', params={

)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/calls/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`DELETE /calls/{id}`

*Deletes a call*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No description|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:calls )
</aside>

# Companies

Everything about your companies

## allCompanies

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/companies \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/companies HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/companies',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/companies',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/companies',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/companies', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/companies");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /companies`

*Get all companies*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
page|query|integer|false|Page number to start from. Omitting the page parameter will return page 1
per_page|query|integer|false|Number of records to return per page. Default = 100.


> Example responses

```json
[
  {
    "id": 1,
    "name": "Company XYZ",
    "owner_id": 1,
    "website": "https://www.apideck.com/crm",
    "email": "info@company.com",
    "image_url": "https://logo.clearbit.com/showpad.com?s=128",
    "description": "Most important account for our company",
    "firmographics": {
      "employees": 350,
      "credit_rating": 10
    },
    "industry": {
      "sector": "string",
      "naics_codes": [
        {
          "code": "string",
          "name": "string"
        }
      ]
    },
    "addresses": [
      {
        "type": "invoicing",
        "name": "HQ US",
        "line1": "Main street",
        "line2": "Main street",
        "city": "San Francisco",
        "state": "CA",
        "postal_code": "94104",
        "country": "US",
        "lattitude": "40.759211",
        "longitude": "-73.984638"
      }
    ],
    "phone_numbers": [
      {
        "number": "111-111-1111",
        "type": "mobile"
      }
    ],
    "tags": [
      "Retail",
      "EMEA"
    ],
    "social_links": [
      {
        "url": "https://www.twitter.com/apideck-io",
        "platform": "twitter"
      }
    ],
    "updated_at": "2017-08-12T20:43:21.291Z",
    "created_at": "2017-08-12T20:43:21.291Z"
  }
]
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|Inline

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[Company](#schemacompany)]|false|No description
» id|integer|false|No description
» name|string|true|No description
» owner_id|integer|false|No description
» website|string|false|No description
» email|string|false|No description
» image_url|string|false|No description
» description|string|false|No description
» firmographics|object|false|No description
»» employees|integer|false|No description
»» credit_rating|integer|false|No description
» industry|object|false|No description
»» sector|string|false|No description
»» naics_codes|[[NaicsCode](#schemanaicscode)]|false|No description
»»» code|string|false|No description
»»» name|string|false|No description
» updated_at|string|false|No description
» created_at|string|false|No description
» addresses|[[Address](#schemaaddress)]|false|No description
»» type|string|false|No description
»» name|string|false|No description
»» line1|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
»» line2|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
»» city|string|false|Name of city.
»» state|string|false|Name of state
»» postal_code|string|false|Zip code or equivalent.
»» country|string|false|country code according to ISO 3166-1 alpha-2.
»» lattitude|string|false|No description
»» longitude|string|false|No description
» phone_numbers|[[PhoneNumber](#schemaphonenumber)]|false|No description
»» number|string|false|No description
»» type|string|false|No description
» social_links|[[SocialLink](#schemasociallink)]|false|No description
»» url|string|false|No description
»» platform|string|false|No description



<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:companies )
</aside>

## addCompany

> Code samples

```shell
# You can also use wget
curl -X POST https://api.apideck.com/crm/companies \
  -H 'Content-Type: application/json'

```

```http
POST https://api.apideck.com/crm/companies HTTP/1.1
Host: api.apideck.com
Content-Type: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/companies',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "name": "Company XYZ",
  "owner_id": 1,
  "website": "https://www.apideck.com/crm",
  "email": "info@company.com",
  "image_url": "https://logo.clearbit.com/showpad.com?s=128",
  "description": "Most important account for our company",
  "firmographics": {
    "employees": 350,
    "credit_rating": 10
  },
  "industry": {
    "sector": "string",
    "naics_codes": [
      {
        "code": "string",
        "name": "string"
      }
    ]
  },
  "addresses": [
    {
      "type": "invoicing",
      "name": "HQ US",
      "line1": "Main street",
      "line2": "Main street",
      "city": "San Francisco",
      "state": "CA",
      "postal_code": "94104",
      "country": "US",
      "lattitude": "40.759211",
      "longitude": "-73.984638"
    }
  ],
  "phone_numbers": [
    {
      "number": "111-111-1111",
      "type": "mobile"
    }
  ],
  "tags": [
    "Retail",
    "EMEA"
  ],
  "social_links": [
    {
      "url": "https://www.twitter.com/apideck-io",
      "platform": "twitter"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json'

};

fetch('https://api.apideck.com/crm/companies',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.post 'https://api.apideck.com/crm/companies',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.post('https://api.apideck.com/crm/companies', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/companies");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /companies`

*Add a new company*

> Body parameter

```json
{
  "name": "Company XYZ",
  "owner_id": 1,
  "website": "https://www.apideck.com/crm",
  "email": "info@company.com",
  "image_url": "https://logo.clearbit.com/showpad.com?s=128",
  "description": "Most important account for our company",
  "firmographics": {
    "employees": 350,
    "credit_rating": 10
  },
  "industry": {
    "sector": "string",
    "naics_codes": [
      {
        "code": "string",
        "name": "string"
      }
    ]
  },
  "addresses": [
    {
      "type": "invoicing",
      "name": "HQ US",
      "line1": "Main street",
      "line2": "Main street",
      "city": "San Francisco",
      "state": "CA",
      "postal_code": "94104",
      "country": "US",
      "lattitude": "40.759211",
      "longitude": "-73.984638"
    }
  ],
  "phone_numbers": [
    {
      "number": "111-111-1111",
      "type": "mobile"
    }
  ],
  "tags": [
    "Retail",
    "EMEA"
  ],
  "social_links": [
    {
      "url": "https://www.twitter.com/apideck-io",
      "platform": "twitter"
    }
  ]
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
body|body|[Company](#schemacompany)|true|Company object that needs to be added
» id|body|integer|false|No description
» name|body|string|true|No description
» owner_id|body|integer|false|No description
» website|body|string|false|No description
» email|body|string|false|No description
» image_url|body|string|false|No description
» description|body|string|false|No description
» firmographics|body|object|false|No description
»» employees|body|integer|false|No description
»» credit_rating|body|integer|false|No description
» industry|body|object|false|No description
»» sector|body|string|false|No description
»» naics_codes|body|[[NaicsCode](#schemanaicscode)]|false|No description
»»» code|body|string|false|No description
»»» name|body|string|false|No description
» updated_at|body|string|false|No description
» created_at|body|string|false|No description
» addresses|body|[[Address](#schemaaddress)]|false|No description
»» type|body|string|false|No description
»» name|body|string|false|No description
»» line1|body|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
»» line2|body|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
»» city|body|string|false|Name of city.
»» state|body|string|false|Name of state
»» postal_code|body|string|false|Zip code or equivalent.
»» country|body|string|false|country code according to ISO 3166-1 alpha-2.
»» lattitude|body|string|false|No description
»» longitude|body|string|false|No description
» phone_numbers|body|[[PhoneNumber](#schemaphonenumber)]|false|No description
»» number|body|string|false|No description
»» type|body|string|false|No description
» social_links|body|[[SocialLink](#schemasociallink)]|false|No description
»» url|body|string|false|No description
»» platform|body|string|false|No description


#### Enumerated Values

|Parameter|Value|
|---|---|
»» type|default|
»» type|invoicing|
»» type|delivery|
»» type|visiting|
»» type|other|
»» type|mobile|
»» type|work|
»» type|home|
»» type|other|
»» platform|facebook|
»» platform|twitter|
»» platform|linkedin|
»» platform|other|

### Responses

Status|Meaning|Description|Schema
---|---|---|---|
201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:companies )
</aside>

## getCompany

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/companies/{id} \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/companies/{id} HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/companies/{id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/companies/{id}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/companies/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/companies/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/companies/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /companies/{id}`

*Find company by ID*

Returns a single company

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


> Example responses

```json
{
  "name": "Company XYZ",
  "owner_id": 1,
  "website": "https://www.apideck.com/crm",
  "email": "info@company.com",
  "image_url": "https://logo.clearbit.com/showpad.com?s=128",
  "description": "Most important account for our company",
  "firmographics": {
    "employees": 350,
    "credit_rating": 10
  },
  "industry": {
    "sector": "string",
    "naics_codes": [
      {
        "code": "string",
        "name": "string"
      }
    ]
  },
  "addresses": [
    {
      "type": "invoicing",
      "name": "HQ US",
      "line1": "Main street",
      "line2": "Main street",
      "city": "San Francisco",
      "state": "CA",
      "postal_code": "94104",
      "country": "US",
      "lattitude": "40.759211",
      "longitude": "-73.984638"
    }
  ],
  "phone_numbers": [
    {
      "number": "111-111-1111",
      "type": "mobile"
    }
  ],
  "tags": [
    "Retail",
    "EMEA"
  ],
  "social_links": [
    {
      "url": "https://www.twitter.com/apideck-io",
      "platform": "twitter"
    }
  ]
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[Company](#schemacompany)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:companies )
</aside>

## updateCompany

> Code samples

```shell
# You can also use wget
curl -X PATCH https://api.apideck.com/crm/companies/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PATCH https://api.apideck.com/crm/companies/{id} HTTP/1.1
Host: api.apideck.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/companies/{id}',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "name": "Company XYZ",
  "owner_id": 1,
  "website": "https://www.apideck.com/crm",
  "email": "info@company.com",
  "image_url": "https://logo.clearbit.com/showpad.com?s=128",
  "description": "Most important account for our company",
  "firmographics": {
    "employees": 350,
    "credit_rating": 10
  },
  "industry": {
    "sector": "string",
    "naics_codes": [
      {
        "code": "string",
        "name": "string"
      }
    ]
  },
  "addresses": [
    {
      "type": "invoicing",
      "name": "HQ US",
      "line1": "Main street",
      "line2": "Main street",
      "city": "San Francisco",
      "state": "CA",
      "postal_code": "94104",
      "country": "US",
      "lattitude": "40.759211",
      "longitude": "-73.984638"
    }
  ],
  "phone_numbers": [
    {
      "number": "111-111-1111",
      "type": "mobile"
    }
  ],
  "tags": [
    "Retail",
    "EMEA"
  ],
  "social_links": [
    {
      "url": "https://www.twitter.com/apideck-io",
      "platform": "twitter"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/companies/{id}',
{
  method: 'PATCH',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.patch 'https://api.apideck.com/crm/companies/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.patch('https://api.apideck.com/crm/companies/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/companies/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`PATCH /companies/{id}`

*Update an existing company*

> Body parameter

```json
{
  "name": "Company XYZ",
  "owner_id": 1,
  "website": "https://www.apideck.com/crm",
  "email": "info@company.com",
  "image_url": "https://logo.clearbit.com/showpad.com?s=128",
  "description": "Most important account for our company",
  "firmographics": {
    "employees": 350,
    "credit_rating": 10
  },
  "industry": {
    "sector": "string",
    "naics_codes": [
      {
        "code": "string",
        "name": "string"
      }
    ]
  },
  "addresses": [
    {
      "type": "invoicing",
      "name": "HQ US",
      "line1": "Main street",
      "line2": "Main street",
      "city": "San Francisco",
      "state": "CA",
      "postal_code": "94104",
      "country": "US",
      "lattitude": "40.759211",
      "longitude": "-73.984638"
    }
  ],
  "phone_numbers": [
    {
      "number": "111-111-1111",
      "type": "mobile"
    }
  ],
  "tags": [
    "Retail",
    "EMEA"
  ],
  "social_links": [
    {
      "url": "https://www.twitter.com/apideck-io",
      "platform": "twitter"
    }
  ]
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return
body|body|[Company](#schemacompany)|true|Fields that need to be updated on the resource
» id|body|integer|false|No description
» name|body|string|true|No description
» owner_id|body|integer|false|No description
» website|body|string|false|No description
» email|body|string|false|No description
» image_url|body|string|false|No description
» description|body|string|false|No description
» firmographics|body|object|false|No description
»» employees|body|integer|false|No description
»» credit_rating|body|integer|false|No description
» industry|body|object|false|No description
»» sector|body|string|false|No description
»» naics_codes|body|[[NaicsCode](#schemanaicscode)]|false|No description
»»» code|body|string|false|No description
»»» name|body|string|false|No description
» updated_at|body|string|false|No description
» created_at|body|string|false|No description
» addresses|body|[[Address](#schemaaddress)]|false|No description
»» type|body|string|false|No description
»» name|body|string|false|No description
»» line1|body|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
»» line2|body|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
»» city|body|string|false|Name of city.
»» state|body|string|false|Name of state
»» postal_code|body|string|false|Zip code or equivalent.
»» country|body|string|false|country code according to ISO 3166-1 alpha-2.
»» lattitude|body|string|false|No description
»» longitude|body|string|false|No description
» phone_numbers|body|[[PhoneNumber](#schemaphonenumber)]|false|No description
»» number|body|string|false|No description
»» type|body|string|false|No description
» social_links|body|[[SocialLink](#schemasociallink)]|false|No description
»» url|body|string|false|No description
»» platform|body|string|false|No description


#### Enumerated Values

|Parameter|Value|
|---|---|
»» type|default|
»» type|invoicing|
»» type|delivery|
»» type|visiting|
»» type|other|
»» type|mobile|
»» type|work|
»» type|home|
»» type|other|
»» platform|facebook|
»» platform|twitter|
»» platform|linkedin|
»» platform|other|

> Example responses

```json
{
  "name": "Company XYZ",
  "owner_id": 1,
  "website": "https://www.apideck.com/crm",
  "email": "info@company.com",
  "image_url": "https://logo.clearbit.com/showpad.com?s=128",
  "description": "Most important account for our company",
  "firmographics": {
    "employees": 350,
    "credit_rating": 10
  },
  "industry": {
    "sector": "string",
    "naics_codes": [
      {
        "code": "string",
        "name": "string"
      }
    ]
  },
  "addresses": [
    {
      "type": "invoicing",
      "name": "HQ US",
      "line1": "Main street",
      "line2": "Main street",
      "city": "San Francisco",
      "state": "CA",
      "postal_code": "94104",
      "country": "US",
      "lattitude": "40.759211",
      "longitude": "-73.984638"
    }
  ],
  "phone_numbers": [
    {
      "number": "111-111-1111",
      "type": "mobile"
    }
  ],
  "tags": [
    "Retail",
    "EMEA"
  ],
  "social_links": [
    {
      "url": "https://www.twitter.com/apideck-io",
      "platform": "twitter"
    }
  ]
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[Company](#schemacompany)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:companies )
</aside>

## deleteCompany

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.apideck.com/crm/companies/{id}

```

```http
DELETE https://api.apideck.com/crm/companies/{id} HTTP/1.1
Host: api.apideck.com


```

```javascript

$.ajax({
  url: 'https://api.apideck.com/crm/companies/{id}',
  method: 'delete',

  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

fetch('https://api.apideck.com/crm/companies/{id}',
{
  method: 'DELETE'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'


result = RestClient.delete 'https://api.apideck.com/crm/companies/{id}',
  params: {
  }

p JSON.parse(result)
```

```python
import requests

r = requests.delete('https://api.apideck.com/crm/companies/{id}', params={

)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/companies/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`DELETE /companies/{id}`

*Deletes a company*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No description|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:companies )
</aside>

# Contacts

Everything about your contacts

## allContacts

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/contacts \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/contacts HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/contacts',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/contacts',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/contacts',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/contacts', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/contacts");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /contacts`

*Get all contacts*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
page|query|integer|false|Page number to start from. Omitting the page parameter will return page 1
per_page|query|integer|false|Number of records to return per page. Default = 100.


> Example responses

```json
[
  {
    "id": 1,
    "owner_id": 1,
    "company_id": 2,
    "lead_id": 3,
    "name": "Tiger Woods",
    "first_name": "Tiger",
    "middle_name": "In The",
    "last_name": "Woods",
    "prefix": "Mr.",
    "suffix": "PhD",
    "email": "tiger@woods.com",
    "title": "CMO",
    "department": "Marketing",
    "language": "EN",
    "gender": "M",
    "birthday": "2000-08-12T20:43:21.291Z",
    "website": "https://www.apideck.com/crm",
    "image": "https://logo.clearbit.com/tigerwoods.com?s=128",
    "description": "Internal champion within his company",
    "addresses": [
      {
        "type": "invoicing",
        "name": "HQ US",
        "line1": "Main street",
        "line2": "Main street",
        "city": "San Francisco",
        "state": "CA",
        "postal_code": "94104",
        "country": "US",
        "lattitude": "40.759211",
        "longitude": "-73.984638"
      }
    ],
    "phone_numbers": [
      {
        "number": "111-111-1111",
        "type": "mobile"
      }
    ],
    "tags": [
      "Retail",
      "EMEA"
    ],
    "social_links": [
      {
        "url": "https://www.twitter.com/apideck-io",
        "platform": "twitter"
      }
    ],
    "updated_at": "2017-08-12T20:43:21.291Z",
    "created_at": "2017-08-12T20:43:21.291Z"
  }
]
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|Inline

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[Contact](#schemacontact)]|false|No description
» id|integer|false|No description
» owner_id|integer|false|No description
» company_id|integer|false|No description
» lead_id|integer|false|No description
» name|string|true|No description
» first_name|string|false|No description
» middle_name|string|false|No description
» last_name|string|false|No description
» prefix|string|false|No description
» suffix|string|false|No description
» email|string|false|No description
» title|string|false|No description
» department|string|false|No description
» language|string|false|language code according to ISO 639-1. For United Kingdom - EN
» gender|string|false|No description
» birthday|string|false|No description
» website|string|false|No description
» image|string|false|No description
» description|string|false|No description
» updated_at|string|false|No description
» created_at|string|false|No description
» addresses|[[Address](#schemaaddress)]|false|No description
»» type|string|false|No description
»» name|string|false|No description
»» line1|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
»» line2|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
»» city|string|false|Name of city.
»» state|string|false|Name of state
»» postal_code|string|false|Zip code or equivalent.
»» country|string|false|country code according to ISO 3166-1 alpha-2.
»» lattitude|string|false|No description
»» longitude|string|false|No description
» phone_numbers|[[PhoneNumber](#schemaphonenumber)]|false|No description
»» number|string|false|No description
»» type|string|false|No description
» social_links|[[SocialLink](#schemasociallink)]|false|No description
»» url|string|false|No description
»» platform|string|false|No description



<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:contacts )
</aside>

## addContact

> Code samples

```shell
# You can also use wget
curl -X POST https://api.apideck.com/crm/contacts \
  -H 'Content-Type: application/json'

```

```http
POST https://api.apideck.com/crm/contacts HTTP/1.1
Host: api.apideck.com
Content-Type: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/contacts',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "owner_id": 1,
  "company_id": 2,
  "lead_id": 3,
  "name": "Tiger Woods",
  "first_name": "Tiger",
  "middle_name": "In The",
  "last_name": "Woods",
  "prefix": "Mr.",
  "suffix": "PhD",
  "email": "tiger@woods.com",
  "title": "CMO",
  "department": "Marketing",
  "language": "EN",
  "gender": "M",
  "birthday": "2000-08-12T20:43:21.291Z",
  "website": "https://www.apideck.com/crm",
  "image": "https://logo.clearbit.com/tigerwoods.com?s=128",
  "description": "Internal champion within his company",
  "addresses": [
    {
      "type": "invoicing",
      "name": "HQ US",
      "line1": "Main street",
      "line2": "Main street",
      "city": "San Francisco",
      "state": "CA",
      "postal_code": "94104",
      "country": "US",
      "lattitude": "40.759211",
      "longitude": "-73.984638"
    }
  ],
  "phone_numbers": [
    {
      "number": "111-111-1111",
      "type": "mobile"
    }
  ],
  "tags": [
    "Retail",
    "EMEA"
  ],
  "social_links": [
    {
      "url": "https://www.twitter.com/apideck-io",
      "platform": "twitter"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json'

};

fetch('https://api.apideck.com/crm/contacts',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.post 'https://api.apideck.com/crm/contacts',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.post('https://api.apideck.com/crm/contacts', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/contacts");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /contacts`

*Add a new contact*

> Body parameter

```json
{
  "owner_id": 1,
  "company_id": 2,
  "lead_id": 3,
  "name": "Tiger Woods",
  "first_name": "Tiger",
  "middle_name": "In The",
  "last_name": "Woods",
  "prefix": "Mr.",
  "suffix": "PhD",
  "email": "tiger@woods.com",
  "title": "CMO",
  "department": "Marketing",
  "language": "EN",
  "gender": "M",
  "birthday": "2000-08-12T20:43:21.291Z",
  "website": "https://www.apideck.com/crm",
  "image": "https://logo.clearbit.com/tigerwoods.com?s=128",
  "description": "Internal champion within his company",
  "addresses": [
    {
      "type": "invoicing",
      "name": "HQ US",
      "line1": "Main street",
      "line2": "Main street",
      "city": "San Francisco",
      "state": "CA",
      "postal_code": "94104",
      "country": "US",
      "lattitude": "40.759211",
      "longitude": "-73.984638"
    }
  ],
  "phone_numbers": [
    {
      "number": "111-111-1111",
      "type": "mobile"
    }
  ],
  "tags": [
    "Retail",
    "EMEA"
  ],
  "social_links": [
    {
      "url": "https://www.twitter.com/apideck-io",
      "platform": "twitter"
    }
  ]
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
body|body|[Contact](#schemacontact)|true|Contact object that needs to be added
» id|body|integer|false|No description
» owner_id|body|integer|false|No description
» company_id|body|integer|false|No description
» lead_id|body|integer|false|No description
» name|body|string|true|No description
» first_name|body|string|false|No description
» middle_name|body|string|false|No description
» last_name|body|string|false|No description
» prefix|body|string|false|No description
» suffix|body|string|false|No description
» email|body|string|false|No description
» title|body|string|false|No description
» department|body|string|false|No description
» language|body|string|false|language code according to ISO 639-1. For United Kingdom - EN
» gender|body|string|false|No description
» birthday|body|string|false|No description
» website|body|string|false|No description
» image|body|string|false|No description
» description|body|string|false|No description
» updated_at|body|string|false|No description
» created_at|body|string|false|No description
» addresses|body|[[Address](#schemaaddress)]|false|No description
»» type|body|string|false|No description
»» name|body|string|false|No description
»» line1|body|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
»» line2|body|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
»» city|body|string|false|Name of city.
»» state|body|string|false|Name of state
»» postal_code|body|string|false|Zip code or equivalent.
»» country|body|string|false|country code according to ISO 3166-1 alpha-2.
»» lattitude|body|string|false|No description
»» longitude|body|string|false|No description
» phone_numbers|body|[[PhoneNumber](#schemaphonenumber)]|false|No description
»» number|body|string|false|No description
»» type|body|string|false|No description
» social_links|body|[[SocialLink](#schemasociallink)]|false|No description
»» url|body|string|false|No description
»» platform|body|string|false|No description


#### Enumerated Values

|Parameter|Value|
|---|---|
» gender|M/F/U|
»» type|default|
»» type|invoicing|
»» type|delivery|
»» type|visiting|
»» type|other|
»» type|mobile|
»» type|work|
»» type|home|
»» type|other|
»» platform|facebook|
»» platform|twitter|
»» platform|linkedin|
»» platform|other|

### Responses

Status|Meaning|Description|Schema
---|---|---|---|
201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:contacts )
</aside>

## getContact

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/contacts/{id} \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/contacts/{id} HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/contacts/{id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/contacts/{id}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/contacts/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/contacts/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/contacts/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /contacts/{id}`

*Find contact by ID*

Returns a single contact

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


> Example responses

```json
{
  "owner_id": 1,
  "company_id": 2,
  "lead_id": 3,
  "name": "Tiger Woods",
  "first_name": "Tiger",
  "middle_name": "In The",
  "last_name": "Woods",
  "prefix": "Mr.",
  "suffix": "PhD",
  "email": "tiger@woods.com",
  "title": "CMO",
  "department": "Marketing",
  "language": "EN",
  "gender": "M",
  "birthday": "2000-08-12T20:43:21.291Z",
  "website": "https://www.apideck.com/crm",
  "image": "https://logo.clearbit.com/tigerwoods.com?s=128",
  "description": "Internal champion within his company",
  "addresses": [
    {
      "type": "invoicing",
      "name": "HQ US",
      "line1": "Main street",
      "line2": "Main street",
      "city": "San Francisco",
      "state": "CA",
      "postal_code": "94104",
      "country": "US",
      "lattitude": "40.759211",
      "longitude": "-73.984638"
    }
  ],
  "phone_numbers": [
    {
      "number": "111-111-1111",
      "type": "mobile"
    }
  ],
  "tags": [
    "Retail",
    "EMEA"
  ],
  "social_links": [
    {
      "url": "https://www.twitter.com/apideck-io",
      "platform": "twitter"
    }
  ]
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[Contact](#schemacontact)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:contacts )
</aside>

## updateContact

> Code samples

```shell
# You can also use wget
curl -X PATCH https://api.apideck.com/crm/contacts/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PATCH https://api.apideck.com/crm/contacts/{id} HTTP/1.1
Host: api.apideck.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/contacts/{id}',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "owner_id": 1,
  "company_id": 2,
  "lead_id": 3,
  "name": "Tiger Woods",
  "first_name": "Tiger",
  "middle_name": "In The",
  "last_name": "Woods",
  "prefix": "Mr.",
  "suffix": "PhD",
  "email": "tiger@woods.com",
  "title": "CMO",
  "department": "Marketing",
  "language": "EN",
  "gender": "M",
  "birthday": "2000-08-12T20:43:21.291Z",
  "website": "https://www.apideck.com/crm",
  "image": "https://logo.clearbit.com/tigerwoods.com?s=128",
  "description": "Internal champion within his company",
  "addresses": [
    {
      "type": "invoicing",
      "name": "HQ US",
      "line1": "Main street",
      "line2": "Main street",
      "city": "San Francisco",
      "state": "CA",
      "postal_code": "94104",
      "country": "US",
      "lattitude": "40.759211",
      "longitude": "-73.984638"
    }
  ],
  "phone_numbers": [
    {
      "number": "111-111-1111",
      "type": "mobile"
    }
  ],
  "tags": [
    "Retail",
    "EMEA"
  ],
  "social_links": [
    {
      "url": "https://www.twitter.com/apideck-io",
      "platform": "twitter"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/contacts/{id}',
{
  method: 'PATCH',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.patch 'https://api.apideck.com/crm/contacts/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.patch('https://api.apideck.com/crm/contacts/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/contacts/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`PATCH /contacts/{id}`

*Update an existing contact*

> Body parameter

```json
{
  "owner_id": 1,
  "company_id": 2,
  "lead_id": 3,
  "name": "Tiger Woods",
  "first_name": "Tiger",
  "middle_name": "In The",
  "last_name": "Woods",
  "prefix": "Mr.",
  "suffix": "PhD",
  "email": "tiger@woods.com",
  "title": "CMO",
  "department": "Marketing",
  "language": "EN",
  "gender": "M",
  "birthday": "2000-08-12T20:43:21.291Z",
  "website": "https://www.apideck.com/crm",
  "image": "https://logo.clearbit.com/tigerwoods.com?s=128",
  "description": "Internal champion within his company",
  "addresses": [
    {
      "type": "invoicing",
      "name": "HQ US",
      "line1": "Main street",
      "line2": "Main street",
      "city": "San Francisco",
      "state": "CA",
      "postal_code": "94104",
      "country": "US",
      "lattitude": "40.759211",
      "longitude": "-73.984638"
    }
  ],
  "phone_numbers": [
    {
      "number": "111-111-1111",
      "type": "mobile"
    }
  ],
  "tags": [
    "Retail",
    "EMEA"
  ],
  "social_links": [
    {
      "url": "https://www.twitter.com/apideck-io",
      "platform": "twitter"
    }
  ]
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return
body|body|[Contact](#schemacontact)|true|Fields that need to be updated on the resource
» id|body|integer|false|No description
» owner_id|body|integer|false|No description
» company_id|body|integer|false|No description
» lead_id|body|integer|false|No description
» name|body|string|true|No description
» first_name|body|string|false|No description
» middle_name|body|string|false|No description
» last_name|body|string|false|No description
» prefix|body|string|false|No description
» suffix|body|string|false|No description
» email|body|string|false|No description
» title|body|string|false|No description
» department|body|string|false|No description
» language|body|string|false|language code according to ISO 639-1. For United Kingdom - EN
» gender|body|string|false|No description
» birthday|body|string|false|No description
» website|body|string|false|No description
» image|body|string|false|No description
» description|body|string|false|No description
» updated_at|body|string|false|No description
» created_at|body|string|false|No description
» addresses|body|[[Address](#schemaaddress)]|false|No description
»» type|body|string|false|No description
»» name|body|string|false|No description
»» line1|body|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
»» line2|body|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
»» city|body|string|false|Name of city.
»» state|body|string|false|Name of state
»» postal_code|body|string|false|Zip code or equivalent.
»» country|body|string|false|country code according to ISO 3166-1 alpha-2.
»» lattitude|body|string|false|No description
»» longitude|body|string|false|No description
» phone_numbers|body|[[PhoneNumber](#schemaphonenumber)]|false|No description
»» number|body|string|false|No description
»» type|body|string|false|No description
» social_links|body|[[SocialLink](#schemasociallink)]|false|No description
»» url|body|string|false|No description
»» platform|body|string|false|No description


#### Enumerated Values

|Parameter|Value|
|---|---|
» gender|M/F/U|
»» type|default|
»» type|invoicing|
»» type|delivery|
»» type|visiting|
»» type|other|
»» type|mobile|
»» type|work|
»» type|home|
»» type|other|
»» platform|facebook|
»» platform|twitter|
»» platform|linkedin|
»» platform|other|

> Example responses

```json
{
  "owner_id": 1,
  "company_id": 2,
  "lead_id": 3,
  "name": "Tiger Woods",
  "first_name": "Tiger",
  "middle_name": "In The",
  "last_name": "Woods",
  "prefix": "Mr.",
  "suffix": "PhD",
  "email": "tiger@woods.com",
  "title": "CMO",
  "department": "Marketing",
  "language": "EN",
  "gender": "M",
  "birthday": "2000-08-12T20:43:21.291Z",
  "website": "https://www.apideck.com/crm",
  "image": "https://logo.clearbit.com/tigerwoods.com?s=128",
  "description": "Internal champion within his company",
  "addresses": [
    {
      "type": "invoicing",
      "name": "HQ US",
      "line1": "Main street",
      "line2": "Main street",
      "city": "San Francisco",
      "state": "CA",
      "postal_code": "94104",
      "country": "US",
      "lattitude": "40.759211",
      "longitude": "-73.984638"
    }
  ],
  "phone_numbers": [
    {
      "number": "111-111-1111",
      "type": "mobile"
    }
  ],
  "tags": [
    "Retail",
    "EMEA"
  ],
  "social_links": [
    {
      "url": "https://www.twitter.com/apideck-io",
      "platform": "twitter"
    }
  ]
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[Contact](#schemacontact)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:contacts )
</aside>

## deleteContact

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.apideck.com/crm/contacts/{id}

```

```http
DELETE https://api.apideck.com/crm/contacts/{id} HTTP/1.1
Host: api.apideck.com


```

```javascript

$.ajax({
  url: 'https://api.apideck.com/crm/contacts/{id}',
  method: 'delete',

  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

fetch('https://api.apideck.com/crm/contacts/{id}',
{
  method: 'DELETE'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'


result = RestClient.delete 'https://api.apideck.com/crm/contacts/{id}',
  params: {
  }

p JSON.parse(result)
```

```python
import requests

r = requests.delete('https://api.apideck.com/crm/contacts/{id}', params={

)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/contacts/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`DELETE /contacts/{id}`

*Deletes a contact*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No description|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:contacts )
</aside>

# Opportunities

Everything about your opportunities

## allOpportunities

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/opportunities \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/opportunities HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/opportunities',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/opportunities',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/opportunities',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/opportunities', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/opportunities");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /opportunities`

*Get all opportunities*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
page|query|integer|false|Page number to start from. Omitting the page parameter will return page 1
per_page|query|integer|false|Number of records to return per page. Default = 100.


> Example responses

```json
[
  {
    "id": 99,
    "name": "Multi-year deal CRM",
    "value": 3000,
    "currency": "USD",
    "description": "Looking into end-to-end solutions",
    "owner_id": 10,
    "contact_id": 15,
    "company_id": 17,
    "stage_id": 20,
    "status": "Open",
    "close_date": "10-05-2016",
    "lost_reason": "Out of budget",
    "probability": 50,
    "source_id": 11,
    "pipeline_id": 2,
    "creator_id": 145,
    "updated_at": "2017-08-12T20:43:21.291Z",
    "created_at": "2017-08-12T20:43:21.291Z"
  }
]
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|Inline

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[Opportunity](#schemaopportunity)]|false|No description
» id|integer|false|No description
» name|string|false|No description
» value|integer|false|No description
» currency|string|false|No description
» description|string|false|No description
» owner_id|integer|false|No description
» contact_id|integer|false|No description
» company_id|integer|false|No description
» stage_id|integer|false|No description
» status|string|false|No description
» close_date|string|false|No description
» lost_reason|string|false|No description
» probability|integer|false|No description
» source_id|integer|false|No description
» pipeline_id|integer|false|No description
» creator_id|integer|false|No description
» updated_at|string|false|No description
» created_at|string|false|No description



<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:opportunities )
</aside>

## addOpportunity

> Code samples

```shell
# You can also use wget
curl -X POST https://api.apideck.com/crm/opportunities \
  -H 'Content-Type: application/json'

```

```http
POST https://api.apideck.com/crm/opportunities HTTP/1.1
Host: api.apideck.com
Content-Type: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/opportunities',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "name": "Multi-year deal CRM",
  "value": 3000,
  "currency": "USD",
  "description": "Looking into end-to-end solutions",
  "owner_id": 10,
  "contact_id": 15,
  "company_id": 17,
  "stage_id": 20,
  "status": "Open",
  "close_date": "10-05-2016",
  "lost_reason": "Out of budget",
  "probability": 50,
  "source_id": 11,
  "pipeline_id": 2,
  "creator_id": 145
}';
const headers = {
  'Content-Type':'application/json'

};

fetch('https://api.apideck.com/crm/opportunities',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.post 'https://api.apideck.com/crm/opportunities',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.post('https://api.apideck.com/crm/opportunities', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/opportunities");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /opportunities`

*Add a new opportunity*

> Body parameter

```json
{
  "name": "Multi-year deal CRM",
  "value": 3000,
  "currency": "USD",
  "description": "Looking into end-to-end solutions",
  "owner_id": 10,
  "contact_id": 15,
  "company_id": 17,
  "stage_id": 20,
  "status": "Open",
  "close_date": "10-05-2016",
  "lost_reason": "Out of budget",
  "probability": 50,
  "source_id": 11,
  "pipeline_id": 2,
  "creator_id": 145
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
body|body|[Opportunity](#schemaopportunity)|true|Opportunity object that needs to be added
» id|body|integer|false|No description
» name|body|string|false|No description
» value|body|integer|false|No description
» currency|body|string|false|No description
» description|body|string|false|No description
» owner_id|body|integer|false|No description
» contact_id|body|integer|false|No description
» company_id|body|integer|false|No description
» stage_id|body|integer|false|No description
» status|body|string|false|No description
» close_date|body|string|false|No description
» lost_reason|body|string|false|No description
» probability|body|integer|false|No description
» source_id|body|integer|false|No description
» pipeline_id|body|integer|false|No description
» creator_id|body|integer|false|No description
» updated_at|body|string|false|No description
» created_at|body|string|false|No description


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:opportunities )
</aside>

## getOpportunity

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/opportunities/{id} \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/opportunities/{id} HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/opportunities/{id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/opportunities/{id}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/opportunities/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/opportunities/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/opportunities/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /opportunities/{id}`

*Find opportunity by ID*

Returns a single opportunity

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


> Example responses

```json
{
  "name": "Multi-year deal CRM",
  "value": 3000,
  "currency": "USD",
  "description": "Looking into end-to-end solutions",
  "owner_id": 10,
  "contact_id": 15,
  "company_id": 17,
  "stage_id": 20,
  "status": "Open",
  "close_date": "10-05-2016",
  "lost_reason": "Out of budget",
  "probability": 50,
  "source_id": 11,
  "pipeline_id": 2,
  "creator_id": 145
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[Opportunity](#schemaopportunity)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:opportunities )
</aside>

## updateOpportunity

> Code samples

```shell
# You can also use wget
curl -X PATCH https://api.apideck.com/crm/opportunities/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PATCH https://api.apideck.com/crm/opportunities/{id} HTTP/1.1
Host: api.apideck.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/opportunities/{id}',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "name": "Multi-year deal CRM",
  "value": 3000,
  "currency": "USD",
  "description": "Looking into end-to-end solutions",
  "owner_id": 10,
  "contact_id": 15,
  "company_id": 17,
  "stage_id": 20,
  "status": "Open",
  "close_date": "10-05-2016",
  "lost_reason": "Out of budget",
  "probability": 50,
  "source_id": 11,
  "pipeline_id": 2,
  "creator_id": 145
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/opportunities/{id}',
{
  method: 'PATCH',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.patch 'https://api.apideck.com/crm/opportunities/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.patch('https://api.apideck.com/crm/opportunities/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/opportunities/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`PATCH /opportunities/{id}`

*Update an existing opportunity*

> Body parameter

```json
{
  "name": "Multi-year deal CRM",
  "value": 3000,
  "currency": "USD",
  "description": "Looking into end-to-end solutions",
  "owner_id": 10,
  "contact_id": 15,
  "company_id": 17,
  "stage_id": 20,
  "status": "Open",
  "close_date": "10-05-2016",
  "lost_reason": "Out of budget",
  "probability": 50,
  "source_id": 11,
  "pipeline_id": 2,
  "creator_id": 145
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return
body|body|[Opportunity](#schemaopportunity)|true|Fields that need to be updated on the resource
» id|body|integer|false|No description
» name|body|string|false|No description
» value|body|integer|false|No description
» currency|body|string|false|No description
» description|body|string|false|No description
» owner_id|body|integer|false|No description
» contact_id|body|integer|false|No description
» company_id|body|integer|false|No description
» stage_id|body|integer|false|No description
» status|body|string|false|No description
» close_date|body|string|false|No description
» lost_reason|body|string|false|No description
» probability|body|integer|false|No description
» source_id|body|integer|false|No description
» pipeline_id|body|integer|false|No description
» creator_id|body|integer|false|No description
» updated_at|body|string|false|No description
» created_at|body|string|false|No description


> Example responses

```json
{
  "name": "Multi-year deal CRM",
  "value": 3000,
  "currency": "USD",
  "description": "Looking into end-to-end solutions",
  "owner_id": 10,
  "contact_id": 15,
  "company_id": 17,
  "stage_id": 20,
  "status": "Open",
  "close_date": "10-05-2016",
  "lost_reason": "Out of budget",
  "probability": 50,
  "source_id": 11,
  "pipeline_id": 2,
  "creator_id": 145
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[Opportunity](#schemaopportunity)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:opportunities )
</aside>

## deleteOpportunity

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.apideck.com/crm/opportunities/{id}

```

```http
DELETE https://api.apideck.com/crm/opportunities/{id} HTTP/1.1
Host: api.apideck.com


```

```javascript

$.ajax({
  url: 'https://api.apideck.com/crm/opportunities/{id}',
  method: 'delete',

  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

fetch('https://api.apideck.com/crm/opportunities/{id}',
{
  method: 'DELETE'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'


result = RestClient.delete 'https://api.apideck.com/crm/opportunities/{id}',
  params: {
  }

p JSON.parse(result)
```

```python
import requests

r = requests.delete('https://api.apideck.com/crm/opportunities/{id}', params={

)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/opportunities/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`DELETE /opportunities/{id}`

*Deletes a opportunity*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No description|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:opportunities )
</aside>

# Leads

Everything about your leads

## allLeads

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/leads \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/leads HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/leads',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/leads',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/leads',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/leads', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/leads");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /leads`

*Get all leads*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
page|query|integer|false|Page number to start from. Omitting the page parameter will return page 1
per_page|query|integer|false|Number of records to return per page. Default = 100.


> Example responses

```json
[
  {
    "id": 0,
    "owner_id": 14,
    "first_name": "Tiger",
    "middle_name": "In The",
    "last_name": "Woods",
    "prefix": "Mr.",
    "suffix": "PhD",
    "title": "CMO",
    "company": "Tiger Inc.",
    "industry": "Sports Industry",
    "status": "Open",
    "rating": "Hot",
    "source_id": 2,
    "description": "Expert in CRM integration.",
    "website": "http://www.tigerwoods.com",
    "email": "tiger@woods.com",
    "addresses": [
      {
        "type": "invoicing",
        "name": "HQ US",
        "line1": "Main street",
        "line2": "Main street",
        "city": "San Francisco",
        "state": "CA",
        "postal_code": "94104",
        "country": "US",
        "lattitude": "40.759211",
        "longitude": "-73.984638"
      }
    ],
    "phone_numbers": [
      {
        "number": "111-111-1111",
        "type": "mobile"
      }
    ],
    "social_links": [
      {
        "url": "https://www.twitter.com/apideck-io",
        "platform": "twitter"
      }
    ],
    "tags": [
      "Retail",
      "Sports"
    ],
    "custom_fields": {
      "known_via": "John"
    },
    "updated_at": "2017-08-12T20:43:21.291Z",
    "created_at": "2017-08-12T20:43:21.291Z"
  }
]
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|Inline

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[Lead](#schemalead)]|false|No description
» id|integer|false|No description
» owner_id|integer|false|No description
» first_name|string|false|No description
» middle_name|string|false|No description
» last_name|string|false|No description
» prefix|string|false|No description
» suffix|string|false|No description
» title|string|false|No description
» company|string|false|No description
» industry|string|false|No description
» status|string|false|No description
» rating|string|false|No description
» source_id|integer|false|No description
» description|string|false|No description
» website|string|false|No description
» email|string|false|No description
» custom_fields|object|false|No description
» updated_at|string|false|No description
» created_at|string|false|No description
» addresses|[[Address](#schemaaddress)]|false|No description
»» type|string|false|No description
»» name|string|false|No description
»» line1|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
»» line2|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
»» city|string|false|Name of city.
»» state|string|false|Name of state
»» postal_code|string|false|Zip code or equivalent.
»» country|string|false|country code according to ISO 3166-1 alpha-2.
»» lattitude|string|false|No description
»» longitude|string|false|No description
» phone_numbers|[[PhoneNumber](#schemaphonenumber)]|false|No description
»» number|string|false|No description
»» type|string|false|No description
» social_links|[[SocialLink](#schemasociallink)]|false|No description
»» url|string|false|No description
»» platform|string|false|No description



<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:leads )
</aside>

## addLead

> Code samples

```shell
# You can also use wget
curl -X POST https://api.apideck.com/crm/leads \
  -H 'Content-Type: application/json'

```

```http
POST https://api.apideck.com/crm/leads HTTP/1.1
Host: api.apideck.com
Content-Type: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/leads',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "owner_id": 14,
  "first_name": "Tiger",
  "middle_name": "In The",
  "last_name": "Woods",
  "prefix": "Mr.",
  "suffix": "PhD",
  "title": "CMO",
  "company": "Tiger Inc.",
  "industry": "Sports Industry",
  "status": "Open",
  "rating": "Hot",
  "source_id": 2,
  "description": "Expert in CRM integration.",
  "website": "http://www.tigerwoods.com",
  "email": "tiger@woods.com",
  "addresses": [
    {
      "type": "invoicing",
      "name": "HQ US",
      "line1": "Main street",
      "line2": "Main street",
      "city": "San Francisco",
      "state": "CA",
      "postal_code": "94104",
      "country": "US",
      "lattitude": "40.759211",
      "longitude": "-73.984638"
    }
  ],
  "phone_numbers": [
    {
      "number": "111-111-1111",
      "type": "mobile"
    }
  ],
  "social_links": [
    {
      "url": "https://www.twitter.com/apideck-io",
      "platform": "twitter"
    }
  ],
  "tags": [
    "Retail",
    "Sports"
  ],
  "custom_fields": {
    "known_via": "John"
  }
}';
const headers = {
  'Content-Type':'application/json'

};

fetch('https://api.apideck.com/crm/leads',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.post 'https://api.apideck.com/crm/leads',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.post('https://api.apideck.com/crm/leads', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/leads");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /leads`

*Add a new lead*

> Body parameter

```json
{
  "owner_id": 14,
  "first_name": "Tiger",
  "middle_name": "In The",
  "last_name": "Woods",
  "prefix": "Mr.",
  "suffix": "PhD",
  "title": "CMO",
  "company": "Tiger Inc.",
  "industry": "Sports Industry",
  "status": "Open",
  "rating": "Hot",
  "source_id": 2,
  "description": "Expert in CRM integration.",
  "website": "http://www.tigerwoods.com",
  "email": "tiger@woods.com",
  "addresses": [
    {
      "type": "invoicing",
      "name": "HQ US",
      "line1": "Main street",
      "line2": "Main street",
      "city": "San Francisco",
      "state": "CA",
      "postal_code": "94104",
      "country": "US",
      "lattitude": "40.759211",
      "longitude": "-73.984638"
    }
  ],
  "phone_numbers": [
    {
      "number": "111-111-1111",
      "type": "mobile"
    }
  ],
  "social_links": [
    {
      "url": "https://www.twitter.com/apideck-io",
      "platform": "twitter"
    }
  ],
  "tags": [
    "Retail",
    "Sports"
  ],
  "custom_fields": {
    "known_via": "John"
  }
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
body|body|[Lead](#schemalead)|true|Lead object that needs to be added
» id|body|integer|false|No description
» owner_id|body|integer|false|No description
» first_name|body|string|false|No description
» middle_name|body|string|false|No description
» last_name|body|string|false|No description
» prefix|body|string|false|No description
» suffix|body|string|false|No description
» title|body|string|false|No description
» company|body|string|false|No description
» industry|body|string|false|No description
» status|body|string|false|No description
» rating|body|string|false|No description
» source_id|body|integer|false|No description
» description|body|string|false|No description
» website|body|string|false|No description
» email|body|string|false|No description
» custom_fields|body|object|false|No description
» updated_at|body|string|false|No description
» created_at|body|string|false|No description
» addresses|body|[[Address](#schemaaddress)]|false|No description
»» type|body|string|false|No description
»» name|body|string|false|No description
»» line1|body|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
»» line2|body|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
»» city|body|string|false|Name of city.
»» state|body|string|false|Name of state
»» postal_code|body|string|false|Zip code or equivalent.
»» country|body|string|false|country code according to ISO 3166-1 alpha-2.
»» lattitude|body|string|false|No description
»» longitude|body|string|false|No description
» phone_numbers|body|[[PhoneNumber](#schemaphonenumber)]|false|No description
»» number|body|string|false|No description
»» type|body|string|false|No description
» social_links|body|[[SocialLink](#schemasociallink)]|false|No description
»» url|body|string|false|No description
»» platform|body|string|false|No description


#### Enumerated Values

|Parameter|Value|
|---|---|
»» type|default|
»» type|invoicing|
»» type|delivery|
»» type|visiting|
»» type|other|
»» type|mobile|
»» type|work|
»» type|home|
»» type|other|
»» platform|facebook|
»» platform|twitter|
»» platform|linkedin|
»» platform|other|

### Responses

Status|Meaning|Description|Schema
---|---|---|---|
201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:leads )
</aside>

## getLead

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/leads/{id} \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/leads/{id} HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/leads/{id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/leads/{id}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/leads/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/leads/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/leads/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /leads/{id}`

*Find lead by ID*

Returns a single lead

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


> Example responses

```json
{
  "owner_id": 14,
  "first_name": "Tiger",
  "middle_name": "In The",
  "last_name": "Woods",
  "prefix": "Mr.",
  "suffix": "PhD",
  "title": "CMO",
  "company": "Tiger Inc.",
  "industry": "Sports Industry",
  "status": "Open",
  "rating": "Hot",
  "source_id": 2,
  "description": "Expert in CRM integration.",
  "website": "http://www.tigerwoods.com",
  "email": "tiger@woods.com",
  "addresses": [
    {
      "type": "invoicing",
      "name": "HQ US",
      "line1": "Main street",
      "line2": "Main street",
      "city": "San Francisco",
      "state": "CA",
      "postal_code": "94104",
      "country": "US",
      "lattitude": "40.759211",
      "longitude": "-73.984638"
    }
  ],
  "phone_numbers": [
    {
      "number": "111-111-1111",
      "type": "mobile"
    }
  ],
  "social_links": [
    {
      "url": "https://www.twitter.com/apideck-io",
      "platform": "twitter"
    }
  ],
  "tags": [
    "Retail",
    "Sports"
  ],
  "custom_fields": {
    "known_via": "John"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[Lead](#schemalead)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:leads )
</aside>

## updateLead

> Code samples

```shell
# You can also use wget
curl -X PATCH https://api.apideck.com/crm/leads/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PATCH https://api.apideck.com/crm/leads/{id} HTTP/1.1
Host: api.apideck.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/leads/{id}',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "owner_id": 14,
  "first_name": "Tiger",
  "middle_name": "In The",
  "last_name": "Woods",
  "prefix": "Mr.",
  "suffix": "PhD",
  "title": "CMO",
  "company": "Tiger Inc.",
  "industry": "Sports Industry",
  "status": "Open",
  "rating": "Hot",
  "source_id": 2,
  "description": "Expert in CRM integration.",
  "website": "http://www.tigerwoods.com",
  "email": "tiger@woods.com",
  "addresses": [
    {
      "type": "invoicing",
      "name": "HQ US",
      "line1": "Main street",
      "line2": "Main street",
      "city": "San Francisco",
      "state": "CA",
      "postal_code": "94104",
      "country": "US",
      "lattitude": "40.759211",
      "longitude": "-73.984638"
    }
  ],
  "phone_numbers": [
    {
      "number": "111-111-1111",
      "type": "mobile"
    }
  ],
  "social_links": [
    {
      "url": "https://www.twitter.com/apideck-io",
      "platform": "twitter"
    }
  ],
  "tags": [
    "Retail",
    "Sports"
  ],
  "custom_fields": {
    "known_via": "John"
  }
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/leads/{id}',
{
  method: 'PATCH',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.patch 'https://api.apideck.com/crm/leads/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.patch('https://api.apideck.com/crm/leads/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/leads/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`PATCH /leads/{id}`

*Update an existing lead*

> Body parameter

```json
{
  "owner_id": 14,
  "first_name": "Tiger",
  "middle_name": "In The",
  "last_name": "Woods",
  "prefix": "Mr.",
  "suffix": "PhD",
  "title": "CMO",
  "company": "Tiger Inc.",
  "industry": "Sports Industry",
  "status": "Open",
  "rating": "Hot",
  "source_id": 2,
  "description": "Expert in CRM integration.",
  "website": "http://www.tigerwoods.com",
  "email": "tiger@woods.com",
  "addresses": [
    {
      "type": "invoicing",
      "name": "HQ US",
      "line1": "Main street",
      "line2": "Main street",
      "city": "San Francisco",
      "state": "CA",
      "postal_code": "94104",
      "country": "US",
      "lattitude": "40.759211",
      "longitude": "-73.984638"
    }
  ],
  "phone_numbers": [
    {
      "number": "111-111-1111",
      "type": "mobile"
    }
  ],
  "social_links": [
    {
      "url": "https://www.twitter.com/apideck-io",
      "platform": "twitter"
    }
  ],
  "tags": [
    "Retail",
    "Sports"
  ],
  "custom_fields": {
    "known_via": "John"
  }
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return
body|body|[Lead](#schemalead)|true|Fields that need to be updated on the resource
» id|body|integer|false|No description
» owner_id|body|integer|false|No description
» first_name|body|string|false|No description
» middle_name|body|string|false|No description
» last_name|body|string|false|No description
» prefix|body|string|false|No description
» suffix|body|string|false|No description
» title|body|string|false|No description
» company|body|string|false|No description
» industry|body|string|false|No description
» status|body|string|false|No description
» rating|body|string|false|No description
» source_id|body|integer|false|No description
» description|body|string|false|No description
» website|body|string|false|No description
» email|body|string|false|No description
» custom_fields|body|object|false|No description
» updated_at|body|string|false|No description
» created_at|body|string|false|No description
» addresses|body|[[Address](#schemaaddress)]|false|No description
»» type|body|string|false|No description
»» name|body|string|false|No description
»» line1|body|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
»» line2|body|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
»» city|body|string|false|Name of city.
»» state|body|string|false|Name of state
»» postal_code|body|string|false|Zip code or equivalent.
»» country|body|string|false|country code according to ISO 3166-1 alpha-2.
»» lattitude|body|string|false|No description
»» longitude|body|string|false|No description
» phone_numbers|body|[[PhoneNumber](#schemaphonenumber)]|false|No description
»» number|body|string|false|No description
»» type|body|string|false|No description
» social_links|body|[[SocialLink](#schemasociallink)]|false|No description
»» url|body|string|false|No description
»» platform|body|string|false|No description


#### Enumerated Values

|Parameter|Value|
|---|---|
»» type|default|
»» type|invoicing|
»» type|delivery|
»» type|visiting|
»» type|other|
»» type|mobile|
»» type|work|
»» type|home|
»» type|other|
»» platform|facebook|
»» platform|twitter|
»» platform|linkedin|
»» platform|other|

> Example responses

```json
{
  "owner_id": 14,
  "first_name": "Tiger",
  "middle_name": "In The",
  "last_name": "Woods",
  "prefix": "Mr.",
  "suffix": "PhD",
  "title": "CMO",
  "company": "Tiger Inc.",
  "industry": "Sports Industry",
  "status": "Open",
  "rating": "Hot",
  "source_id": 2,
  "description": "Expert in CRM integration.",
  "website": "http://www.tigerwoods.com",
  "email": "tiger@woods.com",
  "addresses": [
    {
      "type": "invoicing",
      "name": "HQ US",
      "line1": "Main street",
      "line2": "Main street",
      "city": "San Francisco",
      "state": "CA",
      "postal_code": "94104",
      "country": "US",
      "lattitude": "40.759211",
      "longitude": "-73.984638"
    }
  ],
  "phone_numbers": [
    {
      "number": "111-111-1111",
      "type": "mobile"
    }
  ],
  "social_links": [
    {
      "url": "https://www.twitter.com/apideck-io",
      "platform": "twitter"
    }
  ],
  "tags": [
    "Retail",
    "Sports"
  ],
  "custom_fields": {
    "known_via": "John"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[Lead](#schemalead)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:leads )
</aside>

## deleteLead

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.apideck.com/crm/leads/{id}

```

```http
DELETE https://api.apideck.com/crm/leads/{id} HTTP/1.1
Host: api.apideck.com


```

```javascript

$.ajax({
  url: 'https://api.apideck.com/crm/leads/{id}',
  method: 'delete',

  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

fetch('https://api.apideck.com/crm/leads/{id}',
{
  method: 'DELETE'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'


result = RestClient.delete 'https://api.apideck.com/crm/leads/{id}',
  params: {
  }

p JSON.parse(result)
```

```python
import requests

r = requests.delete('https://api.apideck.com/crm/leads/{id}', params={

)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/leads/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`DELETE /leads/{id}`

*Deletes a lead*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No description|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:leads )
</aside>

# Campaigns

Everything about your campaigns

## allCampaigns

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/campaigns \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/campaigns HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/campaigns',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/campaigns',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/campaigns',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/campaigns', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/campaigns");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /campaigns`

*Get all campaigns*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
page|query|integer|false|Page number to start from. Omitting the page parameter will return page 1
per_page|query|integer|false|Number of records to return per page. Default = 100.


> Example responses

```json
[
  {
    "id": "134",
    "name": "Black Friday Email - 2018",
    "description": "Black friday - email campaign. US-only.",
    "message": "Black Friday - 40% off everything!",
    "objective": "Maximize inbound leads for US customers.",
    "type": "E-mail",
    "status": "Active",
    "start": "2018-11-23T20:00:00.291Z",
    "end": "2018-11-30T00:00:00.291Z",
    "costs": [
      {
        "amount": "100000.00",
        "currency": "EUR",
        "type": "actual"
      }
    ],
    "revenue": [
      {
        "amount": "100000.00",
        "currency": "EUR",
        "type": "expected"
      }
    ],
    "parent_id": "4469",
    "currency": "USD",
    "is_active": true,
    "owner_id": "456",
    "creator_id": "456",
    "updated": "2017-08-12T20:43:21.291Z",
    "created": "2017-08-12T20:43:21.291Z"
  }
]
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|Inline

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[Campaign](#schemacampaign)]|false|No description
» id|string|false|No description
» name|string|false|No description
» description|string|false|No description
» message|string|false|No description
» objective|string|false|No description
» type|string|false|No description
» status|string|false|No description
» start|string|false|No description
» end|string|false|No description
» parent_id|string|false|No description
» currency|string|false|No description
» is_active|boolean|false|No description
» owner_id|string|false|No description
» creator_id|string|false|No description
» updated|string|false|No description
» created|string|false|No description
» costs|[[CampaignCost](#schemacampaigncost)]|false|No description
»» amount|string|false|No description
»» currency|string|false|No description
»» type|string|false|No description
» revenue|[[CampaignRevenue](#schemacampaignrevenue)]|false|No description
»» amount|string|false|No description
»» currency|string|false|No description
»» type|string|false|No description



<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:campaigns )
</aside>

## addCampaign

> Code samples

```shell
# You can also use wget
curl -X POST https://api.apideck.com/crm/campaigns \
  -H 'Content-Type: application/json'

```

```http
POST https://api.apideck.com/crm/campaigns HTTP/1.1
Host: api.apideck.com
Content-Type: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/campaigns',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "name": "Black Friday Email - 2018",
  "description": "Black friday - email campaign. US-only.",
  "message": "Black Friday - 40% off everything!",
  "objective": "Maximize inbound leads for US customers.",
  "type": "E-mail",
  "status": "Active",
  "start": "2018-11-23T20:00:00.291Z",
  "end": "2018-11-30T00:00:00.291Z",
  "costs": [
    {
      "amount": "100000.00",
      "currency": "EUR",
      "type": "actual"
    }
  ],
  "revenue": [
    {
      "amount": "100000.00",
      "currency": "EUR",
      "type": "expected"
    }
  ],
  "parent_id": "4469",
  "currency": "USD",
  "is_active": true
}';
const headers = {
  'Content-Type':'application/json'

};

fetch('https://api.apideck.com/crm/campaigns',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.post 'https://api.apideck.com/crm/campaigns',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.post('https://api.apideck.com/crm/campaigns', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/campaigns");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /campaigns`

*Add a new campaign*

> Body parameter

```json
{
  "name": "Black Friday Email - 2018",
  "description": "Black friday - email campaign. US-only.",
  "message": "Black Friday - 40% off everything!",
  "objective": "Maximize inbound leads for US customers.",
  "type": "E-mail",
  "status": "Active",
  "start": "2018-11-23T20:00:00.291Z",
  "end": "2018-11-30T00:00:00.291Z",
  "costs": [
    {
      "amount": "100000.00",
      "currency": "EUR",
      "type": "actual"
    }
  ],
  "revenue": [
    {
      "amount": "100000.00",
      "currency": "EUR",
      "type": "expected"
    }
  ],
  "parent_id": "4469",
  "currency": "USD",
  "is_active": true
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
body|body|[Campaign](#schemacampaign)|true|Campaign object that needs to be added
» id|body|string|false|No description
» name|body|string|false|No description
» description|body|string|false|No description
» message|body|string|false|No description
» objective|body|string|false|No description
» type|body|string|false|No description
» status|body|string|false|No description
» start|body|string|false|No description
» end|body|string|false|No description
» parent_id|body|string|false|No description
» currency|body|string|false|No description
» is_active|body|boolean|false|No description
» owner_id|body|string|false|No description
» creator_id|body|string|false|No description
» updated|body|string|false|No description
» created|body|string|false|No description
» costs|body|[[CampaignCost](#schemacampaigncost)]|false|No description
»» amount|body|string|false|No description
»» currency|body|string|false|No description
»» type|body|string|false|No description
» revenue|body|[[CampaignRevenue](#schemacampaignrevenue)]|false|No description
»» amount|body|string|false|No description
»» currency|body|string|false|No description
»» type|body|string|false|No description


#### Enumerated Values

|Parameter|Value|
|---|---|
»» type|actual|
»» type|budgeted|
»» type|other|
»» type|actual|
»» type|expected|
»» type|other|

### Responses

Status|Meaning|Description|Schema
---|---|---|---|
201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:campaigns )
</aside>

## getCampaign

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/campaigns/{id} \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/campaigns/{id} HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/campaigns/{id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/campaigns/{id}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/campaigns/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/campaigns/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/campaigns/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /campaigns/{id}`

*Find campaign by ID*

Returns a single campaign

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


> Example responses

```json
{
  "name": "Black Friday Email - 2018",
  "description": "Black friday - email campaign. US-only.",
  "message": "Black Friday - 40% off everything!",
  "objective": "Maximize inbound leads for US customers.",
  "type": "E-mail",
  "status": "Active",
  "start": "2018-11-23T20:00:00.291Z",
  "end": "2018-11-30T00:00:00.291Z",
  "costs": [
    {
      "amount": "100000.00",
      "currency": "EUR",
      "type": "actual"
    }
  ],
  "revenue": [
    {
      "amount": "100000.00",
      "currency": "EUR",
      "type": "expected"
    }
  ],
  "parent_id": "4469",
  "currency": "USD",
  "is_active": true
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[Campaign](#schemacampaign)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:campaigns )
</aside>

## updateCampaign

> Code samples

```shell
# You can also use wget
curl -X PATCH https://api.apideck.com/crm/campaigns/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PATCH https://api.apideck.com/crm/campaigns/{id} HTTP/1.1
Host: api.apideck.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/campaigns/{id}',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "name": "Black Friday Email - 2018",
  "description": "Black friday - email campaign. US-only.",
  "message": "Black Friday - 40% off everything!",
  "objective": "Maximize inbound leads for US customers.",
  "type": "E-mail",
  "status": "Active",
  "start": "2018-11-23T20:00:00.291Z",
  "end": "2018-11-30T00:00:00.291Z",
  "costs": [
    {
      "amount": "100000.00",
      "currency": "EUR",
      "type": "actual"
    }
  ],
  "revenue": [
    {
      "amount": "100000.00",
      "currency": "EUR",
      "type": "expected"
    }
  ],
  "parent_id": "4469",
  "currency": "USD",
  "is_active": true
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/campaigns/{id}',
{
  method: 'PATCH',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.patch 'https://api.apideck.com/crm/campaigns/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.patch('https://api.apideck.com/crm/campaigns/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/campaigns/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`PATCH /campaigns/{id}`

*Update an existing campaign*

> Body parameter

```json
{
  "name": "Black Friday Email - 2018",
  "description": "Black friday - email campaign. US-only.",
  "message": "Black Friday - 40% off everything!",
  "objective": "Maximize inbound leads for US customers.",
  "type": "E-mail",
  "status": "Active",
  "start": "2018-11-23T20:00:00.291Z",
  "end": "2018-11-30T00:00:00.291Z",
  "costs": [
    {
      "amount": "100000.00",
      "currency": "EUR",
      "type": "actual"
    }
  ],
  "revenue": [
    {
      "amount": "100000.00",
      "currency": "EUR",
      "type": "expected"
    }
  ],
  "parent_id": "4469",
  "currency": "USD",
  "is_active": true
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return
body|body|[Campaign](#schemacampaign)|true|Fields that need to be updated on the resource
» id|body|string|false|No description
» name|body|string|false|No description
» description|body|string|false|No description
» message|body|string|false|No description
» objective|body|string|false|No description
» type|body|string|false|No description
» status|body|string|false|No description
» start|body|string|false|No description
» end|body|string|false|No description
» parent_id|body|string|false|No description
» currency|body|string|false|No description
» is_active|body|boolean|false|No description
» owner_id|body|string|false|No description
» creator_id|body|string|false|No description
» updated|body|string|false|No description
» created|body|string|false|No description
» costs|body|[[CampaignCost](#schemacampaigncost)]|false|No description
»» amount|body|string|false|No description
»» currency|body|string|false|No description
»» type|body|string|false|No description
» revenue|body|[[CampaignRevenue](#schemacampaignrevenue)]|false|No description
»» amount|body|string|false|No description
»» currency|body|string|false|No description
»» type|body|string|false|No description


#### Enumerated Values

|Parameter|Value|
|---|---|
»» type|actual|
»» type|budgeted|
»» type|other|
»» type|actual|
»» type|expected|
»» type|other|

> Example responses

```json
{
  "name": "Black Friday Email - 2018",
  "description": "Black friday - email campaign. US-only.",
  "message": "Black Friday - 40% off everything!",
  "objective": "Maximize inbound leads for US customers.",
  "type": "E-mail",
  "status": "Active",
  "start": "2018-11-23T20:00:00.291Z",
  "end": "2018-11-30T00:00:00.291Z",
  "costs": [
    {
      "amount": "100000.00",
      "currency": "EUR",
      "type": "actual"
    }
  ],
  "revenue": [
    {
      "amount": "100000.00",
      "currency": "EUR",
      "type": "expected"
    }
  ],
  "parent_id": "4469",
  "currency": "USD",
  "is_active": true
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[Campaign](#schemacampaign)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:campaigns )
</aside>

## deleteCampaign

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.apideck.com/crm/campaigns/{id}

```

```http
DELETE https://api.apideck.com/crm/campaigns/{id} HTTP/1.1
Host: api.apideck.com


```

```javascript

$.ajax({
  url: 'https://api.apideck.com/crm/campaigns/{id}',
  method: 'delete',

  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

fetch('https://api.apideck.com/crm/campaigns/{id}',
{
  method: 'DELETE'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'


result = RestClient.delete 'https://api.apideck.com/crm/campaigns/{id}',
  params: {
  }

p JSON.parse(result)
```

```python
import requests

r = requests.delete('https://api.apideck.com/crm/campaigns/{id}', params={

)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/campaigns/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`DELETE /campaigns/{id}`

*Deletes a campaign*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No description|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:campaigns )
</aside>

# Tasks

Everything about your tasks

## allTasks

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/tasks \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/tasks HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/tasks',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/tasks',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/tasks',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/tasks', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/tasks");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /tasks`

*Get all tasks*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
page|query|integer|false|Page number to start from. Omitting the page parameter will return page 1
per_page|query|integer|false|Number of records to return per page. Default = 100.


> Example responses

```json
[
  {
    "id": 45,
    "creator_id": 456,
    "owner_id": 349,
    "title": "Contact Marc Benioff",
    "description": "Do a background check before call",
    "due_date": "2020-10-28T15:23:50Z",
    "overdue": false,
    "completed_at": "2019-10-28T15:23:50Z",
    "completed": false,
    "remind_at": "2018-10-28T15:23:50Z",
    "priority": "High",
    "status": "Open",
    "tags": [
      "CRM",
      "Influencer"
    ],
    "custom_fields": {
      "research": "High energy person. Founding CEO Salesforce."
    },
    "linked_resources": [
      {
        "id": 2,
        "type": "Opportunity"
      }
    ],
    "updated_at": "2017-08-12T20:43:21.291Z",
    "created_at": "2017-08-12T20:43:21.291Z"
  }
]
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|Inline

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[Task](#schematask)]|false|No description
» id|integer|false|No description
» creator_id|integer|false|No description
» owner_id|integer|false|No description
» title|string|false|No description
» description|string|false|No description
» due_date|string|false|No description
» overdue|boolean|false|No description
» completed_at|string|false|No description
» completed|boolean|false|No description
» remind_at|string|false|No description
» priority|string|false|No description
» status|string|false|No description
» custom_fields|object|false|No description
» updated_at|string|false|No description
» created_at|string|false|No description
» linked_resources|[[LinkedResource](#schemalinkedresource)]|false|No description
»» id|integer|false|No description
»» type|string|false|No description



<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:tasks )
</aside>

## addTask

> Code samples

```shell
# You can also use wget
curl -X POST https://api.apideck.com/crm/tasks \
  -H 'Content-Type: application/json'

```

```http
POST https://api.apideck.com/crm/tasks HTTP/1.1
Host: api.apideck.com
Content-Type: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/tasks',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "owner_id": 349,
  "title": "Contact Marc Benioff",
  "description": "Do a background check before call",
  "due_date": "2020-10-28T15:23:50Z",
  "overdue": false,
  "completed_at": "2019-10-28T15:23:50Z",
  "completed": false,
  "remind_at": "2018-10-28T15:23:50Z",
  "priority": "High",
  "status": "Open",
  "tags": [
    "CRM",
    "Influencer"
  ],
  "custom_fields": {
    "research": "High energy person. Founding CEO Salesforce."
  },
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json'

};

fetch('https://api.apideck.com/crm/tasks',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.post 'https://api.apideck.com/crm/tasks',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.post('https://api.apideck.com/crm/tasks', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/tasks");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /tasks`

*Add a new task*

> Body parameter

```json
{
  "owner_id": 349,
  "title": "Contact Marc Benioff",
  "description": "Do a background check before call",
  "due_date": "2020-10-28T15:23:50Z",
  "overdue": false,
  "completed_at": "2019-10-28T15:23:50Z",
  "completed": false,
  "remind_at": "2018-10-28T15:23:50Z",
  "priority": "High",
  "status": "Open",
  "tags": [
    "CRM",
    "Influencer"
  ],
  "custom_fields": {
    "research": "High energy person. Founding CEO Salesforce."
  },
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
body|body|[Task](#schematask)|true|Task object that needs to be added
» id|body|integer|false|No description
» creator_id|body|integer|false|No description
» owner_id|body|integer|false|No description
» title|body|string|false|No description
» description|body|string|false|No description
» due_date|body|string|false|No description
» overdue|body|boolean|false|No description
» completed_at|body|string|false|No description
» completed|body|boolean|false|No description
» remind_at|body|string|false|No description
» priority|body|string|false|No description
» status|body|string|false|No description
» custom_fields|body|object|false|No description
» updated_at|body|string|false|No description
» created_at|body|string|false|No description
» linked_resources|body|[[LinkedResource](#schemalinkedresource)]|false|No description
»» id|body|integer|false|No description
»» type|body|string|false|No description


#### Enumerated Values

|Parameter|Value|
|---|---|
»» type|Lead/Opportunity/Person/Company|

### Responses

Status|Meaning|Description|Schema
---|---|---|---|
201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:tasks )
</aside>

## getTask

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/tasks/{id} \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/tasks/{id} HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/tasks/{id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/tasks/{id}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/tasks/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/tasks/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/tasks/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /tasks/{id}`

*Find task by ID*

Returns a single task

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


> Example responses

```json
{
  "owner_id": 349,
  "title": "Contact Marc Benioff",
  "description": "Do a background check before call",
  "due_date": "2020-10-28T15:23:50Z",
  "overdue": false,
  "completed_at": "2019-10-28T15:23:50Z",
  "completed": false,
  "remind_at": "2018-10-28T15:23:50Z",
  "priority": "High",
  "status": "Open",
  "tags": [
    "CRM",
    "Influencer"
  ],
  "custom_fields": {
    "research": "High energy person. Founding CEO Salesforce."
  },
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[Task](#schematask)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:tasks )
</aside>

## updateTask

> Code samples

```shell
# You can also use wget
curl -X PATCH https://api.apideck.com/crm/tasks/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PATCH https://api.apideck.com/crm/tasks/{id} HTTP/1.1
Host: api.apideck.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/tasks/{id}',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "owner_id": 349,
  "title": "Contact Marc Benioff",
  "description": "Do a background check before call",
  "due_date": "2020-10-28T15:23:50Z",
  "overdue": false,
  "completed_at": "2019-10-28T15:23:50Z",
  "completed": false,
  "remind_at": "2018-10-28T15:23:50Z",
  "priority": "High",
  "status": "Open",
  "tags": [
    "CRM",
    "Influencer"
  ],
  "custom_fields": {
    "research": "High energy person. Founding CEO Salesforce."
  },
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/tasks/{id}',
{
  method: 'PATCH',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.patch 'https://api.apideck.com/crm/tasks/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.patch('https://api.apideck.com/crm/tasks/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/tasks/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`PATCH /tasks/{id}`

*Update an existing task*

> Body parameter

```json
{
  "owner_id": 349,
  "title": "Contact Marc Benioff",
  "description": "Do a background check before call",
  "due_date": "2020-10-28T15:23:50Z",
  "overdue": false,
  "completed_at": "2019-10-28T15:23:50Z",
  "completed": false,
  "remind_at": "2018-10-28T15:23:50Z",
  "priority": "High",
  "status": "Open",
  "tags": [
    "CRM",
    "Influencer"
  ],
  "custom_fields": {
    "research": "High energy person. Founding CEO Salesforce."
  },
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return
body|body|[Task](#schematask)|true|Fields that need to be updated on the resource
» id|body|integer|false|No description
» creator_id|body|integer|false|No description
» owner_id|body|integer|false|No description
» title|body|string|false|No description
» description|body|string|false|No description
» due_date|body|string|false|No description
» overdue|body|boolean|false|No description
» completed_at|body|string|false|No description
» completed|body|boolean|false|No description
» remind_at|body|string|false|No description
» priority|body|string|false|No description
» status|body|string|false|No description
» custom_fields|body|object|false|No description
» updated_at|body|string|false|No description
» created_at|body|string|false|No description
» linked_resources|body|[[LinkedResource](#schemalinkedresource)]|false|No description
»» id|body|integer|false|No description
»» type|body|string|false|No description


#### Enumerated Values

|Parameter|Value|
|---|---|
»» type|Lead/Opportunity/Person/Company|

> Example responses

```json
{
  "owner_id": 349,
  "title": "Contact Marc Benioff",
  "description": "Do a background check before call",
  "due_date": "2020-10-28T15:23:50Z",
  "overdue": false,
  "completed_at": "2019-10-28T15:23:50Z",
  "completed": false,
  "remind_at": "2018-10-28T15:23:50Z",
  "priority": "High",
  "status": "Open",
  "tags": [
    "CRM",
    "Influencer"
  ],
  "custom_fields": {
    "research": "High energy person. Founding CEO Salesforce."
  },
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[Task](#schematask)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:tasks )
</aside>

## deleteTask

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.apideck.com/crm/tasks/{id}

```

```http
DELETE https://api.apideck.com/crm/tasks/{id} HTTP/1.1
Host: api.apideck.com


```

```javascript

$.ajax({
  url: 'https://api.apideck.com/crm/tasks/{id}',
  method: 'delete',

  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

fetch('https://api.apideck.com/crm/tasks/{id}',
{
  method: 'DELETE'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'


result = RestClient.delete 'https://api.apideck.com/crm/tasks/{id}',
  params: {
  }

p JSON.parse(result)
```

```python
import requests

r = requests.delete('https://api.apideck.com/crm/tasks/{id}', params={

)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/tasks/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`DELETE /tasks/{id}`

*Deletes a task*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No description|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:tasks )
</aside>

# Products

Everything about your products

## allProducts

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/products \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/products HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/products',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/products',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/products',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/products', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/products");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /products`

*Get all products*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
page|query|integer|false|Page number to start from. Omitting the page parameter will return page 1
per_page|query|integer|false|Number of records to return per page. Default = 100.


> Example responses

```json
[
  {
    "id": 2,
    "name": "1-year Pro subscription",
    "description": "Includes pro subscription with free trial.",
    "is_active": true,
    "external_id": "145E",
    "code": "1-year-pro",
    "sku": "PRO1-EDFG",
    "cost": "40.00",
    "cost_currency": "EUR",
    "stock_amount": 340,
    "prices": [
      {
        "amount": 100,
        "currency": "EUR",
        "tax_percentage": 5
      }
    ],
    "updated_at": "2017-08-12T20:43:21.291Z",
    "created_at": "2017-08-12T20:43:21.291Z"
  }
]
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|Inline

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[Product](#schemaproduct)]|false|No description
» id|integer|false|No description
» name|string|false|No description
» description|string|false|No description
» is_active|boolean|false|No description
» external_id|string|false|No description
» code|string|false|No description
» sku|string|false|No description
» cost|integer|false|No description
» cost_currency|string|false|No description
» stock_amount|integer|false|No description
» updated_at|string|false|No description
» created_at|string|false|No description
» prices|[[ProductPrice](#schemaproductprice)]|false|No description
»» amount|integer|false|No description
»» currency|string|false|No description
»» tax_percentage|number|false|No description



<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:products )
</aside>

## addProduct

> Code samples

```shell
# You can also use wget
curl -X POST https://api.apideck.com/crm/products \
  -H 'Content-Type: application/json'

```

```http
POST https://api.apideck.com/crm/products HTTP/1.1
Host: api.apideck.com
Content-Type: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/products',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "name": "1-year Pro subscription",
  "description": "Includes pro subscription with free trial.",
  "is_active": true,
  "external_id": "145E",
  "code": "1-year-pro",
  "sku": "PRO1-EDFG",
  "cost": "40.00",
  "cost_currency": "EUR",
  "stock_amount": 340,
  "prices": [
    {
      "amount": 100,
      "currency": "EUR",
      "tax_percentage": 5
    }
  ]
}';
const headers = {
  'Content-Type':'application/json'

};

fetch('https://api.apideck.com/crm/products',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.post 'https://api.apideck.com/crm/products',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.post('https://api.apideck.com/crm/products', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/products");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /products`

*Add a new product*

> Body parameter

```json
{
  "name": "1-year Pro subscription",
  "description": "Includes pro subscription with free trial.",
  "is_active": true,
  "external_id": "145E",
  "code": "1-year-pro",
  "sku": "PRO1-EDFG",
  "cost": "40.00",
  "cost_currency": "EUR",
  "stock_amount": 340,
  "prices": [
    {
      "amount": 100,
      "currency": "EUR",
      "tax_percentage": 5
    }
  ]
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
body|body|[Product](#schemaproduct)|true|Product object that needs to be added
» id|body|integer|false|No description
» name|body|string|false|No description
» description|body|string|false|No description
» is_active|body|boolean|false|No description
» external_id|body|string|false|No description
» code|body|string|false|No description
» sku|body|string|false|No description
» cost|body|integer|false|No description
» cost_currency|body|string|false|No description
» stock_amount|body|integer|false|No description
» updated_at|body|string|false|No description
» created_at|body|string|false|No description
» prices|body|[[ProductPrice](#schemaproductprice)]|false|No description
»» amount|body|integer|false|No description
»» currency|body|string|false|No description
»» tax_percentage|body|number|false|No description


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:products )
</aside>

## getProduct

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/products/{id} \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/products/{id} HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/products/{id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/products/{id}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/products/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/products/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/products/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /products/{id}`

*Find product by ID*

Returns a single product

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


> Example responses

```json
{
  "name": "1-year Pro subscription",
  "description": "Includes pro subscription with free trial.",
  "is_active": true,
  "external_id": "145E",
  "code": "1-year-pro",
  "sku": "PRO1-EDFG",
  "cost": "40.00",
  "cost_currency": "EUR",
  "stock_amount": 340,
  "prices": [
    {
      "amount": 100,
      "currency": "EUR",
      "tax_percentage": 5
    }
  ]
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[Product](#schemaproduct)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:products )
</aside>

## updateProduct

> Code samples

```shell
# You can also use wget
curl -X PATCH https://api.apideck.com/crm/products/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PATCH https://api.apideck.com/crm/products/{id} HTTP/1.1
Host: api.apideck.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/products/{id}',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "name": "1-year Pro subscription",
  "description": "Includes pro subscription with free trial.",
  "is_active": true,
  "external_id": "145E",
  "code": "1-year-pro",
  "sku": "PRO1-EDFG",
  "cost": "40.00",
  "cost_currency": "EUR",
  "stock_amount": 340,
  "prices": [
    {
      "amount": 100,
      "currency": "EUR",
      "tax_percentage": 5
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/products/{id}',
{
  method: 'PATCH',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.patch 'https://api.apideck.com/crm/products/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.patch('https://api.apideck.com/crm/products/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/products/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`PATCH /products/{id}`

*Update an existing product*

> Body parameter

```json
{
  "name": "1-year Pro subscription",
  "description": "Includes pro subscription with free trial.",
  "is_active": true,
  "external_id": "145E",
  "code": "1-year-pro",
  "sku": "PRO1-EDFG",
  "cost": "40.00",
  "cost_currency": "EUR",
  "stock_amount": 340,
  "prices": [
    {
      "amount": 100,
      "currency": "EUR",
      "tax_percentage": 5
    }
  ]
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return
body|body|[Product](#schemaproduct)|true|Fields that need to be updated on the resource
» id|body|integer|false|No description
» name|body|string|false|No description
» description|body|string|false|No description
» is_active|body|boolean|false|No description
» external_id|body|string|false|No description
» code|body|string|false|No description
» sku|body|string|false|No description
» cost|body|integer|false|No description
» cost_currency|body|string|false|No description
» stock_amount|body|integer|false|No description
» updated_at|body|string|false|No description
» created_at|body|string|false|No description
» prices|body|[[ProductPrice](#schemaproductprice)]|false|No description
»» amount|body|integer|false|No description
»» currency|body|string|false|No description
»» tax_percentage|body|number|false|No description


> Example responses

```json
{
  "name": "1-year Pro subscription",
  "description": "Includes pro subscription with free trial.",
  "is_active": true,
  "external_id": "145E",
  "code": "1-year-pro",
  "sku": "PRO1-EDFG",
  "cost": "40.00",
  "cost_currency": "EUR",
  "stock_amount": 340,
  "prices": [
    {
      "amount": 100,
      "currency": "EUR",
      "tax_percentage": 5
    }
  ]
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[Product](#schemaproduct)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:products )
</aside>

## deleteProduct

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.apideck.com/crm/products/{id}

```

```http
DELETE https://api.apideck.com/crm/products/{id} HTTP/1.1
Host: api.apideck.com


```

```javascript

$.ajax({
  url: 'https://api.apideck.com/crm/products/{id}',
  method: 'delete',

  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

fetch('https://api.apideck.com/crm/products/{id}',
{
  method: 'DELETE'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'


result = RestClient.delete 'https://api.apideck.com/crm/products/{id}',
  params: {
  }

p JSON.parse(result)
```

```python
import requests

r = requests.delete('https://api.apideck.com/crm/products/{id}', params={

)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/products/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`DELETE /products/{id}`

*Deletes a product*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No description|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:products )
</aside>

# Notes

Everything about your notes

## allNotes

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/notes \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/notes HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/notes',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/notes',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/notes',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/notes', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/notes");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /notes`

*Get all notes*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
page|query|integer|false|Page number to start from. Omitting the page parameter will return page 1
per_page|query|integer|false|Number of records to return per page. Default = 100.


> Example responses

```json
[
  {
    "id": 134,
    "title": "Note to myself",
    "description": "New entrant in market. Look into to this company + references.",
    "linked_resources": [
      {
        "id": 2,
        "type": "Opportunity"
      }
    ],
    "creator_id": "456",
    "updated": "2017-08-12T20:43:21.291Z",
    "created": "2017-08-12T20:43:21.291Z"
  }
]
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|Inline

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[Note](#schemanote)]|false|No description
» id|integer|false|No description
» title|string|false|No description
» description|string|false|No description
» creator_id|string|false|No description
» updated|string|false|No description
» created|string|false|No description
» linked_resources|[[LinkedResource](#schemalinkedresource)]|false|No description
»» id|integer|false|No description
»» type|string|false|No description



<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:notes )
</aside>

## addNote

> Code samples

```shell
# You can also use wget
curl -X POST https://api.apideck.com/crm/notes \
  -H 'Content-Type: application/json'

```

```http
POST https://api.apideck.com/crm/notes HTTP/1.1
Host: api.apideck.com
Content-Type: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/notes',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "title": "Note to myself",
  "description": "New entrant in market. Look into to this company + references.",
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json'

};

fetch('https://api.apideck.com/crm/notes',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.post 'https://api.apideck.com/crm/notes',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.post('https://api.apideck.com/crm/notes', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/notes");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /notes`

*Add a new note*

> Body parameter

```json
{
  "title": "Note to myself",
  "description": "New entrant in market. Look into to this company + references.",
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
body|body|[Note](#schemanote)|true|Note object that needs to be added
» id|body|integer|false|No description
» title|body|string|false|No description
» description|body|string|false|No description
» creator_id|body|string|false|No description
» updated|body|string|false|No description
» created|body|string|false|No description
» linked_resources|body|[[LinkedResource](#schemalinkedresource)]|false|No description
»» id|body|integer|false|No description
»» type|body|string|false|No description


#### Enumerated Values

|Parameter|Value|
|---|---|
»» type|Lead/Opportunity/Person/Company|

### Responses

Status|Meaning|Description|Schema
---|---|---|---|
201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:notes )
</aside>

## getNote

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/notes/{id} \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/notes/{id} HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/notes/{id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/notes/{id}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/notes/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/notes/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/notes/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /notes/{id}`

*Find note by ID*

Returns a single note

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


> Example responses

```json
{
  "title": "Note to myself",
  "description": "New entrant in market. Look into to this company + references.",
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[Note](#schemanote)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:notes )
</aside>

## updateNote

> Code samples

```shell
# You can also use wget
curl -X PATCH https://api.apideck.com/crm/notes/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PATCH https://api.apideck.com/crm/notes/{id} HTTP/1.1
Host: api.apideck.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/notes/{id}',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "title": "Note to myself",
  "description": "New entrant in market. Look into to this company + references.",
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/notes/{id}',
{
  method: 'PATCH',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.patch 'https://api.apideck.com/crm/notes/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.patch('https://api.apideck.com/crm/notes/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/notes/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`PATCH /notes/{id}`

*Update an existing note*

> Body parameter

```json
{
  "title": "Note to myself",
  "description": "New entrant in market. Look into to this company + references.",
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return
body|body|[Note](#schemanote)|true|Fields that need to be updated on the resource
» id|body|integer|false|No description
» title|body|string|false|No description
» description|body|string|false|No description
» creator_id|body|string|false|No description
» updated|body|string|false|No description
» created|body|string|false|No description
» linked_resources|body|[[LinkedResource](#schemalinkedresource)]|false|No description
»» id|body|integer|false|No description
»» type|body|string|false|No description


#### Enumerated Values

|Parameter|Value|
|---|---|
»» type|Lead/Opportunity/Person/Company|

> Example responses

```json
{
  "title": "Note to myself",
  "description": "New entrant in market. Look into to this company + references.",
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[Note](#schemanote)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:notes )
</aside>

## deleteNote

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.apideck.com/crm/notes/{id}

```

```http
DELETE https://api.apideck.com/crm/notes/{id} HTTP/1.1
Host: api.apideck.com


```

```javascript

$.ajax({
  url: 'https://api.apideck.com/crm/notes/{id}',
  method: 'delete',

  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

fetch('https://api.apideck.com/crm/notes/{id}',
{
  method: 'DELETE'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'


result = RestClient.delete 'https://api.apideck.com/crm/notes/{id}',
  params: {
  }

p JSON.parse(result)
```

```python
import requests

r = requests.delete('https://api.apideck.com/crm/notes/{id}', params={

)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/notes/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`DELETE /notes/{id}`

*Deletes a note*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No description|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:notes )
</aside>

# Emails

Everything about your emails

## allEmails

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/emails \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/emails HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/emails',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/emails',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/emails',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/emails', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/emails");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /emails`

*Get all emails*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
page|query|integer|false|Page number to start from. Omitting the page parameter will return page 1
per_page|query|integer|false|Number of records to return per page. Default = 100.


> Example responses

```json
[
  {
    "id": "2",
    "date": "2017-08-14T20:00:00.291Z",
    "subject": "Proposal",
    "body_text": "Dear customer, Please find the proposal in the attachment.",
    "headers": "string",
    "status": "inbox",
    "direction": "incoming",
    "message_id": "45489DFKDF",
    "email_message_id": "<98989854.549549@ec4.us-west-2.compute.amazonaws.com>",
    "thread_id": "4309",
    "gmail_message_id": "<98989854.549549@gmail.com>",
    "gmail_thread_id": "434343EB",
    "is_read": true,
    "send_attempts": 1,
    "open_count": 10,
    "reply_count": 2,
    "has_attachments": true,
    "addresses": {
      "from": {
        "name": "Elon Musk",
        "email": "elon@spacex.com",
        "contact_id": "4559",
        "user_id": ""
      },
      "to": [
        {
          "name": "Elon Musk",
          "email": "elon@spacex.com",
          "contact_id": "4559",
          "user_id": ""
        }
      ],
      "cc": [
        {
          "name": "Elon Musk",
          "email": "elon@spacex.com",
          "contact_id": "4559",
          "user_id": ""
        }
      ],
      "bcc": [
        {
          "name": "Elon Musk",
          "email": "elon@spacex.com",
          "contact_id": "4559",
          "user_id": ""
        }
      ]
    },
    "body": [
      {
        "type": "text/plain",
        "charset": "utf-8",
        "body": "Dear customer, Please find the proposal in the attachment. Best."
      },
      {
        "type": "text/html",
        "charset": "utf-8",
        "body": "<div class=\"pipe-mailbody-fdk985459kjddjk5498\"><div>Body&nbsp; <div><br /></div> <div>Line item</div> <div><br /></div> <div>Bye</div> </div></div>"
      }
    ],
    "attachments": [
      {
        "id": "2256",
        "name": "Proposal.pdf",
        "url": "https://api.apideck.com/crm/files/2256/download"
      }
    ],
    "linked_resources": [
      {
        "id": 2,
        "type": "Opportunity"
      }
    ],
    "owner_id": "456",
    "creator_id": "456",
    "updated": "2017-08-12T20:43:21.291Z",
    "created": "2017-08-12T20:43:21.291Z"
  }
]
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|Inline

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[Email](#schemaemail)]|false|No description
» id|string|false|No description
» date|string|false|No description
» subject|string|false|No description
» body_text|string|false|No description
» headers|string|false|No description
» status|string|false|No description
» direction|string|false|No description
» message_id|string|false|No description
» email_message_id|string|false|No description
» thread_id|string|false|No description
» gmail_message_id|string|false|No description
» gmail_thread_id|string|false|No description
» is_read|boolean|false|No description
» send_attempts|integer|false|No description
» open_count|integer|false|No description
» reply_count|integer|false|No description
» has_attachments|boolean|false|No description
» addresses|object|false|No description
»» from|[EmailAddress](#schemaemailaddress)|false|No description
»»» name|string|false|No description
»»» email|string|false|No description
»»» contact_id|string|false|No description
»»» user_id|string|false|No description
»» to|[[EmailAddress](#schemaemailaddress)]|false|No description
»»» name|string|false|No description
»»» email|string|false|No description
»»» contact_id|string|false|No description
»»» user_id|string|false|No description
»» cc|[[EmailAddress](#schemaemailaddress)]|false|No description
»»» name|string|false|No description
»»» email|string|false|No description
»»» contact_id|string|false|No description
»»» user_id|string|false|No description
»» bcc|[[EmailAddress](#schemaemailaddress)]|false|No description
»»» name|string|false|No description
»»» email|string|false|No description
»»» contact_id|string|false|No description
»»» user_id|string|false|No description
» owner_id|string|false|No description
» creator_id|string|false|No description
» updated|string|false|No description
» created|string|false|No description
» body|[[EmailBody](#schemaemailbody)]|false|No description
»» type|string|false|No description
»» charset|string|false|No description
»» content|string|false|No description
» attachments|[[EmailAttachment](#schemaemailattachment)]|false|No description
»» id|string|false|No description
»» name|string|false|No description
»» url|string|false|No description
» linked_resources|[[LinkedResource](#schemalinkedresource)]|false|No description
»» id|integer|false|No description
»» type|string|false|No description



<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:emails )
</aside>

## addEmail

> Code samples

```shell
# You can also use wget
curl -X POST https://api.apideck.com/crm/emails \
  -H 'Content-Type: application/json'

```

```http
POST https://api.apideck.com/crm/emails HTTP/1.1
Host: api.apideck.com
Content-Type: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/emails',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "date": "2017-08-14T20:00:00.291Z",
  "subject": "Proposal",
  "body_text": "Dear customer, Please find the proposal in the attachment.",
  "headers": "string",
  "status": "inbox",
  "direction": "incoming",
  "message_id": "45489DFKDF",
  "email_message_id": "<98989854.549549@ec4.us-west-2.compute.amazonaws.com>",
  "thread_id": "4309",
  "gmail_message_id": "<98989854.549549@gmail.com>",
  "gmail_thread_id": "434343EB",
  "is_read": true,
  "send_attempts": 1,
  "open_count": 10,
  "reply_count": 2,
  "has_attachments": true,
  "addresses": {
    "from": {
      "name": "Elon Musk",
      "email": "elon@spacex.com",
      "contact_id": "4559",
      "user_id": ""
    },
    "to": [
      {
        "name": "Elon Musk",
        "email": "elon@spacex.com",
        "contact_id": "4559",
        "user_id": ""
      }
    ],
    "cc": [
      {
        "name": "Elon Musk",
        "email": "elon@spacex.com",
        "contact_id": "4559",
        "user_id": ""
      }
    ],
    "bcc": [
      {
        "name": "Elon Musk",
        "email": "elon@spacex.com",
        "contact_id": "4559",
        "user_id": ""
      }
    ]
  },
  "body": [
    {
      "type": "text/plain",
      "charset": "utf-8",
      "body": "Dear customer, Please find the proposal in the attachment. Best."
    },
    {
      "type": "text/html",
      "charset": "utf-8",
      "body": "<div class=\"pipe-mailbody-fdk985459kjddjk5498\"><div>Body&nbsp; <div><br /></div> <div>Line item</div> <div><br /></div> <div>Bye</div> </div></div>"
    }
  ],
  "attachments": [
    {
      "id": "2256",
      "name": "Proposal.pdf",
      "url": "https://api.apideck.com/crm/files/2256/download"
    }
  ],
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json'

};

fetch('https://api.apideck.com/crm/emails',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.post 'https://api.apideck.com/crm/emails',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.post('https://api.apideck.com/crm/emails', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/emails");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /emails`

*Add a new email*

> Body parameter

```json
{
  "date": "2017-08-14T20:00:00.291Z",
  "subject": "Proposal",
  "body_text": "Dear customer, Please find the proposal in the attachment.",
  "headers": "string",
  "status": "inbox",
  "direction": "incoming",
  "message_id": "45489DFKDF",
  "email_message_id": "<98989854.549549@ec4.us-west-2.compute.amazonaws.com>",
  "thread_id": "4309",
  "gmail_message_id": "<98989854.549549@gmail.com>",
  "gmail_thread_id": "434343EB",
  "is_read": true,
  "send_attempts": 1,
  "open_count": 10,
  "reply_count": 2,
  "has_attachments": true,
  "addresses": {
    "from": {
      "name": "Elon Musk",
      "email": "elon@spacex.com",
      "contact_id": "4559",
      "user_id": ""
    },
    "to": [
      {
        "name": "Elon Musk",
        "email": "elon@spacex.com",
        "contact_id": "4559",
        "user_id": ""
      }
    ],
    "cc": [
      {
        "name": "Elon Musk",
        "email": "elon@spacex.com",
        "contact_id": "4559",
        "user_id": ""
      }
    ],
    "bcc": [
      {
        "name": "Elon Musk",
        "email": "elon@spacex.com",
        "contact_id": "4559",
        "user_id": ""
      }
    ]
  },
  "body": [
    {
      "type": "text/plain",
      "charset": "utf-8",
      "body": "Dear customer, Please find the proposal in the attachment. Best."
    },
    {
      "type": "text/html",
      "charset": "utf-8",
      "body": "<div class=\"pipe-mailbody-fdk985459kjddjk5498\"><div>Body&nbsp; <div><br /></div> <div>Line item</div> <div><br /></div> <div>Bye</div> </div></div>"
    }
  ],
  "attachments": [
    {
      "id": "2256",
      "name": "Proposal.pdf",
      "url": "https://api.apideck.com/crm/files/2256/download"
    }
  ],
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
body|body|[Email](#schemaemail)|true|Email object that needs to be added
» id|body|string|false|No description
» date|body|string|false|No description
» subject|body|string|false|No description
» body_text|body|string|false|No description
» headers|body|string|false|No description
» status|body|string|false|No description
» direction|body|string|false|No description
» message_id|body|string|false|No description
» email_message_id|body|string|false|No description
» thread_id|body|string|false|No description
» gmail_message_id|body|string|false|No description
» gmail_thread_id|body|string|false|No description
» is_read|body|boolean|false|No description
» send_attempts|body|integer|false|No description
» open_count|body|integer|false|No description
» reply_count|body|integer|false|No description
» has_attachments|body|boolean|false|No description
» addresses|body|object|false|No description
»» from|body|[EmailAddress](#schemaemailaddress)|false|No description
»»» name|body|string|false|No description
»»» email|body|string|false|No description
»»» contact_id|body|string|false|No description
»»» user_id|body|string|false|No description
»» to|body|[[EmailAddress](#schemaemailaddress)]|false|No description
»»» name|body|string|false|No description
»»» email|body|string|false|No description
»»» contact_id|body|string|false|No description
»»» user_id|body|string|false|No description
»» cc|body|[[EmailAddress](#schemaemailaddress)]|false|No description
»»» name|body|string|false|No description
»»» email|body|string|false|No description
»»» contact_id|body|string|false|No description
»»» user_id|body|string|false|No description
»» bcc|body|[[EmailAddress](#schemaemailaddress)]|false|No description
»»» name|body|string|false|No description
»»» email|body|string|false|No description
»»» contact_id|body|string|false|No description
»»» user_id|body|string|false|No description
» owner_id|body|string|false|No description
» creator_id|body|string|false|No description
» updated|body|string|false|No description
» created|body|string|false|No description
» body|body|[[EmailBody](#schemaemailbody)]|false|No description
»» type|body|string|false|No description
»» charset|body|string|false|No description
»» content|body|string|false|No description
» attachments|body|[[EmailAttachment](#schemaemailattachment)]|false|No description
»» id|body|string|false|No description
»» name|body|string|false|No description
»» url|body|string|false|No description
» linked_resources|body|[[LinkedResource](#schemalinkedresource)]|false|No description
»» id|body|integer|false|No description
»» type|body|string|false|No description


#### Enumerated Values

|Parameter|Value|
|---|---|
» status|inbox|
» status|draft|
» status|scheduled|
» status|outbox|
» status|sent|
» direction|incoming|
» direction|outgoing|
»» type|Lead/Opportunity/Person/Company|

### Responses

Status|Meaning|Description|Schema
---|---|---|---|
201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:emails )
</aside>

## getEmail

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/emails/{id} \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/emails/{id} HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/emails/{id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/emails/{id}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/emails/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/emails/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/emails/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /emails/{id}`

*Find email by ID*

Returns a single email

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


> Example responses

```json
{
  "date": "2017-08-14T20:00:00.291Z",
  "subject": "Proposal",
  "body_text": "Dear customer, Please find the proposal in the attachment.",
  "headers": "string",
  "status": "inbox",
  "direction": "incoming",
  "message_id": "45489DFKDF",
  "email_message_id": "<98989854.549549@ec4.us-west-2.compute.amazonaws.com>",
  "thread_id": "4309",
  "gmail_message_id": "<98989854.549549@gmail.com>",
  "gmail_thread_id": "434343EB",
  "is_read": true,
  "send_attempts": 1,
  "open_count": 10,
  "reply_count": 2,
  "has_attachments": true,
  "addresses": {
    "from": {
      "name": "Elon Musk",
      "email": "elon@spacex.com",
      "contact_id": "4559",
      "user_id": ""
    },
    "to": [
      {
        "name": "Elon Musk",
        "email": "elon@spacex.com",
        "contact_id": "4559",
        "user_id": ""
      }
    ],
    "cc": [
      {
        "name": "Elon Musk",
        "email": "elon@spacex.com",
        "contact_id": "4559",
        "user_id": ""
      }
    ],
    "bcc": [
      {
        "name": "Elon Musk",
        "email": "elon@spacex.com",
        "contact_id": "4559",
        "user_id": ""
      }
    ]
  },
  "body": [
    {
      "type": "text/plain",
      "charset": "utf-8",
      "body": "Dear customer, Please find the proposal in the attachment. Best."
    },
    {
      "type": "text/html",
      "charset": "utf-8",
      "body": "<div class=\"pipe-mailbody-fdk985459kjddjk5498\"><div>Body&nbsp; <div><br /></div> <div>Line item</div> <div><br /></div> <div>Bye</div> </div></div>"
    }
  ],
  "attachments": [
    {
      "id": "2256",
      "name": "Proposal.pdf",
      "url": "https://api.apideck.com/crm/files/2256/download"
    }
  ],
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[Email](#schemaemail)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:emails )
</aside>

## updateEmail

> Code samples

```shell
# You can also use wget
curl -X PATCH https://api.apideck.com/crm/emails/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PATCH https://api.apideck.com/crm/emails/{id} HTTP/1.1
Host: api.apideck.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/emails/{id}',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "date": "2017-08-14T20:00:00.291Z",
  "subject": "Proposal",
  "body_text": "Dear customer, Please find the proposal in the attachment.",
  "headers": "string",
  "status": "inbox",
  "direction": "incoming",
  "message_id": "45489DFKDF",
  "email_message_id": "<98989854.549549@ec4.us-west-2.compute.amazonaws.com>",
  "thread_id": "4309",
  "gmail_message_id": "<98989854.549549@gmail.com>",
  "gmail_thread_id": "434343EB",
  "is_read": true,
  "send_attempts": 1,
  "open_count": 10,
  "reply_count": 2,
  "has_attachments": true,
  "addresses": {
    "from": {
      "name": "Elon Musk",
      "email": "elon@spacex.com",
      "contact_id": "4559",
      "user_id": ""
    },
    "to": [
      {
        "name": "Elon Musk",
        "email": "elon@spacex.com",
        "contact_id": "4559",
        "user_id": ""
      }
    ],
    "cc": [
      {
        "name": "Elon Musk",
        "email": "elon@spacex.com",
        "contact_id": "4559",
        "user_id": ""
      }
    ],
    "bcc": [
      {
        "name": "Elon Musk",
        "email": "elon@spacex.com",
        "contact_id": "4559",
        "user_id": ""
      }
    ]
  },
  "body": [
    {
      "type": "text/plain",
      "charset": "utf-8",
      "body": "Dear customer, Please find the proposal in the attachment. Best."
    },
    {
      "type": "text/html",
      "charset": "utf-8",
      "body": "<div class=\"pipe-mailbody-fdk985459kjddjk5498\"><div>Body&nbsp; <div><br /></div> <div>Line item</div> <div><br /></div> <div>Bye</div> </div></div>"
    }
  ],
  "attachments": [
    {
      "id": "2256",
      "name": "Proposal.pdf",
      "url": "https://api.apideck.com/crm/files/2256/download"
    }
  ],
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/emails/{id}',
{
  method: 'PATCH',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.patch 'https://api.apideck.com/crm/emails/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.patch('https://api.apideck.com/crm/emails/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/emails/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`PATCH /emails/{id}`

*Update an existing email*

> Body parameter

```json
{
  "date": "2017-08-14T20:00:00.291Z",
  "subject": "Proposal",
  "body_text": "Dear customer, Please find the proposal in the attachment.",
  "headers": "string",
  "status": "inbox",
  "direction": "incoming",
  "message_id": "45489DFKDF",
  "email_message_id": "<98989854.549549@ec4.us-west-2.compute.amazonaws.com>",
  "thread_id": "4309",
  "gmail_message_id": "<98989854.549549@gmail.com>",
  "gmail_thread_id": "434343EB",
  "is_read": true,
  "send_attempts": 1,
  "open_count": 10,
  "reply_count": 2,
  "has_attachments": true,
  "addresses": {
    "from": {
      "name": "Elon Musk",
      "email": "elon@spacex.com",
      "contact_id": "4559",
      "user_id": ""
    },
    "to": [
      {
        "name": "Elon Musk",
        "email": "elon@spacex.com",
        "contact_id": "4559",
        "user_id": ""
      }
    ],
    "cc": [
      {
        "name": "Elon Musk",
        "email": "elon@spacex.com",
        "contact_id": "4559",
        "user_id": ""
      }
    ],
    "bcc": [
      {
        "name": "Elon Musk",
        "email": "elon@spacex.com",
        "contact_id": "4559",
        "user_id": ""
      }
    ]
  },
  "body": [
    {
      "type": "text/plain",
      "charset": "utf-8",
      "body": "Dear customer, Please find the proposal in the attachment. Best."
    },
    {
      "type": "text/html",
      "charset": "utf-8",
      "body": "<div class=\"pipe-mailbody-fdk985459kjddjk5498\"><div>Body&nbsp; <div><br /></div> <div>Line item</div> <div><br /></div> <div>Bye</div> </div></div>"
    }
  ],
  "attachments": [
    {
      "id": "2256",
      "name": "Proposal.pdf",
      "url": "https://api.apideck.com/crm/files/2256/download"
    }
  ],
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return
body|body|[Email](#schemaemail)|true|Fields that need to be updated on the resource
» id|body|string|false|No description
» date|body|string|false|No description
» subject|body|string|false|No description
» body_text|body|string|false|No description
» headers|body|string|false|No description
» status|body|string|false|No description
» direction|body|string|false|No description
» message_id|body|string|false|No description
» email_message_id|body|string|false|No description
» thread_id|body|string|false|No description
» gmail_message_id|body|string|false|No description
» gmail_thread_id|body|string|false|No description
» is_read|body|boolean|false|No description
» send_attempts|body|integer|false|No description
» open_count|body|integer|false|No description
» reply_count|body|integer|false|No description
» has_attachments|body|boolean|false|No description
» addresses|body|object|false|No description
»» from|body|[EmailAddress](#schemaemailaddress)|false|No description
»»» name|body|string|false|No description
»»» email|body|string|false|No description
»»» contact_id|body|string|false|No description
»»» user_id|body|string|false|No description
»» to|body|[[EmailAddress](#schemaemailaddress)]|false|No description
»»» name|body|string|false|No description
»»» email|body|string|false|No description
»»» contact_id|body|string|false|No description
»»» user_id|body|string|false|No description
»» cc|body|[[EmailAddress](#schemaemailaddress)]|false|No description
»»» name|body|string|false|No description
»»» email|body|string|false|No description
»»» contact_id|body|string|false|No description
»»» user_id|body|string|false|No description
»» bcc|body|[[EmailAddress](#schemaemailaddress)]|false|No description
»»» name|body|string|false|No description
»»» email|body|string|false|No description
»»» contact_id|body|string|false|No description
»»» user_id|body|string|false|No description
» owner_id|body|string|false|No description
» creator_id|body|string|false|No description
» updated|body|string|false|No description
» created|body|string|false|No description
» body|body|[[EmailBody](#schemaemailbody)]|false|No description
»» type|body|string|false|No description
»» charset|body|string|false|No description
»» content|body|string|false|No description
» attachments|body|[[EmailAttachment](#schemaemailattachment)]|false|No description
»» id|body|string|false|No description
»» name|body|string|false|No description
»» url|body|string|false|No description
» linked_resources|body|[[LinkedResource](#schemalinkedresource)]|false|No description
»» id|body|integer|false|No description
»» type|body|string|false|No description


#### Enumerated Values

|Parameter|Value|
|---|---|
» status|inbox|
» status|draft|
» status|scheduled|
» status|outbox|
» status|sent|
» direction|incoming|
» direction|outgoing|
»» type|Lead/Opportunity/Person/Company|

> Example responses

```json
{
  "date": "2017-08-14T20:00:00.291Z",
  "subject": "Proposal",
  "body_text": "Dear customer, Please find the proposal in the attachment.",
  "headers": "string",
  "status": "inbox",
  "direction": "incoming",
  "message_id": "45489DFKDF",
  "email_message_id": "<98989854.549549@ec4.us-west-2.compute.amazonaws.com>",
  "thread_id": "4309",
  "gmail_message_id": "<98989854.549549@gmail.com>",
  "gmail_thread_id": "434343EB",
  "is_read": true,
  "send_attempts": 1,
  "open_count": 10,
  "reply_count": 2,
  "has_attachments": true,
  "addresses": {
    "from": {
      "name": "Elon Musk",
      "email": "elon@spacex.com",
      "contact_id": "4559",
      "user_id": ""
    },
    "to": [
      {
        "name": "Elon Musk",
        "email": "elon@spacex.com",
        "contact_id": "4559",
        "user_id": ""
      }
    ],
    "cc": [
      {
        "name": "Elon Musk",
        "email": "elon@spacex.com",
        "contact_id": "4559",
        "user_id": ""
      }
    ],
    "bcc": [
      {
        "name": "Elon Musk",
        "email": "elon@spacex.com",
        "contact_id": "4559",
        "user_id": ""
      }
    ]
  },
  "body": [
    {
      "type": "text/plain",
      "charset": "utf-8",
      "body": "Dear customer, Please find the proposal in the attachment. Best."
    },
    {
      "type": "text/html",
      "charset": "utf-8",
      "body": "<div class=\"pipe-mailbody-fdk985459kjddjk5498\"><div>Body&nbsp; <div><br /></div> <div>Line item</div> <div><br /></div> <div>Bye</div> </div></div>"
    }
  ],
  "attachments": [
    {
      "id": "2256",
      "name": "Proposal.pdf",
      "url": "https://api.apideck.com/crm/files/2256/download"
    }
  ],
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[Email](#schemaemail)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:emails )
</aside>

## deleteEmail

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.apideck.com/crm/emails/{id}

```

```http
DELETE https://api.apideck.com/crm/emails/{id} HTTP/1.1
Host: api.apideck.com


```

```javascript

$.ajax({
  url: 'https://api.apideck.com/crm/emails/{id}',
  method: 'delete',

  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

fetch('https://api.apideck.com/crm/emails/{id}',
{
  method: 'DELETE'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'


result = RestClient.delete 'https://api.apideck.com/crm/emails/{id}',
  params: {
  }

p JSON.parse(result)
```

```python
import requests

r = requests.delete('https://api.apideck.com/crm/emails/{id}', params={

)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/emails/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`DELETE /emails/{id}`

*Deletes a email*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No description|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:emails )
</aside>

# Files

Everything about your files

## allFiles

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/files \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/files HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/files',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/files',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/files',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/files', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/files");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /files`

*Get all files*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
page|query|integer|false|Page number to start from. Omitting the page parameter will return page 1
per_page|query|integer|false|Number of records to return per page. Default = 100.


> Example responses

```json
[
  {
    "id": "13",
    "name": "Signed_Contract.pdf",
    "size": 466610,
    "mime_type": "application/pdf",
    "url": "https://api.apideck.com/crm/files/13/download",
    "description": "Signed contract of new deal!",
    "linked_resources": [
      {
        "id": 2,
        "type": "Opportunity"
      }
    ],
    "owner_id": "456",
    "creator_id": "456",
    "updated_at": "2017-08-12T20:43:21.291Z",
    "created_at": "2017-08-12T20:43:21.291Z"
  }
]
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|Inline

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[File](#schemafile)]|false|No description
» id|string|false|No description
» name|string|false|No description
» size|integer(int64)|false|No description
» mime_type|string|false|No description
» url|string|false|No description
» description|string|false|No description
» owner_id|string|false|No description
» creator_id|string|false|No description
» updated_at|string|false|No description
» created_at|string|false|No description
» linked_resources|[[LinkedResource](#schemalinkedresource)]|false|No description
»» id|integer|false|No description
»» type|string|false|No description



<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:files )
</aside>

## addFiles

> Code samples

```shell
# You can also use wget
curl -X POST https://api.apideck.com/crm/files \
  -H 'Content-Type: application/json'

```

```http
POST https://api.apideck.com/crm/files HTTP/1.1
Host: api.apideck.com
Content-Type: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/files',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "name": "Signed_Contract.pdf",
  "size": 466610,
  "mime_type": "application/pdf",
  "url": "https://api.apideck.com/crm/files/13/download",
  "description": "Signed contract of new deal!",
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json'

};

fetch('https://api.apideck.com/crm/files',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.post 'https://api.apideck.com/crm/files',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.post('https://api.apideck.com/crm/files', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/files");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /files`

*Add a new files*

> Body parameter

```json
{
  "name": "Signed_Contract.pdf",
  "size": 466610,
  "mime_type": "application/pdf",
  "url": "https://api.apideck.com/crm/files/13/download",
  "description": "Signed contract of new deal!",
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
body|body|[File](#schemafile)|true|Files object that needs to be added
» id|body|string|false|No description
» name|body|string|false|No description
» size|body|integer(int64)|false|No description
» mime_type|body|string|false|No description
» url|body|string|false|No description
» description|body|string|false|No description
» owner_id|body|string|false|No description
» creator_id|body|string|false|No description
» updated_at|body|string|false|No description
» created_at|body|string|false|No description
» linked_resources|body|[[LinkedResource](#schemalinkedresource)]|false|No description
»» id|body|integer|false|No description
»» type|body|string|false|No description


#### Enumerated Values

|Parameter|Value|
|---|---|
»» type|Lead/Opportunity/Person/Company|

### Responses

Status|Meaning|Description|Schema
---|---|---|---|
201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:files )
</aside>

## getFiles

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/files/{id} \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/files/{id} HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/files/{id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/files/{id}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/files/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/files/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/files/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /files/{id}`

*Find files by ID*

Returns a single files

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


> Example responses

```json
{
  "name": "Signed_Contract.pdf",
  "size": 466610,
  "mime_type": "application/pdf",
  "url": "https://api.apideck.com/crm/files/13/download",
  "description": "Signed contract of new deal!",
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[File](#schemafile)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:files )
</aside>

## updateFiles

> Code samples

```shell
# You can also use wget
curl -X PATCH https://api.apideck.com/crm/files/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PATCH https://api.apideck.com/crm/files/{id} HTTP/1.1
Host: api.apideck.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/files/{id}',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "name": "Signed_Contract.pdf",
  "size": 466610,
  "mime_type": "application/pdf",
  "url": "https://api.apideck.com/crm/files/13/download",
  "description": "Signed contract of new deal!",
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/files/{id}',
{
  method: 'PATCH',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.patch 'https://api.apideck.com/crm/files/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.patch('https://api.apideck.com/crm/files/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/files/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`PATCH /files/{id}`

*Update an existing files*

> Body parameter

```json
{
  "name": "Signed_Contract.pdf",
  "size": 466610,
  "mime_type": "application/pdf",
  "url": "https://api.apideck.com/crm/files/13/download",
  "description": "Signed contract of new deal!",
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return
body|body|[File](#schemafile)|true|Fields that need to be updated on the resource
» id|body|string|false|No description
» name|body|string|false|No description
» size|body|integer(int64)|false|No description
» mime_type|body|string|false|No description
» url|body|string|false|No description
» description|body|string|false|No description
» owner_id|body|string|false|No description
» creator_id|body|string|false|No description
» updated_at|body|string|false|No description
» created_at|body|string|false|No description
» linked_resources|body|[[LinkedResource](#schemalinkedresource)]|false|No description
»» id|body|integer|false|No description
»» type|body|string|false|No description


#### Enumerated Values

|Parameter|Value|
|---|---|
»» type|Lead/Opportunity/Person/Company|

> Example responses

```json
{
  "name": "Signed_Contract.pdf",
  "size": 466610,
  "mime_type": "application/pdf",
  "url": "https://api.apideck.com/crm/files/13/download",
  "description": "Signed contract of new deal!",
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[File](#schemafile)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:files )
</aside>

## deleteFiles

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.apideck.com/crm/files/{id}

```

```http
DELETE https://api.apideck.com/crm/files/{id} HTTP/1.1
Host: api.apideck.com


```

```javascript

$.ajax({
  url: 'https://api.apideck.com/crm/files/{id}',
  method: 'delete',

  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

fetch('https://api.apideck.com/crm/files/{id}',
{
  method: 'DELETE'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'


result = RestClient.delete 'https://api.apideck.com/crm/files/{id}',
  params: {
  }

p JSON.parse(result)
```

```python
import requests

r = requests.delete('https://api.apideck.com/crm/files/{id}', params={

)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/files/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`DELETE /files/{id}`

*Deletes a files*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No description|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:files )
</aside>

# Users

Everything about your users

## allUsers

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/users \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/users HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/users',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/users',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/users',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/users', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/users");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /users`

*Get all users*

Returns a list of users

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
ids|query|string|false|Comma-separated list of user IDs
name|query|string|false|Name of user
email|query|string|false|Email of user
is_admin|query|boolean|false|Search for users who are admins
is_active|query|boolean|false|Search for activated users
role|query|string|false|Role of the users


> Example responses

```json
[
  {
    "id": 134,
    "name": "Elon Musk",
    "email": "elon@x.com",
    "is_active": true,
    "is_admin": true,
    "role": "user",
    "phone_numbers": [
      {
        "number": "111-111-1111",
        "type": "mobile"
      }
    ],
    "creator_id": "456",
    "updated_at": "2017-08-12T20:43:21.291Z",
    "created_at": "2017-08-12T20:43:21.291Z"
  }
]
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|Inline

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[User](#schemauser)]|false|No description
» id|integer|false|No description
» name|string|false|No description
» email|string|false|No description
» is_active|boolean|false|No description
» is_admin|boolean|false|No description
» role|string|false|No description
» creator_id|string|false|No description
» updated_at|string|false|No description
» created_at|string|false|No description
» phone_numbers|[[PhoneNumber](#schemaphonenumber)]|false|No description
»» number|string|false|No description
»» type|string|false|No description



<aside class="success">
This operation does not require authentication
</aside>

## userById

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/users/{userId} \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/users/{userId} HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/users/{userId}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/users/{userId}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/users/{userId}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/users/{userId}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/users/{userId}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /users/{userId}`

*Get user by ID*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


> Example responses

```json
{
  "name": "Elon Musk",
  "email": "elon@x.com",
  "is_active": true,
  "is_admin": true,
  "role": "user",
  "phone_numbers": [
    {
      "number": "111-111-1111",
      "type": "mobile"
    }
  ]
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|todo|[User](#schemauser)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="success">
This operation does not require authentication
</aside>

## userMe

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/users/me \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/users/me HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/users/me',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/users/me',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/users/me',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/users/me', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/users/me");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /users/me`

*Get information about the currently authenticated user*

> Example responses

```json
{
  "name": "Elon Musk",
  "email": "elon@x.com",
  "is_active": true,
  "is_admin": true,
  "role": "user",
  "phone_numbers": [
    {
      "number": "111-111-1111",
      "type": "mobile"
    }
  ]
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|todo|[User](#schemauser)

<aside class="success">
This operation does not require authentication
</aside>

# Webhooks

Everything about your webhooks

## allWebhooks

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/webhooks \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/webhooks HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/webhooks',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/webhooks',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/webhooks',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/webhooks', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/webhooks");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /webhooks`

*Get all webhooks*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
page|query|integer|false|Page number to start from. Omitting the page parameter will return page 1
per_page|query|integer|false|Number of records to return per page. Default = 100.


> Example responses

```json
[
  {
    "id": 2,
    "url": "https://www.saas.io/webhook",
    "event": {
      "action": "Update",
      "resource": "Lead"
    },
    "auth": {
      "key": "account@service.com",
      "secret": "5454lklk5445DFKFD954945"
    },
    "creator_id": 456,
    "updated_at": "2017-08-12T20:43:21.291Z",
    "created_at": "2017-08-12T20:43:21.291Z"
  }
]
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|Inline

### Response Schema

Status Code **200**

Name|Type|Required|Description
---|---|---|---|---|
anonymous|[[Webhook](#schemawebhook)]|false|No description
» id|integer|false|No description
» url|string|false|No description
» event|object|false|No description
»» action|string|false|No description
»» resource|string|false|No description
» auth|object|false|No description
»» key|string|false|No description
»» secret|string|false|No description
» creator_id|integer|false|No description
» updated_at|string|false|No description
» created_at|string|false|No description



<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:webhooks )
</aside>

## addWebhook

> Code samples

```shell
# You can also use wget
curl -X POST https://api.apideck.com/crm/webhooks \
  -H 'Content-Type: application/json'

```

```http
POST https://api.apideck.com/crm/webhooks HTTP/1.1
Host: api.apideck.com
Content-Type: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/webhooks',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "url": "https://www.saas.io/webhook",
  "event": {
    "action": "Update",
    "resource": "Lead"
  },
  "auth": {
    "key": "account@service.com",
    "secret": "5454lklk5445DFKFD954945"
  }
}';
const headers = {
  'Content-Type':'application/json'

};

fetch('https://api.apideck.com/crm/webhooks',
{
  method: 'POST',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json'
}

result = RestClient.post 'https://api.apideck.com/crm/webhooks',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json'
}

r = requests.post('https://api.apideck.com/crm/webhooks', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/webhooks");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("POST");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`POST /webhooks`

*Add a new webhook*

> Body parameter

```json
{
  "url": "https://www.saas.io/webhook",
  "event": {
    "action": "Update",
    "resource": "Lead"
  },
  "auth": {
    "key": "account@service.com",
    "secret": "5454lklk5445DFKFD954945"
  }
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
body|body|[Webhook](#schemawebhook)|true|Webhook object that needs to be added
» id|body|integer|false|No description
» url|body|string|false|No description
» event|body|object|false|No description
»» action|body|string|false|No description
»» resource|body|string|false|No description
» auth|body|object|false|No description
»» key|body|string|false|No description
»» secret|body|string|false|No description
» creator_id|body|integer|false|No description
» updated_at|body|string|false|No description
» created_at|body|string|false|No description


#### Enumerated Values

|Parameter|Value|
|---|---|
»» action|Create|
»» action|Update|
»» action|Delete|
»» resource|Company|
»» resource|Contact|
»» resource|Lead|
»» resource|Opportunity|
»» resource|User|
»» resource|Task|
»» resource|Note|

### Responses

Status|Meaning|Description|Schema
---|---|---|---|
201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:webhooks )
</aside>

## getWebhook

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/crm/webhooks/{id} \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/crm/webhooks/{id} HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/webhooks/{id}',
  method: 'get',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

const headers = {
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/webhooks/{id}',
{
  method: 'GET',

  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Accept' => 'application/json'
}

result = RestClient.get 'https://api.apideck.com/crm/webhooks/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/crm/webhooks/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/webhooks/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("GET");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`GET /webhooks/{id}`

*Find webhook by ID*

Returns a single webhook

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


> Example responses

```json
{
  "url": "https://www.saas.io/webhook",
  "event": {
    "action": "Update",
    "resource": "Lead"
  },
  "auth": {
    "key": "account@service.com",
    "secret": "5454lklk5445DFKFD954945"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[Webhook](#schemawebhook)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: read:webhooks )
</aside>

## updateWebhook

> Code samples

```shell
# You can also use wget
curl -X PATCH https://api.apideck.com/crm/webhooks/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PATCH https://api.apideck.com/crm/webhooks/{id} HTTP/1.1
Host: api.apideck.com
Content-Type: application/json
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/crm/webhooks/{id}',
  method: 'patch',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "url": "https://www.saas.io/webhook",
  "event": {
    "action": "Update",
    "resource": "Lead"
  },
  "auth": {
    "key": "account@service.com",
    "secret": "5454lklk5445DFKFD954945"
  }
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.apideck.com/crm/webhooks/{id}',
{
  method: 'PATCH',
  body: inputBody,
  headers: headers
})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'

headers = {
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.patch 'https://api.apideck.com/crm/webhooks/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/json',
  'Accept': 'application/json'
}

r = requests.patch('https://api.apideck.com/crm/webhooks/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/webhooks/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PATCH");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`PATCH /webhooks/{id}`

*Update an existing webhook*

> Body parameter

```json
{
  "url": "https://www.saas.io/webhook",
  "event": {
    "action": "Update",
    "resource": "Lead"
  },
  "auth": {
    "key": "account@service.com",
    "secret": "5454lklk5445DFKFD954945"
  }
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return
body|body|[Webhook](#schemawebhook)|true|Fields that need to be updated on the resource
» id|body|integer|false|No description
» url|body|string|false|No description
» event|body|object|false|No description
»» action|body|string|false|No description
»» resource|body|string|false|No description
» auth|body|object|false|No description
»» key|body|string|false|No description
»» secret|body|string|false|No description
» creator_id|body|integer|false|No description
» updated_at|body|string|false|No description
» created_at|body|string|false|No description


#### Enumerated Values

|Parameter|Value|
|---|---|
»» action|Create|
»» action|Update|
»» action|Delete|
»» resource|Company|
»» resource|Contact|
»» resource|Lead|
»» resource|Opportunity|
»» resource|User|
»» resource|Task|
»» resource|Note|

> Example responses

```json
{
  "url": "https://www.saas.io/webhook",
  "event": {
    "action": "Update",
    "resource": "Lead"
  },
  "auth": {
    "key": "account@service.com",
    "secret": "5454lklk5445DFKFD954945"
  }
}
```
### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|ok|[Webhook](#schemawebhook)
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:webhooks )
</aside>

## deleteWebhook

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.apideck.com/crm/webhooks/{id}

```

```http
DELETE https://api.apideck.com/crm/webhooks/{id} HTTP/1.1
Host: api.apideck.com


```

```javascript

$.ajax({
  url: 'https://api.apideck.com/crm/webhooks/{id}',
  method: 'delete',

  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');

fetch('https://api.apideck.com/crm/webhooks/{id}',
{
  method: 'DELETE'

})
.then(function(res) {
    return res.json();
}).then(function(body) {
    console.log(body);
});
```

```ruby
require 'rest-client'
require 'json'


result = RestClient.delete 'https://api.apideck.com/crm/webhooks/{id}',
  params: {
  }

p JSON.parse(result)
```

```python
import requests

r = requests.delete('https://api.apideck.com/crm/webhooks/{id}', params={

)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/crm/webhooks/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("DELETE");
int responseCode = con.getResponseCode();
BufferedReader in = new BufferedReader(
    new InputStreamReader(con.getInputStream()));
String inputLine;
StringBuffer response = new StringBuffer();
while ((inputLine = in.readLine()) != null) {
    response.append(inputLine);
}
in.close();
System.out.println(response.toString());
```

`DELETE /webhooks/{id}`

*Deletes a webhook*

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer|true|ID of the resource to return


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
204|[No Content](https://tools.ietf.org/html/rfc7231#section-6.3.5)|No description|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None

<aside class="warning">
To perform this operation, you must be authenticated by means of one of the following methods:
oauth2 ( Scopes: write:webhooks )
</aside>

# Schemas

## GeneralError

<a name="schemageneralerror"></a>

```json
[
  {}
] 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
anonymous|[[Error](#schemaerror)]|false|No description
» code|string|false|No description
» title|string|false|No description
» message|string|false|No description
» href|string|false|No description



## Error

<a name="schemaerror"></a>

```json
{} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
code|string|false|No description
title|string|false|No description
message|string|false|No description
href|string|false|No description



## Company

<a name="schemacompany"></a>

```json
{
  "name": "Company XYZ",
  "owner_id": 1,
  "website": "https://www.apideck.com/crm",
  "email": "info@company.com",
  "image_url": "https://logo.clearbit.com/showpad.com?s=128",
  "description": "Most important account for our company",
  "firmographics": {
    "employees": 350,
    "credit_rating": 10
  },
  "industry": {
    "sector": "string",
    "naics_codes": [
      {
        "code": "string",
        "name": "string"
      }
    ]
  },
  "addresses": [
    {
      "type": "invoicing",
      "name": "HQ US",
      "line1": "Main street",
      "line2": "Main street",
      "city": "San Francisco",
      "state": "CA",
      "postal_code": "94104",
      "country": "US",
      "lattitude": "40.759211",
      "longitude": "-73.984638"
    }
  ],
  "phone_numbers": [
    {
      "number": "111-111-1111",
      "type": "mobile"
    }
  ],
  "tags": [
    "Retail",
    "EMEA"
  ],
  "social_links": [
    {
      "url": "https://www.twitter.com/apideck-io",
      "platform": "twitter"
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|integer|false|No description
name|string|true|No description
owner_id|integer|false|No description
website|string|false|No description
email|string|false|No description
image_url|string|false|No description
description|string|false|No description
firmographics|object|false|No description
» employees|integer|false|No description
» credit_rating|integer|false|No description
industry|object|false|No description
» sector|string|false|No description
» naics_codes|[[NaicsCode](#schemanaicscode)]|false|No description
»» code|string|false|No description
»» name|string|false|No description
updated_at|string|false|No description
created_at|string|false|No description
addresses|[[Address](#schemaaddress)]|false|No description
» type|string|false|No description
» name|string|false|No description
» line1|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
» line2|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
» city|string|false|Name of city.
» state|string|false|Name of state
» postal_code|string|false|Zip code or equivalent.
» country|string|false|country code according to ISO 3166-1 alpha-2.
» lattitude|string|false|No description
» longitude|string|false|No description
phone_numbers|[[PhoneNumber](#schemaphonenumber)]|false|No description
» number|string|false|No description
» type|string|false|No description
social_links|[[SocialLink](#schemasociallink)]|false|No description
» url|string|false|No description
» platform|string|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
» type|default|
» type|invoicing|
» type|delivery|
» type|visiting|
» type|other|
» type|mobile|
» type|work|
» type|home|
» type|other|
» platform|facebook|
» platform|twitter|
» platform|linkedin|
» platform|other|


## Contact

<a name="schemacontact"></a>

```json
{
  "owner_id": 1,
  "company_id": 2,
  "lead_id": 3,
  "name": "Tiger Woods",
  "first_name": "Tiger",
  "middle_name": "In The",
  "last_name": "Woods",
  "prefix": "Mr.",
  "suffix": "PhD",
  "email": "tiger@woods.com",
  "title": "CMO",
  "department": "Marketing",
  "language": "EN",
  "gender": "M",
  "birthday": "2000-08-12T20:43:21.291Z",
  "website": "https://www.apideck.com/crm",
  "image": "https://logo.clearbit.com/tigerwoods.com?s=128",
  "description": "Internal champion within his company",
  "addresses": [
    {
      "type": "invoicing",
      "name": "HQ US",
      "line1": "Main street",
      "line2": "Main street",
      "city": "San Francisco",
      "state": "CA",
      "postal_code": "94104",
      "country": "US",
      "lattitude": "40.759211",
      "longitude": "-73.984638"
    }
  ],
  "phone_numbers": [
    {
      "number": "111-111-1111",
      "type": "mobile"
    }
  ],
  "tags": [
    "Retail",
    "EMEA"
  ],
  "social_links": [
    {
      "url": "https://www.twitter.com/apideck-io",
      "platform": "twitter"
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|integer|false|No description
owner_id|integer|false|No description
company_id|integer|false|No description
lead_id|integer|false|No description
name|string|true|No description
first_name|string|false|No description
middle_name|string|false|No description
last_name|string|false|No description
prefix|string|false|No description
suffix|string|false|No description
email|string|false|No description
title|string|false|No description
department|string|false|No description
language|string|false|language code according to ISO 639-1. For United Kingdom - EN
gender|string|false|No description
birthday|string|false|No description
website|string|false|No description
image|string|false|No description
description|string|false|No description
updated_at|string|false|No description
created_at|string|false|No description
addresses|[[Address](#schemaaddress)]|false|No description
» type|string|false|No description
» name|string|false|No description
» line1|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
» line2|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
» city|string|false|Name of city.
» state|string|false|Name of state
» postal_code|string|false|Zip code or equivalent.
» country|string|false|country code according to ISO 3166-1 alpha-2.
» lattitude|string|false|No description
» longitude|string|false|No description
phone_numbers|[[PhoneNumber](#schemaphonenumber)]|false|No description
» number|string|false|No description
» type|string|false|No description
social_links|[[SocialLink](#schemasociallink)]|false|No description
» url|string|false|No description
» platform|string|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
gender|M/F/U|
» type|default|
» type|invoicing|
» type|delivery|
» type|visiting|
» type|other|
» type|mobile|
» type|work|
» type|home|
» type|other|
» platform|facebook|
» platform|twitter|
» platform|linkedin|
» platform|other|


## Opportunity

<a name="schemaopportunity"></a>

```json
{
  "name": "Multi-year deal CRM",
  "value": 3000,
  "currency": "USD",
  "description": "Looking into end-to-end solutions",
  "owner_id": 10,
  "contact_id": 15,
  "company_id": 17,
  "stage_id": 20,
  "status": "Open",
  "close_date": "10-05-2016",
  "lost_reason": "Out of budget",
  "probability": 50,
  "source_id": 11,
  "pipeline_id": 2,
  "creator_id": 145
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|integer|false|No description
name|string|false|No description
value|integer|false|No description
currency|string|false|No description
description|string|false|No description
owner_id|integer|false|No description
contact_id|integer|false|No description
company_id|integer|false|No description
stage_id|integer|false|No description
status|string|false|No description
close_date|string|false|No description
lost_reason|string|false|No description
probability|integer|false|No description
source_id|integer|false|No description
pipeline_id|integer|false|No description
creator_id|integer|false|No description
updated_at|string|false|No description
created_at|string|false|No description



## Lead

<a name="schemalead"></a>

```json
{
  "owner_id": 14,
  "first_name": "Tiger",
  "middle_name": "In The",
  "last_name": "Woods",
  "prefix": "Mr.",
  "suffix": "PhD",
  "title": "CMO",
  "company": "Tiger Inc.",
  "industry": "Sports Industry",
  "status": "Open",
  "rating": "Hot",
  "source_id": 2,
  "description": "Expert in CRM integration.",
  "website": "http://www.tigerwoods.com",
  "email": "tiger@woods.com",
  "addresses": [
    {
      "type": "invoicing",
      "name": "HQ US",
      "line1": "Main street",
      "line2": "Main street",
      "city": "San Francisco",
      "state": "CA",
      "postal_code": "94104",
      "country": "US",
      "lattitude": "40.759211",
      "longitude": "-73.984638"
    }
  ],
  "phone_numbers": [
    {
      "number": "111-111-1111",
      "type": "mobile"
    }
  ],
  "social_links": [
    {
      "url": "https://www.twitter.com/apideck-io",
      "platform": "twitter"
    }
  ],
  "tags": [
    "Retail",
    "Sports"
  ],
  "custom_fields": {
    "known_via": "John"
  }
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|integer|false|No description
owner_id|integer|false|No description
first_name|string|false|No description
middle_name|string|false|No description
last_name|string|false|No description
prefix|string|false|No description
suffix|string|false|No description
title|string|false|No description
company|string|false|No description
industry|string|false|No description
status|string|false|No description
rating|string|false|No description
source_id|integer|false|No description
description|string|false|No description
website|string|false|No description
email|string|false|No description
custom_fields|object|false|No description
updated_at|string|false|No description
created_at|string|false|No description
addresses|[[Address](#schemaaddress)]|false|No description
» type|string|false|No description
» name|string|false|No description
» line1|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
» line2|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
» city|string|false|Name of city.
» state|string|false|Name of state
» postal_code|string|false|Zip code or equivalent.
» country|string|false|country code according to ISO 3166-1 alpha-2.
» lattitude|string|false|No description
» longitude|string|false|No description
phone_numbers|[[PhoneNumber](#schemaphonenumber)]|false|No description
» number|string|false|No description
» type|string|false|No description
social_links|[[SocialLink](#schemasociallink)]|false|No description
» url|string|false|No description
» platform|string|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
» type|default|
» type|invoicing|
» type|delivery|
» type|visiting|
» type|other|
» type|mobile|
» type|work|
» type|home|
» type|other|
» platform|facebook|
» platform|twitter|
» platform|linkedin|
» platform|other|


## Task

<a name="schematask"></a>

```json
{
  "owner_id": 349,
  "title": "Contact Marc Benioff",
  "description": "Do a background check before call",
  "due_date": "2020-10-28T15:23:50Z",
  "overdue": false,
  "completed_at": "2019-10-28T15:23:50Z",
  "completed": false,
  "remind_at": "2018-10-28T15:23:50Z",
  "priority": "High",
  "status": "Open",
  "tags": [
    "CRM",
    "Influencer"
  ],
  "custom_fields": {
    "research": "High energy person. Founding CEO Salesforce."
  },
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|integer|false|No description
creator_id|integer|false|No description
owner_id|integer|false|No description
title|string|false|No description
description|string|false|No description
due_date|string|false|No description
overdue|boolean|false|No description
completed_at|string|false|No description
completed|boolean|false|No description
remind_at|string|false|No description
priority|string|false|No description
status|string|false|No description
custom_fields|object|false|No description
updated_at|string|false|No description
created_at|string|false|No description
linked_resources|[[LinkedResource](#schemalinkedresource)]|false|No description
» id|integer|false|No description
» type|string|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
» type|Lead/Opportunity/Person/Company|


## Call

<a name="schemacall"></a>

```json
{
  "id": "124",
  "owner_id": "349",
  "subject": "Call Marc Benioff",
  "description": "Go over the details of the contract",
  "start": "2017-08-12T14:00:00.001Z",
  "end": "2017-08-12T16:00:00.001Z",
  "actual_start": "2017-08-12T14:00:00.001Z",
  "actual_end": "2017-08-12T16:00:00.001Z",
  "recording_url": "https://api.apideck.com/files/1350945",
  "voicemail_url": "https://api.apideck.com/files/139045945",
  "direction": "incoming",
  "missed": false,
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|string|false|No description
owner_id|string|false|No description
subject|string|false|No description
description|string|false|No description
start|string|false|No description
end|string|false|No description
duration|integer|false|No description
actual_start|string|false|No description
actual_end|string|false|No description
actual_duration|integer|false|No description
recording_url|string|false|No description
voicemail_url|string|false|No description
direction|string|false|No description
missed|boolean|false|No description
creator_id|string|false|No description
updated_at|string|false|No description
created_at|string|false|No description
linked_resources|[[LinkedResource](#schemalinkedresource)]|false|No description
» id|integer|false|No description
» type|string|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
direction|incoming/outgoing|
» type|Lead/Opportunity/Person/Company|


## Activity

<a name="schemaactivity"></a>

```json
{
  "id": "124",
  "owner_id": "349",
  "title": "Meeting Marc Benioff",
  "description": "Do a background check before meeting",
  "location": "22 Main street, NY, US",
  "type": "Meeting",
  "visibility": "Busy",
  "is_private": false,
  "start_date": "2017-08-12T14:00:00.001Z",
  "end_date": "2017-08-12T16:00:00.001Z",
  "all_day": false,
  "reminder_date": "2017-08-10T16:00:00.001Z",
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|string|false|No description
owner_id|string|false|No description
title|string|true|No description
description|string|false|No description
location|string|false|No description
type|string|true|No description
visibility|string|false|No description
is_private|boolean|false|No description
start_date|string|false|No description
end_date|string|false|No description
duration|integer|false|No description
all_day|boolean|false|No description
reminder_date|string|false|No description
creator_id|integer|false|No description
updated_at|string|false|No description
created_at|string|false|No description
linked_resources|[[LinkedResource](#schemalinkedresource)]|false|No description
» id|integer|false|No description
» type|string|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
type|Meeting/Call/Task|
visibility|Busy/OutOfOffice/Free|
» type|Lead/Opportunity/Person/Company|


## Email

<a name="schemaemail"></a>

```json
{
  "date": "2017-08-14T20:00:00.291Z",
  "subject": "Proposal",
  "body_text": "Dear customer, Please find the proposal in the attachment.",
  "headers": "string",
  "status": "inbox",
  "direction": "incoming",
  "message_id": "45489DFKDF",
  "email_message_id": "<98989854.549549@ec4.us-west-2.compute.amazonaws.com>",
  "thread_id": "4309",
  "gmail_message_id": "<98989854.549549@gmail.com>",
  "gmail_thread_id": "434343EB",
  "is_read": true,
  "send_attempts": 1,
  "open_count": 10,
  "reply_count": 2,
  "has_attachments": true,
  "addresses": {
    "from": {
      "name": "Elon Musk",
      "email": "elon@spacex.com",
      "contact_id": "4559",
      "user_id": ""
    },
    "to": [
      {
        "name": "Elon Musk",
        "email": "elon@spacex.com",
        "contact_id": "4559",
        "user_id": ""
      }
    ],
    "cc": [
      {
        "name": "Elon Musk",
        "email": "elon@spacex.com",
        "contact_id": "4559",
        "user_id": ""
      }
    ],
    "bcc": [
      {
        "name": "Elon Musk",
        "email": "elon@spacex.com",
        "contact_id": "4559",
        "user_id": ""
      }
    ]
  },
  "body": [
    {
      "type": "text/plain",
      "charset": "utf-8",
      "body": "Dear customer, Please find the proposal in the attachment. Best."
    },
    {
      "type": "text/html",
      "charset": "utf-8",
      "body": "<div class=\"pipe-mailbody-fdk985459kjddjk5498\"><div>Body&nbsp; <div><br /></div> <div>Line item</div> <div><br /></div> <div>Bye</div> </div></div>"
    }
  ],
  "attachments": [
    {
      "id": "2256",
      "name": "Proposal.pdf",
      "url": "https://api.apideck.com/crm/files/2256/download"
    }
  ],
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|string|false|No description
date|string|false|No description
subject|string|false|No description
body_text|string|false|No description
headers|string|false|No description
status|string|false|No description
direction|string|false|No description
message_id|string|false|No description
email_message_id|string|false|No description
thread_id|string|false|No description
gmail_message_id|string|false|No description
gmail_thread_id|string|false|No description
is_read|boolean|false|No description
send_attempts|integer|false|No description
open_count|integer|false|No description
reply_count|integer|false|No description
has_attachments|boolean|false|No description
addresses|object|false|No description
» from|[EmailAddress](#schemaemailaddress)|false|No description
»» name|string|false|No description
»» email|string|false|No description
»» contact_id|string|false|No description
»» user_id|string|false|No description
» to|[[EmailAddress](#schemaemailaddress)]|false|No description
»» name|string|false|No description
»» email|string|false|No description
»» contact_id|string|false|No description
»» user_id|string|false|No description
» cc|[[EmailAddress](#schemaemailaddress)]|false|No description
»» name|string|false|No description
»» email|string|false|No description
»» contact_id|string|false|No description
»» user_id|string|false|No description
» bcc|[[EmailAddress](#schemaemailaddress)]|false|No description
»» name|string|false|No description
»» email|string|false|No description
»» contact_id|string|false|No description
»» user_id|string|false|No description
owner_id|string|false|No description
creator_id|string|false|No description
updated|string|false|No description
created|string|false|No description
body|[[EmailBody](#schemaemailbody)]|false|No description
» type|string|false|No description
» charset|string|false|No description
» content|string|false|No description
attachments|[[EmailAttachment](#schemaemailattachment)]|false|No description
» id|string|false|No description
» name|string|false|No description
» url|string|false|No description
linked_resources|[[LinkedResource](#schemalinkedresource)]|false|No description
» id|integer|false|No description
» type|string|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
status|inbox|
status|draft|
status|scheduled|
status|outbox|
status|sent|
direction|incoming|
direction|outgoing|
» type|Lead/Opportunity/Person/Company|


## EmailBody

<a name="schemaemailbody"></a>

```json
{
  "type": "text/plain",
  "charset": "utf-8",
  "content": "Dear customer, Please find the proposal in the attachment. Best."
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
type|string|false|No description
charset|string|false|No description
content|string|false|No description



## EmailAddress

<a name="schemaemailaddress"></a>

```json
{
  "name": "Elon Musk",
  "email": "elon@spacex.com",
  "contact_id": "4559",
  "user_id": ""
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
name|string|false|No description
email|string|false|No description
contact_id|string|false|No description
user_id|string|false|No description



## EmailAttachment

<a name="schemaemailattachment"></a>

```json
{
  "id": "2256",
  "name": "Proposal.pdf",
  "url": "https://api.apideck.com/crm/files/2256/download"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|string|false|No description
name|string|false|No description
url|string|false|No description



## Product

<a name="schemaproduct"></a>

```json
{
  "name": "1-year Pro subscription",
  "description": "Includes pro subscription with free trial.",
  "is_active": true,
  "external_id": "145E",
  "code": "1-year-pro",
  "sku": "PRO1-EDFG",
  "cost": "40.00",
  "cost_currency": "EUR",
  "stock_amount": 340,
  "prices": [
    {
      "amount": 100,
      "currency": "EUR",
      "tax_percentage": 5
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|integer|false|No description
name|string|false|No description
description|string|false|No description
is_active|boolean|false|No description
external_id|string|false|No description
code|string|false|No description
sku|string|false|No description
cost|integer|false|No description
cost_currency|string|false|No description
stock_amount|integer|false|No description
updated_at|string|false|No description
created_at|string|false|No description
prices|[[ProductPrice](#schemaproductprice)]|false|No description
» amount|integer|false|No description
» currency|string|false|No description
» tax_percentage|number|false|No description



## Note

<a name="schemanote"></a>

```json
{
  "title": "Note to myself",
  "description": "New entrant in market. Look into to this company + references.",
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|integer|false|No description
title|string|false|No description
description|string|false|No description
creator_id|string|false|No description
updated|string|false|No description
created|string|false|No description
linked_resources|[[LinkedResource](#schemalinkedresource)]|false|No description
» id|integer|false|No description
» type|string|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
» type|Lead/Opportunity/Person/Company|


## File

<a name="schemafile"></a>

```json
{
  "name": "Signed_Contract.pdf",
  "size": 466610,
  "mime_type": "application/pdf",
  "url": "https://api.apideck.com/crm/files/13/download",
  "description": "Signed contract of new deal!",
  "linked_resources": [
    {
      "id": 2,
      "type": "Opportunity"
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|string|false|No description
name|string|false|No description
size|integer(int64)|false|No description
mime_type|string|false|No description
url|string|false|No description
description|string|false|No description
owner_id|string|false|No description
creator_id|string|false|No description
updated_at|string|false|No description
created_at|string|false|No description
linked_resources|[[LinkedResource](#schemalinkedresource)]|false|No description
» id|integer|false|No description
» type|string|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
» type|Lead/Opportunity/Person/Company|


## LinkedResource

<a name="schemalinkedresource"></a>

```json
{
  "id": 2,
  "type": "Opportunity"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|integer|false|No description
type|string|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
type|Lead/Opportunity/Person/Company|


## Campaign

<a name="schemacampaign"></a>

```json
{
  "name": "Black Friday Email - 2018",
  "description": "Black friday - email campaign. US-only.",
  "message": "Black Friday - 40% off everything!",
  "objective": "Maximize inbound leads for US customers.",
  "type": "E-mail",
  "status": "Active",
  "start": "2018-11-23T20:00:00.291Z",
  "end": "2018-11-30T00:00:00.291Z",
  "costs": [
    {
      "amount": "100000.00",
      "currency": "EUR",
      "type": "actual"
    }
  ],
  "revenue": [
    {
      "amount": "100000.00",
      "currency": "EUR",
      "type": "expected"
    }
  ],
  "parent_id": "4469",
  "currency": "USD",
  "is_active": true
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|string|false|No description
name|string|false|No description
description|string|false|No description
message|string|false|No description
objective|string|false|No description
type|string|false|No description
status|string|false|No description
start|string|false|No description
end|string|false|No description
parent_id|string|false|No description
currency|string|false|No description
is_active|boolean|false|No description
owner_id|string|false|No description
creator_id|string|false|No description
updated|string|false|No description
created|string|false|No description
costs|[[CampaignCost](#schemacampaigncost)]|false|No description
» amount|string|false|No description
» currency|string|false|No description
» type|string|false|No description
revenue|[[CampaignRevenue](#schemacampaignrevenue)]|false|No description
» amount|string|false|No description
» currency|string|false|No description
» type|string|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
» type|actual|
» type|budgeted|
» type|other|
» type|actual|
» type|expected|
» type|other|


## CampaignCost

<a name="schemacampaigncost"></a>

```json
{
  "amount": "100000.00",
  "currency": "EUR",
  "type": "actual"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
amount|string|false|No description
currency|string|false|No description
type|string|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
type|actual|
type|budgeted|
type|other|


## CampaignRevenue

<a name="schemacampaignrevenue"></a>

```json
{
  "amount": "100000.00",
  "currency": "EUR",
  "type": "expected"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
amount|string|false|No description
currency|string|false|No description
type|string|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
type|actual|
type|expected|
type|other|


## Source

<a name="schemasource"></a>

```json
{
  "name": "Note to myself"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|string|false|No description
name|string|false|No description
creator_id|string|false|No description
updated|string|false|No description
created|string|false|No description



## User

<a name="schemauser"></a>

```json
{
  "name": "Elon Musk",
  "email": "elon@x.com",
  "is_active": true,
  "is_admin": true,
  "role": "user",
  "phone_numbers": [
    {
      "number": "111-111-1111",
      "type": "mobile"
    }
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|integer|false|No description
name|string|false|No description
email|string|false|No description
is_active|boolean|false|No description
is_admin|boolean|false|No description
role|string|false|No description
creator_id|string|false|No description
updated_at|string|false|No description
created_at|string|false|No description
phone_numbers|[[PhoneNumber](#schemaphonenumber)]|false|No description
» number|string|false|No description
» type|string|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
» type|mobile|
» type|work|
» type|home|
» type|other|


## Webhook

<a name="schemawebhook"></a>

```json
{
  "url": "https://www.saas.io/webhook",
  "event": {
    "action": "Update",
    "resource": "Lead"
  },
  "auth": {
    "key": "account@service.com",
    "secret": "5454lklk5445DFKFD954945"
  }
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|integer|false|No description
url|string|false|No description
event|object|false|No description
» action|string|false|No description
» resource|string|false|No description
auth|object|false|No description
» key|string|false|No description
» secret|string|false|No description
creator_id|integer|false|No description
updated_at|string|false|No description
created_at|string|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
» action|Create|
» action|Update|
» action|Delete|
» resource|Company|
» resource|Contact|
» resource|Lead|
» resource|Opportunity|
» resource|User|
» resource|Task|
» resource|Note|


## Address

<a name="schemaaddress"></a>

```json
{
  "type": "invoicing",
  "name": "HQ US",
  "line1": "Main street",
  "line2": "Main street",
  "city": "San Francisco",
  "state": "CA",
  "postal_code": "94104",
  "country": "US",
  "lattitude": "40.759211",
  "longitude": "-73.984638"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
type|string|false|No description
name|string|false|No description
line1|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
line2|string|false|Line 1 of the address e.g. number, street, suite, apt #, etc.
city|string|false|Name of city.
state|string|false|Name of state
postal_code|string|false|Zip code or equivalent.
country|string|false|country code according to ISO 3166-1 alpha-2.
lattitude|string|false|No description
longitude|string|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
type|default|
type|invoicing|
type|delivery|
type|visiting|
type|other|


## PhoneNumber

<a name="schemaphonenumber"></a>

```json
{
  "number": "111-111-1111",
  "type": "mobile"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
number|string|false|No description
type|string|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
type|mobile|
type|work|
type|home|
type|other|


## SocialLink

<a name="schemasociallink"></a>

```json
{
  "url": "https://www.twitter.com/apideck-io",
  "platform": "twitter"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
url|string|false|No description
platform|string|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
platform|facebook|
platform|twitter|
platform|linkedin|
platform|other|


## NaicsCode

<a name="schemanaicscode"></a>

```json
{
  "code": "string",
  "name": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
code|string|false|No description
name|string|false|No description



## ProductPrice

<a name="schemaproductprice"></a>

```json
{
  "amount": 100,
  "currency": "EUR",
  "tax_percentage": 5
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
amount|integer|false|No description
currency|string|false|No description
tax_percentage|number|false|No description





