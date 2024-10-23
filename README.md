# Microsoft Search API Plugin Documentation

## 1. Overview

The **Microsoft Search API Plugin** enables interaction with Microsoft Search, allowing users to perform queries, manage acronyms, and search for specific entities. The API supports searching for content across Microsoft services. Authentication is handled through a **Bearer Access Token** using `microsoft_access_token`.

## 2. Available Methods

### 1. **Search Entity: Query**
   - **Endpoint**: `POST https://graph.microsoft.com/v1.0/search/query`
   - **What it does**: Executes a search query across various Microsoft services (e.g., SharePoint, OneDrive).
   - **Configuration**:
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
     - The request body must contain the search query and options.
   - **Use case**: Use this method to search across different Microsoft services like SharePoint and OneDrive to retrieve documents, files, and other data.

#### Example Request Body:
```json
{
  "requests": [
    {
      "entityTypes": ["driveItem", "listItem"],
      "query": {
        "queryString": "marketing report"
      }
    }
  ]
}
```

#### Example Request:
```http
POST https://graph.microsoft.com/v1.0/search/query
Authorization: Bearer {{microsoft_access_token}}
Content-Type: application/json
```

### 2. **List Acronyms**
   - **Endpoint**: `GET https://graph.microsoft.com/v1.0/search/acronyms`
   - **What it does**: Retrieves a list of all acronyms managed within the Microsoft Search system.
   - **Configuration**:
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
   - **Use case**: Use this method to list all known acronyms in your organization for easy reference and management.

#### Example Request:
```http
GET https://graph.microsoft.com/v1.0/search/acronyms
Authorization: Bearer {{microsoft_access_token}}
```

### 3. **Get Acronym by ID**
   - **Endpoint**: `GET https://graph.microsoft.com/v1.0/search/acronyms/{{acronymsId}}`
   - **What it does**: Retrieves a specific acronym by its unique ID.
   - **Configuration**:
     - Requires `acronymsId`, the unique identifier of the acronym.
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
   - **Use case**: Use this method to retrieve detailed information about a specific acronym, such as its definition and related terms.

#### Example Request:
```http
GET https://graph.microsoft.com/v1.0/search/acronyms/{{acronymsId}}
Authorization: Bearer {{microsoft_access_token}}
```

### 4. **Create Acronym**
   - **Endpoint**: `POST https://graph.microsoft.com/v1.0/search/acronyms`
   - **What it does**: Creates a new acronym within the Microsoft Search system.
   - **Configuration**:
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
     - The request body must include the acronym, definition, and related metadata.
   - **Use case**: Use this method to add a new acronym to your organization’s Microsoft Search database for shared understanding and reference.

#### Example Request Body:
```json
{
  "displayName": "API",
  "description": "Application Programming Interface",
  "sources": [
    {
      "type": "internal"
    }
  ]
}
```

#### Example Request:
```http
POST https://graph.microsoft.com/v1.0/search/acronyms
Authorization: Bearer {{microsoft_access_token}}
Content-Type: application/json
```

## 3. Configuration

To use the Microsoft Search API, you need to authenticate using an **OAuth2 Bearer Token**. This token provides access to search and manage acronyms across Microsoft services.

### 1. **Bearer Token Setup**
   - The Microsoft Graph API requires OAuth2 authentication to generate an access token.
   - Obtain an access token by following the OAuth2 flow for Microsoft services using the **Microsoft Identity platform**.
   - The access token must be included in the Authorization header for each API request.

### 2. **Required Scopes**
   The following OAuth2 scopes are typically required:
   - `Search.Query.All`: Allows querying content and managing acronyms across Microsoft services.

### 3. **JSON Configuration Example**

```json
{
  "microsoft_access_token": "your_microsoft_oauth2_access_token"
}
```

This configuration allows secure access to Microsoft Search for querying and managing acronyms.

## 4. Links to Documentation

- [Microsoft Search API Documentation](https://learn.microsoft.com/en-us/graph/api/resources/search-api-overview?view=graph-rest-1.0)
- [Microsoft Graph API Access Setup](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-auth-code-flow)

This documentation provides a guide to interacting with the Microsoft Search API, allowing for secure search queries and acronym management across Microsoft services with OAuth2 Bearer Token authentication.
