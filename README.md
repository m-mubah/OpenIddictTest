# OpenIddictTest

This is a project to test and play around with OpenIddict.

It is setup to work with Postgres but should be easy enough to switch to another database.

## Running the project
- Run the migrations with `Update-Database` or `dotnet ef database update`.
- Run the project.

## Testing
- The built in swagger UI works to create a user, but currently there is no way to test login in and token refresh with the swagger UI (as far as I know).

### Postman
- It is very easy to test the login and refresh token with postman
#### Login
1. Set a new POST request to the url: `https://localhost:7277/connect/token`.
2. Go to `Headers` set the following:

| KEY | VALUE |
| ----------- | ----------- |
| Content-Type | application/x-www-form-urlencoded |

3. Go to Body and select x-www-form-urlencoded and set the following:

| KEY | VALUE |
| ----------- | ----------- |
| grant_type | password |
| username | your_username |
| password | your_password |
| scope | openid offline_access |

You can also add other scopes to get more data such as roles, currently allowed scopes are `openid email profile offline_access roles`.

#### Token Refresh
1. Set a new POST request to the url: `https://localhost:7277/connect/token`.
2. Go to `Headers` set the following:

| KEY | VALUE |
| ----------- | ----------- |
| Content-Type | application/x-www-form-urlencoded |

3. Go to Body and select x-www-form-urlencoded and set the following:

| KEY | VALUE |
| ----------- | ----------- |
| grant_type | refresh_token |
| refresh_token | refresh_token_from_login |
