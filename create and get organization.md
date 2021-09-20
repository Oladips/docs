# Create an Organization
This is a request endpoint that creates an organizaion or workspace. It requires the creators email which will need to be a valid email

AUTHORIZATIONS: 'cookieAuth' or 'bearerAuth'

##  End-point
<details>
<summary> POST /organizations
 </summary>
Zuri Chat Core API:
https://api.zuri.chat/organizations
</details>
| **REQUEST BODY SCHEMA:** | application/json |
| ----------- | ------------ |
| creator_email| string|


## Request Sample
How requests are made.

**Content type** <br> application/json
```
"url": "http://api.zuri.chat/organizations/creator_email"
```

 ## Responses:
 ### **201**:  Successfully created the resource <br>

```
RESPONSE SCHEMA: application/json

code required       integer <int32>
message required    string
data                object
```

## Example <br>
**Content type** <br> application/json
```sh
  {
  "code": 201,
  "message": "string",
  "data": {
    "InsertedID": "6137d69b21d3c78fc9a84bdf"
    }
  }
```
For 4xx and 5xx the integer code error and string message will be displayed.


# Get an organization using the Organizarion Id
This is a request endpoint that gets an organizaion or workspace detail. It requires the organization id which was generated when the organization was created.

## AUTHORIZATIONS: 'cookieAuth' or 'bearerAuth'

### End-point
<details>
<summary> GET/organizations/{organization_id}
 </summary>
Zuri Chat Core API: 
https://api.zuri.chat/organizations/{organization_id}

</details>
| **PATH PARAMETER:** | application/json |
| ----------- | ------------ |
| organization_id required| string|
| Example :| 6137d69b21d3c78fc9a84bdf |
| | |

### REQUEST SAMPLE
How requests are made

**Content type** <br> application/json
```
organization_id: 6137d69b21d3c78fc9a84bdf

"url": 'https://api.zuri.chat/organizations/6137d69b21d3c78fc9a84bdf'
```
 ## Responses:
 ### **200:**  Successfully retrieve the resource
 ```
RESPONSE SCHEMA: application/json

code required       integer <int32>
message required    string
data                object(Organization)
```
## Example <br>
**Content type** <br> application/json

```sh
  {
  "code": 200,
  "message": "string",
  "data": {
    "_id": "6137d69b21d3c78fc9a84bdf",
    "name": "HNG",
    "creator_email": "hng@email.com",
    "creator_id": "6137d69b21d3c78fc9a84bdf",
    "logo_url": "hng.zuri.chat",
    "created_at": "2021-09-14",
    "deleted_at": "2021-09-14",
    "organization_settings": {
      "global_settings": {
        "allow_user_add_plugins": true,
        "allow_only_admin_invite": true
      },
      "plugin_settings": {
        "chess_plugin": {
          "allow_in_every_channel": false
        }
      }
    }
  }
}
```
For 4xx and 5xx the integer code error and string message will be displayed.

## Standard Error Responses 
The Authentication API may return the following HTTP Status Codes:

---

### **400** Bad Request, e.g wrong user id <br>

```
RESPONSE SCHEMA: application/json

code required      integer <int32> 
message required   string

 ```


### **401** Access token is missing or invalid <br>

```
 RESPONSE SCHEMA:   application/json

code required        integer <int32>
message required     string


```

### **500** Internal server error occured during operation

```

RESPONSE SCHEMA:     application/json

code required         integer <int32>
message required      string

```