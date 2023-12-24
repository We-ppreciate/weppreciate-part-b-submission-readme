# T3A2-B Katie Lock and Nate Picone

## You work hard. We'ppreciate you.

### We'ppreciate - a full stack MERN application. Readme for Part-B submission


## Helpful links

[Repo for T3A2-A submission readme.md](https://github.com/We-ppreciate/weppreciate-part-a)

[Part-B Backend repo](https://github.com/We-ppreciate/weppreciate-part-b-backend)

[Part-B Backend deployment](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/)

[Part-B Frontend repo](https://github.com/We-ppreciate/weppreciate-part-b-frontend)

[Part-B Frontend deployment](https://playful-pudding-8faa4e.netlify.app/)


## R1 At minimum use MongoDB, Express, React, Node
We used the following packages, frameworks and technology:

### Backend

#### Node


#### npm


#### MongoDB


#### Express


#### Google Cloud Storage


#### bcrypt / bcryptjs


#### cors


#### dotenv


#### jasonwebtoken


#### mongoose


#### nodemon


#### joi
`joi` and `joi/date`

#### jest


#### supertest


### Frontend


## 2 Write well designed code



## R3 Employ and utilise proper source control methodology (git)



## R4 Demonstrate your ability to work in a team

### Use a recognised project management methodology

We continued our application of Agile methedology throughout this project, keeping user stories at the heart of our deliverables, while buring down our sprints.

We elected to run 6 one-week sprints, and while we understand the regular timespan of a sprint to be two weeks, we felt one week allowed us to more comfortably pace our task delivery. In practise this meant most weeks had items that were incomplete and carried over, but we stand by the decision and the benefit it gave us through planning and development.

Around Sprint 3 ( we started at sprint 0), we presented a [Client Pack](https://weppreciate.notion.site/We-pprecite-Client-Pack-586c89a97cdb444993671762320bb764?pvs=4) for alignment and requirements sign off. While this ideally should have been completed earlier, and delivered through a meeting, the operational needs of the business meant the client was unavaiable, and our timing was a little behind schedule. We presented this in an email, inviting the client to review and respond with questions.

![Weppreciate Client Pack](./docs/weppreciate-client-pack.jpg)

![Client confirmation of requirements](./docs/weppreciate-client-requirements-signoff.jpg)

The allocation of tasks were essentially split into the back end plus databases, and the front end plus styling. We discussed the allocation of duties, and agreed that Katie's skills were stronger with React and styling, and that while Nate was keen to improve his front end skills, our plan was ambitious for the time available, which meant we needed to aim for maximum efficiency.

We continued the path we laid down in Part-A, with dividing the enitre project into six sub-projects:

1. Application Requirements
1. Application Design
1. Database
1. Back End
1. Front End
1. Rubric fulfilment

![Demonstrating the sub-projects. This was taken toward the end of Part-B, so many of the tasks making up the project have been completed.](./docs/demonstrating-projects.jpg)

Requirements and Design were mostly completed in Part-A.


### Use a recognised task delegation methodology

Within the remaining Sub-projects, Tasks were allocated a three-tiered effort score, of low, moderate, or high effort. We discussed these in out three-times-per-week standups, as the project progressed. This was partly to sense check the rating, but was mostly as a way to check in on each other's workload and ensure one of us was not being overloaded, and that there was balance. A higher number of low effort tasks was equivalent with a moderate task, etc. This was not a scientific approach, but gavce a clear, approximate indication and worked well.

Although dependencies were not well captured in Notion, these were also discussed as we planned our next focusses for delivery. It was Nate's intent to delivery just in time API functionality to allow Katie to develop the front end. This also worked very well, for the most part, and allowed whoever was waiting for a dependency to finish, to take the next task of highest value, whether that be the next dependency, administration and rubric requirements, or styling.

Prioritisation of tasks, and continually assessing them against our Minimum Viable Product (MVP) cireteria were also key to our development cycles.

![Screenshot demonstrating tasks, which were used as discussion points through standups, for dependency identification, and task scheduling and allocation](./docs/example-tasks.jpg)


## R5 Produce a working application that meets client and user needs

Due to the client's business being in end of year closure, we are unable to get full sign off from the client before submitting this project for assessment. We have, however, aligned with the client at multiple points through the development cycle, and have invited partial User Acceptance Testing and feeddback from the client. We recognise the client is on holiday, driving from Melvourne to Western Australia, so it would be unreasonable to expect full UAT and substantial feedback. Were this a commercial project, we would seek UAT, feedback and acceptance from the client's delegate.

### API Routes


#### Errors

This API uses the following error codes:

- `400 Bad Request`: Often handled by ErrorController.js, the 400 Error Response will reply with `Your intent is good but the request was bad. ${statusCode}, ${err.message}`, but on some routes, custom 400 error messages are used to return more specific information about what cause it. This error also covers expired token usage.
- `401 Unauthorised`: Handled by ErrorController.js, where the user is not logged in, and responded to with the message `It looks like I'm missing your login credentials. Let's have another go. ${statusCode}, ${err.message}`
- `403 Forbidden`: Generally handled within the route, where the required level of access is not he ld by the user - generally isAdmin or isSeniorManager. A generic 403 is available in ErrorController.js, should it be needed, with format of `You are not authorised to do that. We'pologise. ${statusCode}, ${err.message}`
- `404 Not found`: Generaly handled by ErrorController.js, some in-route 404 errors are generated where requested records are not found. The generic 404 has the format `This is not the page you are looking for. ${statusCode}, ${err.message}`
- `500 Internal Server Error`: Has been implemented in two ways. If a 500 error is the error generated by the application, the message appears as `Sorry. That's a problem on our side. Mavis is looking into it now... well, after her tea. ${statusCode}: ${err.message}`, and an additional catch-all error has been created to cover any other error, with message `Sorry. That\'s a problem on our side. Look like Mavis spilled her tea on the server. ${statusCode}, ${err.message}`

#### Base URL

|  |  |
|--|--|
|Endpoint|`GET /`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/)|
|Parameters|None|
|Response|Returns a JSON object with the following properties: `message` - a static reponse from the server|

**Example**

Request:
```
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/
```

Response:

```
{
  "message": "You work hard. We'ppreciate you."
}
```



#### End Points

Four main paths are available in the API:

1. `/auth` for authentication. Routes on this path handle login and password changes
2. `/users` for actions relating to documents in the users collection
3. `/nominations` for actions relating to documents in the nominations collection
4. `/comments` for actions relating to comments that users can make on others' recognition posts in the app.

#### /auth

|  |  |
|--|--|
|Endpoint|`POST /auth/login`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/auth/login`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/auth/login)|
|Parameters|*email*: string; *password*: sting|
|Response|Returns a JSON object with the following properties: *id* - the document id from the User collection; *name.first* - first name of the user; *name.last* - last name of the user; *businessUnit* - the business unit of the user; *lineManbagerId* - the id of the User document, linked as the user's line manager; *userTagLine* - self-supplied bio or tagline of the user; *userPhotoKey* - the public URL of the user's photo. In the client's application, this would be obtained from Azure AD, and this would be applied as the application was integrated with existing corporate structure and security needs; *isFullUser* - boolean to indicate whether the user had full access or was a guest user; *isLineManager* - boolean used for Line Manager restricted access authorisation; *isAdmin* - boolean used for Admin restricted access authorisation; *token* JWT returned to the user and used for authentication as they use the service.|
|Note|The JWT has been set with a 7-day expiry, allowing the client to test and explore the service without the inconveience of a short validity period. In the commercial applciation, a better application would be to carry a shorter validity, such as 24 hours, with a longer refresh token, but on deployment for the client, the authentication would be moved to SAML SSO, through Azure, we did not implement the refresh token in this case.|

**Example**

Request:
```

POST https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/auth/login

REQUEST BODY

{
  "name": "your.name@yourcompany.com",
  "password": "youRSup3rS3cRet"
}
```

Response:

```
{
    "id": "657d7c33d8b97e77efe01931",
    "name": {
        "first": "Nate",
        "last": "Picone"
    },
    "email": "nate.picone@yourcompany.com",
    "businessUnit": "Business Services",
    "lineManagerId": "657d7c33d8b97e77efe01935",
    "userTagLine": "Tell me you access woes and I will disappear them.",
    "userPhotoKey": "https://storage.googleapis.com/weppreciate-store/profile/00109-3081462005.png",
    "isFullUser": true,
    "isLineManager": false,
    "isSeniorManager": false,
    "isAdmin": false,
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOiI2NTdkNdMzM2Q4Yjk3ZTc3ZWZlMDE5MzEiLCJpYXQiOjE3MD5zMzE1MjksImV4cCI6MTcwMzkzNjNyOX0.MGxXGoJx-qJCAnb_wqslMds0vwAlwuGmv0lHCKSV-BQ"
}
```


|  |  |
|--|--|
|Endpoint|`PATCH /auth/reset/:id`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/auth/reset/:id`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/auth/reset/:id)|
|Parameters|**URL query** *:id* - forms the query within the URL and is the id of the account requiring the password reset; **request body** *newPassword*: string|
|Response|Returns a JSON object with the following properties: **message** |

**Example**

Request:
```
PATCH https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/auth/reset/657d7c33d8b97e77efe01931

REQUEST BODY

{
  "newPassword": "youRSup3rS3cRetNEW"
}
```

Response:

```
{
    "message": "Password reset successful. With great passwords come great responsibility."
}
```

#### /users

|  |  |
|--|--|
|Endpoint|`GET /users/all`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/all`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/all)|
|Parameters|none|
|Response|*message* - a welcome message, depending on whether the requestor has isAdmin: true or false; Returns a JSON object with an array of all user objects in the User collection. Note: passwordHashes are not returned in the array.|

**Example**

Request:
```
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/all
```

Response:

```
{
    "message": "Hello non-Admin",
    "Users": [
        {
            "name": {
                "first": "Nate",
                "last": "Picone"
            },
            "_id": "657d7c33d8b97e77efe01931",
            "email": "nate.picone@yourcompany.com",
            "businessUnit": "Business Services",
            "lineManagerId": "657d7c33d8b97e77efe01935",
            "userTagLine": "Tell me you access woes and I will disappear them.",
            "userPhotoKey": "https://storage.googleapis.com/weppreciate-store/profile/00109-3081462005.png",
            "isFullUser": true,
            "isLineManager": false,
            "isSeniorManager": false,
            "isAdmin": false,
            "upn": "nate.picone",
            "__v": 0
        },
        // ... more document objects
    ]
}
```

|  |  |
|--|--|
|Endpoint|`GET /users/all/fullusers`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/all/fullusers/`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/all/fullusers/)|
|Parameters|none|
|Response|Returns a JSON object with an array of all user objects in the User collection, where fullUser: true. Note: passwordHashes are not returned in the array.|

**Example**

Request:
```
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/all/fullusers/
```

Response:

```
{
    "Users": [
        {
            "name": {
                "first": "Nate",
                "last": "Picone"
            },
            "_id": "657d7c33d8b97e77efe01931",
            "email": "nate.picone@yourcompany.com",
            "businessUnit": "Business Services",
            "lineManagerId": "657d7c33d8b97e77efe01935",
            "userTagLine": "Tell me you access woes and I will disappear them.",
            "userPhotoKey": "https://storage.googleapis.com/weppreciate-store/profile/00109-3081462005.png",
            "isFullUser": true,
            "isLineManager": false,
            "isSeniorManager": false,
            "isAdmin": false,
            "upn": "nate.picone",
            "__v": 0
        },
        // ... more document objects
    ]
}
```

|  |  |
|--|--|
|Endpoint|`GET /users/one/id/:id`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/one/id/:id`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/one/id/:id)|
|Parameters|**URL Query** *:id* is the id of the User document to be returned; **Request body** none.|
|Response|Returns a JSON object with the User document, with matching id. passwordHash is not returned.|

**Example**

Request:
```
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/one/id/657d7c33d8b97e77efe01931
```

Response:

```
{
    "User": {
        "name": {
            "first": "Nate",
            "last": "Picone"
        },
        "_id": "657d7c33d8b97e77efe01931",
        "email": "nate.picone@yourcompany.com",
        "businessUnit": "Business Services",
        "lineManagerId": "657d7c33d8b97e77efe01935",
        "userTagLine": "Tell me you access woes and I will disappear them.",
        "userPhotoKey": "https://storage.googleapis.com/weppreciate-store/profile/00109-3081462005.png",
        "isFullUser": true,
        "isLineManager": false,
        "isSeniorManager": false,
        "isAdmin": false,
        "upn": "nate.picone",
        "__v": 0
    }
}
```

|  |  |
|--|--|
|Endpoint|`GET /users/one/name/:first/:last`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/usersone/name/:first/:last`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/one/name/:first/:last)|
|Parameters|**URL Query** *:first* is the full name.first within the desired User document - note this is not case sensitive; *:last*: is the full name.last within the desired user document - note this is not case sensitive; **Request body** none.|
|Response|Returns a JSON object with one User document, with matching name.first AND name.second. passwordHash is not returned.|

**Example**

Request:
```
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/usersone/name/nate/picone
```

Response:

```
{
    "Users": {
        "name": {
            "first": "Nate",
            "last": "Picone"
        },
        "_id": "657d7c33d8b97e77efe01931",
        "email": "nate.picone@yourcompany.com",
        "businessUnit": "Business Services",
        "lineManagerId": "657d7c33d8b97e77efe01935",
        "userTagLine": "Tell me you access woes and I will disappear them.",
        "userPhotoKey": "https://storage.googleapis.com/weppreciate-store/profile/00109-3081462005.png",
        "isFullUser": true,
        "isLineManager": false,
        "isSeniorManager": false,
        "isAdmin": false,
        "upn": "nate.picone",
        "__v": 0
    }
}
```

|  |  |
|--|--|
|Endpoint|`GET /users/search/:string`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/search/:string`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/search/:string)|
|Parameters|**URL Query** *:string* - is matched against `name.first` and `name.last` within the User documents, and matching documents are added to an array - note that the search string is case insensitive and, as applied, can only be a contiguous string without spaces; **Request body** none.|
|Response|Returns a JSON object with User documents. passwordHash is not returned.|

**Example**

Request:
```
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/search/ar
```

Response:

```
{
    "Users": [
        {
            "name": {
                "first": "Alex",
                "last": "Greatbeard"
            },
            "_id": "657d7c33d8b97e77efe01942",
            "email": "alex.greatbeard@yourcompany.com",
            "businessUnit": "Pokemon Development",
            "lineManagerId": "657d7c33d8b97e77efe01939",
            "userTagLine": "One more than eight tendos",
            "userPhotoKey": "https://storage.googleapis.com/weppreciate-store/profile/00068-348350141.png",
            "isFullUser": true,
            "isLineManager": false,
            "isSeniorManager": false,
            "isAdmin": false,
            "upn": "alex.greatbeard",
            "__v": 0
        },
        {
            "name": {
                "first": "Carolina",
                "last": "Reaper"
            },
            "_id": "657d7c34d8b97e77efe01945",
            "email": "carolina.reaper@yourcompany.com",
            "businessUnit": "Business Services",
            "lineManagerId": "6580eb56bfd09ef5a5f9ebdd",
            "userTagLine": "It's a bit chilly in here",
            "userPhotoKey": "https://storage.googleapis.com/weppreciate-store/profile/00033-2773725908.png",
            "isFullUser": true,
            "isLineManager": true,
            "isSeniorManager": true,
            "isAdmin": false,
            "upn": "carolina.reaper",
            "__v": 0
        },
        {
            "name": {
                "first": "Sally",
                "last": "Superstar"
            },
            "_id": "65801d0c388ed1fa5e929dfd",
            "email": "sally.superstar@yourcompany.com",
            "businessUnit": "Business Services",
            "lineManagerId": "657d7c34d8b97e77efe01945",
            "userTagLine": "I aim for a little better than average",
            "userPhotoKey": "https://storage.googleapis.com/weppreciate-store/profile/00080-1412353387.png",
            "isFullUser": true,
            "isLineManager": false,
            "isSeniorManager": false,
            "isAdmin": false,
            "__v": 0
        }
    ]
}
```

|  |  |
|--|--|
|Endpoint|`GET /users/all/manager/:id`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/all/manager/:id`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/all/manager/:id)|
|Parameters|**URL Query** *:id* is the id of lineManager, within the User documents to be returned - matched documents are added to an array; **Request body** none.|
|Response|Returns a JSON object with an array of User documents, with matching lineManager id. passwordHash is not returned.|
|Note|Authentication restricts access to accounts where `isLineManager: true` or `isAdmin: true`|

