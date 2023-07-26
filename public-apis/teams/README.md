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

Get the list of Teams I've joined, in reverse chronological order. Note that this interface is authenticated based on the user's login token, so the user won't be able to get information about Teams they haven't joined. It will show that you don't have permission.
  
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
            "config": 0 
        },
        "permission" { 
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

Update team config.

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

Updated customizable permissions settings in the team, which now include.  

- Switch to allow editor and viewer to invite members.  
- A switch to allow the editor and viewer to manage members (including moving team members out of the team within the permission level).
  
In the future, this permission will be a global permission for the team, with a lower priority than the attribute system, i.e. the attribute system will override this permission if the user has customized it (not yet implemented).

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
