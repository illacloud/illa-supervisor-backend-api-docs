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
- [Remove TeamMembers](#remove-teammembers)
  - [Desd](#desd)
  - [API Endpoint](#api-endpoint-5)
  - [Request Body](#request-body-5)
  - [Response](#response-5)


# Consts

## User Role In Team

- USER_ROLE_OWNER = 1
- USER_ROLE_ADMIN = 2
- USER_ROLE_EDITOR = 3
- USER_ROLE_VIEWER = 4

## User Status In Team

- STATUS_OK = 1 
- STATUS_PENDING = 2 


# Get All TeamMembers By TeamID

## Desc

Gets information about all members of the user team. The return structure couples the user table and the team_members table's user-related displayable fields. 
This includes the user's role in the team (userRole) and invited status (userStatus).

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
        "userRole": 1,   // The role of the user in the team
        "userStatus": 1, // The status of the user in the team
        "permission": { // Reserved field for the user's permission in this team.
            "reserved": ""
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
        "userStatus": 2, 
        "permission": { 
            "reserved": ""
        },
        "createdAt": "ISO-8601 timestamp",
        "updatedAt": "ISO-8601 timestamp",
    },
    ...
]
```

# Get Team User By TeamID userID

## Desc

The user gets information about the user's permissions in the team. The return structure couples the user-related displayable fields of the user and team_members tables.

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
        "userRole": 1,   
        "userStatus": 1, 
        "permission": { 
            "reserved": ""
        },
        "createdAt": "ISO-8601 timestamp",
        "updatedAt": "ISO-8601 timestamp",
    }
]
```


# Change TeamMembers Role

Note that if the current user is the owner, setting another user as the owner will cause you to lose your owner privileges. The client should prompt you accordingly.
That is, this interface can be used as a transfer owner.
Of course, this interface has attribute detection, so you can't override the role.

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

Configure whether team can invite users using links

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
        "reserved"
    }
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

Remove Team Members
Can also be used to leave the team yourself
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
