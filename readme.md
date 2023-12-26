# T3A2-B Katie Lock and Nate Picone

## You work hard. We'ppreciate you

### We'ppreciate - a full stack MERN application. Readme for Part-B submission

## Helpful links

[Repo for T3A2-A submission readme.md](https://github.com/We-ppreciate/weppreciate-part-a)

[Part-B Backend repo](https://github.com/We-ppreciate/weppreciate-part-b-backend)

[Part-B Backend deployment](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/)

[Part-B Frontend repo](https://github.com/We-ppreciate/weppreciate-part-b-frontend)

[Part-B Frontend deployment](https://playful-pudding-8faa4e.netlify.app/)

### Notion

[We'ppreciate Client pack](https://weppreciate.notion.site/We-pprecite-Client-Pack-586c89a97cdb444993671762320bb764?pvs=4)

[Tasks](https://weppreciate.notion.site/75b89fa68e894f5f954787c5eeef489f?v=989fd6fd0ad146e4af4e6ada44b70641&pvs=4)

[Projects](https://weppreciate.notion.site/fd3c53db9a1f4e27b59dcc063b46864a?v=41b6032216174cf59edfa04a8e317941&pvs=4)

[Sprint board](https://weppreciate.notion.site/8230b9bd9475472a97c6031be273cdbc?v=75f37625837d4278a914328bf30de9e1&pvs=4)

[Sprints](https://weppreciate.notion.site/096aac0b89cd4d4ba7fcd0b02ce6187a?v=b9b2dde3fc2e4b53b59e3509f8c3d2b2&pvs=4)

[Meetings](https://weppreciate.notion.site/33e465ae7b2c4bdf9a261acbbf5167e0?v=00a1f910091e4b5c98a984ca396519f6&pvs=4)

[Docs](https://weppreciate.notion.site/59318e1ab6b840efbb38de4eb82117ec?v=c5f3f0c8a680426482b9cb31b7ec58ce&pvs=4)

## R1 At minimum use MongoDB, Express, React, Node

We used the following packages, frameworks and technology:

### Backend

#### Node.js

Framework for all API server code.

#### npm

Used for package installation and management.

#### MongoDB

Used as the sole database. Structure contains 4x collections (Users, Nominations, Values, Comments), with respective documents contained within.

#### ExpressJS

Used as the API router, handing endpoints and logic.

#### Google Cloud Storage

Profile photos and award category photos were uploaded to GCS, and given public URLs. We understand that in a commercial application this is not a desirable scenario. As the enterprise application would pull profile photos from Azure, through SAML SSO, and these profile pics were AI generated, there is no current privacy risk.

#### bcrypt

bcrypt has been deployed to handle salting and hashing of user passwords, in this case, applying the default 10 rounds of hashing. In the enterprise deployment, Azure SAML SSO is the security structure required by the client.

Hashed passwords are saved to User documents, to allow for comparison on routes where JWT is required to be supplied, confirming legitimate access to the endpoint.

#### cors

Cors was required to allow the front end on Netlify to communicate with the API, deployed to Heroku.

#### dotenv

dotenv allows sensitive variables, such as usernames and passwords, to be obscured and saved to a .env file, then used as variables through the application.

#### jsonwebtoken

JWT was deployed to assign and decrypt user tokens, to confirm legitimate access to the application. In this case, the token validity was set to 7 days, which is well above the recommended validity. This was to allow for uninterrupted client UAT, and further development, prior to potential enterprise deployment.

Given the pending change to security used by the application, and the lack of real data, we decided to take this approach. If actual user data were to be included int eh application, we would shorten the token validity to something like 24 hours, and add a refresh token, to allow for automatic token refreshing.

#### mongoose

mongoose creates the schema, or data structure, used for the mongo database. This allows consistency across documents in the database.

#### nodemon

Added to the dev environment to resume the local development server, after errors. An essential part of the development process.

#### joi

`joi` was added for input validation and extended with `joi/date`. Used for most of this API's POST and PATCH routes, Joi creates an additional schema to those created by Mongoose for the purpose of data validation, allowing for clearer responses where data formatting is not consistent with the needs of the database.

### Frontend

#### React

React was used as the JavaScript framework for the frontend portion of the application's code. In-built React functionality that was used in the application include useState and useEffect hooks.

#### npm

Used for package installation and management.

#### react-router-dom

React Router DOM was used to manage routing for the different pages within the single-page-application. BrowserRouter, Link, useNavigate and useParams were used to render the desired page based on the URL and user actions.

#### MUI

MUI (formerly known as Material UI) is a React design system. MUI components were implemented into the application to save time on styling and provide a consistent look and feel across the application. As this was the first time using MUI and there was a learning curve, regular CSS was also used to make additional styling overrides to the standard MUI styling/themes.

#### jwt-decode

jwt-decode was used as part of the authentication provider, to check whether a JWT token stored in local storage was still valid - and redirecting the user to login if it had expired/was invalid.

#### jest

Jest was deployed for testing. Limited unit testing has been applied to the API, as most testing was manual.

## R2 Write well designed code

This assessment requirement specified the following:
- Separates the program into modules that each deal with one particular focus, or concern
- Demonstrates DRY (Don’t Repeat Yourself) coding principles
- Uses appropriate libraries
- Demonstrates good code flow control for user stories
- Applies Object Oriented (OO) principles/patterns
- Uses appropriate data structures

We would like to think that we have done a reasonable job of achieving the above requirements within our time and ability constraints, but we are no experts. Therefore we will let you - our educators - decide on this one!

## R3 Employ and utilise proper source control methodology (git)

GitHub desktop was used throughout, where an organisation was created, and four repos were created:

1. Part A
1. Part B backend
1. Part B front end
1. Part B readme

For Part B backend and frontend, feature branches were created to actively work on - with no changes being permitted directly on main, and pull requests were required.

We then included an additional rule within GitHub, where feature branches could not be automatically merged into main without the review and approval of the other. This kept us across changes being made by the other teammate, and allowed us to catch several potential issues before they became actual issues.

## R4 Demonstrate your ability to work in a team

### Use a recognised project management methodology

We continued our application of Agile methodology throughout this project, keeping user stories at the heart of our deliverables, while burning down our sprints.

We elected to run 6 one-week sprints, and while we understand the regular timespan of a sprint to be two weeks, we felt one week allowed us to more comfortably divide and pace our task delivery. In practise this meant most weeks had items that were incomplete and carried over, but we stand by the decision and the benefit it gave us through planning and development.

As sprints were burned down, and at the end of each, a review took place to discuss what was achieved and closed, what which items were delayed, along with dependencies, or any downstream impacts.

Each sprint had three stand-ups scheduled, in addition to the communication carried out over Discord and through notes, comments and "@" through Notion's platform. On occasion, we were unable to complete all standups in a week, and in those cases, we ran an "async" standup, where we updated each other on progress and asked questions, not in real time.

We continued utilising Standup Meeting records, Task delegation updating and control, timelines, and kanban throughout.

Screenshots of our workspace at the end of each sprint:

#### End of Sprint 2

![Documents list at the end of Sprint 2](./docs/Notion-PM-screenshots/end-wk-2/docs-end-sprint-2.jpg)

![Projects at the end of Sprint 2](./docs/Notion-PM-screenshots/end-wk-2/project-end-sprint-2.jpg)

![Sprint task board end of Sprint 2](./docs/Notion-PM-screenshots/end-wk-2/sprint-board-end-wk-2.jpg)

![Stand-up 1 in Sprint 2](./docs/Notion-PM-screenshots/end-wk-2/standup-1-wk-2.jpg)

![Stand-up 2 in Sprint 2](./docs/Notion-PM-screenshots/end-wk-2/standup-2-wk-2.jpg)

![Task timeline, end of Sprint 2](./docs/Notion-PM-screenshots/end-wk-2/task-timeline-end-wk-2.jpg)

![Tasks by Project at end of Sprint 2](./docs/Notion-PM-screenshots/end-wk-2/tasks-by-project-end-wk-2.jpg)

#### End of Sprint 3

![Documents list at the end of Sprint 3](./docs/Notion-PM-screenshots/end-wk-3/docs-end-sprint-3.jpg)

![Projects at the end of Sprint 3](./docs/Notion-PM-screenshots/end-wk-3/projects-end-sprint-3.jpg)

![Sprint task board end of Sprint 3](./docs/Notion-PM-screenshots/end-wk-3/sprint-board-end-wk-3.jpg)

![Stand-up 1 in Sprint 3](./docs/Notion-PM-screenshots/end-wk-3/standup-1-wk-3.jpg)

![Stand-up 2 in Sprint 3](./docs/Notion-PM-screenshots/end-wk-3/standup-2-wk-3.jpg)

![Task timeline, end of Sprint 3](./docs/Notion-PM-screenshots/end-wk-3/task-timeline-end-wk-3.jpg)

![Tasks by Project at end of Sprint 3 (part a)](./docs/Notion-PM-screenshots/end-wk-3/tasks-by-project-end-sprint-3a.jpg)

![Tasks by Project at end of Sprint 3 (part b)](./docs/Notion-PM-screenshots/end-wk-3/tasks-by-project-end-wk-3b.jpg)

#### End of Sprint 4

![Documents list at the end of Sprint 4](./docs/Notion-PM-screenshots/end-wk-4/docs-end-sprint-4.jpg)

![Projects at the end of Sprint 4](./docs/Notion-PM-screenshots/end-wk-4/project-end-sprint-4.jpg)

![Sprint task board end of Sprint 4](./docs/Notion-PM-screenshots/end-wk-4/sprint-board-end-wk-4.jpg)

![Stand-up 1 in Sprint 4](./docs/Notion-PM-screenshots/end-wk-4/standup-1-wk-4.jpg)

![Stand-up 2 in Sprint 4](./docs/Notion-PM-screenshots/end-wk-4/standup-2-wk-4.jpg)

![Stand-up 2 in Sprint 4](./docs/Notion-PM-screenshots/end-wk-4/standup-3-wk-4.jpg)

![Task timeline, end of Sprint 4](./docs/Notion-PM-screenshots/end-wk-4/task-timeline-end-wk-4.jpg)

![Tasks by Project at end of Sprint 4 (part a)](./docs/Notion-PM-screenshots/end-wk-4/task-by-project-end-wk-4.jpg)

#### End of Sprint 5

![Documents list at the end of Sprint 4](./docs/Notion-PM-screenshots/end-wk-5/docs-end-sprint-5.jpg)

![Projects at the end of Sprint 4](./docs/Notion-PM-screenshots/end-wk-5/project-end-sprint-5.jpg)


![Meetings at end of project](./docs/Notion-PM-screenshots/end-wk-5/meetings-end-wk-5.jpg)

![Task timeline, end of Sprint 4](./docs/Notion-PM-screenshots/end-wk-5/task-timeline-wk-5.jpg)

![Tasks by Project at end of Sprint 4 (part a)](./docs/Notion-PM-screenshots/end-wk-5/tasks-by-project-wk-5.jpg)

### Use a recognised task delegation methodology

The allocation of tasks were essentially split into two groupings: the backend plus databases, and the frontend plus styling. We discussed the allocation of duties, and agreed that Katie's skills were stronger with React and styling, and that while Nate was keen to improve his frontend skills, our plan was ambitious for the time available, which meant we needed to aim for maximum efficiency.

We continued the path we laid down in Part-A, with dividing the entire project into six sub-projects:

1. Application Requirements
2. Application Design
3. Database
4. Back End
5. Front End
6. Rubric fulfilment

![Demonstrating the sub-projects. This was taken toward the end of Part-B, so many of the tasks making up the project have been completed.](./docs/demonstrating-projects.jpg)

Requirements and Design were mostly completed in Part-A.

Within the remaining Sub-projects, Tasks were allocated a three-tiered effort score, of low, moderate, or high effort, which was determined based on level of difficulty, level of time required, or a combination of both. We discussed these in out three-times-per-week stand-ups, as the project progressed, and this was partly to sense check the rating, but was mostly as a way to check in on each other's workload and ensure relative balance in workload and task allocation. A higher number of low effort tasks was equivalent with a moderate task, etc. This was not a scientific approach, but gave a clear, approximate indication and worked well.

Although dependencies were not well captured in Notion, these were also discussed as we planned our next focusses for delivery. It was Nate's intent to deliver API functionality just in time to allow Katie to develop the front end. For the most part, this also worked exceedingly  well, and allowed whoever was waiting for a dependency to finish, to take the next task of highest value, whether that be the next dependency, some administration or rubric requirements, or pick up some non-time-sensitive activity, such as styling.

Prioritisation of tasks, and continually assessing them against our Minimum Viable Product (MVP) criteria were also key to our development cycles.

![Screenshot demonstrating tasks, which were used as discussion points through stand-ups, for dependency identification, and task scheduling and allocation](./docs/example-tasks.jpg)

## R5 Produce a working application that meets client and user needs

Around Sprint 3 (we started at sprint 0), we presented a [Client Pack](https://weppreciate.notion.site/We-pprecite-Client-Pack-586c89a97cdb444993671762320bb764?pvs=4) for alignment and requirements sign off. While this ideally should have been completed earlier, and delivered through a meeting, the operational needs of the business meant the client was unavailable, and our timing was a little behind schedule. We presented this in an email, inviting the client to review and respond with questions.

![We'ppreciate Client Pack](./docs/weppreciate-client-pack.jpg)

![Client confirmation of requirements](./docs/weppreciate-client-requirements-signoff.jpg)

Due to the client being closed for the end of year period, we are unable to get full sign off from the client before submitting this project for assessment.

We did, however, align with the client at multiple points through the development cycle, and invited both partial User Acceptance Testing and feedback from the client. We recognise the client is on holiday, driving from Melbourne to Western Australia. Coupled with UAT being sought prior to the completion of the project, UAT was incomplete, but the client was able to provide some feedback and identify some defects, which were welcome, and the defects were addressed.

![Client responding to UAT, along with feedback](./docs/client-UAT.jpg)

Were this a commercial project, we would seek UAT, feedback and acceptance from the client's delegate, in her absence.

### API Routes

#### Errors

This API uses the following error codes:

- `400 Bad Request`: Often handled by ErrorController.js, the 400 Error Response will reply with `Your intent is good but the request was bad. ${statusCode}, ${err.message}`, but on some routes, custom 400 error messages are used to return more specific information about what cause it. This error also covers expired token usage.
- `401 Unauthorised`: Handled by ErrorController.js, where the user is not logged in, and responded to with the message `It looks like I'm missing your login credentials. Let's have another go. ${statusCode}, ${err.message}`
- `403 Forbidden`: Generally handled within the route, where the required level of access is not he ld by the user - generally isAdmin or isSeniorManager. A generic 403 is available in ErrorController.js, should it be needed, with format of `You are not authorised to do that. We'pologise. ${statusCode}, ${err.message}`
- `404 Not found`: Generally handled by ErrorController.js, some in-route 404 errors are generated where requested records are not found. The generic 404 has the format `This is not the page you are looking for. ${statusCode}, ${err.message}`
- `500 Internal Server Error`: Has been implemented in two ways. If a 500 error is the error generated by the application, the message appears as `Sorry. That's a problem on our side. Mavis is looking into it now... well, after her tea. ${statusCode}: ${err.message}`, and an additional catch-all error has been created to cover any other error, with message `Sorry. That\'s a problem on our side. Look like Mavis spilled her tea on the server. ${statusCode}, ${err.message}`

#### Base URL

|  |  |
|--|--|
|Endpoint|`GET /`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/)|
|Parameters|None|
|Response|Returns a JSON object with the following properties: `message` - a static response from the server|

EXAMPLE:

Request:

``` javascript
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/
```

Response:

``` javascript
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
|Response|Returns a JSON object of the user's User document, with the following properties: *id* - the document id from the User collection; *name.first* - first name of the user; *name.last* - last name of the user; *businessUnit* - the business unit of the user; *lineManagerId* - the id of the User document, linked as the user's line manager; *userTagLine* - self-supplied bio or tagline of the user; *userPhotoKey* - the public URL of the user's photo. In the client's application, this would be obtained from Azure AD, and this would be applied as the application was integrated with existing corporate structure and security needs; *isFullUser* - boolean to indicate whether the user had full access or was a guest user; *isLineManager* - boolean used for Line Manager restricted access authorisation; *isAdmin* - boolean used for Admin restricted access authorisation; *token* JWT returned to the user and used for authentication as they use the service.|
|Note|The JWT has been set with a 7-day expiry, allowing the client to test and explore the service without the inconvenience of a short validity period. In the commercial application, a better application would be to carry a shorter validity, such as 24 hours, with a longer refresh token, but on deployment for the client, the authentication would be moved to SAML SSO, through Azure, we did not implement the refresh token in this case. *passworHash* is not sent in the response|

EXAMPLE:

Request:

``` javascript

POST https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/auth/login

REQUEST BODY

{
  "name": "your.name@yourcompany.com",
  "password": "youRSup3rS3cRet"
}
```

Response:

``` javascript
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

EXAMPLE:

Request:

``` javascript
PATCH https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/auth/reset/657d7c33d8b97e77efe01931

REQUEST BODY

{
  "newPassword": "youRSup3rS3cRetNEW"
}
```

Response:

``` javascript
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
|Response|*message* - a welcome message, depending on whether the requester has isAdmin: true or false; Returns a JSON object with an array of all user objects in the User collection. Note: passwordHashes are not returned in the array.|
|Note|The reponse message serves no function, other than it being legacy code from early testing.|

EXAMPLE:

Request:

``` javascript
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/all
```

Response:

``` javascript
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

EXAMPLE:

Request:

``` javascript
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/all/fullusers/
```

Response:

``` javascript
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

EXAMPLE:

Request:

``` javascript
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/one/id/657d7c33d8b97e77efe01931
```

Response:

``` javascript
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
|Parameters|**URL Query** *:first* is the full `name.first` within the desired User document - note this is not case sensitive; *:last*: is the full `name.last` within the desired user document - note this is not case sensitive; **Request body** none.|
|Response|Returns a JSON object with one User document, with matching `name.first` AND `name.last`. passwordHash is not returned.|

EXAMPLE:

Request:

``` javascript
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/usersone/name/nate/picone
```

Response:

``` javascript
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
|Parameters|**URL Query** *:string* - is matched within `name.first` and `name.last` within the User documents, and matching documents are added to an array - note that the search string is case insensitive and, as currently applied, can only be a contiguous string without spaces. Future iterations will look to expand this functionality further; **Request body** none.|
|Response|Returns a JSON object with User documents. passwordHash is not returned.|

EXAMPLE:

Request:

``` javascript
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/search/ar
```

Response:

``` javascript
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

EXAMPLE:

Request:

``` javascript
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/all/manager/657d7c33d8b97e77efe01939
```

Response:

``` javascript
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

EXAMPLE:

Request:

``` javascript
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/one/alex.greatbeard@yourcompany.com
```

Response:

``` javascript
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

EXAMPLE:

Request:

``` javascript
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

``` javascript
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

EXAMPLE:

Request:

``` javascript
PATCH https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/update/self/657d7c33d8b97e77efe01931

REQUEST BODY

{
    "userTagLine": "I'm not new here any more. Still excited!"
}

```

Response:

``` javascript
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

EXAMPLE:

Request:

``` javascript
PATCH https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/update/self/657d7c33d8b97e77efe01931

REQUEST BODY

{
    "userTagLine": "I'm not new here any more. Still excited!"
}

```

Response:

``` javascript
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

EXAMPLE:

Request:

``` javascript
PATCH https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/update/admin/657d7c33d8b97e77efe01931

REQUEST BODY

{
    "isLineManager": true
}

```

Response:

``` javascript
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

EXAMPLE:

Request:

``` javascript
DELETE https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/users/delete/admin/65875811253eeecd52862523
```

Response:

``` javascript
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

EXAMPLE:

Request:

``` javascript
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/all
```

Response:

``` javascript
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

EXAMPLE:

Request:

``` javascript
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/all/recipient/657d7c33d8b97e77efe01935
```

Response:

``` javascript
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

EXAMPLE:

Request:

``` javascript
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/all/nominator/katie/lock
```

Response:

``` javascript
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
|Parameters|**URL Query** *:page* - returns all nominations, in descending submission date order, in a pagination format, with 20 items per page. **Request body** none |
|Response||

EXAMPLE:

Request:

``` javascript
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/page/1
```

Response:

``` javascript
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

EXAMPLE:

Request:

``` javascript
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/one/nominator/657d7c33d8b97e77efe0193c
```

Response:

``` javascript
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

EXAMPLE:

Request:

``` javascript
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/all/nominator/:id
```

Response:

``` javascript
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

EXAMPLE:

Request:

``` javascript
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/one/recipient/657d7c33d8b97e77efe0193c
```

Response:

``` javascript
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

EXAMPLE:

Request:

``` javascript
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/one/nomination/657d7c34d8b97e77efe01955
```

Response:

``` javascript
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
|nominatorFullUser|string, optional|The ID of the person submitting the recognition, if a full user|
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
|isReleased|boolean, required, default:false|true, where the Senior Manager released the nominations and award winner posts to users' dashboards|
|releaseDate|string, optional, allow null|captures the date the recognition is released to dashboards|

EXAMPLE:

Request:

``` javascript
POST https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/new

REQUEST BODY

{
    "recipientUser": "657d7c33d8b97e77efe0193c",
    "nominatorFullUser": "657d7c33d8b97e77efe01935",
    "nominationValue": "Commitment",
    "nominationBody": "Katie has perseverance and fortitude.",
    "nominationDate": "24-12-2023",
    "isNominatorFullUser": true,
    "isNominationInstant": true,
    "isAward": false,
    "isReleased": true,
    "releaseDate": "24-12-2023"
}
```

Response:

``` javascript
{
    "Nomination": {
        "recipientUser": "657d7c33d8b97e77efe0193c",
        "nominatorFullUser": "657d7c33d8b97e77efe01935",
        "nominationValue": [
            "Commitment"
        ],
        "nominationBody": "Katie has perseverance and fortitude.",
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

EXAMPLE:

Request:

``` javascript
PATCH https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/update/nom/65878017c3b522e42ebe9ad8

REQUEST BODY
{
    "isAward": true,
    "isReleased": true,
    "releaseDate": "24-12-2023"
}
```

Response:

``` javascript
{
    "_id": "65878017c3b522e42ebe9ad8",
    "recipientUser": "657d7c33d8b97e77efe0193c",
    "nominatorFullUser": "657d7c33d8b97e77efe01935",
    "nominationValue": [
        "Commitment"
    ],
    "nominationBody": "Katie has perseverance and fortitude.",
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

EXAMPLE:

Request:

``` javascript
DELETE https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/nominations/delete/65878017c3b522e42ebe9ad8
```

Response:

``` javascript
{
    "Nominations": {
        "_id": "65878017c3b522e42ebe9ad8",
        "recipientUser": "657d7c33d8b97e77efe0193c",
        "nominatorFullUser": "657d7c33d8b97e77efe01935",
        "nominationValue": [
            "Commitment"
        ],
        "nominationBody": "Katie has perseverance and fortitude.",
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

|  |  |
|--|--|
|Endpoint|`GET /comments/all`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/comments/all`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/comments/all)|
|Parameters|none|
|Response|Returns an array of all document objects in the Comments collection.|

EXAMPLE:

Request:

``` javascript
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/comments/all
```

Response:

``` javascript
[
    {
        "_id": "6580a58f14332fff07a04c76",
        "nominationId": "657d7c34d8b97e77efe01955",
        "commenterId": "657d7c33d8b97e77efe01931",
        "commentBody": "Nice work Katie!",
        "__v": 0,
        "commentDate": "2023-12-24T02:39:17.361Z"
    },
    {
        "_id": "6580a58f14332fff07a04c75",
        "nominationId": "657d7c34d8b97e77efe01955",
        "commenterId": "657d7c33d8b97e77efe01935",
        "commentBody": "Nice work Katie!",
        "__v": 0,
        "commentDate": "2023-12-24T02:39:17.362Z"
    },
    // ... more document objects
]
```

|  |  |
|--|--|
|Endpoint|`GET /comments/all/nomination/:id`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/comments/all/nomination/:id`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/comments/all/nomination/:id)|
|Parameters|**URL Query** *:id* is the Nomination id. It is used to retrieve all comments linked to the nomination|
|Response|Returns an array of all Comment objects linked to the provided Nomination.|

EXAMPLE:

Request:

``` javascript
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/comments/all/nomination/657d7c34d8b97e77efe01955
```

Response:

``` javascript
[
    {
        "_id": "6580a58f14332fff07a04c76",
        "nominationId": "657d7c34d8b97e77efe01955",
        "commenterId": "657d7c33d8b97e77efe01931",
        "commentBody": "Nice work Katie!",
        "__v": 0,
        "commentDate": "2023-12-24T02:48:38.967Z"
    },
    {
        "_id": "6580a58f14332fff07a04c75",
        "nominationId": "657d7c34d8b97e77efe01955",
        "commenterId": "657d7c33d8b97e77efe01935",
        "commentBody": "Nice work Katie!",
        "__v": 0,
        "commentDate": "2023-12-24T02:48:38.968Z"
    }
]
```

|  |  |
|--|--|
|Endpoint|`GET /one/nomination/:id`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/comments/one/nomination/:id`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/comments/one/nomination/:id)|
|Parameters|**URL Query** *:id* is the Comment id. It is used to retrieve one comments, with the id specified.|
|Response|Returns an object of the Comment objects with id provided in the URL.|

EXAMPLE:

Request:

``` javascript
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/comments/one/nomination/6580a58f14332fff07a04c76
```

Response:

``` javascript
{
    "_id": "6580a58f14332fff07a04c76",
    "nominationId": "657d7c34d8b97e77efe01955",
    "commenterId": "657d7c33d8b97e77efe01931",
    "commentBody": "Nice work Katie!",
    "__v": 0,
    "commentDate": "2023-12-24T02:50:59.002Z"
}
```

|  |  |
|--|--|
|Endpoint|`GET /all/user/:id`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/comments/all/user/:id`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/comments/all/user/:id)|
|Parameters|**URL Query** *:id* is the `commenterId`, which matches the User id. It is used to retrieve all comments comments, with the id specified.|
|Response|Returns an array of all Comment objects created by the user, with id provided in the URL.|

EXAMPLE:

Request:

``` javascript
GET https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/comments/all/user/657d7c33d8b97e77efe01931
```

Response:

``` javascript
[
    {
        "_id": "6580a58f14332fff07a04c76",
        "nominationId": "657d7c34d8b97e77efe01955",
        "commenterId": "657d7c33d8b97e77efe01931",
        "commentBody": "Nice work Katie!",
        "__v": 0,
        "commentDate": "2023-12-24T02:54:13.847Z"
    },
    {
        "_id": "65875c67dfb25e55787c5a7c",
        "nominationId": "6583bb80d035032876b04baf",
        "commenterId": "657d7c33d8b97e77efe01931",
        "commentBody": "Well done, Ed!",
        "commentDate": "2023-12-23T22:17:11.729Z",
        "__v": 0
    }
]
```

|  |  |
|--|--|
|Endpoint|`POST /post/:id`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/comments/post/:id`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/comments/post/:id)|
|Parameters|**URL Query** *:id* is the id of the Nomination document, allowing a comment to be linked to the Nomination document the user is commenting on. **Request body** *nominationId* the id of the document in the Nomination collection; *commenterId* is the ID of the account creating the comment; *commentBody* the text of the comment; *commentDate* the date the comment was left|
|Response|Returns the object of the comment linked to the Nomination document. |

> [!NOTE] Valid key/value pairs for creating a new record:

|Key|Value|
|--|--|
|nominationId|string, required|
|commenterId|string, required|
|commentBody|string, required|
|commentDate|date, required, format 'D-MM-YYYY'|

EXAMPLE:

Request:

``` javascript
POST https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/comments/post/657d7c34d8b97e77efe01955

REQUEST BODY

{
    "nominationId": "657d7c34d8b97e77efe01955",
    "commenterId": "658760dc985de4ddc824dbd6",
    "commentBody": "Nice work Katie!",
    "commentDate": "24-12-2023"
}
```

Response:

``` javascript
{
    "Comment": {
        "nominationId": "657d7c34d8b97e77efe01955",
        "commenterId": "658760dc985de4ddc824dbd6",
        "commentBody": "Nice work Katie!",
        "commentDate": "24-12-2023",
        "_id": "6587ab356f7308138926be17",
        "__v": 0
    }
}
```

|  |  |
|--|--|
|Endpoint|`PATCH /update/:id`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/comments/update/:id`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/comments/update/:id)|
|Parameters|**URL Query** id of the comment record to be updated. **Request body** *commentBody* the updated comment body|
|Response|Returns the object of the comment linked to the Nomination document, after updating. |

EXAMPLE:

Request:

``` javascript
PATCH https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/comments/update/65875c67dfb25e55787c5a7c

REQUEST BODY

{
    "commentBody": "Kicking goals!"
}
```

Response:

``` javascript
{
    "Comment": {
        "_id": "65878a87c3b522e42ebe9b76",
        "nominationId": "65878a68c3b522e42ebe9b68",
        "commenterId": "657d7c33d8b97e77efe0193c",
        "commentBody": "Kicking goals!",
        "commentDate": "Sun Dec 24 2023 11:33:59 GMT+1000 (GMT+10:00)",
        "__v": 0
    }
}
```

|  |  |
|--|--|
|Endpoint|`DELETE /delete/:id`|
|Route|[`https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/comments/delete/:id`](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/comments/delete/:id)|
|Parameters|**URL Query** id of the comment record to be updated. **Request body** none|
|Response|Returns the object of the comment linked to the Nomination document, after updating. |

EXAMPLE:

Request:

``` javascript
DELETE https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/comments/delete/6587bf16cbd9348c16ac0f42
```

Response:

``` javascript
{
    "Comment": {
        "_id": "6587bf16cbd9348c16ac0f42",
        "nominationId": "65878a68c3b522e42ebe9b68",
        "commenterId": "658760dc985de4ddc824dbd6",
        "commentBody": "Fire!",
        "commentDate": "24-12-2023",
        "__v": 0
    }
}
```

## R6 Deploy the application to a cloud hosting service

[The API was deployed to Heroku here](https://weppreciate-api-05b8eaa3cdc2.herokuapp.com/)

![Screenshot of Heroku deployment, with logs showing activity](./docs/heroku-logs.jpg)

The Database was deployed to Atlas on mongodb.com:
![Screenshot of Atlas GUI on mongodb.com](./docs/atlas-mongobd.jpg)

[The front end was deployed to Netlify](https://playful-pudding-8faa4e.netlify.app/)

![Screenshot of Netlify deploy logs](./docs/netlify-deploy-logs.jpg)

## R7 Produce an application with an intuitive user interface

Our application uses a simple interface with common design elements that can be found in other web applications, to make it easy for users to navigate without any prior experience with it.

The colour scheme is simple and accessible, and all pages have been optimised for mobile and tablet views, in addition to a standard desktop-sized experience.

### Landing page

The root landing page for our application has a simple design, providing the visitor with two options:
- Login
- Learn more

These are clearly actions for the user to take, indicated by the use of a button and a visual icon linked to the action. As we did not build a traditional "marketing website" for our web application with more information about the application available prior to logging in, we linked the users to our GitHub so they could find out more about our project.

![A screenshot of the application landing page](./docs/interface-screenshots/landing-page.png)

### Login page

The login page continues the trend of having a simple user interface. By using a MUI template for a login page, it provides a familiar design structure for a login page - with clearly labelled fields and a submit button.

![A screenshot of the application login page](./docs/interface-screenshots/login-page.png)

### Dashboard page

The dashboard is the first page that a user experiences in our application once logged in. It is the first time they will see the common design elements that are used across the application, such as the header. This header uses a typical design for an application - with a logo that redirects to the dashboard from other pages, a responsive search bar, and their photo (or avatar) in the top-right hand corner rendering a menu. The elements that show in this menu are where a standard user would expect - for example, settings and log out.

![A screenshot of the header menu](./docs/interface-screenshots/header-menu.png)

The dashboard itself has a clear "action item" with the "Send recognition" button being brought to their attention. The posts resemble a typical social media "feed", with the most recent items at the top. While no words are on the action buttons on each post, common design symbols are used here:
- the arrow indicates "expanding" - clicking on this expands and displays comments
- the comment button is obvious to a user, due to the use of the + on it
- the delete button is obvious to an admin user, due to the use of the trash can icon that is typically associated with deleting

![A screenshot of the application dashboard page](./docs/interface-screenshots/dashboard-page.png)

The dashboard is also the first area of the application where a user will experience a modal pop-up. This draws their attention to what action is expected from them by blurring out the background. In line with standard application design elements, there is a "x" icon to close the modal pop-up, and the action on the pop-up is indicated with a button.

![A screenshot of the modal pop-up](./docs/interface-screenshots/modal-popup.png)

### Profile page

Similar to other social media-type platforms, all users have a profile page that displays more information about them, along with posts that are related to them. This makes the interface feel familiar.

![A screenshot of the application profile page](./docs/interface-screenshots/profile-page.png)

### Settings page

The settings page conditionally renders different settings options, based on the user's permissions. Standard users just see their account settings, whilst admins and senior managers have team settings options available to them.

Clicking on each of these settings will either create a modal pop-up, or update the display to a more detailed page to navigate.

![A screenshot of the application settings page](./docs/interface-screenshots/settings-page.png)

The "Manage users" sub-page uses typical design elements of an admin user panel, giving them the option to see existing users, update their records, add new users or delete users:

![A screenshot of the manage users page](./docs/interface-screenshots/manage-users.png)

The "Release awards" sub-page also gives a similar "admin panel" type experience, where authenticated users can see items that need their approval:

![A screenshot of the release awards page](./docs/interface-screenshots/release-awards.png)


## R8 Provides evidence of user testing

### Client user testing

Included earlier, repeating the inclusion of the email. This was sent after completion of user testing.

As noted, the client was on holiday, and driving from Melbourne to Western Australia, so her opportunities to test were limited, but we are grateful for the amount of testing she was able to do.

The feedback allowed some changes to me made in response to the testing conducted.

![Email from client, after user testing](./docs/client-UAT.jpg)

### Front end user testing

Frontend user testing was exported from Notion, and is viewable as a PDF [here]

Screenshots of testing results are also saved in this submission, to `../docs/frontend-user-testing-screenshots/` with the filenames matching the test ID number (ie FE-UT-18.png).

Also viewable on Notion:
![Screenshot of frontend testing page on Notion](./docs/notion-frontend-testing.jpg) at this [URL](https://weppreciate.notion.site/Front-end-manual-testing-5a8b5cf1876b406ba9e167af397996cd?pvs=4)

### Back end user testing

Backend user testing was exported from Notion, and is viewable as a PDF [here](./docs/backend-user-testing/backend-user-testing.pdf).

Screenshots of the Postman results are also saved in this submission, to `../backend-user-testing/backend-testing-screenshots/` with the filenames matching the test ID number (ie UT-1.png).

Also viewable on Notion:
![Screenshot of backend testing page on Notion](./docs/notion-backend-testing.jpg) at this [URL](https://weppreciate.notion.site/Backend-testing-b66ded2a07984aff8566a682a2d77f39?pvs=4)

## R9 Utilises a formal testing framework

Due to time constraints, our testing framework was not as comprehensive as we would have liked. We recognise in a real-world scenario that a larger amount of automated tests should be used in an application of this size.

We conducted very comprehensive manual user testing of both the frontend and backend, as explained above in R8. This formal manual testing was conducted at the very end of our application development, to ensure that additional pull requests did not impact the outcome of the tests.

Informal manual testing was also occurring constantly as we built our application, both in the development and production environments. This was done to give us the reassurance that our code was operating as expected, and that no further regression occurred with new updates.

A small suite of automated tests were written for the frontend of the application using Jest:

![Screenshot of Jest tests running in the development environment](./docs/jest-tests.png)

As a large part of our application uses private routes that require authentication, this proved to be a challenge for writing Jest tests for a larger number of features. We felt confident that all features of our application were working as expected due the breadth of manual user testing - but in future we would have built more Jest tests earlier in the application development.
