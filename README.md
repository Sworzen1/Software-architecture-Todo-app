# Software-architecture-Todo-app

## 1. Description:

Todo app is simple and usefull tool, users can manage tasks and responsibilities effectively. App gives opportunity to create, track and prioritize tasks, ensuring that nothing important gets overlooked. The goal of the project is to help users stay organized, increase productivity.

### 1a. Main futures:

- Task creation: Users can easily create new tasks by entering a title and description set due date and reminder.
- Task edition: User can edit existing tasks, change title, description, date etc.
- Task deletion: User can delete taska
- Prioritization: Users can assign priority tasks, indicating their relative importance or urgency. This helps in focusing on high-priority tasks and ensuring that essential work gets completed on time.
- Reminders and Notifications: To ensure the tasks are not forgotten, user should have opportunity to set reminders and notifications. These can be set up to alert users at specific times.
- Progress Tracking: Progress tracking of user tasks. This can be done by marking tasks as complete, setting subtasks, or adding comments or notes to provide updates on the task's status.
- Customization: User can personalize the app appearance, choose different themes, or adjust settings to suit his workflow.

## 2. Context

The Todo List App is the software system being represented. It contains the necessary functionality to create, track, and manage tasks. The User interacts with the Todo List App through a user interface, which is a mobile app. Written using Typescript language and React Native framework.

![Context](images/Context.png)

## 3. Container

App will have three containers:

- Mobile application
- Rest API
- Database

#### User

The user represents the person who interacts with the To Do List app through the mobile app. The user interacts with the application by sending requests, based on which it receives responses consistent with the state of the database.

### 3a. Mobile application

App has a minimalist, intuitive and simple interface. Focused on simplicity and clarity, such an interface may only contain basic elements such as a task list, buttons for adding. We can use simple but nice animations, additionally add gestures to enhance the user experience.

### 3b. Rest API

API methods for main features:

GET:

- Retrieves a representation of the to-do list
- Filters and proritizes list
- Returns task's details

POST:

- Creates a new tasks based on the provided data

PUT:

- Updates an existing tasks

DELETE:

- Deletes the tasks

URIs: Resources are identified using URIs. For example, a URI for a task resource in a Todo List API could be
`BASEURL/tasks/{taskId}.`

Data Format: We will use JSON (JavaScript Object Notation) JSON is used because of its simplicity and ease of parsing and reusing on frontend side.

Authentication and Authorization: We will authorize the user and store his sessions based on the JWT Token.

Notifications: We'll use Firebase and his SDK for push notifications.

### 3a. Database

The database container represents the storage system for the application. It stores data related to tasks, users and other relevant information. The best choice for this simple application is the cloud-hosted and non-relational Firebase database. In addition, Firebase provides a lot of SDKs that can help in development.

![Container](images/Container.png)

## 4. Components

Each of three application's containers are build from components. We want to present the tasks and responsibilities of each of them to make it easier to implement them. This is very important because it shows the full scope of the application's functionality. Thanks to this, it will also be easier to accurately price the application.


### 4a. API

#### Controllers
The main components will be the controllers, they define the endpoints that define the parameters and data accepted by requests. Additionally, the controllers decide which action should be done.

  - Sign in/ Sign up/ Reset password controllers - allow user to makes actions connected with account
  - Create task/ Delete task/ Update task controllers - allow user to makes actions connected with tasks
  - Progress controller - gives user informations about his account progress
#### Services
Services store methods that will be executed if we use them in controllers or by other methods. They perform operations and modify data.

  - User service - contains methods like create account with password encryption, login to account, change password  
  - Task service - contains methods connected with create, delete, update tasks like simple CRUD (Create, Read, Update, Delete)
  - Notifications service - has methods connected with notification like send messages

#### SDKs
External SDKs will be used for faster development, thanks to which we will save time and do not have to worry about writing everything from scratch. SDKs provides a package of methods that we can use in an easy and accessible way. The entire implementation process is described in the certain SDK documentation.

  - Firebase Cloud Messaging - is tool that lets you reliably send messages.

![APIComponents](images/APIComponents.png)


### 4b. Mobile app

#### Screens
They show the user the actual state of the application. They are adapted so that navigating the application is intuitive and easy for new users. They contain animations and gestures that attract the user to want to use the software. They use hooks to get information stored in the database and perform API actions.

  - Sign in/ Sign up/ Change password screen - these are forms, through the inputs they read the data that the user provides and pass to the API methods
  - Tasks list screen - this is scroll view which has list of tasks and modal for edit and create the new
  - Settings screen - contains all informations about user, application and notifications

#### Hooks
Hooks are files with application logic on the frontend side, they manage data and app state. Are written in typesscript using already existing React hooks. Thanks to them, we avoid excess content in UI files by moving the logic.

  - useGetTasksQuery - fetch certain user tasks
  - useGetUserProgressQuery - fetch user progress
  - useGetUserInformationsQuery - fetch user information like user nickname or age etc.
  - useCreateTaskMutation - create new task
  - useDeleteTaskMutation - delete existing task
  - useUpdateTaskMutation - update existing task
  - useChangePasswordMutation - change user password
  - useRegisterMutation - create new account
  - useAuthMutation - authentication existing user

![MobileAppComponents](images/MobileAppComponents.png)