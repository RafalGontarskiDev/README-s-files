# Microsoft Teams API Plugin Documentation

## 1. Overview

The **Microsoft Teams API Plugin** allows integration with Microsoft Teams for managing teams, adding members, and creating new teams. Authentication is handled through a **Bearer Access Token** using `microsoft_access_token`, which enables secure access to Teams resources via Microsoft Graph API.

## 2. Available Methods

### 1. **Get Team**
   - **Endpoint**: `GET https://graph.microsoft.com/v1.0/teams/{{teamId}}`
   - **What it does**: Retrieves details of a specific team by its `teamId`.
   - **Configuration**:
     - Requires `teamId`, the unique identifier of the team.
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
   - **Use case**: Use this method to fetch information about a team, such as team name, description, members, and settings.

#### Example Request:
```http
GET https://graph.microsoft.com/v1.0/teams/{{teamId}}
Authorization: Bearer {{microsoft_access_token}}
```

### 2. **Add Member to a Team**
   - **Endpoint**: `POST https://graph.microsoft.com/v1.0/teams/{{teamId}}/members`
   - **What it does**: Adds a new member to a specific team.
   - **Configuration**:
     - Requires `teamId`, the unique identifier of the team.
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
     - The request body must include the member's user details and role (e.g., owner or member).
   - **Use case**: Use this method to add new members to a team, either as team owners or regular members.

#### Example Request Body:
```json
{
  "@odata.type": "#microsoft.graph.aadUserConversationMember",
  "roles": ["member"],
  "user@odata.bind": "https://graph.microsoft.com/v1.0/users/{{userId}}"
}
```

#### Example Request:
```http
POST https://graph.microsoft.com/v1.0/teams/{{teamId}}/members
Authorization: Bearer {{microsoft_access_token}}
Content-Type: application/json
```

### 3. **Create Team**
   - **Endpoint**: `POST https://graph.microsoft.com/v1.0/teams`
   - **What it does**: Creates a new team in Microsoft Teams.
   - **Configuration**:
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
     - The request body must include the team's details, such as display name, description, and member settings.
   - **Use case**: Use this method to create a new Microsoft Teams team for collaboration, project management, or communication.

#### Example Request Body:
```json
{
  "displayName": "New Team",
  "description": "This is a new team created via the API",
  "members": [
    {
      "@odata.type": "#microsoft.graph.aadUserConversationMember",
      "roles": ["owner"],
      "user@odata.bind": "https://graph.microsoft.com/v1.0/users/{{userId}}"
    }
  ]
}
```

#### Example Request:
```http
POST https://graph.microsoft.com/v1.0/teams
Authorization: Bearer {{microsoft_access_token}}
Content-Type: application/json
```

## 3. Configuration

To use the Microsoft Teams API, you need to authenticate using an **OAuth2 Bearer Token**. This token provides access to Teams resources for managing teams, members, and other settings.

### 1. **Bearer Token Setup**
   - The Microsoft Graph API requires OAuth2 authentication to generate an access token.
   - Obtain an access token by following the OAuth2 flow for Microsoft services, using the **Microsoft Identity platform**.
   - The access token must be included in the Authorization header for each API request.

### 2. **Required Scopes**
   The following OAuth2 scopes are typically required:
   - `Group.ReadWrite.All`: Allows reading and writing Microsoft Teams groups and their properties.
   - `User.ReadBasic.All`: Allows reading basic user profiles.

### 3. **JSON Configuration Example**

```json
{
  "microsoft_access_token": "your_microsoft_oauth2_access_token"
}
```

This configuration allows secure access to Microsoft Teams for managing teams, members, and related settings.

## 4. Links to Documentation

- [Microsoft Teams API Documentation](https://learn.microsoft.com/en-us/graph/teams-concept-overview)
- [Microsoft Graph API Access Setup](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-auth-code-flow)

This documentation provides a guide to interacting with the Microsoft Teams API, enabling secure and efficient management of teams and their members using OAuth2 Bearer Token authentication.
