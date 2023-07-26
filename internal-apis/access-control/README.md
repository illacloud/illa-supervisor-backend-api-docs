ILLA Supervisor Backend AccessControl APIs
------------------------------------------


# Desc

Those APIs design for authorization token verification.

Note that all requests require a RequestToken field in the request header, generated from the other fields in the request + the internal rotor_token MD5.

# Index

- [Desc](#desc)
- [Index](#index)
- [Consts](#consts)
- [Validate User Account](#validate-user-account)
  - [Desc](#desc-1)
  - [API Endpoint](#api-endpoint)
  - [Request Header](#request-header)
  - [Request Body](#request-body)
  - [Response](#response)
- [Can Access](#can-access)
  - [Desc](#desc-2)
  - [API Endpoint](#api-endpoint-1)
  - [Request Header](#request-header-1)
  - [Request Body](#request-body-1)
  - [Response](#response-1)
- [Can Manage](#can-manage)
  - [Desc](#desc-3)
  - [API Endpoint](#api-endpoint-2)
  - [Request Header](#request-header-2)
  - [Request Body](#request-body-2)
  - [Response](#response-2)
- [Can ManageSpecial](#can-managespecial)
  - [Desc](#desc-4)
  - [API Endpoint](#api-endpoint-3)
  - [Request Header](#request-header-3)
  - [Request Body](#request-body-3)
  - [Response](#response-3)
- [Can Modify](#can-modify)
  - [Desc](#desc-5)
  - [API Endpoint](#api-endpoint-4)
  - [Request Header](#request-header-4)
  - [Request Body](#request-body-4)
  - [Response](#response-4)
- [Can Delete](#can-delete)
  - [Desc](#desc-6)
  - [API Endpoint](#api-endpoint-5)
  - [Request Header](#request-header-5)
  - [Request Body](#request-body-5)
  - [Response](#response-5)


# Consts


```go
const UNIT_TYPE_TEAM        = 1 // cloud team
const UNIT_TYPE_TEAM_MEMBER = 2 // cloud team member
const UNIT_TYPE_USER        = 3 // cloud user
const UNIT_TYPE_INVITE      = 4 // cloud invite
const UNIT_TYPE_DOMAIN      = 5 // cloud domain
const UNIT_TYPE_BILLING     = 6 // cloud billing
const UNIT_TYPE_APP         = 7 // builder app
const UNIT_TYPE_COMPONENTS  = 8 // builder components
const UNIT_TYPE_RESOURCE    = 9 // resource resource
const UNIT_TYPE_ACTION      = 10 // resource action
const UNIT_TYPE_TRANSFORMER = 11 // resource transformer
const UNIT_TYPE_JOB         = 12 // hub job

```

# Validate User Account

## Desc

Check if the current user is legal.

## API Endpoint

```API Endpoint
GET  /api/v1/accessControl/account/validateResult
```

## Request Header

```
Authorization: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjoxNiwidXVpZCI6IjdlNzY0ZDBlLWM4NjAtNDNjMS04ZThjLWUwMGRkMzEyNTExMyIsInJuZCI6IjAwMDI5OSIsImlzcyI6IklMTEEiLCJleHAiOjE2NzM5NDI5Nzh9.bVAtUusjnZSipfquPKmKileXJbFfl1XoLJbRSQ-Mk2c"
RequestToken: bash64(md5(sort($Authorization)))
```

## Request Body

```JSON
// none
```

## Response

```JSON
// HTTP 200
// or
// HTTP 400
```


# Can Access


## Desc

Whether the current user can have access to the resource.


## API Endpoint

```API Endpoint
GET  /api/v1/accessControl/team/:teamID/unitType/:unitType/unitID/:unitID/attribute/canAccess/:attributeID
```

## Request Header

```
Authorization: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjoxNiwidXVpZCI6IjdlNzY0ZDBlLWM4NjAtNDNjMS04ZThjLWUwMGRkMzEyNTExMyIsInJuZCI6IjAwMDI5OSIsImlzcyI6IklMTEEiLCJleHAiOjE2NzM5NDI5Nzh9.bVAtUusjnZSipfquPKmKileXJbFfl1XoLJbRSQ-Mk2c"
RequestToken: bash64(md5(sort($Authorization+$teamID+$unitType+$unitID+$attributeID)))
```

## Request Body

```JSON
// none
```

## Response

```JSON
// HTTP 200
// or
// HTTP 400
```

# Can Manage


## Desc

Whether the current user can manage the resource

## API Endpoint

```API Endpoint
GET  /api/v1/accessControl/team/:teamID/unitType/:unitType/unitID/:unitID/attribute/canManage/:attributeID
```

## Request Header

```
Authorization: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjoxNiwidXVpZCI6IjdlNzY0ZDBlLWM4NjAtNDNjMS04ZThjLWUwMGRkMzEyNTExMyIsInJuZCI6IjAwMDI5OSIsImlzcyI6IklMTEEiLCJleHAiOjE2NzM5NDI5Nzh9.bVAtUusjnZSipfquPKmKileXJbFfl1XoLJbRSQ-Mk2c"
RequestToken: bash64(md5(sort($Authorization+$teamID+$unitType+$unitID+$attributeID)))
```

## Request Body

```JSON
// none
```

## Response

```JSON
// HTTP 200
// or
// HTTP 400
```

# Can ManageSpecial



## Desc

Whether the current user can manage special attributes of the current resource.

## API Endpoint

```API Endpoint
GET  /api/v1/accessControl/team/:teamID/unitType/:unitType/unitID/:unitID/attribute/canManageSpecial/:attributeID
```

## Request Header

```
Authorization: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjoxNiwidXVpZCI6IjdlNzY0ZDBlLWM4NjAtNDNjMS04ZThjLWUwMGRkMzEyNTExMyIsInJuZCI6IjAwMDI5OSIsImlzcyI6IklMTEEiLCJleHAiOjE2NzM5NDI5Nzh9.bVAtUusjnZSipfquPKmKileXJbFfl1XoLJbRSQ-Mk2c"
RequestToken: bash64(md5(sort($Authorization+$teamID+$unitType+$unitID+$attributeID)))
```

## Request Body

```JSON
// none
```

## Response

```JSON
// HTTP 200
// or
// HTTP 400
```


# Can Modify

## Desc

Whether the current user can modify the resource.

## API Endpoint

```API Endpoint
GET  /api/v1/accessControl/team/:teamID/unitType/:unitType/unitID/:unitID/attribute/canModify/:attributeID/from/:fromID/to/:toID
```

## Request Header

```
Authorization: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjoxNiwidXVpZCI6IjdlNzY0ZDBlLWM4NjAtNDNjMS04ZThjLWUwMGRkMzEyNTExMyIsInJuZCI6IjAwMDI5OSIsImlzcyI6IklMTEEiLCJleHAiOjE2NzM5NDI5Nzh9.bVAtUusjnZSipfquPKmKileXJbFfl1XoLJbRSQ-Mk2c"
RequestToken: bash64(md5(sort($Authorization+$teamID+$unitType+$unitID+$attributeID+$from+$to)))
```

## Request Body

```JSON
// none
```

## Response

```JSON
// HTTP 200
// or
// HTTP 400
```

# Can Delete



## Desc

Whether the current user can delete the resource.

## API Endpoint

```API Endpoint
GET  /api/v1/accessControl/team/:teamID/unitType/:unitType/unitID/:unitID/attribute/canDelete/:attributeID
```

## Request Header

```
Authorization: "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyIjoxNiwidXVpZCI6IjdlNzY0ZDBlLWM4NjAtNDNjMS04ZThjLWUwMGRkMzEyNTExMyIsInJuZCI6IjAwMDI5OSIsImlzcyI6IklMTEEiLCJleHAiOjE2NzM5NDI5Nzh9.bVAtUusjnZSipfquPKmKileXJbFfl1XoLJbRSQ-Mk2c"
RequestToken: bash64(md5(sort($Authorization+$teamID+$unitType+$unitID+$attributeID)))
```

## Request Body

```JSON
// none
```

## Response

```JSON
// HTTP 200
// or
// HTTP 400
```
