# Microsoft Files API Plugin Documentation

## 1. Overview

The **Microsoft Files API Plugin** provides access to file storage and container management within the Microsoft Graph API. It allows users to list, create, and retrieve file storage containers. Authentication is managed through a **Bearer Access Token** using `microsoft_access_token`, ensuring secure access to file storage resources.

## 2. Available Methods

### 1. **List Containers**
   - **Endpoint**: `GET https://graph.microsoft.com/v1.0/storage/fileStorage/containers?$filter=containerTypeId eq {{containerTypeId}}`
   - **What it does**: Retrieves a list of file storage containers filtered by their `containerTypeId`.
   - **Configuration**:
     - Requires `containerTypeId`, the unique identifier of the container type.
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
   - **Use case**: Use this method to list containers of a specific type in the user's file storage.

#### Example Request:
```http
GET https://graph.microsoft.com/v1.0/storage/fileStorage/containers?$filter=containerTypeId eq {{containerTypeId}}
Authorization: Bearer {{microsoft_access_token}}
```

### 2. **Create File Storage Container**
   - **Endpoint**: `POST https://graph.microsoft.com/v1.0/storage/fileStorage/containers`
   - **What it does**: Creates a new file storage container for managing files and folders.
   - **Configuration**:
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
     - The request body must contain the name and type of the container being created.
   - **Use case**: Use this method to create new containers in Microsoft file storage for organizing files and other resources.

#### Example Request Body:
```json
{
  "name": "NewContainer",
  "containerTypeId": "custom-container-type"
}
```

#### Example Request:
```http
POST https://graph.microsoft.com/v1.0/storage/fileStorage/containers
Authorization: Bearer {{microsoft_access_token}}
Content-Type: application/json
```

### 3. **Get File Storage Container**
   - **Endpoint**: `GET https://graph.microsoft.com/v1.0/storage/fileStorage/containers/{{containerId}}`
   - **What it does**: Retrieves details of a specific file storage container by its `containerId`.
   - **Configuration**:
     - Requires `containerId`, the unique identifier of the container.
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
   - **Use case**: Use this method to retrieve information about a specific file storage container, such as its name, size, and contents.

#### Example Request:
```http
GET https://graph.microsoft.com/v1.0/storage/fileStorage/containers/{{containerId}}
Authorization: Bearer {{microsoft_access_token}}
```

## 3. Configuration

To use the Microsoft Files API, you must authenticate using an **OAuth2 Bearer Token**. This token provides access to file storage containers for managing files and folders programmatically.

### 1. **Bearer Token Setup**
   - The Microsoft Graph API requires OAuth2 authentication to generate an access token.
   - Obtain an access token by following the OAuth2 flow for Microsoft services, using the **Microsoft Identity platform**.
   - The access token must be included in the Authorization header for each API request.

### 2. **Required Scopes**
   The following OAuth2 scopes are typically required:
   - `Files.ReadWrite.All`: Allows reading and writing to all file storage containers.

### 3. **JSON Configuration Example**

```json
{
  "microsoft_access_token": "your_microsoft_oauth2_access_token"
}
```

This configuration allows secure access to Microsoft Files for managing file storage containers.

## 4. Links to Documentation

- [Microsoft Files API Documentation](https://learn.microsoft.com/en-us/graph/api/resources/drive?view=graph-rest-1.0)
- [Microsoft Graph API Access Setup](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-auth-code-flow)

This documentation provides a guide to interacting with the Microsoft Files API, enabling secure access to file storage containers and resources using OAuth2 Bearer Token authentication.
