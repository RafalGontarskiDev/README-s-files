# Atlassian Trello API Plugin Documentation

## 1. Overview

The **Atlassian Trello API Plugin** allows seamless integration with Trello to manage boards and lists. You can create boards, add lists to boards, retrieve board information, and delete boards using the Trello API. Authentication is handled via a **Bearer OAuth Access Token** for secure access to Trello resources.

## 2. Available Methods

### 1. **Create a Board**
   - **Endpoint**: `POST https://api.trello.com/1/boards/?name={{name}}`
   - **What it does**: Creates a new board in Trello with a specified name.
   - **Configuration**:
     - Requires `name`, the desired name for the new board.
     - Requires Bearer OAuth access token for authentication.
   - **Use case**: Use this method to create a new Trello board to organize tasks, projects, or collaborative workspaces.

#### Example Request:
```http
POST https://api.trello.com/1/boards/?name=New%20Project%20Board
Authorization: Bearer {{oauth_access_token}}
```

### 2. **Create a List on a Board**
   - **Endpoint**: `POST https://api.trello.com/1/boards/{{id}}/lists?name={{name}}`
   - **What it does**: Adds a new list to a specified Trello board.
   - **Configuration**:
     - Requires `id`, the unique identifier of the board.
     - Requires `name`, the desired name of the new list.
     - Requires Bearer OAuth access token for authentication.
   - **Use case**: Use this method to create lists within a Trello board to categorize tasks or workflows.

#### Example Request:
```http
POST https://api.trello.com/1/boards/{{board_id}}/lists?name=To%20Do
Authorization: Bearer {{oauth_access_token}}
```

### 3. **Get Board by ID**
   - **Endpoint**: `GET https://api.trello.com/1/boards/{{id}}`
   - **What it does**: Retrieves details of a specific Trello board by its ID.
   - **Configuration**:
     - Requires `id`, the unique identifier of the board.
     - Requires Bearer OAuth access token for authentication.
   - **Use case**: Use this method to fetch detailed information about a specific Trello board, such as its lists, members, and settings.

#### Example Request:
```http
GET https://api.trello.com/1/boards/{{board_id}}
Authorization: Bearer {{oauth_access_token}}
```

### 4. **Delete a Board**
   - **Endpoint**: `DELETE https://api.trello.com/1/boards/{{id}}`
   - **What it does**: Deletes a specified Trello board by its ID.
   - **Configuration**:
     - Requires `id`, the unique identifier of the board.
     - Requires Bearer OAuth access token for authentication.
   - **Use case**: Use this method to remove an unwanted or completed Trello board from your workspace.

#### Example Request:
```http
DELETE https://api.trello.com/1/boards/{{board_id}}
Authorization: Bearer {{oauth_access_token}}
```

## 3. Configuration

To use this plugin, you need to authenticate using a **Bearer OAuth Access Token**. This token must have the appropriate permissions for accessing Trello’s API resources based on the actions you intend to perform.

### 1. **OAuth Access Token Setup**
   - You can generate an OAuth access token through Trello's developer portal.
   - The token should be included in the headers of all API requests to authenticate and authorize actions on the Trello boards.

### 2. **JSON Configuration Example**

```json
{
  "oauth_access_token": "your_trello_oauth_access_token"
}
```

This configuration ensures secure access to the Trello API and allows the plugin to interact with boards and lists.

## 4. Links to Documentation

- [Trello API Documentation](https://developer.atlassian.com/cloud/trello/rest/api-group-boards/)
- [Trello API Access Setup](https://developer.atlassian.com/cloud/trello/guides/rest-api/authorization/)

This documentation provides a guide for managing Trello boards and lists using the API with secure OAuth access token authentication.
