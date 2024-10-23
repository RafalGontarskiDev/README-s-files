# Google Drive API Plugin Documentation

## 1. Overview

The **Google Drive API Plugin** provides integration with Google Drive, enabling you to retrieve file lists, export files in different formats, and manage sharing permissions. This plugin allows you to programmatically access and manage your files in Google Drive. The plugin uses OAuth2 for authentication with delegated access, allowing secure user-specific actions.

## 2. Available Methods

### 1. **Get Files List**
   - **Endpoint**: `GET https://www.googleapis.com/drive/v3/files`
   - **What it does**: Retrieves a list of files from the user's Google Drive.
   - **Configuration**:
     - Requires OAuth2 authentication with the scope `https://www.googleapis.com/auth/drive.readonly` for read-only access, or `https://www.googleapis.com/auth/drive` for full access.
   - **Use case**: Use this method to fetch a list of files in the user's Google Drive, such as when building a file explorer or searching for documents.

### 2. **Export File**
   - **Endpoint**: `GET https://www.googleapis.com/drive/v3/files/{{fileId}}/export`
   - **What it does**: Exports a Google Docs file into a specified format (e.g., PDF, DOCX).
   - **Configuration**:
     - Requires `fileId`, the unique identifier of the file in Google Drive.
     - Requires OAuth2 authentication with the `https://www.googleapis.com/auth/drive.readonly` or `https://www.googleapis.com/auth/drive.file` scope.
     - The request must include the `mimeType` of the desired export format (e.g., `application/pdf` for PDF).
   - **Use case**: Convert Google Docs, Sheets, or Slides files into different formats for download, sharing, or offline usage.

#### Example Request Parameters:
```http
GET https://www.googleapis.com/drive/v3/files/{{fileId}}/export?mimeType=application/pdf
```

### 3. **Share File (Manage Permissions)**
   - **Endpoint**: `POST https://www.googleapis.com/drive/v3/files/{{fileId}}/permissions`
   - **What it does**: Shares a file by updating its permissions, allowing it to be viewed or edited by other users.
   - **Configuration**:
     - Requires `fileId`, the unique identifier of the file in Google Drive.
     - Requires OAuth2 authentication with the `https://www.googleapis.com/auth/drive` scope for full file access and permission management.
     - The request body must include the permission type (`role`) and the user or group being granted access (`emailAddress` for individuals, `domain` for groups).
   - **Use case**: Use this method to share a file with specific users or make it public, enabling collaboration on Google Drive documents.

#### Example Request Body:
```json
{
  "role": "reader",
  "type": "user",
  "emailAddress": "user@example.com"
}
```

## 3. Configuration

To use this plugin, you will need to authenticate using OAuth2 and provide the appropriate scopes based on the actions you intend to perform. This can be set up with **delegated access** for users, allowing the plugin to act on behalf of the user within their Google Drive environment.

### 1. **OAuth2 Setup for Google Drive**
   - **Delegated access** means that the plugin acts on behalf of the authenticated user.
   - The following OAuth2 scopes are required based on the methods used:
     - `https://www.googleapis.com/auth/drive.readonly`: Read-only access to Google Drive files.
     - `https://www.googleapis.com/auth/drive.file`: Access to the user's files, including the ability to export and modify them.
     - `https://www.googleapis.com/auth/drive`: Full access to Google Drive, including managing file sharing permissions.

### 2. **Steps to Configure OAuth2**
   - In Google Cloud Console, create an OAuth2 client for your application.
   - Add the relevant scopes depending on the API actions you want to perform.
   - Obtain the OAuth2 access token for each user by directing them through Google's OAuth2 consent flow.

### 3. **JSON Configuration Example**

```json
{
  "access_token": "your_google_oauth_access_token"
}
```

This configuration allows the plugin to authenticate with Google Drive and perform the described actions, such as retrieving files, exporting them, and managing permissions.

## 4. Links to Documentation

- [Google Drive API Documentation](https://developers.google.com/drive/api/v3/reference)
- [Google OAuth2 Access Setup](https://developers.google.com/identity/protocols/oauth2)

This documentation provides an easy guide to integrating with the Google Drive API, ensuring secure access and management of files, exports, and sharing permissions.
