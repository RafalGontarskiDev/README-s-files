# Microsoft Planner API Plugin Documentation

## 1. Overview

The **Microsoft Planner API Plugin** provides integration with Microsoft Planner, allowing users to retrieve, create, and manage plans and buckets. Authentication is handled through a **Bearer Access Token** using the `microsoft_access_token`. This API enables smooth task management and project organization in Microsoft Planner.

## 2. Available Methods

### 1. **Get Planner Plan**
   - **Endpoint**: `GET https://graph.microsoft.com/v1.0/planner/plans/{{planId}}`
   - **What it does**: Retrieves the details of a specific plan by its `planId`.
   - **Configuration**:
     - Requires `planId`, the unique identifier of the plan.
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
   - **Use case**: Use this method to get detailed information about a specific Microsoft Planner plan, such as the plan title, owner, and creation date.

#### Example Request:
```http
GET https://graph.microsoft.com/v1.0/planner/plans/{{planId}}
Authorization: Bearer {{microsoft_access_token}}
```

### 2. **List Buckets in a Plan**
   - **Endpoint**: `GET https://graph.microsoft.com/v1.0/planner/plans/{{planId}}/buckets`
   - **What it does**: Retrieves a list of all buckets within a specific plan.
   - **Configuration**:
     - Requires `planId`, the unique identifier of the plan.
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
   - **Use case**: Use this method to get a list of all buckets (task categories) in a specific plan for task organization.

#### Example Request:
```http
GET https://graph.microsoft.com/v1.0/planner/plans/{{planId}}/buckets
Authorization: Bearer {{microsoft_access_token}}
```

### 3. **Create Planner Plan**
   - **Endpoint**: `POST https://graph.microsoft.com/v1.0/planner/plans`
   - **What it does**: Creates a new plan in Microsoft Planner.
   - **Configuration**:
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
     - The request body must include details such as the title of the plan and the owner group ID.
   - **Use case**: Use this method to programmatically create new plans for project management or task organization in Microsoft Planner.

#### Example Request Body:
```json
{
  "title": "New Project Plan",
  "owner": "group-id"
}
```

#### Example Request:
```http
POST https://graph.microsoft.com/v1.0/planner/plans
Authorization: Bearer {{microsoft_access_token}}
Content-Type: application/json
```

## 3. Configuration

To use the Microsoft Planner API, you need to authenticate using an **OAuth2 Bearer Token**. This token provides access to Planner resources like plans and buckets for the authenticated user.

### 1. **Bearer Token Setup**
   - The Microsoft Graph API requires OAuth2 authentication to generate an access token.
   - Obtain an access token by following the OAuth2 flow for Microsoft services, using the **Microsoft Identity platform**.
   - The access token must be included in the Authorization header for each API request.

### 2. **Required Scopes**
   The following OAuth2 scopes are typically required:
   - `Tasks.Read`: Allows reading Microsoft Planner tasks and plans.
   - `Tasks.ReadWrite`: Allows reading and writing Microsoft Planner tasks and plans.

### 3. **JSON Configuration Example**

```json
{
  "microsoft_access_token": "your_microsoft_oauth2_access_token"
}
```

This configuration allows secure access to Microsoft Planner for retrieving and managing plans and buckets.

## 4. Links to Documentation

- [Microsoft Planner API Documentation](https://learn.microsoft.com/en-us/graph/api/resources/planner-overview?view=graph-rest-1.0)
- [Microsoft Graph API Access Setup](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-auth-code-flow)

This documentation provides an easy guide to integrating with Microsoft Planner through the Graph API, allowing for secure and efficient management of plans and buckets using OAuth2 Bearer Token authentication.
