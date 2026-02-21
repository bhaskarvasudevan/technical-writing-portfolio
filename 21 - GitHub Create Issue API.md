# Create Issue — GitHub REST API

## API Overview
Creates a new issue in a GitHub repository.
* The API is an HTTP POST endpoint.
* The response format is JSON by default.
* The API returns details of the issue created.

## Endpoint
```
POST https://api.github.com/repos/{owner}/{repo}/issues
```

- Base URL: `https://api.github.com`
- Resource Path: `/repos/{owner}/{repo}/issues`

## Authentication
This endpoint requires authentication using a personal access token (PAT) or GitHub App token. 

The required token scope:
- repo (private repositories)
- public_repo (public repositories)
  
See details in the **Request Headers** section. 

## Request Headers
For every request, the following must be set as request headers.
```
Accept: application/vnd.github+json
Authorization: Bearer <TOKEN>
X-GitHub-Api-Version: 2022-11-28
Content-Type: application/json
```
Replace `<TOKEN>` with your unique token. You can find your token on your settings page under the **Tokens** tab. 

## Path Parameters
Set the path parameters below: 
| Parameter | Type   | Required | Description               |
| --------- | ------ | -------- | ------------------------- |
| owner     | string | Yes      | Repository owner username |
| repo      | string | Yes      | Repository name           |


## Request Body (JSON)
### Required
| Field | Type   | Required | Description        |
| ----- | ------ | -------- | ------------------ |
| title | string | Yes      | Title of the issue |


### Optional
| Field     | Type          | Description                                                                        |
| --------- | ------------- | ---------------------------------------------------------------------------------- |
| body      | string        | Issue description                                                                  |
| assignees | array[string] | GitHub usernames. Users must already exist. Assignees must have repository access. |
| labels    | array[string] | Labels to assign. Must already exist in the repository.                            |


## Example Request
``` 
curl -L \
  -X POST \
  -H "Accept: application/vnd.github+json" \
  -H "Authorization: Bearer <TOKEN>" \
  -H "X-GitHub-Api-Version: 2022-11-28" \
  -H "Content-Type: application/json" \
  https://api.github.com/repos/bhaskarvasudevan/technical-writing-portfolio/issues \
  -d '{
    "title": "Bug: Missing error examples",
    "body": "Steps to reproduce the issue...",
    "labels": ["bug"]
  }'
```

## Example Response
Below is a typical response. 

Returns 201 Created on success. 

The response has been truncated for brevity.

``` 
{
  "id": 1,
  "number": 1347,
  "title": "Bug: Missing error examples",
  "state": "open",
  "body": "Steps to reproduce the issue...",
  "user": {
    "login": "bhaskarvasudevan"
  }
}
```

See the table below to interpret the fields in the response:  

| Field                 | Type   | Description                                           |
| --------------------- | ------ | ----------------------------------------------------- |
| id                    | number | Unique identifier of the issue created                |
| number                | number | Unique issue number created                           |
| title                 | string | Title of the issue created. Same as the input title.  |
| state                 | string | State of the issue created. Starting state is `open`  |
| body                  | string | Details of the issue created. Same as the input body. |
| user.login            | string | user whose token was used to create the issue.        |



## Possible Error Codes
| Code | Meaning                                   |
| ---- | ----------------------------------------- |
| 201  | Created                                   |
| 401  | Unauthorized                              |
| 403  | Forbidden                                 |
| 404  | Repository not found                      |
| 422  | Validation failed (e.g., missing title)   |

Here is an example error response: 
```
{
  "message": "Bad credentials",
  "documentation_url": "https://docs.github.com/rest"
}
```

## Rate Limits
This endpoint is subject to GitHub REST API rate limits.