**Example**

Request:
```
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/all/manager/657d7c33d8b97e77efe01939
```

Response:

```
{
    "User": [
        {
            "name": {
                "first": "Ed",
                "last": "Dougherty"
            },
            "_id": "657d7c33d8b97e77efe01935",
            "email": "ed.dougherty@yourcompany.com",
            "businessUnit": "Business Services",
            "lineManagerId": "657d7c33d8b97e77efe01939",
            "userTagLine": "The tulips!",
            "userPhotoKey": "https://storage.googleapis.com/weppreciate-store/profile/00058-960922821.png",
            "isFullUser": true,
            "isLineManager": true,
            "isSeniorManager": false,
            "isAdmin": false,
            "upn": "ed.dougherty",
            "__v": 0
        },
        {
            "name": {
                "first": "Alex",
                "last": "Greatbeard"
            },
            "_id": "657d7c33d8b97e77efe01942",
            "email": "alex.greatbeard@yourcompany.com",
            "businessUnit": "Pokemon Development",
            "lineManagerId": "657d7c33d8b97e77efe01939",
            "userTagLine": "One more than eight tendos",
            "userPhotoKey": "https://storage.googleapis.com/weppreciate-store/profile/00068-348350141.png",
            "isFullUser": true,
            "isLineManager": false,
            "isSeniorManager": false,
            "isAdmin": false,
            "upn": "alex.greatbeard",
            "__v": 0
        }
    ]
}
```

