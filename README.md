# Microsoft Sites and Lists API Plugin Documentation

## 1. Overview

The **Microsoft Sites and Lists API Plugin** allows interaction with Microsoft SharePoint sites and lists. You can retrieve, search, create, and manage sites, lists, and list items. Authentication is handled through a **Bearer Access Token** using the `microsoft_access_token`, ensuring secure access to resources within Microsoft SharePoint.

## 2. Available Methods

### 1. **Get Site by Server Relative URL**
   - **Endpoint**: `GET https://graph.microsoft.com/v1.0/sites/{{hostname}}:/sites/{{serverRelativePath}}`
   - **What it does**: Retrieves a site by its server-relative URL.
   - **Configuration**:
     - Requires `hostname` (e.g., `example.sharepoint.com`).
     - Requires `serverRelativePath`, the path to the site.
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
   - **Use case**: Use this method to retrieve site metadata and details based on the server-relative URL.

#### Example Request:
```http
GET https://graph.microsoft.com/v1.0/sites/{{hostname}}:/sites/{{serverRelativePath}}
Authorization: Bearer {{microsoft_access_token}}
```

### 2. **Get Metadata for a List**
   - **Endpoint**: `GET https://graph.microsoft.com/v1.0/sites/{{siteId}}/lists/{{listId}}`
   - **What it does**: Retrieves metadata for a specific list by its `listId`.
   - **Configuration**:
     - Requires `siteId` and `listId`.
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
   - **Use case**: Use this method to retrieve information about a specific list on a SharePoint site.

#### Example Request:
```http
GET https://graph.microsoft.com/v1.0/sites/{{siteId}}/lists/{{listId}}
Authorization: Bearer {{microsoft_access_token}}
```

### 3. **Get List Item**
   - **Endpoint**: `GET https://graph.microsoft.com/v1.0/sites/{{siteId}}/lists/{{listId}}/items/{{itemId}}`
   - **What it does**: Retrieves a specific item from a list by its `itemId`.
   - **Configuration**:
     - Requires `siteId`, `listId`, and `itemId`.
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
   - **Use case**: Use this method to fetch a specific item (e.g., a task or document) from a SharePoint list.

#### Example Request:
```http
GET https://graph.microsoft.com/v1.0/sites/{{siteId}}/lists/{{listId}}/items/{{itemId}}
Authorization: Bearer {{microsoft_access_token}}
```

### 4. **Search for Sites**
   - **Endpoint**: `GET https://graph.microsoft.com/v1.0/sites?search={{query}}`
   - **What it does**: Searches for sites within a tenant based on a query string.
   - **Configuration**:
     - Requires `query`, the search term to find matching sites.
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
   - **Use case**: Use this method to search for SharePoint sites matching a specific query (e.g., "marketing" or "projects").

#### Example Request:
```http
GET https://graph.microsoft.com/v1.0/sites?search={{query}}
Authorization: Bearer {{microsoft_access_token}}
```

### 5. **Create a New List**
   - **Endpoint**: `POST https://graph.microsoft.com/v1.0/sites/{{siteId}}/lists`
   - **What it does**: Creates a new list on a specified SharePoint site.
   - **Configuration**:
     - Requires `siteId`, the unique identifier of the site.
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
     - The request body must contain the list name and other relevant details.
   - **Use case**: Use this method to create a new list for managing items such as tasks, documents, or inventory.

#### Example Request Body:
```json
{
  "displayName": "New List",
  "list": {
    "template": "genericList"
  }
}
```

#### Example Request:
```http
POST https://graph.microsoft.com/v1.0/sites/{{siteId}}/lists
Authorization: Bearer {{microsoft_access_token}}
Content-Type: application/json
```

### 6. **Create a List Item**
   - **Endpoint**: `POST https://graph.microsoft.com/v1.0/sites/{{siteId}}/lists/{{listId}}/items`
   - **What it does**: Adds a new item to a specific list on a SharePoint site.
   - **Configuration**:
     - Requires `siteId` and `listId`.
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
     - The request body should contain the fields and values for the new item.
   - **Use case**: Use this method to programmatically add items to an existing list, such as tasks or records.

#### Example Request Body:
```json
{
  "fields": {
    "Title": "New Task",
    "Description": "Description for the new task"
  }
}
```

#### Example Request:
```http
POST https://graph.microsoft.com/v1.0/sites/{{siteId}}/lists/{{listId}}/items
Authorization: Bearer {{microsoft_access_token}}
Content-Type: application/json
```

## 3. Configuration

To use the Microsoft Sites and Lists API, you need to authenticate using an **OAuth2 Bearer Token**. This token provides access to SharePoint sites and lists for the authenticated user.

### 1. **Bearer Token Setup**
   - The Microsoft Graph API requires OAuth2 authentication to generate an access token.
   - Obtain an access token by following the OAuth2 flow for Microsoft services, using the **Microsoft Identity platform**.
   - The access token must be included in the Authorization header for each API request.

### 2. **Required Scopes**
   The following OAuth2 scopes are typically required:
   - `Sites.Read.All`: Allows reading SharePoint sites and lists.
   - `Sites.ReadWrite.All`: Allows reading and writing to SharePoint sites and lists.

### 3. **JSON Configuration Example**

```json
{
  "microsoft_access_token": "your_microsoft_oauth2_access_token"
}
```

This configuration allows secure access to Microsoft SharePoint sites and lists for managing content programmatically.

## 4. Links to Documentation

- [Microsoft Sites and Lists API Documentation](https://learn.microsoft.com/en-us/graph/api/resources/sharepoint?view=graph-rest-1.0)
- [Microsoft Graph API Access Setup](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-auth-code-flow)

This documentation provides a clear guide to interacting with Microsoft SharePoint sites and lists using the Microsoft Graph API with OAuth2 Bearer Token authentication.
