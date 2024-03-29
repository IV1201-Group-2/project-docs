# Personal Info Endpoint

`GET /api/application-form/applicant/personal-info/`

## Additional requirements

* The user must be logged in when calling this API
* The user's JWT token must be included in the `Authorization` header

## Successful response

The API returns an object with the following structure:

```json
{
    "id": 1,
    "name": "John",
    "surname": "Doe",
    "pnr": "1234567890",
    "email": "johndoe@example.com",
    "username": "johndoe",
    "role": 2
}
```

## Error responses

#### `USER_NOT_FOUND` (404 Not Found)

No user was found with the ID specified in the JWT token

#### `COULD_NOT_FETCH_USER` (500 Internal Server Error)

There was an issue with the database operation when trying to fetch the user's information

#### `UNAUTHORIZED` (401 Unauthorized)

User is not logged in (JWT token was not provided or is invalid)

#### `INVALID_TOKEN` (401 Unauthorized)

The provided JWT token is invalid (e.g., it is expired, not yet valid, or does not contain the required claims)

#### `TOKEN_NOT_PROVIDED` (401 Unauthorized)

No JWT token was provided in the `Authorization` header

#### `TOKEN_REVOKED` (401 Unauthorized)

The provided JWT token has been revoked

#### `INTERNAL_SERVER_ERROR` (500 Internal Server Error)

An unexpected error occurred