|  |  |
|--|--|
|Endpoint|`GET /users/one/:email`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/one/:email`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/one/:email)|
|Parameters|**URL Query** *:email* - is matched against `email` within the User documents, and one matching document is returned- note that the search string is case insensitive; **Request body** none.|
|Response|Returns a JSON object with User documents. passwordHash is not returned.|

**Example**

Request:
```
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/one/alex.greatbeard@yourcompany.com
```

Response:

```
{
    "Users": [
        {
            "name": {
                "first": "Alex",
                "last": "Greatbeard"
            },
            "_id": "657d7c33d8b97e77efe01942",
            "email": "alex.greatbeard@yourcompany.com",
            "businessUnit": "Pokemon Development",
            "lineManagerId": "657d7c33d8b97e77efe01939",
            "userTagLine": "One more than eight tendos",
            "userPhotoKey": "https://storage.googleapis.com/weppreciate-store/profile/00068-348350141.png",
            "isFullUser": true,
            "isLineManager": false,
            "isSeniorManager": false,
            "isAdmin": false,
            "upn": "alex.greatbeard",
            "__v": 0
        },
        //... more document objects
    ]
}
```

|  |  |
|--|--|
|Endpoint|`POST /users/new`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/new`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/new)|
|Parameters|**Request body** key value pairs that make up the user document, see table below|
|Response|Returns a JSON object with User documents. passwordHash is not returned.|
|Note|Authorisation restricts access to accounts where `isLineManager: true` or `isAdmin: true`|


