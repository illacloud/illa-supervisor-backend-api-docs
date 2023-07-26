ILLA Supervisor Backend Authorization APIs
------------------------------------------

# Index

- [Index](#index)
- [Verification](#verification)
  - [Desc](#desc)
  - [API Endpoint](#api-endpoint)
  - [Request Body](#request-body)
  - [Response](#response)
- [Signup](#signup)
  - [Desc](#desc-1)
  - [API Endpoint](#api-endpoint-1)
  - [Request Body](#request-body-1)
  - [Response](#response-1)
- [Signin](#signin)
  - [Desc](#desc-2)
  - [API Endpoint](#api-endpoint-2)
  - [Request Body](#request-body-2)
  - [Response](#response-2)
- [Forget Password](#forget-password)
  - [Desc](#desc-3)
  - [API Endpoint](#api-endpoint-3)
  - [Request Body](#request-body-3)
  - [Response](#response-3)


# Verification

## Desc

获取 verification token

## API Endpoint

```API Endpoint
POST  /api/v1/auth/verification
```

## Request Body

```JSON
{
    "email": "youremail@domain.com",
    "usage": "signup"
}
```

## Response

```JSON
{
    "verificationToken":"tokenxxxxxxxxxxxxxx"
}
```

# Signup

## Desc

注册

## API Endpoint

```API Endpoint
POST  /api/v1/auth/signup
```

## Request Body

```JSON
{
  "nickname": "your_nickname",
  "email": "youremail@domain.com",
  "verificationCode": "000000", // leave this empty for to be invited by the email 
  "inviteToken": "invite_token_digiest", // leave this empty for not to be invited by the link or email
  "password": "passwordpassword",
  "verificationToken": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx",
  "language": "en-US",
  "isSubscribed": false
}
```

## Response

```JSON
none
```


# Signin

## Desc

登录

## API Endpoint

```API Endpoint
POST  /api/v1/auth/signin
```

## Request Body

```JSON
{
    "email": "youremail@domain.com",
    "password": "yourpassword"
}
```

## Response

```JSON
{
    "userID": "1",
    "nickname": "your_nickname",
    "avatar": "https://cnd.illasoft.com/avatar01-png",
    "email": "youremail@domain.com",
    "language": "en-US"
}
```


# Forget Password

## Desc

忘记密码

## API Endpoint

```API Endpoint
POST  /api/v1/auth/forgetPassword
```

## Request Body

```JSON
{
  "email": "youremail@domain.com",
  "verificationCode": "000000",
  "newPassword": "yourpassword",
  "verificationToken": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
}
```

## Response

```JSON
// HTTP 200
```


