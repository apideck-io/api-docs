---
title: Unified API - Storage v0.0.1
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - javascript--nodejs: Node.JS
  - ruby: Ruby
  - python: Python
  - java: Java
toc_footers: []
includes: []
search: true
highlight_theme: darkula
---

# Unified API - Storage v0.0.1

> Scroll down for code samples, example requests and responses. Select a language for code samples from the tabs above or the mobile navigation menu.

This is the File Storage API from Apideck. You can find
out more about Apideck at
[https://apideck.com](https://apideck.com) or on
[apideck-io.slack.com, #crm](https://apideck-io.slack.com).

Base URLs:

* <a href="https://api.apideck.com/storage">https://api.apideck.com/storage</a>


<a href="https://apideck.com/terms/">Terms of service</a>
Email: <a href="mailto:hello@apideck.com">Support</a> 
License: <a href="http://www.apache.org/licenses/LICENSE-2.0.html">Apache 2.0</a>

# Accounts

Everything about accounts

## accountMe

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/storage/accounts/me/info \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/storage/accounts/me/info HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/storage/accounts/me/info',
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

fetch('https://api.apideck.com/storage/accounts/me/info',
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

result = RestClient.get 'https://api.apideck.com/storage/accounts/me/info',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/storage/accounts/me/info', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/storage/accounts/me/info");
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

`GET /accounts/me/info`

*Get information about the currently authenticated account*

Get information about the currently authenticated account

### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|return currently authenticated account|None

<aside class="success">
This operation does not require authentication
</aside>

# Files

Everything about files

## uploadFile

> Code samples

```shell
# You can also use wget
curl -X POST https://api.apideck.com/storage/files \
  -H 'name: string' \
  -H 'parent: string' \
  -H 'Content-Type: application/octet-stream' \
  -H 'Accept: application/json'

```

```http
POST https://api.apideck.com/storage/files HTTP/1.1
Host: api.apideck.com
Content-Type: application/octet-stream
Accept: application/json
name: string
parent: string

```

```javascript
var headers = {
  'name':'string',
  'parent':'string',
  'Content-Type':'application/octet-stream',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/storage/files',
  method: 'post',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = ''string'';
const headers = {
  'name':'string',
  'parent':'string',
  'Content-Type':'application/octet-stream',
  'Accept':'application/json'

};

fetch('https://api.apideck.com/storage/files',
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
  'name' => 'string',
  'parent' => 'string',
  'Content-Type' => 'application/octet-stream',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.apideck.com/storage/files',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'name': 'string',
  'parent': 'string',
  'Content-Type': 'application/octet-stream',
  'Accept': 'application/json'
}

r = requests.post('https://api.apideck.com/storage/files', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/storage/files");
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

*Upload a file*

Upload a file

> Body parameter

```yaml
string

```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
overwrite|query|boolean|false|Should file be overwritten
name|header|string|true|name of the uploaded file
parent|header|string|true|id of the parent folder
body|body|[inputStream](#schema+inputstream)(binary)|false|file input stream


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|No description|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None
default|Default|No description|None

<aside class="success">
This operation does not require authentication
</aside>

## getFileMetaData

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/storage/files/{id} \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/storage/files/{id} HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/storage/files/{id}',
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

fetch('https://api.apideck.com/storage/files/{id}',
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

result = RestClient.get 'https://api.apideck.com/storage/files/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/storage/files/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/storage/files/{id}");
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

*Get metadata of a file*

Get metadata of a file

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer(string)|true|ID of the resource to return


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|No description|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None
default|Default|No description|None

<aside class="success">
This operation does not require authentication
</aside>

## updateFile

> Code samples

```shell
# You can also use wget
curl -X PUT https://api.apideck.com/storage/files/{id} \
  -H 'Content-Type: application/octet-stream' \
  -H 'Accept: application/json'

```

```http
PUT https://api.apideck.com/storage/files/{id} HTTP/1.1
Host: api.apideck.com
Content-Type: application/octet-stream
Accept: application/json

```

```javascript
var headers = {
  'Content-Type':'application/octet-stream',
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/storage/files/{id}',
  method: 'put',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = ''string'';
const headers = {
  'Content-Type':'application/octet-stream',
  'Accept':'application/json'

};

fetch('https://api.apideck.com/storage/files/{id}',
{
  method: 'PUT',
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
  'Content-Type' => 'application/octet-stream',
  'Accept' => 'application/json'
}

result = RestClient.put 'https://api.apideck.com/storage/files/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Content-Type': 'application/octet-stream',
  'Accept': 'application/json'
}

r = requests.put('https://api.apideck.com/storage/files/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/storage/files/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
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

`PUT /files/{id}`

*Update a file*

Update a file

> Body parameter

```yaml
string

```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer(string)(string)|true|ID of the resource to return
body|body|[inputStream](#schema+inputstream)(binary)|false|file input stream


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|No description|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None
default|Default|No description|None

<aside class="success">
This operation does not require authentication
</aside>

## moveFile

> Code samples

```shell
# You can also use wget
curl -X PATCH https://api.apideck.com/storage/files/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PATCH https://api.apideck.com/storage/files/{id} HTTP/1.1
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
  url: 'https://api.apideck.com/storage/files/{id}',
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
  "parent_id": "string",
  "name": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.apideck.com/storage/files/{id}',
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

result = RestClient.patch 'https://api.apideck.com/storage/files/{id}',
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

r = requests.patch('https://api.apideck.com/storage/files/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/storage/files/{id}");
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

*Move or rename a file*

Move or rename a file

> Body parameter

```json
{
  "parent_id": "string",
  "name": "string"
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer(string)(string)(string)|true|ID of the resource to return
body|body|[FileAction](#schemafileaction)|false|move/rename file
» parent_id|body|string|false|id of the parent folder
» name|body|string|false|name of the file


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|No description|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None
default|Default|No description|None

<aside class="success">
This operation does not require authentication
</aside>

## deleteFile

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.apideck.com/storage/files/{id} \
  -H 'Accept: application/json'

```

```http
DELETE https://api.apideck.com/storage/files/{id} HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/storage/files/{id}',
  method: 'delete',

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

fetch('https://api.apideck.com/storage/files/{id}',
{
  method: 'DELETE',

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

result = RestClient.delete 'https://api.apideck.com/storage/files/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.delete('https://api.apideck.com/storage/files/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/storage/files/{id}");
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

*delete a file*

delete a file

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer(string)(string)(string)(string)|true|ID of the resource to return
permanent|query|boolean|false|Should resource be deleted permanently


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|File has been marked for deletion|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None
default|Default|No description|None

<aside class="success">
This operation does not require authentication
</aside>

## copyFile

> Code samples

```shell
# You can also use wget
curl -X POST https://api.apideck.com/storage/files/{id}/copy \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://api.apideck.com/storage/files/{id}/copy HTTP/1.1
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
  url: 'https://api.apideck.com/storage/files/{id}/copy',
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
  "parent_id": "string",
  "name": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.apideck.com/storage/files/{id}/copy',
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
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.apideck.com/storage/files/{id}/copy',
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

r = requests.post('https://api.apideck.com/storage/files/{id}/copy', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/storage/files/{id}/copy");
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

`POST /files/{id}/copy`

*Copy a file*

copy a file

> Body parameter

```json
{
  "parent_id": "string",
  "name": "string"
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer(string)(string)(string)(string)(string)|true|ID of the resource to return
body|body|[FileAction](#schemafileaction)|false|copy file
» parent_id|body|string|false|id of the parent folder
» name|body|string|false|name of the file


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|File has been copied|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None
default|Default|No description|None

<aside class="success">
This operation does not require authentication
</aside>

## downloadFile

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/storage/files/{id}/contents \
  -H 'Accept: application/octet-stream'

```

```http
GET https://api.apideck.com/storage/files/{id}/contents HTTP/1.1
Host: api.apideck.com

Accept: application/octet-stream

```

```javascript
var headers = {
  'Accept':'application/octet-stream'

};

$.ajax({
  url: 'https://api.apideck.com/storage/files/{id}/contents',
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
  'Accept':'application/octet-stream'

};

fetch('https://api.apideck.com/storage/files/{id}/contents',
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
  'Accept' => 'application/octet-stream'
}

result = RestClient.get 'https://api.apideck.com/storage/files/{id}/contents',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/octet-stream'
}

r = requests.get('https://api.apideck.com/storage/files/{id}/contents', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/storage/files/{id}/contents");
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

`GET /files/{id}/contents`

*Get Content of a file*

Get Content of a file

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer(string)(string)(string)(string)(string)(string)|true|ID of the resource to return


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|File content of the file that has been returned|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None
default|Default|No description|None

<aside class="success">
This operation does not require authentication
</aside>

# Folders

Everthing about folders

## createFolder

> Code samples

```shell
# You can also use wget
curl -X POST https://api.apideck.com/storage/folders \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://api.apideck.com/storage/folders HTTP/1.1
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
  url: 'https://api.apideck.com/storage/folders',
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
  "parent_id": "string",
  "name": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.apideck.com/storage/folders',
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
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.apideck.com/storage/folders',
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

r = requests.post('https://api.apideck.com/storage/folders', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/storage/folders");
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

`POST /folders`

*Create a folder*

Create a folder

> Body parameter

```json
{
  "parent_id": "string",
  "name": "string"
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
body|body|[FolderAction](#schemafolderaction)|false|create folder
» parent_id|body|string|false|id of the parent folder
» name|body|string|false|name of the folder


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
201|[Created](https://tools.ietf.org/html/rfc7231#section-6.3.2)|Folder has been created succesfully|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None
default|Default|No description|None

<aside class="success">
This operation does not require authentication
</aside>

## getFolderMetadata

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/storage/folders/{id} \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/storage/folders/{id} HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/storage/folders/{id}',
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

fetch('https://api.apideck.com/storage/folders/{id}',
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

result = RestClient.get 'https://api.apideck.com/storage/folders/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/storage/folders/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/storage/folders/{id}");
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

`GET /folders/{id}`

*Get metadata of a folder*

Get metadata of a folder

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer(string)(string)(string)(string)(string)(string)(string)|true|ID of the resource to return


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|No description|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None
default|Default|No description|None

<aside class="success">
This operation does not require authentication
</aside>

## moveOrRenameFolder

> Code samples

```shell
# You can also use wget
curl -X PATCH https://api.apideck.com/storage/folders/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PATCH https://api.apideck.com/storage/folders/{id} HTTP/1.1
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
  url: 'https://api.apideck.com/storage/folders/{id}',
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
  "parent_id": "string",
  "name": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.apideck.com/storage/folders/{id}',
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

result = RestClient.patch 'https://api.apideck.com/storage/folders/{id}',
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

r = requests.patch('https://api.apideck.com/storage/folders/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/storage/folders/{id}");
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

`PATCH /folders/{id}`

*Move or rename a folder*

Move or rename a folder

> Body parameter

```json
{
  "parent_id": "string",
  "name": "string"
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer(string)(string)(string)(string)(string)(string)(string)(string)|true|ID of the resource to return
body|body|[FolderAction](#schemafolderaction)|false|move/rename folder
» parent_id|body|string|false|id of the parent folder
» name|body|string|false|name of the folder


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Folder has been moved or renamed succesfully|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None
default|Default|No description|None

<aside class="success">
This operation does not require authentication
</aside>

## deleteFolder

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.apideck.com/storage/folders/{id} \
  -H 'Accept: application/json'

```

```http
DELETE https://api.apideck.com/storage/folders/{id} HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/storage/folders/{id}',
  method: 'delete',

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

fetch('https://api.apideck.com/storage/folders/{id}',
{
  method: 'DELETE',

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

result = RestClient.delete 'https://api.apideck.com/storage/folders/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.delete('https://api.apideck.com/storage/folders/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/storage/folders/{id}");
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

`DELETE /folders/{id}`

*delete a folder*

delete a folder

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer(string)(string)(string)(string)(string)(string)(string)(string)(string)|true|ID of the resource to return
permanent|query|boolean|false|Should resource be deleted permanently
recursive|query|boolean|false|Folders will be deleted even if folders are not empty


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|Folder has been marked for deletion|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None
default|Default|No description|None

<aside class="success">
This operation does not require authentication
</aside>

## copyFolder

> Code samples

```shell
# You can also use wget
curl -X POST https://api.apideck.com/storage/folders/{id}/copy \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
POST https://api.apideck.com/storage/folders/{id}/copy HTTP/1.1
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
  url: 'https://api.apideck.com/storage/folders/{id}/copy',
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
  "parent_id": "string",
  "name": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.apideck.com/storage/folders/{id}/copy',
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
  'Content-Type' => 'application/json',
  'Accept' => 'application/json'
}

result = RestClient.post 'https://api.apideck.com/storage/folders/{id}/copy',
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

r = requests.post('https://api.apideck.com/storage/folders/{id}/copy', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/storage/folders/{id}/copy");
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

`POST /folders/{id}/copy`

*Copy a folder*

Copy a folder

> Body parameter

```json
{
  "parent_id": "string",
  "name": "string"
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer(string)(string)(string)(string)(string)(string)(string)(string)(string)(string)|true|ID of the resource to return
body|body|[FolderAction](#schemafolderaction)|false|copy folder
» parent_id|body|string|false|id of the parent folder
» name|body|string|false|name of the folder


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|Folder has been copied succesfully|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|No description|None
405|[Method Not Allowed](https://tools.ietf.org/html/rfc7231#section-6.5.5)|No description|None
default|Default|No description|None

<aside class="success">
This operation does not require authentication
</aside>

## getFolderContent

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/storage/folders/{id}/contents \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/storage/folders/{id}/contents HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/storage/folders/{id}/contents',
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

fetch('https://api.apideck.com/storage/folders/{id}/contents',
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

result = RestClient.get 'https://api.apideck.com/storage/folders/{id}/contents',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/storage/folders/{id}/contents', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/storage/folders/{id}/contents");
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

`GET /folders/{id}/contents`

*Get contents of a folder*

Get contents of a folder

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer(string)(string)(string)(string)(string)(string)(string)(string)(string)(string)(string)|true|ID of the resource to return
page|query|integer(int32)|false|Page number to start from. Omitting the page parameter will return page 1
per_page|query|integer(int32)|false|Number of records to return per page. Default = 100.
recursive|query|boolean|false|return all storage resources within this folder


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|No description|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|No description|None
404|[Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4)|Not Found|None
default|Default|No description|None

<aside class="success">
This operation does not require authentication
</aside>

# Webhooks

Webhooks enable you to attach event triggers to files and folders. Event triggers monitor events on objects and notify your application when they occur. A webhook notifies your application by sending HTTP requests to a URL of your choosing.

## listWebhooks

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/storage/webhooks \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/storage/webhooks HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/storage/webhooks',
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

fetch('https://api.apideck.com/storage/webhooks',
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

result = RestClient.get 'https://api.apideck.com/storage/webhooks',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/storage/webhooks', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/storage/webhooks");
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

Get all webhooks

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
page|query|integer(int32)(int32)|false|Page number to start from. Omitting the page parameter will return page 1
per_page|query|integer(int32)(int32)|false|Number of records to return per page. Default = 100.


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|No description|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|No description|None
default|Default|No description|None

<aside class="success">
This operation does not require authentication
</aside>

## getWebhook

> Code samples

```shell
# You can also use wget
curl -X GET https://api.apideck.com/storage/webhooks/{id} \
  -H 'Accept: application/json'

```

```http
GET https://api.apideck.com/storage/webhooks/{id} HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/storage/webhooks/{id}',
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

fetch('https://api.apideck.com/storage/webhooks/{id}',
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

result = RestClient.get 'https://api.apideck.com/storage/webhooks/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.get('https://api.apideck.com/storage/webhooks/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/storage/webhooks/{id}");
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

*Get a webhook*

Get a webhook

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer(string)(string)(string)(string)(string)(string)(string)(string)(string)(string)(string)(string)|true|ID of the resource to return


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|No description|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|No description|None
default|Default|No description|None

<aside class="success">
This operation does not require authentication
</aside>

## updateWebhook

> Code samples

```shell
# You can also use wget
curl -X PUT https://api.apideck.com/storage/webhooks/{id} \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'

```

```http
PUT https://api.apideck.com/storage/webhooks/{id} HTTP/1.1
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
  url: 'https://api.apideck.com/storage/webhooks/{id}',
  method: 'put',

  headers: headers,
  success: function(data) {
    console.log(JSON.stringify(data));
  }
})
```

```javascript--nodejs
const request = require('node-fetch');
const inputBody = '{
  "target_id": "string",
  "triggers": [
    {}
  ],
  "address": "string"
}';
const headers = {
  'Content-Type':'application/json',
  'Accept':'application/json'

};

fetch('https://api.apideck.com/storage/webhooks/{id}',
{
  method: 'PUT',
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

result = RestClient.put 'https://api.apideck.com/storage/webhooks/{id}',
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

r = requests.put('https://api.apideck.com/storage/webhooks/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/storage/webhooks/{id}");
HttpURLConnection con = (HttpURLConnection) obj.openConnection();
con.setRequestMethod("PUT");
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

`PUT /webhooks/{id}`

*Update a webhook*

Update a webhook

> Body parameter

```json
{
  "target_id": "string",
  "triggers": [
    "FILE_UPLOADED"
  ],
  "address": "string"
}
```
### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer(string)(string)(string)(string)(string)(string)(string)(string)(string)(string)(string)(string)(string)|true|ID of the resource to return
body|body|[updateWebhook](#schema+updatewebhook)|false|update webhook
» target_id|body|string|false|The ID of the target object (file or folder)
» address|body|string|false|The notification URL of the webhook. The notification URL is the URL used by Apideck to send a notification when the webhook is triggered.
» triggers|body|[[Event](#schemaevent)]|false|No description


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
200|[OK](https://tools.ietf.org/html/rfc7231#section-6.3.1)|No description|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|No description|None
default|Default|No description|None

<aside class="success">
This operation does not require authentication
</aside>

## deleteWebhook

> Code samples

```shell
# You can also use wget
curl -X DELETE https://api.apideck.com/storage/webhooks/{id} \
  -H 'Accept: application/json'

```

```http
DELETE https://api.apideck.com/storage/webhooks/{id} HTTP/1.1
Host: api.apideck.com

Accept: application/json

```

```javascript
var headers = {
  'Accept':'application/json'

};

$.ajax({
  url: 'https://api.apideck.com/storage/webhooks/{id}',
  method: 'delete',

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

fetch('https://api.apideck.com/storage/webhooks/{id}',
{
  method: 'DELETE',

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

result = RestClient.delete 'https://api.apideck.com/storage/webhooks/{id}',
  params: {
  }, headers: headers

p JSON.parse(result)
```

```python
import requests
headers = {
  'Accept': 'application/json'
}

r = requests.delete('https://api.apideck.com/storage/webhooks/{id}', params={

}, headers = headers)

print r.json()
```

```java
URL obj = new URL("https://api.apideck.com/storage/webhooks/{id}");
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

*Delete a webhook*

Delete a webhook

### Parameters

Parameter|In|Type|Required|Description
---|---|---|---|---|
id|path|integer(string)(string)(string)(string)(string)(string)(string)(string)(string)(string)(string)(string)(string)(string)|true|ID of the resource to return


### Responses

Status|Meaning|Description|Schema
---|---|---|---|
202|[Accepted](https://tools.ietf.org/html/rfc7231#section-6.3.3)|Webhook has been marked for deletion|None
400|[Bad Request](https://tools.ietf.org/html/rfc7231#section-6.5.1)|No description|None
403|[Forbidden](https://tools.ietf.org/html/rfc7231#section-6.5.3)|No description|None
default|Default|No description|None

<aside class="success">
This operation does not require authentication
</aside>

# Schemas

## Account

<a name="schemaaccount"></a>

```json
{
  "id": "string",
  "type": "team",
  "email": "user@example.com",
  "name": "string",
  "role": {
    "name": "owner"
  },
  "disabled": true
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|string|false|No description
type|string|false|No description
email|string(email)|false|No description
name|string|false|No description
role|[Role](#schemarole)|false|No description
» name|string|false|No description
disabled|boolean|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
type|team|
type|user|
» name|owner|
» name|previewer|
» name|reader|
» name|writer|


## StorageResource

<a name="schemastorageresource"></a>

```json
{
  "id": "string",
  "name": "string",
  "size": 0,
  "created": "2017-09-19T20:17:12Z",
  "modified": "2017-09-19T20:17:12Z",
  "account": {
    "id": "string",
    "type": "team",
    "email": "user@example.com",
    "name": "string",
    "role": {
      "name": "owner"
    },
    "disabled": true
  },
  "path": "string",
  "parent": {
    "id": "string"
  },
  "kind": "string",
  "ancestors": [
    {}
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|string|false|No description
name|string|false|No description
size|integer(int64)|false|No description
created|string(date-time)|false|No description
modified|string(date-time)|false|No description
account|[Account](#schemaaccount)|false|No description
» id|string|false|No description
» type|string|false|No description
» email|string(email)|false|No description
» name|string|false|No description
» role|[Role](#schemarole)|false|No description
»» name|string|false|No description
» disabled|boolean|false|No description
path|string|false|No description
parent|[Parent](#schemaparent)|false|No description
» id|string|false|No description
kind|string|false|No description
ancestors|[[Folder](#schemafolder)]|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
» type|team|
» type|user|
»» name|owner|
»» name|previewer|
»» name|reader|
»» name|writer|


## Folder

<a name="schemafolder"></a>

```json
{
  "id": "e2ed6b5c-b74a-4d02-9828-dddd640e7c73",
  "name": "FolderName",
  "size": 123456,
  "created": "2017-09-19T20:17:12Z",
  "modified": "2017-09-19T20:17:12Z",
  "account": {
    "id": "string",
    "type": "team",
    "email": "user@example.com",
    "name": "string",
    "role": {
      "name": "owner"
    },
    "disabled": true
  },
  "path": "string",
  "parent": {
    "id": "string"
  },
  "kind": "folder",
  "ancestors": [
    {}
  ],
  "canCreateFolders": true,
  "canUploadFolders": true
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|string|false|No description
name|string|false|No description
size|integer(int64)|false|No description
created|string(date-time)|false|No description
modified|string(date-time)|false|No description
account|[Account](#schemaaccount)|false|No description
» id|string|false|No description
» type|string|false|No description
» email|string(email)|false|No description
» name|string|false|No description
» role|[Role](#schemarole)|false|No description
»» name|string|false|No description
» disabled|boolean|false|No description
path|string|false|No description
parent|[Parent](#schemaparent)|false|No description
» id|string|false|No description
kind|string|false|No description
canCreateFolders|boolean|false|No description
canUploadFolders|boolean|false|No description
ancestors|[[Folder](#schemafolder)]|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
» type|team|
» type|user|
»» name|owner|
»» name|previewer|
»» name|reader|
»» name|writer|


## File

<a name="schemafile"></a>

```json
{
  "kind": "string",
  "mimeType": "string",
  "owner": {
    "id": "string",
    "type": "team",
    "email": "user@example.com",
    "name": "string",
    "role": {
      "name": "owner"
    },
    "disabled": true
  },
  "creator": {
    "id": "string",
    "type": "team",
    "email": "user@example.com",
    "name": "string",
    "role": {
      "name": "owner"
    },
    "disabled": true
  },
  "lastModifier": {
    "id": "string",
    "type": "team",
    "email": "user@example.com",
    "name": "string",
    "role": {
      "name": "owner"
    },
    "disabled": true
  }
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
kind|string|false|No description
mimeType|string|false|No description
owner|[Account](#schemaaccount)|false|No description
» id|string|false|No description
» type|string|false|No description
» email|string(email)|false|No description
» name|string|false|No description
» role|[Role](#schemarole)|false|No description
»» name|string|false|No description
» disabled|boolean|false|No description
creator|[Account](#schemaaccount)|false|No description
» id|string|false|No description
» type|string|false|No description
» email|string(email)|false|No description
» name|string|false|No description
» role|[Role](#schemarole)|false|No description
»» name|string|false|No description
» disabled|boolean|false|No description
lastModifier|[Account](#schemaaccount)|false|No description
» id|string|false|No description
» type|string|false|No description
» email|string(email)|false|No description
» name|string|false|No description
» role|[Role](#schemarole)|false|No description
»» name|string|false|No description
» disabled|boolean|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
» type|team|
» type|user|
»» name|owner|
»» name|previewer|
»» name|reader|
»» name|writer|
» type|team|
» type|user|
»» name|owner|
»» name|previewer|
»» name|reader|
»» name|writer|
» type|team|
» type|user|
»» name|owner|
»» name|previewer|
»» name|reader|
»» name|writer|


## Parent

<a name="schemaparent"></a>

```json
{
  "id": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|string|false|No description



## Role

<a name="schemarole"></a>

```json
{
  "name": "owner"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
name|string|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
name|owner|
name|previewer|
name|reader|
name|writer|


## CreateFolderInput

<a name="schemacreatefolderinput"></a>

```json
{
  "parentId": "string",
  "name": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
parentId|string|false|No description
name|string|false|No description



## FolderContent

<a name="schemafoldercontent"></a>

```json
{
  "count": 0,
  "page": 0,
  "nextPage": 0,
  "objects": [
    {}
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
count|integer|false|No description
page|integer|false|No description
nextPage|integer|false|No description
objects|[Unknown]|false|No description



## Webhook

<a name="schemawebhook"></a>

```json
{
  "id": "string",
  "target_id": "string",
  "created_by": "string",
  "created": "2017-09-19T20:17:12Z",
  "address": "string",
  "triggers": [
    "FILE_UPLOADED"
  ]
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|string|false|No description
target_id|string|false|ID of the target of the webhook. Target can be a file or folder that the webhook monitors 
created_by|string|false|ID of the user that created the webhook 
created|string(date-time)|false|An RFC-3339 timestamp identifying the time that the webhook was created 
address|string|false|The notification URL of the webhook. The notification URL is the URL used by Apideck to send a notification when the webhook is triggered. 
triggers|[string]|false|No description


#### Enumerated Values

|Property|Value|
|---|---|
triggers|FILE_UPLOADED|
triggers|FILE_MOVED|
triggers|FILE_RENAMED|
triggers|FILE_DELETED|
triggers|FILE_COPIED|
triggers|FILE_UPDATED|
triggers|FILE_DOWNLOADED|
triggers|FOLDER_CREATED|
triggers|FOLDER_MOVED|
triggers|FOLDER_RENAMED|
triggers|FOLDER_DELETED|
triggers|FOLDER_COPIED|


## Notification

<a name="schemanotification"></a>

```json
{
  "id": "string",
  "created_by": {
    "id": "string",
    "type": "team",
    "email": "user@example.com",
    "name": "string",
    "role": {
      "name": "owner"
    },
    "disabled": true
  },
  "created": "2017-09-19T20:17:12Z",
  "event": "FILE_UPLOADED",
  "source": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
id|string|false|id of the notification
created_by|[Account](#schemaaccount)|false|No description
» id|string|false|No description
» type|string|false|No description
» email|string(email)|false|No description
» name|string|false|No description
» role|[Role](#schemarole)|false|No description
»» name|string|false|No description
» disabled|boolean|false|No description
created|string(date-time)|false|when was did this event occured
event|string|false|No description
source|string|false|which event has triggered this notification


#### Enumerated Values

|Property|Value|
|---|---|
» type|team|
» type|user|
»» name|owner|
»» name|previewer|
»» name|reader|
»» name|writer|
event|FILE_UPLOADED|
event|FILE_MOVED|
event|FILE_RENAMED|
event|FILE_DELETED|
event|FILE_COPIED|
event|FILE_UPDATED|
event|FILE_DOWNLOADED|
event|FOLDER_CREATED|
event|FOLDER_MOVED|
event|FOLDER_RENAMED|
event|FOLDER_DELETED|
event|FOLDER_COPIED|


## Event

<a name="schemaevent"></a>

```json
"FILE_UPLOADED" 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
simple|string|false|No description



## FileAction

<a name="schemafileaction"></a>

```json
{
  "parent_id": "string",
  "name": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
parent_id|string|false|id of the parent folder
name|string|false|name of the file



## FolderAction

<a name="schemafolderaction"></a>

```json
{
  "parent_id": "string",
  "name": "string"
} 
```

### Properties

Name|Type|Required|Description
---|---|---|---|
parent_id|string|false|id of the parent folder
name|string|false|name of the folder



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