> [!NOTE] Valid key/value pairs for creating a new record:

|Key|Value|
|--|--|
|name|object, required|
| .first|string, required, min:2, max:60|
| .last|string, required, min:2, max:60|
|email|string, required, email validation, lowercase applied|
|businessUnit|string, required, min:2, max:60|
|passwordHash|string, required, min:8, max:120|
|lineManagerId|string, required|
|userTagline|string|
|isFullUser|boolean, required, default:false|
|isLineManager|boolean, required, default:false|
|isSeniorManager|boolean, required, default:false|
|isAdmin|boolean, required, default:false|


**Example**

Request:
```
POST https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/new

REQUEST BODY

{
    "name": {
        "first": "Georgia",
        "last": "Wyoming"
    },
    "email": "georgia.wyoming@yourcompany.com",
    "businessUnit": "Business Services",
    "lineManagerId": "657d7c34d8b97e77efe01945",
    "userTagLine": "I'm new here. So excited!",
    "userPhotoKey": "replacewithURL",
    "isFullUser": true,
    "isLineManager": false,
    "isSeniorManager": false,
    "isAdmin": false
}
```

Response:

```
{
    "User": {
        "email": "georgia.wyoming@yourcompany.com",
        "name": {
            "first": "Georgia",
            "last": "Wyoming"
        },
        "businessUnit": "Business Services",
        "lineManagerId": "657d7c34d8b97e77efe01945",
        "userTagLine": "I'm new here. So excited!",
        "userPhotoKey": "replacewithURL",
        "isFullUser": true,
        "isLineManager": false,
        "isSeniorManager": false,
        "isAdmin": false,
        "_id": "65875811253eeecd52862523",
        "__v": 0
    }
}
```

