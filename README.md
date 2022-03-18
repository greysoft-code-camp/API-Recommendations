# API-Recommendations
> These recommendations describe how all Code Camp APIs should be implemented.

## RESPONSE AND IMPLEMENTATION
1. Validation errors should return **422** response code.
2. Authentication errors should return **401** response code.
3. All request to save data should implement the _POST_ http request method.
4. Successfull _POST_ requests to create new records should return **201** response code.
5. Successfull _GET_, _DELETE_ requests should return **200** response code.
6. If something goes wrong, return **400** response code.

## EXTRA DATA
> Provide the following data set in your response:
1. **message**: This should have an understandable reason for why you returned a specific response code or just _OK_ for get requests with a _data_ entity.
2. **status**: This should hold either of _error_, _info_, _warning_, or _error_ depending on the response code or message.
3. **code**: This should be the same as the returned response code.
4. **data**: This should either be an an empty object or an object holding all the required data set.

## SAMPLE RECOMMENDED RESPONSE
```json
{
  "message": "OK",
  "status": "success",
  "code": 200,
  "data": {
    "user": {
      "id": 1,
      "username": "realralphg",
      "email": "realralphg@gmail.com",
      "name": "Raphael Issah",
      "photo": "https://demosite.com/photos/realralphg/18236391_12312321_01278219.jpg"
    },
    "posts": []
  }
}
```

## AUTHENTICATION
Registration and Authentication requests should return the same _EXTRA DATA_ set as other requests with the addition of an authentication token.
```json
{
  "message": "OK",
  "message": "Registration was successful",
  "status": "success",
  "code": 201,
  "token": "1|0912u312m312nn83z321noxsermxew34",
  "data": {
    "user": {
      "id": 1,
      "username": "realralphg",
      "email": "realralphg@gmail.com",
      "name": "Raphael Issah",
      "photo": "https://demosite.com/photos/default.jpg"
    },
  }
}
```

### AUTH IMPLEMENTATION
Authentication should be implemented by passing the authentication token as a _Bearer_ token to the _Authorization_ header property.
```json
{
  "headers": {
    "Authorization": "Bearer 1|0912u312m312nn83z321noxsermxew34"
  }
}
```

## DATA PROPERTY NAMING
All **data** properties should be named in such manner that describes the data held by the property.
- **Plural Nouns** should be used to identify collections. 
- **Singular Nouns** should identify single collection items.
```json
{
  "data": {
    "user": {
      "username": "realralphg",
      ...
    },
    "posts": [
      {
        "id": 1,
        ...
      },
      {
        "id": 2,
        ...
      },
      ...
    ]
  }
}
```

## USE NOUNS
Use plural nouns for collections, this plural naming convention becomes a global code. This also helps normal people to understand that these groups of APIs form a collection.

| Collection           | Role                                         |
|----------------------|----------------------------------------------|
| /users               | list all users                               |
| /users/123           | specific user                                |
| /users/123/posts     | list of posts that belong to a specific user |
| /users/123/posts/321 | specific post of a specific users post list  |


## DISCLAIMER
This document is only a recommendation and is subject to change without prior notice.


_Author_: [3m1n3nc3](https://github.com/3m1n3nc3 "3m1n3nc3") _for_ [Greysoft Code Camp](https://github.com/greysoft-code-camp "Greysoft Code Camp")
