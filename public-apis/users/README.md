ILLA Supervisor Backend Users APIs
------------------------------------------

# Index

- [Index](#index)
- [Update Password](#update-password)
  - [Desc](#desc)
  - [API Endpoint](#api-endpoint)
  - [Request Body](#request-body)
  - [Response](#response)
- [Update Nickname](#update-nickname)
  - [Desc](#desc-1)
  - [API Endpoint](#api-endpoint-1)
  - [Request Body](#request-body-1)
  - [Response](#response-1)
- [Update Avatar](#update-avatar)
  - [Desc](#desc-2)
  - [API Endpoint](#api-endpoint-2)
  - [Request Body](#request-body-2)
  - [Response](#response-2)
- [Get User Avatar PreSigned Put URL](#get-user-avatar-presigned-put-url)
  - [Desc](#desc-3)
  - [API Endpoint](#api-endpoint-3)
  - [Request Body](#request-body-3)
  - [Response](#response-3)
- [Update Language](#update-language)
  - [Desc](#desc-4)
  - [API Endpoint](#api-endpoint-4)
  - [Request Body](#request-body-4)
  - [Response](#response-4)
- [Update Tutorial Viewed](#update-tutorial-viewed)
  - [Desc](#desc-5)
  - [API Endpoint](#api-endpoint-5)
  - [Request Body](#request-body-5)
  - [Response](#response-5)
- [Get Users](#get-users)
    - [Desc](#desc-6)
  - [API Endpoint](#api-endpoint-6)
  - [Request Body](#request-body-6)
  - [Response](#response-6)
- [Delete User](#delete-user)
  - [Desc](#desc-7)
  - [API Endpoint](#api-endpoint-7)
  - [Request Body](#request-body-7)
  - [Response](#response-7)
- [logout](#logout)
  - [Desc](#desc-8)
  - [API Endpoint](#api-endpoint-8)
  - [Request Body](#request-body-8)
  - [Response](#response-8)


# Update Password

## Desc

Update user's password.

## API Endpoint

```API Endpoint
PATCH  /api/v1/users/password
```

## Request Body

```JSON
{
  "currentPassword": "old_password",
  "newPassword": "new_password"
}
```

## Response

```JSON
none
```

# Update Nickname 

## Desc

Update user's nickname.


## API Endpoint

```API Endpoint
PATCH  /api/v1/users/nickname
```

## Request Body

```JSON
{
    "nickname": "yournickname"
}
```

## Response

```JSON
none
```

# Update Avatar 

## Desc

Update user's avatar.

## API Endpoint

```API Endpoint
PATCH  /api/v1/users/avatar
```

## Request Body

```JSON
{
    "avatar": "https://cdn.illacloud.com/avatar.png"
}
```

## Response

```JSON
none
```

# Get User Avatar PreSigned Put URL

## Desc

Get the upload address of the user's avatar.

## API Endpoint

```API Endpoint
GET  /api/v1/users/avatar/uploadAddress/fileName/:fileName
```

## Request Body

```JSON
none
```
## Response

```JSON
{
    "uploadAddress":"http://api.com/xxxxxxx"
}
```


# Update Language

## Desc

Update user language settings.

## API Endpoint

```API Endpoint
PATCH  /api/v1/users/language
```

## Request Body

```JSON
{
    "language": "en-US"
}
```

## Response

```JSON
none
```

# Update Tutorial Viewed

## Desc

Update whether the user has seen the tutorial.

## API Endpoint

```API Endpoint
PATCH  /api/v1/users/tutorialViewed
```

## Request Body

```JSON
{
    "isTutorialViewed": true
}
```

## Response

```JSON
// HTTP 200
none
```

# Get Users

### Desc

Get current user information, no parameter required, will be based on the currently logged in user's TOKEN to resolve the user ID, and then based on the ID to get the user information.

## API Endpoint

```API Endpoint
GET  /api/v1/users
```

## Request Body

```JSON
none
```

## Response

```JSON
{
    "userID": "1",
    "uid": "uuid",
    "nickname": "your_nickname",
    "avatar": "https://cdn.illasoft.com/userID/avatar.png",
    "email": "youremail@domain.com",
    "language": "en-US",
    "isTutorialViewed": false,
    "isPasswordSetted": true,
    "createdAt": "2023-03-03 15:54:17.486328",
    "updatedAt": "2023-03-03 15:54:17.486328"
}
```

# Delete User

## Desc

User deletes himself/herself
If the user is an owner, he/she must transfer all his/her owners before deleting himself/herself.

## API Endpoint

```API Endpoint
DELETE  /api/v1/users
```

## Request Body

```JSON
none
```

## Response

```JSON
// HTTP 200
// or
// HTTP 500
```

# logout

## Desc

logout.

## API Endpoint

```API Endpoint
POST  /api/v1/users/logout
```

## Request Body

```JSON
// none
```

## Response

```JSON
// HTTP 200
```

