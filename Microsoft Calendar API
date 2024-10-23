# Microsoft Calendar API Plugin Documentation

## 1. Overview

The **Microsoft Calendar API Plugin** allows integration with Microsoft Calendar, enabling users to manage calendars, events, and calendar views. Authentication is managed through a **Bearer Access Token** using `microsoft_access_token`, providing secure access to user calendars via Microsoft Graph API.

## 2. Available Methods

### 1. **List Calendar View**
   - **Endpoint**: `GET https://graph.microsoft.com/v1.0/users/{{userId}}/calendars/{{calendarId}}/calendarView?startDateTime={{startDatetime}}&endDateTime={{endDatetime}}`
   - **What it does**: Retrieves the events from a specific calendar within a date-time range.
   - **Configuration**:
     - Requires `userId`, `calendarId`, `startDatetime`, and `endDatetime` in ISO 8601 format.
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
   - **Use case**: Use this method to retrieve all calendar events in a specific date range, such as meetings or appointments within a week or month.

#### Example Request:
```http
GET https://graph.microsoft.com/v1.0/users/{{userId}}/calendars/{{calendarId}}/calendarView?startDateTime=2024-10-01T00:00:00Z&endDateTime=2024-10-31T23:59:59Z
Authorization: Bearer {{microsoft_access_token}}
```

### 2. **List Calendars**
   - **Endpoint**: `GET https://graph.microsoft.com/v1.0/users/{{userId}}/calendars`
   - **What it does**: Retrieves a list of all calendars associated with a user.
   - **Configuration**:
     - Requires `userId` (the unique identifier of the user).
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
   - **Use case**: Use this method to list all calendars for a specific user, such as personal, work, or shared calendars.

#### Example Request:
```http
GET https://graph.microsoft.com/v1.0/users/{{userId}}/calendars
Authorization: Bearer {{microsoft_access_token}}
```

### 3. **Create Calendar**
   - **Endpoint**: `POST https://graph.microsoft.com/v1.0/users/{{userId}}/calendars`
   - **What it does**: Creates a new calendar for a specific user.
   - **Configuration**:
     - Requires `userId` (the unique identifier of the user).
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
     - The request body must contain the calendar name and other optional details.
   - **Use case**: Use this method to programmatically create new calendars for organizing events or meetings.

#### Example Request Body:
```json
{
  "name": "New Calendar"
}
```

#### Example Request:
```http
POST https://graph.microsoft.com/v1.0/users/{{userId}}/calendars
Authorization: Bearer {{microsoft_access_token}}
Content-Type: application/json
```

### 4. **Create Event**
   - **Endpoint**: `POST https://graph.microsoft.com/v1.0/users/{{userId}}/calendars/{{calendarId}}/events`
   - **What it does**: Creates a new event in a specified calendar for a specific user.
   - **Configuration**:
     - Requires `userId`, `calendarId` (the unique identifiers of the user and calendar).
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
     - The request body must include details of the event such as subject, start and end time, location, and attendees.
   - **Use case**: Use this method to schedule meetings, appointments, or reminders programmatically.

#### Example Request Body:
```json
{
  "subject": "Team Meeting",
  "body": {
    "contentType": "HTML",
    "content": "Discuss project updates."
  },
  "start": {
    "dateTime": "2024-10-10T14:00:00",
    "timeZone": "Pacific Standard Time"
  },
  "end": {
    "dateTime": "2024-10-10T15:00:00",
    "timeZone": "Pacific Standard Time"
  },
  "location": {
    "displayName": "Conference Room"
  },
  "attendees": [
    {
      "emailAddress": {
        "address": "user@example.com",
        "name": "User Example"
      },
      "type": "required"
    }
  ]
}
```

#### Example Request:
```http
POST https://graph.microsoft.com/v1.0/users/{{userId}}/calendars/{{calendarId}}/events
Authorization: Bearer {{microsoft_access_token}}
Content-Type: application/json
```

### 5. **Get Calendar**
   - **Endpoint**: `GET https://graph.microsoft.com/v1.0/users/{{userId}}/calendars/{{calendarId}}`
   - **What it does**: Retrieves details of a specific calendar by its `calendarId`.
   - **Configuration**:
     - Requires `userId` and `calendarId` (the unique identifiers of the user and the calendar).
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
   - **Use case**: Use this method to retrieve details about a specific calendar, such as its name, owner, and events.

#### Example Request:
```http
GET https://graph.microsoft.com/v1.0/users/{{userId}}/calendars/{{calendarId}}
Authorization: Bearer {{microsoft_access_token}}
```

## 3. Configuration

To use the Microsoft Calendar API, you must authenticate using an **OAuth2 Bearer Token**. This token provides access to the user's calendars and events for managing their schedule programmatically.

### 1. **Bearer Token Setup**
   - The Microsoft Graph API requires OAuth2 authentication to generate an access token.
   - Obtain an access token by following the OAuth2 flow for Microsoft services, using the **Microsoft Identity platform**.
   - The access token must be included in the Authorization header for each API request.

### 2. **Required Scopes**
   The following OAuth2 scopes are typically required:
   - `Calendars.Read`: Allows reading user calendars.
   - `Calendars.ReadWrite`: Allows reading and writing user calendars and events.

### 3. **JSON Configuration Example**

```json
{
  "microsoft_access_token": "your_microsoft_oauth2_access_token"
}
```

This configuration allows secure access to Microsoft Calendar for managing and retrieving user calendars and events.

## 4. Links to Documentation

- [Microsoft Calendar API Documentation](https://learn.microsoft.com/en-us/graph/api/resources/calendar?view=graph-rest-1.0)
- [Microsoft Graph API Access Setup](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-auth-code-flow)

This documentation provides a guide to interacting with the Microsoft Calendar API, enabling secure access to calendars and events with OAuth2 Bearer Token authentication.
