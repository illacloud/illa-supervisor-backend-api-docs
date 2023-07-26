ILLA Supervisor Backend DataControl APIs
----------------------------------------


# Desc

该接口用于获取 supervisor 的内部数据.
注意, 所有请求的请求头均需要带 RequestToken 字段, 由请求内其他字段+内部 rotor_token MD5 生成.


# Index

- [Desc](#desc)
- [Index](#index)
- [Consts](#consts)
- [Get Tatget User Info](#get-tatget-user-info)
  - [Desc](#desc-1)
  - [API Endpoint](#api-endpoint)
  - [Request Header](#request-header)
  - [Request Body](#request-body)
  - [Response](#response)
- [Get Tatget Users Info Multiple](#get-tatget-users-info-multiple)
  - [Desc](#desc-2)
  - [API Endpoint](#api-endpoint-1)
  - [Request Header](#request-header-1)
  - [Request Body](#request-body-1)
  - [Response](#response-1)


# Consts


# Get Tatget User Info

## Desc

获取目标用户信息

## API Endpoint

```API Endpoint
GET  /api/v1/dataControl/users/:targetUserID
```

## Request Header

```
RequestToken: bash64(md5(sort($targetUserID)))
```

## Request Body

```JSON
// hone
```

## Response

```JSON
{
    "userID": "ILAdx4p1C7f2",
    "userUID": "70776ddc-3300-41ca-81c9-9fb0e19963a3",
    "nickname": "your_nickname",
    "avatar": "https://cdn.illasoft.com/userID/avatar.png",
    "email": "youremail@domain.com",
    "language": "en-US"
}
```

# Get Tatget Users Info Multiple

## Desc

获取多个目标用户信息

## API Endpoint

```API Endpoint
GET  /api/v1/dataControl/users/multi/:targetUserIDs 
```

:targetUserIDs 格式为 {userID1},{userID2},...

## Request Header

```
RequestToken: bash64(md5(sort($targetUserIDs)))
```

## Request Body

```JSON
// hone
```

## Response

为对象, 对象的 key 为 userID (int 类型).

```JSON
{
    "users": {
        "14898": {
            "id": "ILAdx4p1C7f2",
            "uid": "70776ddc-3300-41ca-81c9-9fb0e19963a3",
            "teamMemberID": "",
            "nickname": "karminski-g",
            "email": "zhangxuhong@illasoft.com",
            "avatar": "",
            "language": "en-US",
            "isSubscribed": false,
            "created_at": "2023-03-03T15:54:17.486328Z",
            "updated_at": "2023-03-03T15:54:17.486328Z"
        },
        "14899": {
            "id": "ILAdx4p1C7f1",
            "uid": "51a53bc8-264c-4fe7-97c8-66b8bd73bbd5",
            "teamMemberID": "",
            "nickname": "karminski-g",
            "email": "karminski@outlook.com",
            "avatar": "",
            "language": "en-US",
            "isSubscribed": false,
            "created_at": "2023-04-26T13:46:35.127597Z",
            "updated_at": "2023-04-26T13:46:35.127597Z"
        }
    }
}
```

