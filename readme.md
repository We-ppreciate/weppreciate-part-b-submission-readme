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
|Endpoint:|`GET /`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/)|
|Parameters|None|
|Response|Returns a JSON object with the following properties: `message` - a static reponse from the server|

**Example**

Request:
```

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
|Endpoint:|`POST /auth/login`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/auth/login`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/auth/login)|
|Parameters|*email*: string; *password*: sting|
|Response|Returns a JSON object with the following properties: *id* - the document id from the User collection; *name.first* - first name of the user; *name.last* - last name of the user; *businessUnit* - the business unit of the user; *lineManbagerId* - the id of the User document, linked as the user's line manager; *userTagLine* - self-supplied bio or tagline of the user; *userPhotoKey* - the public URL of the user's photo. In the client's application, this would be obtained from Azure AD, and this would be applied as the application was integrated with existing corporate structure and security needs; *isFullUser* - boolean to indicate whether the user had full access or was a guest user; *isLineManager* - boolean used for Line Manager restricted access authorisation; *isAdmin* - boolean used for Admin restricted access authorisation; *token* JWT returned to the user and used for authentication as they use the service. The JWT has been set with a 7-day expiry, allowing the client to test and explore the service without the inconveience of a short validity period. In the commercial applciation, the authentication would be moved to SAML SSO through Azure, aligning with the client's requirements.|

**Example**

Request:
```
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
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOiI2NTdkN2MzM2Q4Yjk3ZTc3ZWZlMDE5MzEiLCJpYXQiOjE3MDMzMzE1MjksImV4cCI6MTcwMzkzNjMyOX0.MGxXGoJx-qJCAnb_wqslMds0vwAlwuFmv0lHCKSV-BQ"
}
```


|  |  |
|--|--|
|Endpoint:|`PATCH /auth/reset/:id`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/auth/reset/:id`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/auth/reset/:id)|
|Parameters|**URL query** *:id* - forms the query within the URL and is the id of the account requiring the password reset; **request body** *newPassword*: string|
|Response|Returns a JSON object with the following properties: **message** |

**Example**

Request:
```
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
|Endpoint:|`GET /users/all`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/all`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/all)|
|Parameters|none|
|Response|*message* - a welcome message, depending on whether the requestor has isAdmin: true or false; Returns a JSON object with an array of all user objects in the User collection. Note: passwordHashes are not returned in the array.|

**Example**

Request:
```

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
|Endpoint:|`GET /users/all/fullusers`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/all/fullusers/`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/all/fullusers/)|
|Parameters|none|
|Response|Returns a JSON object with an array of all user objects in the User collection, where fullUser: true. Note: passwordHashes are not returned in the array.|

**Example**

Request:
```

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
|Endpoint:|`GET /users/one/id/:id`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/one/id/:id`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/one/id/:id)|
|Parameters|**URL Query** *:id* is the id of the User document to be returned; **Request body** none.|
|Response|Returns a JSON object with the User document, with matching id. passwordHash is not returned.|

**Example**

Request:
```

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
|Endpoint:|`GET /users/one/name/:first/:last`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/usersone/name/:first/:last`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/one/name/:first/:last)|
|Parameters|**URL Query** *:first* is the full name.first within the desired User document - note this is not case sensitive; *:last*: is the full name.last within the desired user document - note this is not case sensitive; **Request body** none.|
|Response|Returns a JSON object with one User document, with matching name.first AND name.second. passwordHash is not returned.|

**Example**

Request:
```

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
|Endpoint:|`GET /users/search/:string`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/search/:string`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/search/:string)|
|Parameters|**URL Query** *:string* - `name.first` and `name.last` within  ; **Request body** none.|
|Response|Returns a JSON object with one User document, with matching name.first AND name.second. passwordHash is not returned.|

**Example**

Request:
```

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


## R6 Deploy the application to a cloud hosting service

### API
The API was deployed to Heroku - 

The Database was deployed to Mongo Atlas - 

The front end was deployed to Netlify - 

## R7 Produce an application with an intuitive user interface



## R8 Provides evidence of user testing



## R9 Utilises a formal testing framework
