# Microsoft To-Do API Plugin Documentation

## 1. Overview

The **Microsoft To-Do API Plugin** enables integration with Microsoft To-Do, allowing you to manage task lists and tasks. This API allows for the listing, retrieval, creation, and updating of tasks and task lists. Authentication is handled through **Bearer Access Token** using a `microsoft_access_token`.

## 2. Available Methods

### 1. **List Task Lists**
   - **Endpoint**: `GET https://graph.microsoft.com/v1.0/users/{{userIdOrName}}/todo/lists`
   - **What it does**: Retrieves a list of all task lists associated with a user.
   - **Configuration**:
     - Requires `userIdOrName` (the user's ID or username).
     - Requires **Bearer Token** authentication with `microsoft_access_token`.
   - **Use case**: Use this method to fetch and display all task lists created by a user in Microsoft To-Do.

#### Example Request:
```http
GET https://graph.microsoft.com/v1.0/users/{{userIdOrName}}/todo/lists
Authorization: Bearer {{microsoft_access_token}}
```

### 2. **Get Task List by ID**
   - **Endpoint**: `GET https://graph.microsoft.com/v1.0/users/{{userIdOrName}}/todo/lists/{{todoTaskListId}}`
   - **What it does**: Retrieves the details of a specific task list by its `todoTaskListId`.
   - **Configuration**:
     - Requires `userIdOrName` and `todoTaskListId`.
     - Requires **Bearer Token** authentication with `microsoft_access_token`.
   - **Use case**: Use this method to retrieve detailed information about a specific task list, such as its name, creation date, and tasks.

#### Example Request:
```http
GET https://graph.microsoft.com/v1.0/users/{{userIdOrName}}/todo/lists/{{todoTaskListId}}
Authorization: Bearer {{microsoft_access_token}}
```

### 3. **List Tasks in a Task List**
   - **Endpoint**: `GET https://graph.microsoft.com/v1.0/users/{{userIdOrName}}/todo/lists/{{todoTaskListId}}/tasks`
   - **What it does**: Retrieves all tasks from a specified task list.
   - **Configuration**:
     - Requires `userIdOrName` and `todoTaskListId`.
     - Requires **Bearer Token** authentication with `microsoft_access_token`.
   - **Use case**: Use this method to retrieve a list of tasks from a specific task list.

#### Example Request:
```http
GET https://graph.microsoft.com/v1.0/users/{{userIdOrName}}/todo/lists/{{todoTaskListId}}/tasks
Authorization: Bearer {{microsoft_access_token}}
```

### 4. **Create a Task List**
   - **Endpoint**: `POST https://graph.microsoft.com/v1.0/users/{{userIdOrName}}/todo/lists`
   - **What it does**: Creates a new task list under the authenticated user.
   - **Configuration**:
     - Requires `userIdOrName`.
     - Requires **Bearer Token** authentication with `microsoft_access_token`.
     - The request body must contain the name of the task list.
   - **Use case**: Use this method to create a new task list to organize tasks for a specific project or purpose.

#### Example Request Body:
```json
{
  "displayName": "New Task List"
}
```

#### Example Request:
```http
POST https://graph.microsoft.com/v1.0/users/{{userIdOrName}}/todo/lists
Authorization: Bearer {{microsoft_access_token}}
Content-Type: application/json
```

### 5. **Create a Task in a Task List**
   - **Endpoint**: `POST https://graph.microsoft.com/v1.0/users/{{userIdOrName}}/todo/lists/{{todoTaskListId}}/tasks`
   - **What it does**: Creates a new task within a specified task list.
   - **Configuration**:
     - Requires `userIdOrName` and `todoTaskListId`.
     - Requires **Bearer Token** authentication with `microsoft_access_token`.
     - The request body must include task details, such as title, due date, and status.
   - **Use case**: Use this method to create a new task within an existing task list, for example, to track action items for a project.

#### Example Request Body:
```json
{
  "title": "New Task",
  "dueDateTime": {
    "dateTime": "2024-10-30T17:00:00",
    "timeZone": "UTC"
  }
}
```

#### Example Request:
```http
POST https://graph.microsoft.com/v1.0/users/{{userIdOrName}}/todo/lists/{{todoTaskListId}}/tasks
Authorization: Bearer {{microsoft_access_token}}
Content-Type: application/json
```

### 6. **Update a Task List**
   - **Endpoint**: `PATCH https://graph.microsoft.com/v1.0/users/{{userIdOrName}}/todo/lists/{{todoTaskListId}}`
   - **What it does**: Updates details of a specified task list.
   - **Configuration**:
     - Requires `userIdOrName` and `todoTaskListId`.
     - Requires **Bearer Token** authentication with `microsoft_access_token`.
     - The request body should include the fields to be updated (e.g., `displayName`).
   - **Use case**: Use this method to update the name or other properties of an existing task list.

#### Example Request Body:
```json
{
  "displayName": "Updated Task List Name"
}
```

#### Example Request:
```http
PATCH https://graph.microsoft.com/v1.0/users/{{userIdOrName}}/todo/lists/{{todoTaskListId}}
Authorization: Bearer {{microsoft_access_token}}
Content-Type: application/json
```

## 3. Configuration

To use the Microsoft To-Do API, you need to authenticate using an **OAuth2 Bearer Token**. This token provides access to the user's task lists and tasks.

### 1. **Bearer Token Setup**
   - The Microsoft Graph API requires OAuth2 authentication to generate an access token.
   - Obtain an access token by following the OAuth2 flow for Microsoft services, using the **Microsoft Identity platform**.
   - The access token must be included in the Authorization header for each API request.

### 2. **Required Scopes**
   The following OAuth2 scopes are typically required:
   - `Tasks.Read`: Allows reading tasks and task lists.
   - `Tasks.ReadWrite`: Allows reading and writing tasks and task lists.

### 3. **JSON Configuration Example**

```json
{
  "microsoft_access_token": "your_microsoft_oauth2_access_token"
}
```

This configuration allows secure access to Microsoft To-Do tasks and lists for managing tasks programmatically.

## 4. Links to Documentation

- [Microsoft To-Do API Documentation](https://learn.microsoft.com/en-us/graph/api/resources/todo-overview?view=graph-rest-1.0)
- [Microsoft Graph API Access Setup](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-auth-code-flow)

This documentation provides a clear guide to interacting with the Microsoft To-Do API, allowing for secure management of tasks and task lists using OAuth2 Bearer Token authentication.