|  |  |
|--|--|
|Endpoint|`PATCH /users/update/self/:id`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/update/self/:id`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/update/self/:id)|
|Parameters|**URL Query** *:id* - is matched against `id` within the User documents, and one matching document is returned this is then checked against the user id provided through the JWT token, as an additional check before documents are updated; **Request body** userTagline is currently the only field updatable by users.|
|Response|Returns a JSON object with User document. passwordHash is not returned.|

**Example**

Request:
```
PATCH https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/update/self/657d7c33d8b97e77efe01931

REQUEST BODY

{
    "userTagLine": "I'm not new here any more. Still excited!"
}

```

Response:

```
{
    "name": {
        "first": "Nate",
        "last": "Picone"
    },
    "_id": "657d7c33d8b97e77efe01931",
    "email": "nate.picone@yourcompany.com",
    "businessUnit": "Business Services",
    "lineManagerId": "657d7c33d8b97e77efe01935",
    "userTagLine": "I'm not new here any more. Still excited!",
    "userPhotoKey": "https://storage.googleapis.com/weppreciate-store/profile/00109-3081462005.png",
    "isFullUser": true,
    "isLineManager": false,
    "isSeniorManager": false,
    "isAdmin": true,
    "upn": "nate.picone",
    "__v": 0
}
```

|  |  |
|--|--|
|Endpoint|`PATCH /users/update/self/:id`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/update/self/:id`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/update/self/:id)|
|Parameters|**URL Query** *:id* - is matched against `id` within the User documents, and one matching document is returned this is then checked against the user id provided through the JWT token, as an additional check before documents are updated; **Request body** userTagline is currently the only field updatable by users.|
|Response|Returns a JSON object with User document. passwordHash is not returned.|

**Example**

Request:
```
PATCH https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/update/self/657d7c33d8b97e77efe01931

REQUEST BODY

{
    "userTagLine": "I'm not new here any more. Still excited!"
}

```

Response:

```
{
    "name": {
        "first": "Nate",
        "last": "Picone"
    },
    "_id": "657d7c33d8b97e77efe01931",
    "email": "nate.picone@yourcompany.com",
    "businessUnit": "Business Services",
    "lineManagerId": "657d7c33d8b97e77efe01935",
    "userTagLine": "I'm not new here any more. Still excited!",
    "userPhotoKey": "https://storage.googleapis.com/weppreciate-store/profile/00109-3081462005.png",
    "isFullUser": true,
    "isLineManager": false,
    "isSeniorManager": false,
    "isAdmin": true,
    "upn": "nate.picone",
    "__v": 0
}
```


|  |  |
|--|--|
|Endpoint|`PATCH /users/update/admin/:id`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/update/admin/:id`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/update/admin/:id)|
|Parameters|**URL Query** *:id* - is matched against `id` within the User documents, and one matching document is returned. **Request body** *name.first* string, optional; *name.first* string, optional; *email* string, optional; *businessUnit* string, optional; *LineManagerId* string, optional; *userTagLine* string, optional; *userPhotoKey* string, optional; *isFullUser* boolean, optional; *isLineManager* boolean, optional; *isSeniorManager* boolean, optional; *isAdmin* boolean, optional. Value validation also applies.|
|Response|Returns a JSON object with User document. passwordHash is not returned.|

**Example**

Request:
```
PATCH https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/update/admin/657d7c33d8b97e77efe01931

REQUEST BODY

{
    "isLineManager": true
}

```

Response:

```
{
    "name": {
        "first": "Nate",
        "last": "Picone"
    },
    "_id": "657d7c33d8b97e77efe01931",
    "email": "nate.picone@yourcompany.com",
    "businessUnit": "Business Services",
    "lineManagerId": "657d7c33d8b97e77efe01935",
    "userTagLine": "I'm not new here any more. Still excited!",
    "userPhotoKey": "https://storage.googleapis.com/weppreciate-store/profile/00109-3081462005.png",
    "isFullUser": true,
    "isLineManager": true,
    "isSeniorManager": false,
    "isAdmin": true,
    "upn": "nate.picone",
    "__v": 0
}
```

|  |  |
|--|--|
|Endpoint|`DELETE /users/delete/admin/:id`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/delete/admin/:id`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/update/admin/:id)|
|Parameters|**URL Query** *:id* - is matched against `id` within the User documents, and one matching document is returned and deleted. **Request body** none|
|Response|Returns a JSON object with User document. passwordHash is not returned.|

**Example**

Request:
```
DELETE https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/delete/admin/65875811253eeecd52862523
```

Response:

```
{
    "User": {
        "name": {
            "first": "Georgia",
            "last": "Wyoming"
        },
        "_id": "65875811253eeecd52862523",
        "email": "georgia.wyoming@yourcompany.com",
        "businessUnit": "Business Services",
        "lineManagerId": "657d7c34d8b97e77efe01945",
        "userTagLine": "I'm new here. So excited!",
        "userPhotoKey": "replacewithURL",
        "isFullUser": true,
        "isLineManager": false,
        "isSeniorManager": false,
        "isAdmin": false,
        "__v": 0
    }
}
```

