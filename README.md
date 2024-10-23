# Microsoft Contacts API Plugin Documentation

## 1. Overview

The **Microsoft Contacts API Plugin** allows integration with Microsoft Contacts, enabling users to manage their contacts by retrieving and creating contact information. Authentication is managed through a **Bearer Access Token** using `microsoft_access_token`, which provides secure access to user contacts via the Microsoft Graph API.

## 2. Available Methods

### 1. **Get Contact**
   - **Endpoint**: `GET https://graph.microsoft.com/v1.0/users/{{userId}}/contacts/{{contactId}}`
   - **What it does**: Retrieves a specific contact by its `contactId` for a given user.
   - **Configuration**:
     - Requires `userId` and `contactId` (the unique identifiers for the user and the contact).
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
   - **Use case**: Use this method to fetch detailed information about a specific contact, including their name, email, phone number, and other details.

#### Example Request:
```http
GET https://graph.microsoft.com/v1.0/users/{{userId}}/contacts/{{contactId}}
Authorization: Bearer {{microsoft_access_token}}
```

### 2. **Create Contact**
   - **Endpoint**: `POST https://graph.microsoft.com/v1.0/users/{{userId}}/contacts`
   - **What it does**: Creates a new contact for a specific user.
   - **Configuration**:
     - Requires `userId`, the unique identifier of the user.
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
     - The request body must contain the contact details such as name, email, and phone number.
   - **Use case**: Use this method to programmatically add new contacts to a user's address book.

#### Example Request Body:
```json
{
  "givenName": "John",
  "surname": "Doe",
  "emailAddresses": [
    {
      "address": "johndoe@example.com",
      "name": "John Doe"
    }
  ],
  "businessPhones": ["+1 555 555 5555"]
}
```

#### Example Request:
```http
POST https://graph.microsoft.com/v1.0/users/{{userId}}/contacts
Authorization: Bearer {{microsoft_access_token}}
Content-Type: application/json
```

## 3. Configuration

To use the Microsoft Contacts API, you need to authenticate using an **OAuth2 Bearer Token**. This token provides access to the user's contacts for retrieving or adding contact information.

### 1. **Bearer Token Setup**
   - The Microsoft Graph API requires OAuth2 authentication to generate an access token.
   - Obtain an access token by following the OAuth2 flow for Microsoft services, using the **Microsoft Identity platform**.
   - The access token must be included in the Authorization header for each API request.

### 2. **Required Scopes**
   The following OAuth2 scopes are typically required:
   - `Contacts.Read`: Allows reading user contacts.
   - `Contacts.ReadWrite`: Allows reading and writing user contacts.

### 3. **JSON Configuration Example**

```json
{
  "microsoft_access_token": "your_microsoft_oauth2_access_token"
}
```

This configuration allows secure access to Microsoft Contacts for managing and retrieving user contacts programmatically.

## 4. Links to Documentation

- [Microsoft Contacts API Documentation](https://learn.microsoft.com/en-us/graph/api/resources/contact?view=graph-rest-1.0)
- [Microsoft Graph API Access Setup](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-auth-code-flow)

This documentation provides a guide to interacting with the Microsoft Contacts API, allowing secure access to contacts and enabling the creation and retrieval of contact information using OAuth2 Bearer Token authentication.
