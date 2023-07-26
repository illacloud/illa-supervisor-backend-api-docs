ILLA Supervisor Backend Invite APIs
------------------------------------------

# Index

- [Index](#index)
- [Consts](#consts)
  - [Invite Record Category](#invite-record-category)
  - [Invite Record Status](#invite-record-status)
  - [User Role](#user-role)
  - [Redirect Page](#redirect-page)
- [Get Invite Link](#get-invite-link)
  - [Desc](#desc)
  - [API Endpoint](#api-endpoint)
  - [Request Body](#request-body)
  - [Response](#response)
- [Renew Invite Link](#renew-invite-link)
  - [Desc](#desc-1)
  - [API Endpoint](#api-endpoint-1)
  - [Request Body](#request-body-1)
  - [Response](#response-1)
- [Disable Invite Link](#disable-invite-link)
  - [Desc](#desc-2)
  - [API Endpoint](#api-endpoint-2)
  - [Request Body](#request-body-2)
  - [Response](#response-2)
- [Enable Invite Link](#enable-invite-link)
  - [Desc](#desc-3)
  - [API Endpoint](#api-endpoint-3)
  - [Request Body](#request-body-3)
  - [Response](#response-3)
- [Invite by Email](#invite-by-email)
  - [Desc](#desc-4)
  - [API Endpoint](#api-endpoint-4)
  - [Request Body](#request-body-4)
  - [Success Response](#success-response)
- [Join Team by Invite Link (Already logged in)](#join-team-by-invite-link-already-logged-in)
  - [Desc](#desc-5)
  - [API Endpoint](#api-endpoint-5)
  - [Request Body](#request-body-5)
  - [Response](#response-4)
- [Change invite by email user role](#change-invite-by-email-user-role)
  - [Desc](#desc-6)
  - [Tips](#tips)
- [Get Share App Link](#get-share-app-link)
  - [Desc](#desc-7)
  - [API Endpoint](#api-endpoint-6)
  - [Request Body](#request-body-6)
  - [Response](#response-5)
- [Renew Share App Link](#renew-share-app-link)
  - [Desc](#desc-8)
  - [API Endpoint](#api-endpoint-7)
  - [Request Body](#request-body-7)
  - [Response](#response-6)
- [Share App by Email](#share-app-by-email)
  - [Desc](#desc-9)
  - [API Endpoint](#api-endpoint-8)
  - [Request Body](#request-body-8)
  - [Success Response](#success-response-1)
  - [Tips](#tips-1)


# Consts

## Invite Record Category

- CATEGORY_INVITE_BY_LINK = 1
- CATEGORY_INVITE_BY_EMAIL = 2

## Invite Record Status

- INVITE_RECORD_STATUS_OK = 1
- INVITE_RECORD_STATUS_USED = 2
- INVITE_RECORD_STATUS_SUSPEND = 3


## User Role

- USER_ROLE_ANONYMOUS = -1
- USER_ROLE_OWNER     = 1
- USER_ROLE_ADMIN     = 2
- USER_ROLE_EDITOR    = 3
- USER_ROLE_VIEWER    = 4

## Redirect Page

- SHARE_LINK_REDIRECT_PAGE_EDIT = "edit"
- SHARE_LINK_REDIRECT_PAGE_RELEASE = "release"

# Get Invite Link

## Desc

获取邀请链接

## API Endpoint

```API Endpoint
GET  /api/v1/teams/:teamID/inviteLink/userRole/:userRole
```

- userRole
  - 参考 [User Role](#user-role)


## Request Body

```JSON
none
```

## Response

```JSON
{
    "inviteLink": "https://cloud-api.illacloud.com/api/v1/join/xxxxxxxxxxxxxxxxxxxxxxxxxx",
    "teamID": 12,
    "userRole": 2
}
```

# Renew Invite Link

## Desc

重新生成邀请链接
注意只有 team owner 和 admin 拥有该权限, 其他用户请求会返回非法请求.

## API Endpoint

```API Endpoint
GET  /api/v1/teams/:teamID/newInviteLink/userRole/:userRole
```

## Request Body

```JSON
none
```

## Response

```JSON
{
    "inviteLink": "https://cloud-api.illacloud.com/api/v1/join/xxxxxxxxxxxxxxxxxxxxxxxxxx",
    "teamID": 12,
    "userRole": 2
}
```

# Disable Invite Link

## Desc

关闭邀请链接

## API Endpoint

```API Endpoint
PUT  /api/v1/teams/:teamID/disableAllInviteLink
```

## Request Body

```JSON
none
```

## Response

```JSON
// HTTP 200
// or
// HTTP 400
```

# Enable Invite Link

## Desc

打开邀请链接

## API Endpoint

```API Endpoint
PUT  /api/v1/teams/:teamID/enableAllInviteLink
```

## Request Body

```JSON
none
```

## Response

```JSON
// HTTP 200
// or
// HTTP 400
```

# Invite by Email

## Desc

根据邮件发送邀请链接

## API Endpoint

```API Endpoint
POST  /api/v1/teams/:teamID/inviteByEmail
```

## Request Body

```JSON

{
    "email": "user1@email.com",
    "userRole": 2

```

## Success Response

```JSON
{
    "email": "user1@email.com",
    "teamID": 12,
    "userRole": 2,
    "emailStatus": true
}
```

# Join Team by Invite Link (Already logged in)

## Desc

根据邀请链接加入团队
该接口仅适用于已经登陆的情况

## API Endpoint

```API Endpoint
PUT  /api/v1/join/:inviteLinkHash
```

## Request Body

```JSON
none
```

## Response

```JSON
// HTTP 200
```

# Change invite by email user role


## Desc 

修改基于邮箱邀请的用户的角色

## Tips

- 已经发送邀请邮件后, 数据库 team_membrs 表其实就已经创建了用户, 这时候修改用户角色可以用"修改团队中用户角色" [# Change TeamMembers Role](../team_members/README.md) 接口来修改.



# Get Share App Link

## Desc

获取分享 APP 链接, 比邀请加入链接多了个 appID 方便跳转.

## API Endpoint

```API Endpoint
GET  /api/v1/teams/:teamID/shareAppLink/userRole/:userRole/apps/:appID/redirectPage/:redirectPage
```

- userRole
  - 参考 [User Role](##user-role)
- appID
  - APP 的 string 类型 ID
- redirectPage
  - 参考 [Redirect Page](#redirect-page)

## Request Body

```JSON
none
```

## Response

```JSON
{
    "teamID": "ILAfx4p1C7cR",
    "appID": "ILAfx4p1C7ec",
    "userRole": 3,
    "inviteLink": "https://cloud.illacloud.com/?inviteToken=ZjU2NzBiNjUtOGZjZC00Y2UzLTliYmMtNmIyYmRlNjA2Y2Vi&appID=ILAfx4p1C7ec&redirectPage=edit"
}
```

# Renew Share App Link

## Desc

重新生成邀请链接
注意只有 team owner 和 admin 拥有该权限, 其他用户请求会返回非法请求.

## API Endpoint

```API Endpoint
GET  /api/v1/teams/:teamID/newShareAppLink/userRole/:userRole/apps/:appID/redirectPage/:redirectPage
```

- userRole
  - 参考 [User Role](##user-role)
- appID
  - APP 的 string 类型 ID
- redirectPage
  - 参考 [Redirect Page](#redirect-page)

## Request Body

```JSON
none
```

## Response

```JSON
{
    "teamID": "ILAfx4p1C7cR",
    "appID": "ILAfx4p1C7ec",
    "userRole": 3,
    "inviteLink": "https://cloud.illacloud.com/?inviteToken=ZjNmYjBiMzQtYjBiMi00ZTM5LThkZTgtODFlYzZhNjViOTA5&appID=ILAfx4p1C7ec&redirectPage=release"
}
```


# Share App by Email

## Desc

根据邮件分享 App

## API Endpoint

```API Endpoint
POST  /api/v1/teams/:teamID/shareAppByEmail
```

## Request Body

```JSON

{
    "email": "user1@email.com",
    "userRole": 2,
    "appID": 81312,
    "redirectPage": "release",
}

```

## Success Response

```JSON
{
    "email": "user1@email.com",
    "teamID": 12,
    "userRole": 2,
    "appID": 81312,
    "redirectPage": "release",
    "emailStatus": true
}
```


## Tips 

邮件里的链接带 email 和 appID, 方便注册和注册后跳转:

```
https://cloud.illacloud.com/?inviteToken=YWU0MmFjMjctODc2NC00OWEyLWExZjUtNDRhNzBkN2I0OWM1&email=youremail@outlook.com&appID=xxxxxxxx
```
