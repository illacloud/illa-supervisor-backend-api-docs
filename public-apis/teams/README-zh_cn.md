ILLA Supervisor Backend Team APIs
------------------------------------------

# Index

- [Index](#index)
- [Get My Teams](#get-my-teams)
  - [Desc](#desc)
  - [API Endpoint](#api-endpoint)
  - [Request Body](#request-body)
  - [Response](#response)
- [Update Team Config](#update-team-config)
  - [Desc](#desc-1)
  - [API Endpoint](#api-endpoint-1)
  - [Request Body](#request-body-1)
  - [Response](#response-1)
- [Update Team Permission Config](#update-team-permission-config)
  - [Desc](#desc-2)
  - [API Endpoint](#api-endpoint-2)
  - [Request Body](#request-body-2)
  - [Response](#response-2)


# Get My Teams 

## Desc

- 获取我加入的团队的列表, 默认按照加入团队的时间顺序倒排. 注意该接口会根据用户登录 token 鉴权, 因此用户拿不到自己未加入的 Team 的信息.会显示无权限.
- 增加了 personal config. 用于表示用户在团队内得个人设置.
- 
## API Endpoint

```API Endpoint
GET  /api/v1/teams/my
```

## Request Body

```JSON
none
```

## Response

```JSON
[
    {
        "id": "ILAfx4p1C7es",
        "uid": "0af23d3f-ae32-4a70-9302-2e8025c30f14",
        "name": "t2",
        "identifier": "t2",
        "icon": "https://illa-cloud-storage.illacloud.com/system-assets/images/people.png",
        "myRole": 1, // root
        "teamMemberID": "ILAfx4p1C7eG",
        "teamMemberPermission": {
            "config": 0
        },
        "permission": {
            "allowEditorInvite": true,
            "allowViewerInvite": true,
            "allowEditorManageTeamMember": true,
            "allowViewerManageTeamMember": true,
            "inviteLinkEnabled": true
        }
        }
    },
    {
        "id":"ILAfx4p1C7eR",
        "uid":"uuid",
        "name":"team_name_b",
        "identifier":"team_identifier",
        "icon":"http://teamcion.com/icon.png",
        "myRole": 4 // viewer
        "teamMemberID": "ILAfx4p1C7X3",
        "teamMemberPermission": {
            "config": 0 // 用户自己在团队中的 permission 设置
        },
        "permission" { // team 的全局 permission 设置
            "allowEditorInvite": true,
            "allowViewerInvite": true,
            "allowEditorManageTeamMember": true,
            "allowViewerManageTeamMember": true,
            "inviteLinkEnabled": true
        }
    },
    ...
]
```


# Update Team Config

## Desc

更新团队设置

## API Endpoint

```API Endpoint
PATCH  /api/v1/teams/:teamID/config
```

## Request Body

```JSON
{
    "name":"team_name",
    "identifier":"team_identifier",
    "icon":"http://teamcion.com/icon.png"
}
```

## Response

```JSON
none
```

# Update Team Permission Config

## Desc

更新团队中的自定义权限设置, 目前有:  

- 允许 editor 和 viewer 邀请成员的开关.  
- 允许 editor 和 viewer 管理成员(包含在权限等级内将团队成员移出团队)的开关.
- 
未来这个权限是团队全局权限, 优先级低于 attribute 系统, 即 attribute 系统如果用户有自定义, 会覆盖这个权限(目前还没有实现)


## API Endpoint

```API Endpoint
PATCH  /api/v1/teams/:teamID/permission
```

## Request Body

```JSON
{
    "allowEditorInvite": true,
    "allowViewerInvite": true,
    "allowEditorManageTeamMember": true,
    "allowViewerManageTeamMember": true
}
```

## Response

```JSON
none
```