#### /nominations

|  |  |
|--|--|
|Endpoint|`GET /nominations/all`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/all`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/all)|
|Parameters|*message* - Returns a JSON object with an array of all Nomination objects in the User collection. |
|Response||

**Example**

Request:
```
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/all
```

Response:

```
{
    "Nominations": [
        {
            "_id": "657d7c34d8b97e77efe0194c",
            "recipientUser": "657d7c33d8b97e77efe01931",
            "nominatorFullUser": "657d7c33d8b97e77efe01935",
            "nominationValue": [
                "Commitment"
            ],
            "nominationBody": "Nate is a great guy!",
            "nominationDate": "09-12-2023",
            "isNominatorFullUser": true,
            "isNominationInstant": true,
            "isAward": false,
            "isReleased": false,
            "releaseDate": null,
            "__v": 0
        },
        // ... more document objects
    ]
}
```

|  |  |
|--|--|
|Endpoint|`GET /nominations/all/recipient/:id`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/all/recipient/:id`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/all/recipient/:id)|
|Parameters|**URL Query** *:id* - is matched against `id` within the Nominations documents, and an array of all matching documents is returned. **Request body** none|
|Response| |

**Example**

Request:
```
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/all/recipient/657d7c33d8b97e77efe01935
```

Response:

```
{
    "Nominations": [
        {
            "_id": "657d7c34d8b97e77efe0194f",
            "recipientUser": "657d7c33d8b97e77efe01935",
            "nominatorFullUser": "657d7c33d8b97e77efe0193c",
            "nominationValue": [
                "Commitment"
            ],
            "nominationBody": "Ed is also a great guy!",
            "nominationDate": "02-12-2023",
            "isNominatorFullUser": true,
            "isNominationInstant": true,
            "isAward": false,
            "isReleased": false,
            "releaseDate": null,
            "__v": 0
        },
        {
            "nominatorBasicUser": {
                "basicName": {
                    "first": "Naomi",
                    "last": "SkyCaptain"
                },
                "basicEmail": "naomi.skycaptain@yourcompany.com"
            },
            "_id": "657d7c34d8b97e77efe01952",
            "recipientUser": "657d7c33d8b97e77efe01935",
            "nominatorFullUser": null,
            "nominationValue": [
                "Challenging"
            ],
            "nominationBody": "Ed is a challenger!",
            "nominationDate": "10-12-2023",
            "isNominatorFullUser": false,
            "isNominationInstant": false,
            "isAward": true,
            "isReleased": true,
            "releaseDate": "21-12-2023",
            "__v": 0
        },
        //... more document objects
    ]
}
```

|  |  |
|--|--|
|Endpoint|`GET /nominations/all/nominator/:firstName/:lastName`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/all/nominator/:firstName/:lastName`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/all/all/nominator/:firstName/:lastName)|
|Parameters|**URL Query** *:firstName* - is matched against `name.first` within the User documents, *:lastName* is matched against `name.last` in the User documents, to return the ID of the nominator, which is then matched against nominatorFullUser Nomination documents. If no matching `User.name` is found, the same values are used to match against `nominatorBasicUser.basicName` in the Nominations collection, and an array of all matching Nomination documents is returned. **Request body** none |
|Response||

**Example**

Request:
```
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/all/nominator/katie/lock
```

Response:

```
{
    "Nominations": [
        {
            "_id": "657d7c34d8b97e77efe0194f",
            "recipientUser": "657d7c33d8b97e77efe01935",
            "nominatorFullUser": "657d7c33d8b97e77efe0193c",
            "nominationValue": [
                "Commitment"
            ],
            "nominationBody": "Ed is also a great guy!",
            "nominationDate": "02-12-2023",
            "isNominatorFullUser": true,
            "isNominationInstant": true,
            "isAward": false,
            "isReleased": false,
            "releaseDate": null,
            "__v": 0
        },
        {
            "_id": "657e8472642ef3da540d1b6b",
            "recipientUser": "657d7c33d8b97e77efe01931",
            "nominatorFullUser": "657d7c33d8b97e77efe0193c",
            "nominationValue": [
                "Spirited"
            ],
            "nominationBody": "Nate is the only reason I will pass this assignment. Bless his soul. Give him ice cream.",
            "nominationDate": "16-12-2023",
            "isNominatorFullUser": true,
            "isNominationInstant": true,
            "isAward": false,
            "isReleased": false,
            "releaseDate": "16-12-2023",
            "__v": 0
        },
        // ... more document objects
    ]
}
```

|  |  |
|--|--|
|Endpoint|`GET /nominations/page/:page`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/page/:page`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/all/all/nominator/page/:page)|
|Parameters|**URL Query** *:page* - returns all nominations, in descending sumbission date order, in a pagenation format, with 20 items per page. **Request body** none |
|Response||

**Example**

Request:
```
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/page/1
```

Response:

