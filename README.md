# Google Docs API Plugin Documentation

## 1. Overview

The **Google Docs API Plugin** allows for seamless interaction with Google Docs. With this plugin, you can create new documents, retrieve documents by ID, and update documents using batch operations. Authentication is managed through OAuth2 with delegated access, ensuring secure user-specific document access.

## 2. Available Methods

### 1. **Create Document**
   - **Endpoint**: `POST https://docs.googleapis.com/v1/documents`
   - **What it does**: Creates a new Google Doc.
   - **Configuration**:
     - Requires OAuth2 authentication with proper scopes (`https://www.googleapis.com/auth/documents`).
   - **Use case**: Automatically generate new Google Docs for various use cases such as reports, invoices, or document templates.

#### Example Request Body:
```json
{
  "title": "New Document"
}
```

### 2. **Get Document by ID**
   - **Endpoint**: `GET https://docs.googleapis.com/v1/documents/{{documentId}}`
   - **What it does**: Retrieves the content and metadata of a specific Google Doc by its document ID.
   - **Configuration**:
     - Requires `documentId`, the unique ID of the document.
     - Requires OAuth2 authentication with proper scopes (`https://www.googleapis.com/auth/documents.readonly` or `https://www.googleapis.com/auth/documents`).
   - **Use case**: Retrieve the document's content for viewing, exporting, or analyzing its contents.

### 3. **BatchUpdate Document**
   - **Endpoint**: `POST https://docs.googleapis.com/v1/documents/{{documentId}}:batchUpdate`
   - **What it does**: Applies a set of updates to a Google Doc, such as text insertions, deletions, or styling changes.
   - **Configuration**:
     - Requires `documentId`, the unique ID of the document.
     - Requires OAuth2 authentication with proper scopes (`https://www.googleapis.com/auth/documents`).
     - The request body must contain the specific updates to be made.
   - **Use case**: Use this method for programmatic document editing, such as formatting or inserting data into a template document.

#### Example Request Body:
```json
{
  "requests": [
    {
      "insertText": {
        "location": {
          "index": 1
        },
        "text": "Hello, World!"
      }
    }
  ]
}
```

## 3. Configuration

To use this plugin, you need to authenticate using OAuth2 and provide the appropriate scopes for the actions you intend to perform. This can be set up with **delegated access** for users, allowing the plugin to act on behalf of the user within their Google Docs environment.

### 1. **OAuth2 Setup**
   - **Delegated access** means that the plugin acts on behalf of the authenticated user.
   - Ensure you have set up OAuth2 with the following scopes:
     - `https://www.googleapis.com/auth/documents` for full access to create and edit documents.
     - `https://www.googleapis.com/auth/documents.readonly` for read-only access to documents.

### 2. **Steps to Configure OAuth2**
   - In Google Cloud Console, create an OAuth2 client for your application.
   - Add the relevant scopes depending on the API actions you want to perform.
   - Obtain the OAuth2 access token for each user by directing them through Google's OAuth2 consent flow.

### 3. **JSON Configuration Example**

```json
{
  "access_token": "your_oauth2_access_token"
}
```

## 4. Links to Documentation

- [Google Docs API Documentation](https://developers.google.com/docs/api/reference/rest)
- [Google OAuth2 Access Setup](https://developers.google.com/identity/protocols/oauth2)

This documentation provides a clear guide to utilizing the Google Docs API for creating, fetching, and updating Google Docs, ensuring secure and delegated user access.
