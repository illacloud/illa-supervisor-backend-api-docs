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

For generate invite link. 

## API Endpoint

```API Endpoint
GET  /api/v1/teams/:teamID/inviteLink/userRole/:userRole
```

- userRole
  - see [User Role](#user-role)


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

Re-generate the invitation link
Note that only the team owner and admin have this privilege, other users will get an illegal request.

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

For disable the invite link.

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

For enable the invite link.

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

Send invitation links based on emails.

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

Join the team by following the invitation link.
This interface is only available if you are already logged in.

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

Modify roles for users based on email invitations.

## Tips

- After the invitation email has been sent, a user has been created in the team_membrs table of the database, and the user's role can be changed using the "Change Team Members Role" [# Change TeamMembers Role](. /team_members/README.md) API.



# Get Share App Link

## Desc

Get the Share APP link, which has an appID more than the Invite to join link to facilitate the jump.

## API Endpoint

```API Endpoint
GET  /api/v1/teams/:teamID/shareAppLink/userRole/:userRole/apps/:appID/redirectPage/:redirectPage
```

- userRole
  - see [User Role](#user-role)
- appID
  - APP ID in string.
- redirectPage
  - see [Redirect Page](#redirect-page)

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

Re-generate the invitation link.
Note that only the team owner and admin have this privilege, other users will get an illegal request.

## API Endpoint

```API Endpoint
GET  /api/v1/teams/:teamID/newShareAppLink/userRole/:userRole/apps/:appID/redirectPage/:redirectPage
```

- userRole
  - see [User Role](#user-role)
- appID
  - APP ID in string.
- redirectPage
  - see [Redirect Page](#redirect-page)
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

Share App by Email.

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

The link in the email has an email and appID, so it's easy to sign up and jump afterward.

```
https://cloud.illacloud.com/?inviteToken=YWU0MmFjMjctODc2NC00OWEyLWExZjUtNDRhNzBkN2I0OWM1&email=youremail@outlook.com&appID=xxxxxxxx
```