```
{
    "Nominations": [
        {
            "_id": "6584e35ee2c8545acd85faaf",
            "recipientUser": "6580eb56bfd09ef5a5f9ebdd",
            "nominatorFullUser": "657d7c33d8b97e77efe0193c",
            "nominationValue": [
                "Spirited"
            ],
            "nominationBody": "Being a great leader",
            "nominationDate": "22-12-2023",
            "isNominatorFullUser": true,
            "isNominationInstant": false,
            "isAward": true,
            "isReleased": true,
            "__v": 0,
            "releaseDate": "22-12-2023"
        },
        {
            "_id": "6583fcd6e2c8545acd85f7bb",
            "recipientUser": "657d7c33d8b97e77efe01931",
            "nominatorFullUser": "657d7c33d8b97e77efe0193c",
            "nominationValue": [
                "Collaborate"
            ],
            "nominationBody": "Great teamwork",
            "nominationDate": "21-12-2023",
            "isNominatorFullUser": true,
            "isNominationInstant": true,
            "isAward": false,
            "isReleased": false,
            "releaseDate": "21-12-2023",
            "__v": 0
        },
        // ... more document objects
    ]
}
```

|  |  |
|--|--|
|Endpoint|`GET /nominations/one/nominator/:id`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/one/nominator/:id`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/all/all/nominator/one/nominator/:id)|
|Parameters|**URL Query** *:id* - returns most recent nomination raised by the nominator's id provided. **Request body** none|
|Response| |

**Example**

Request:
```
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/one/nominator/657d7c33d8b97e77efe0193c
```

Response:

```
{
    "Nominations": {
        "_id": "657d7c34d8b97e77efe0194f",
        "recipientUser": "657d7c33d8b97e77efe01935",
        "nominatorFullUser": "657d7c33d8b97e77efe0193c",
        "nominationValue": [
            "Commitment"
        ],
        "nominationBody": "Ed is also a great guy!",
        "nominationDate": "02-12-2023",
        "isNominatorFullUser": true,
        "isNominationInstant": true,
        "isAward": false,
        "isReleased": false,
        "releaseDate": null,
        "__v": 0
    }
}
```

|  |  |
|--|--|
|Endpoint|`GET /nominations/all/nominator/:id`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/all/nominator/:id`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/all/all/nominator/:id)|
|Parameters|**URL Query** *:page* - returns all nominations, raised by the nominator's id provided. **Request body** none |
|Response||

**Example**

Request:
```
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/all/nominator/:id
```

Response:

```
{
    "Nominations": [
        {
            "_id": "657d7c34d8b97e77efe0194f",
            "recipientUser": "657d7c33d8b97e77efe01935",
            "nominatorFullUser": "657d7c33d8b97e77efe0193c",
            "nominationValue": [
                "Commitment"
            ],
            "nominationBody": "Ed is also a great guy!",
            "nominationDate": "02-12-2023",
            "isNominatorFullUser": true,
            "isNominationInstant": true,
            "isAward": false,
            "isReleased": false,
            "releaseDate": null,
            "__v": 0
        },
        {
            "_id": "657e8472642ef3da540d1b6b",
            "recipientUser": "657d7c33d8b97e77efe01931",
            "nominatorFullUser": "657d7c33d8b97e77efe0193c",
            "nominationValue": [
                "Spirited"
            ],
            "nominationBody": "Bless his soul. Give him ice cream.",
            "nominationDate": "16-12-2023",
            "isNominatorFullUser": true,
            "isNominationInstant": true,
            "isAward": false,
            "isReleased": false,
            "releaseDate": "16-12-2023",
            "__v": 0
        },
        // ... more document objects
    ]
}
```


|  |  |
|--|--|
|Endpoint|`GET /nominations/one/recipient/:id`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/one/recipient/:id`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/all/all/nominator/one/recipient/:id)|
|Parameters|**URL Query** *:id* - returns the recent nomination raised to the recipient's id provided. **Request body** none|
|Response| |

**Example**

Request:
```
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/one/recipient/657d7c33d8b97e77efe0193c
```

Response:

```
{
    "Nominations": {
        "_id": "657d7c34d8b97e77efe01955",
        "recipientUser": "657d7c33d8b97e77efe0193c",
        "nominatorFullUser": "657d7c33d8b97e77efe01935",
        "nominationValue": [
            "Commitment"
        ],
        "nominationBody": "Katie deserves this because of the thing what she did at the time.",
        "nominationDate": "02-11-2023",
        "isNominatorFullUser": true,
        "isNominationInstant": true,
        "isAward": true,
        "isReleased": true,
        "releaseDate": null,
        "__v": 0
    }
}
```

|  |  |
|--|--|
|Endpoint|`GET /nominations/one/nomination/:id`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/one/nomination/:id`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/one/nomination/:id)|
|Parameters|**URL Query** *:id* - returns the Nomination document object with ID specified in the URL. **Request body** none|
|Response| |

**Example**

Request:
```
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/one/nomination/657d7c34d8b97e77efe01955
```

Response:

```
{
    "Nominations": {
        "_id": "657d7c34d8b97e77efe01955",
        "recipientUser": "657d7c33d8b97e77efe0193c",
        "nominatorFullUser": "657d7c33d8b97e77efe01935",
        "nominationValue": [
            "Commitment"
        ],
        "nominationBody": "Katie deserves this because of the thing what she did at the time.",
        "nominationDate": "02-11-2023",
        "isNominatorFullUser": true,
        "isNominationInstant": true,
        "isAward": true,
        "isReleased": true,
        "releaseDate": null,
        "__v": 0
    }
}
```

