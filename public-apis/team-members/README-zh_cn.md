ILLA Supervisor Backend TeamMembers APIs
------------------------------------------

# Index
- [Index](#index)
- [Consts](#consts)
  - [User Role In Team](#user-role-in-team)
  - [User Status In Team](#user-status-in-team)
- [Get All TeamMembers By TeamID](#get-all-teammembers-by-teamid)
  - [Desc](#desc)
  - [API Endpoint](#api-endpoint)
  - [Request Body](#request-body)
  - [Response](#response)
- [Get Team User By TeamID userID](#get-team-user-by-teamid-userid)
  - [Desc](#desc-1)
  - [API Endpoint](#api-endpoint-1)
  - [Request Body](#request-body-1)
  - [Response](#response-1)
- [Change TeamMembers Role](#change-teammembers-role)
  - [API Endpoint](#api-endpoint-2)
  - [Request Body](#request-body-2)
  - [Response](#response-2)
- [Config Invite Link](#config-invite-link)
  - [API Endpoint](#api-endpoint-3)
  - [Request Body](#request-body-3)
  - [Response](#response-3)
- [Change TeamMembers Permission](#change-teammembers-permission)
  - [API Endpoint](#api-endpoint-4)
  - [Request Body](#request-body-4)
  - [Response](#response-4)
- [Change TeamMembers Config](#change-teammembers-config)
  - [Desc](#desc-2)
  - [API Endpoint](#api-endpoint-5)
  - [Request Body](#request-body-5)
  - [Response](#response-5)
- [Remove TeamMembers](#remove-teammembers)
  - [Desd](#desd)
  - [API Endpoint](#api-endpoint-6)
  - [Request Body](#request-body-6)
  - [Response](#response-6)


# Consts

## User Role In Team

- USER_ROLE_OWNER = 1
- USER_ROLE_ADMIN = 2
- USER_ROLE_EDITOR = 3
- USER_ROLE_VIEWER = 4

## User Status In Team

- STATUS_OK = 1 (正常用户)
- STATUS_PENDING = 2 (已发出邀请, 还未加入Team)


# Get All TeamMembers By TeamID

## Desc

获取用团队中所有成员的信息. 该返回结构耦合了 user 表和 team_members 表的用户相关的可展示字段. 
包括这些用户在团队中的角色 (userRole) 和受邀请状态 (userStatus).

## API Endpoint

```API Endpoint
GET  /api/v1/teams/:teamID/members
```

## Request Body

```JSON
none
```

## Response

```JSON
[
    {
        "userID": "1",
        "nickname": "your_nickname",
        "email": "youremail@domain.com",
        "avatar": "https://cdn.illacloud.com/team/1/user/12/avatar.png",
        "userRole": 1,   // 用户在团队中的角色
        "userStatus": 1, // 用户在团队中的 status
        "permission": { // 保留字段, 该字段为该用户在这个团队中的 permission
            "reserved": "暂时保留该字段"
        },
        "createdAt": "ISO-8601 timestamp",
        "updatedAt": "ISO-8601 timestamp",
    },
    {
        "userID": "2",
        "nickname": "your_nickname",
        "email": "youremail@domain.com",
        "avatar": "https://cdn.illacloud.com/team/1/user/12/avatar.png",
        "userRole": 2, 
        "userStatus": 2, // 用户在团队中的 status
        "permission": { // 保留字段, 该字段为该用户在这个团队中的 permission
            "reserved": "暂时保留该字段"
        },
        "createdAt": "ISO-8601 timestamp",
        "updatedAt": "ISO-8601 timestamp",
    },
    ...
]
```

# Get Team User By TeamID userID

## Desc

用户获取用户在团队中的权限信息. 该返回结构耦合了 user 表和 team_members 表的用户相关的可展示字段.

## API Endpoint

```API Endpoint
GET  /api/v1/teams/:teamID/users/:targetUserID
```

## Request Body

```JSON
none
```

## Response

```JSON
[
    {
        "userID": "1",
        "uid": "uuidxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
        "nickname": "your_nickname",
        "email": "youremail@domain.com",
        "avatar": "https://cdn.illacloud.com/team/1/user/12/avatar.png",
        "language": "en-US",
        "isSubscribed": false,
        "userRole": 1,   // 用户在团队中的角色
        "userStatus": 1, // 用户在团队中的 status
        "permission": { // 保留字段, 该字段为该用户在这个团队中的 permission
            "reserved": "暂时保留该字段"
        },
        "createdAt": "ISO-8601 timestamp",
        "updatedAt": "ISO-8601 timestamp",
    }
]
```


# Change TeamMembers Role

注意这个如果当前用户是 owner, 将其他用户设置为 owner, 会导致自己失去 owner 权限. 客户端应给与相应提示.
即, 这个接口可以用作 transfer owner.
当然这个接口有 attribute 检测, 不可以越级修改 role.

## API Endpoint

```API Endpoint
PATCH  /api/v1/teams/:teamID/users/:targetUserID/role
```

## Request Body

```JSON
{
    "userRole": 2
}
```

## Response

```JSON
none
```

# Config Invite Link

配置 team 是否可以使用链接邀请用户

## API Endpoint

```API Endpoint
PATCH  /api/v1/teams/:teamID/configInviteLink
```

## Request Body

```JSON
{
    "inviteLinkEnabled": true
}
```

## Response

```JSON
// HTTP 200
// or 
// HTTP 400
```


# Change TeamMembers Permission


## API Endpoint

```API Endpoint
PATCH  /api/v1/teams/:teamID/users/:userID/permission
```

## Request Body

```JSON
{
    "permission": {
        预留字段, 暂时还没有
    }
}
```

## Response

```JSON
// HTTP 200
// or 
// HTTP 400
```

# Change TeamMembers Config

## Desc

- 修改团队成员的私人个性化设置和专属配置, 比如 owner 是否看过 license 到期的提醒.

## API Endpoint

```API Endpoint
PATCH  /api/v1/teams/:teamID/teamMembers/config
```

## Request Body

```JSON
{
    "teamLicenseSubscribeExpiredPopupShowed": false, // 是否展示过团队license 弹窗, 该属性只对 owner 角色生效
    "teamLicenseSubscribeExpiredBannerShowed": false, // 是否展示过团队 license banner, 该属性只对 owner 角色生效
}
```

## Response

```JSON
// HTTP 200
// or 
// HTTP 400
```


# Remove TeamMembers

## Desd 

移除团队成员
也可用于自己离开团队

## API Endpoint

```API Endpoint
DELETE  /api/v1/teams/:teamID/users/:userID
```

## Request Body

```JSON
none
```

## Response

```JSON
none
```
