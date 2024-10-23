# Microsoft Outlook (Mail) API Plugin Documentation

## 1. Overview

The **Microsoft Outlook (Mail) API Plugin** allows integration with Microsoft Outlook email services, enabling users to list, filter, and create email messages. Authentication is managed through a **Bearer Access Token** using `microsoft_access_token`, providing secure access to users' mailboxes via Microsoft Graph API.

## 2. Available Methods

### 1. **List Messages**
   - **Endpoint**: `GET https://graph.microsoft.com/v1.0/users/{{userId}}/messages`
   - **What it does**: Retrieves a list of email messages from a specified user's mailbox.
   - **Configuration**:
     - Requires `userId` (the unique identifier of the user).
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
   - **Use case**: Use this method to list all messages in the user's mailbox for reading or processing.

#### Example Request:
```http
GET https://graph.microsoft.com/v1.0/users/{{userId}}/messages
Authorization: Bearer {{microsoft_access_token}}
```

### 2. **Get Message by ID**
   - **Endpoint**: `GET https://graph.microsoft.com/v1.0/users/{{userId}}/messages/{{messageId}}`
   - **What it does**: Retrieves the details of a specific email message by its `messageId`.
   - **Configuration**:
     - Requires `userId` and `messageId` (the unique identifiers for the user and message).
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
   - **Use case**: Use this method to get detailed information about a particular email message, such as the sender, recipients, subject, and content.

#### Example Request:
```http
GET https://graph.microsoft.com/v1.0/users/{{userId}}/messages/{{messageId}}
Authorization: Bearer {{microsoft_access_token}}
```

### 3. **Create Draft Message**
   - **Endpoint**: `POST https://graph.microsoft.com/v1.0/users/{{userId}}/messages`
   - **What it does**: Creates a draft email message for a specified user.
   - **Configuration**:
     - Requires `userId` (the unique identifier of the user).
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
     - The request body must include the email content, such as subject, body, and recipients.
   - **Use case**: Use this method to programmatically create draft emails that can be later sent by the user.

#### Example Request Body:
```json
{
  "subject": "Project Update",
  "body": {
    "contentType": "HTML",
    "content": "Here's the latest update on the project..."
  },
  "toRecipients": [
    {
      "emailAddress": {
        "address": "recipient@example.com"
      }
    }
  ]
}
```

#### Example Request:
```http
POST https://graph.microsoft.com/v1.0/users/{{userId}}/messages
Authorization: Bearer {{microsoft_access_token}}
Content-Type: application/json
```

### 4. **Filter Messages Since a Certain Date**
   - **Endpoint**: `GET https://graph.microsoft.com/v1.0/users/{{userId}}/messages?$filter=receivedDateTime ge {{certainDate}}`
   - **What it does**: Retrieves a list of messages received since a specific date.
   - **Configuration**:
     - Requires `userId` and `certainDate` (in ISO 8601 format).
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
   - **Use case**: Use this method to filter and retrieve messages based on the date they were received, useful for narrowing down email searches.

#### Example Request:
```http
GET https://graph.microsoft.com/v1.0/users/{{userId}}/messages?$filter=receivedDateTime ge 2024-10-01T00:00:00Z
Authorization: Bearer {{microsoft_access_token}}
```

### 5. **Filter Messages by Attachments**
   - **Endpoint**: `GET https://graph.microsoft.com/v1.0/users/{{userId}}/messages?$filter=hasAttachments eq true`
   - **What it does**: Retrieves a list of messages that have attachments.
   - **Configuration**:
     - Requires `userId` (the unique identifier of the user).
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
   - **Use case**: Use this method to retrieve only the messages that include file attachments.

#### Example Request:
```http
GET https://graph.microsoft.com/v1.0/users/{{userId}}/messages?$filter=hasAttachments eq true
Authorization: Bearer {{microsoft_access_token}}
```

## 3. Configuration

To use the Microsoft Outlook API, you must authenticate using an **OAuth2 Bearer Token**. This token provides access to the user's email messages and allows for the creation, filtering, and retrieval of messages.

### 1. **Bearer Token Setup**
   - The Microsoft Graph API requires OAuth2 authentication to generate an access token.
   - Obtain an access token by following the OAuth2 flow for Microsoft services, using the **Microsoft Identity platform**.
   - The access token must be included in the Authorization header for each API request.

### 2. **Required Scopes**
   The following OAuth2 scopes are typically required:
   - `Mail.Read`: Allows reading user email messages.
   - `Mail.ReadWrite`: Allows reading and writing user email messages.

### 3. **JSON Configuration Example**

```json
{
  "microsoft_access_token": "your_microsoft_oauth2_access_token"
}
```

This configuration allows secure access to Microsoft Outlook for managing, filtering, and retrieving emails programmatically.

## 4. Links to Documentation

- [Microsoft Outlook (Mail) API Documentation](https://learn.microsoft.com/en-us/graph/api/resources/mail-api-overview?view=graph-rest-1.0)
- [Microsoft Graph API Access Setup](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-auth-code-flow)

This documentation provides a guide to interacting with the Microsoft Outlook (Mail) API, enabling secure access to email messages and supporting features like filtering, listing, and creating draft messages using OAuth2 Bearer Token authentication.
