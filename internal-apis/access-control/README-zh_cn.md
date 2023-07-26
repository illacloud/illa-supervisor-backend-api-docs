ILLA Supervisor Backend AccessControl APIs
------------------------------------------


# Desc

该接口用于检查当前用户是否有访问某种资源的权限.
注意, 所有请求的请求头均需要带 RequestToken 字段, 由请求内其他字段+内部 rotor_token MD5 生成.

# Index

- [Desc](#desc)
- [Index](#index)
- [Consts](#consts)
- [Unit Types](#unit-types)
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

# Unit Types

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

检查当前用户是否合法

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
// hone
```

## Response

```JSON
// HTTP 200
// or
// HTTP 400
```

# Can Access


## Desc

当前用户是否可以访问该资源

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

当前用户是否可以管理该资源

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

当前用户是否可以管理该资源的特殊属性

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

当前用户是否可以更改该资源

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

当前用户是否可以删除该资源

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
