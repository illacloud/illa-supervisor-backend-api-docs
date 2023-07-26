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

更新用户密码

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

更新用户昵称

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

更新用户头像

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

获取用户头像的上传地址

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

更新用户语言设置

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

更新用户是否看过了教程

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

获取当前用户信息, 无需参数, 会根据当前登录用户的 TOKEN 解析出用户 ID, 然后根据 ID 获取用户信息.

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

用户注销自己
如果用户是owner, 必须把自己所有的owner全都转移出去后, 才能删除自己

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

登出

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

