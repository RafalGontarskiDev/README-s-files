# Typeform API Plugin Documentation

## 1. Overview

The **Typeform API Plugin** allows integration with Typeform, enabling users to manage workspaces, forms, and themes. This plugin supports retrieving, creating, and updating workspaces, forms, and themes using **Bearer Personal Access Token** authentication. The API provides robust methods to manage your Typeform data and streamline form workflows.

## 2. Available Methods

### 1. **Retrieve Workspaces**
   - **Endpoint**: `GET https://api.typeform.com/workspaces`
   - **What it does**: Fetches a list of all workspaces in the account.
   - **Configuration**:
     - Requires Bearer Token authentication with a `PERSONAL_ACCESS_TOKEN`.
   - **Use case**: Use this method to retrieve a list of workspaces that are available in your Typeform account for organization or management purposes.

#### Example Request:
```http
GET https://api.typeform.com/workspaces
Authorization: Bearer {{PERSONAL_ACCESS_TOKEN}}
```

### 2. **Retrieve Workspace**
   - **Endpoint**: `GET https://api.typeform.com/workspaces/{{workspaceId}}`
   - **What it does**: Retrieves information about a specific workspace by its `workspaceId`.
   - **Configuration**:
     - Requires `workspaceId`, the unique identifier of the workspace.
     - Requires Bearer Token authentication with a `PERSONAL_ACCESS_TOKEN`.
   - **Use case**: Fetch detailed information about a specific workspace to view its settings, forms, and members.

#### Example Request:
```http
GET https://api.typeform.com/workspaces/{{workspaceId}}
Authorization: Bearer {{PERSONAL_ACCESS_TOKEN}}
```

### 3. **Retrieve Account Workspaces**
   - **Endpoint**: `GET https://api.typeform.com/accounts/{{accountId}}/workspaces`
   - **What it does**: Retrieves all workspaces associated with a specific account.
   - **Configuration**:
     - Requires `accountId`, the unique identifier of the account.
     - Requires Bearer Token authentication with a `PERSONAL_ACCESS_TOKEN`.
   - **Use case**: Use this method to fetch all workspaces tied to a specific Typeform account for organization or auditing purposes.

#### Example Request:
```http
GET https://api.typeform.com/accounts/{{accountId}}/workspaces
Authorization: Bearer {{PERSONAL_ACCESS_TOKEN}}
```

### 4. **Create Account Workspace**
   - **Endpoint**: `POST https://api.typeform.com/accounts/{{account_id}}/workspaces`
   - **What it does**: Creates a new workspace under a specified account.
   - **Configuration**:
     - Requires `account_id`, the unique identifier of the account.
     - Requires Bearer Token authentication with a `PERSONAL_ACCESS_TOKEN`.
     - The request body must contain details like the workspace name.
   - **Use case**: Use this method to create a new workspace under a specific account for organizing forms and other resources.

#### Example Request Body:
```json
{
  "name": "New Workspace"
}
```

### 5. **Create Workspace**
   - **Endpoint**: `POST https://api.typeform.com/workspaces`
   - **What it does**: Creates a new workspace for organizing forms and resources.
   - **Configuration**:
     - Requires Bearer Token authentication with a `PERSONAL_ACCESS_TOKEN`.
     - The request body must contain details like the workspace name.
   - **Use case**: Use this method to create a new workspace for better resource management within Typeform.

#### Example Request Body:
```json
{
  "name": "Marketing Workspace"
}
```

### 6. **Create Theme**
   - **Endpoint**: `POST https://api.typeform.com/themes`
   - **What it does**: Creates a new theme that can be applied to forms.
   - **Configuration**:
     - Requires Bearer Token authentication with a `PERSONAL_ACCESS_TOKEN`.
     - The request body must include details like the theme name and styles (e.g., colors, fonts).
   - **Use case**: Use this method to define custom themes for Typeform forms, aligning them with branding or visual preferences.

#### Example Request Body:
```json
{
  "name": "Corporate Theme",
  "colors": {
    "question": "#000000",
    "answer": "#ffffff"
  }
}
```

### 7. **Create Form**
   - **Endpoint**: `POST https://api.typeform.com/forms`
   - **What it does**: Creates a new form in Typeform.
   - **Configuration**:
     - Requires Bearer Token authentication with a `PERSONAL_ACCESS_TOKEN`.
     - The request body should include form fields, logic, and layout.
   - **Use case**: Use this method to programmatically create new forms for surveys, data collection, or feedback.

#### Example Request Body:
```json
{
  "title": "Customer Feedback",
  "fields": [
    {
      "title": "How satisfied are you with our service?",
      "type": "rating",
      "properties": {
        "steps": 5
      }
    }
  ]
}
```

### 8. **Update Workspace**
   - **Endpoint**: `PATCH https://api.typeform.com/workspaces/{{workspaceId}}`
   - **What it does**: Updates details of a specific workspace, such as its name or members.
   - **Configuration**:
     - Requires `workspaceId`, the unique identifier of the workspace.
     - Requires Bearer Token authentication with a `PERSONAL_ACCESS_TOKEN`.
     - The request body must include the fields to update, such as the new name or updated members.
   - **Use case**: Use this method to modify existing workspaces, update their configurations, or rename them for better organization.

#### Example Request Body:
```json
{
  "name": "Updated Workspace Name"
}
```

## 3. Configuration

To use this plugin, you need to authenticate using a **Bearer Personal Access Token**. This token should be securely stored and passed in the headers of all requests to the Typeform API.

### 1. **Bearer Token Setup**
   - You can generate a Personal Access Token from your Typeform account settings.
   - This token should be included in the authorization headers of your API requests.

### 2. **JSON Configuration Example**

```json
{
  "PERSONAL_ACCESS_TOKEN": "your_typeform_access_token"
}
```

This configuration ensures secure access to Typeform's API for managing workspaces, forms, and themes.

## 4. Links to Documentation

- [Typeform API Documentation](https://developer.typeform.com/)
- [Typeform API Access Setup](https://www.typeform.com/help/a/where-can-i-find-my-api-key-360029581691/)

This documentation provides a detailed guide to interacting with the Typeform API, enabling seamless management of workspaces, forms, and themes using secure Bearer Token authentication.