|  |  |
|--|--|
|Endpoint|`POST /nominations/new`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/new`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/new)|
|Parameters|**Request body** key/value pairs, as described in the below table|
|Response|A JSON object with the new Nomination document, including values provided in the request, along with *_id* for the nomination id.|

> [!NOTE] Valid key/value pairs for creating a new record:

|Key|Value|Description|
|--|--|--|
|recipientUser|string, required|The ID of the person receiving the recognition|
|nomintaorFullUser|string, optional|The ID of the person submitting the recognition, if a full user|
|NominatorBasicUser|object, optional|Used where the person submitting is not a full user|
|.basicName|object, optional|Object consisting of .first and .last|
|.first|string, optional|Non-full user's first name|
|.last|string, optional|Non-full user's last name|
|.basicEmail|string, optional|Non-full-user's email address|
|nominationValue|string, required|Corporate value for which the behaviour is being recognised; predefined list|
|nominationBody|string, required|Reason for recognition. Cannot be blank|
|nominationDate|string, required, D-MM-YYYY format|Date the recognition was submitted|
|isNominatorFullUser|boolean, required, default:false|true is the user is a full user of the application|
|isNominationInstant|boolean, required, default:false|true if the recognition is instant; false if recognition is a nomination for an official award|
|isAward|boolean, required, default:false|true, where the Senior Manager has promoted the nomination to an award|
|isReleased|boolean, required, default:false|true, where the Senior Manager released the nominations and award winner posts to users' ddashboards|
|releaseDate|string, optional, allow null|captures the date the recognition is released to dashboards|

**Example**

Request:
```
POST https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/new

REQUEST BODY

{
    "recipientUser": "657d7c33d8b97e77efe0193c",
    "nominatorFullUser": "657d7c33d8b97e77efe01935",
    "nominationValue": "Commitment",
    "nominationBody": "Katie has perseverence and fortitude.",
    "nominationDate": "24-12-2023",
    "isNominatorFullUser": true,
    "isNominationInstant": true,
    "isAward": false,
    "isReleased": true,
    "releaseDate": "24-12-2023"
}
```

Response:

```
{
    "Nomination": {
        "recipientUser": "657d7c33d8b97e77efe0193c",
        "nominatorFullUser": "657d7c33d8b97e77efe01935",
        "nominationValue": [
            "Commitment"
        ],
        "nominationBody": "Katie has perseverence and fortitude.",
        "nominationDate": "24-12-2023",
        "isNominatorFullUser": true,
        "isNominationInstant": true,
        "isAward": false,
        "isReleased": true,
        "releaseDate": "24-12-2023",
        "_id": "65878017c3b522e42ebe9ad8",
        "__v": 0
    }
}
```

|  |  |
|--|--|
|Endpoint|`PATCH /nominations/update/nom/:id`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/update/nom/:id`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/update/nom/:id)|
|Parameters|**URL Query** *:id* - finds the Nomination document object with ID specified in the URL. **Request body** the fields requiring an state change, but is restricted to: *nominationId* legacy code and is optional - id is already provided in URL query; *isAward* boolean, optional; *isReleased* boolean, optional; *releaseDate* string in D-MM-YYYY format|
|Response|A JSON object with the updated Nomination. |

**Example**

Request:
```
PATCH https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/update/nom/65878017c3b522e42ebe9ad8

REQUEST BODY
{
    "isAward": true,
    "isReleased": true,
    "releaseDate": "24-12-2023"
}
```

Response:

```
{
    "_id": "65878017c3b522e42ebe9ad8",
    "recipientUser": "657d7c33d8b97e77efe0193c",
    "nominatorFullUser": "657d7c33d8b97e77efe01935",
    "nominationValue": [
        "Commitment"
    ],
    "nominationBody": "Katie has perseverence and fortitude.",
    "nominationDate": "24-12-2023",
    "isNominatorFullUser": true,
    "isNominationInstant": true,
    "isAward": true,
    "isReleased": true,
    "releaseDate": "24-12-2023",
    "__v": 0
}
```

|  |  |
|--|--|
|Endpoint|`DELETE /nominations/delete/:id`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/delete/:id`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/delete/:id)|
|Parameters|**URL Query** *:id* - is matched against `id` within the Nomination documents, and one matching document is returned and deleted. **Request body** none|
|Response|Returns a JSON object with Nomination document. passwordHash is not returned.|

**Example**

Request:
```
DELETE https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/delete/65878017c3b522e42ebe9ad8
```

Response:

```
{
    "Nominations": {
        "_id": "65878017c3b522e42ebe9ad8",
        "recipientUser": "657d7c33d8b97e77efe0193c",
        "nominatorFullUser": "657d7c33d8b97e77efe01935",
        "nominationValue": [
            "Commitment"
        ],
        "nominationBody": "Katie has perseverence and fortitude.",
        "nominationDate": "24-12-2023",
        "isNominatorFullUser": true,
        "isNominationInstant": true,
        "isAward": true,
        "isReleased": true,
        "releaseDate": "24-12-2023",
        "__v": 0
    }
}
```



#### /comments


## R6 Deploy the application to a cloud hosting service

### API
The API was deployed to Heroku - 

The Database was deployed to Mongo Atlas - 

The front end was deployed to Netlify - 

## R7 Produce an application with an intuitive user interface



## R8 Provides evidence of user testing



## R9 Utilises a formal testing framework
