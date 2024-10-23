# Microsoft Bookings API Plugin Documentation

## 1. Overview

The **Microsoft Bookings API Plugin** allows integration with Microsoft Bookings, enabling users to manage booking businesses and customers. With this API, you can list, retrieve, and create booking businesses and customers. Authentication is managed through a **Bearer Access Token** using `microsoft_access_token`, providing secure access via the Microsoft Graph API.

## 2. Available Methods

### 1. **List Booking Businesses**
   - **Endpoint**: `GET https://graph.microsoft.com/v1.0/solutions/bookingBusinesses`
   - **What it does**: Retrieves a list of all booking businesses associated with the authenticated user.
   - **Configuration**:
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
   - **Use case**: Use this method to retrieve all booking businesses under the authenticated account for management or display.

#### Example Request:
```http
GET https://graph.microsoft.com/v1.0/solutions/bookingBusinesses
Authorization: Bearer {{microsoft_access_token}}
```

### 2. **Get Booking Business**
   - **Endpoint**: `GET https://graph.microsoft.com/v1.0/solutions/bookingBusinesses/{{bookingBusinessId}}`
   - **What it does**: Retrieves details of a specific booking business by its `bookingBusinessId`.
   - **Configuration**:
     - Requires `bookingBusinessId`, the unique identifier of the booking business.
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
   - **Use case**: Use this method to get detailed information about a specific booking business, including its name, services, and settings.

#### Example Request:
```http
GET https://graph.microsoft.com/v1.0/solutions/bookingBusinesses/{{bookingBusinessId}}
Authorization: Bearer {{microsoft_access_token}}
```

### 3. **Create Booking Business**
   - **Endpoint**: `POST https://graph.microsoft.com/v1.0/solutions/bookingBusinesses`
   - **What it does**: Creates a new booking business for managing appointments and services.
   - **Configuration**:
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
     - The request body must contain the details of the booking business such as the business name, address, and other relevant information.
   - **Use case**: Use this method to programmatically create new booking businesses for managing appointments and schedules.

#### Example Request Body:
```json
{
  "displayName": "New Booking Business",
  "address": {
    "street": "123 Main St",
    "city": "City",
    "state": "State",
    "postalCode": "12345",
    "countryOrRegion": "USA"
  },
  "businessType": "Consulting"
}
```

#### Example Request:
```http
POST https://graph.microsoft.com/v1.0/solutions/bookingBusinesses
Authorization: Bearer {{microsoft_access_token}}
Content-Type: application/json
```

### 4. **Create Booking Customer**
   - **Endpoint**: `POST https://graph.microsoft.com/v1.0/solutions/bookingBusinesses/{{bookingBusinessId}}/customers`
   - **What it does**: Creates a new customer for a specific booking business.
   - **Configuration**:
     - Requires `bookingBusinessId`, the unique identifier of the booking business.
     - Requires **Bearer Token** authentication using `microsoft_access_token`.
     - The request body must include the customer's details such as their name, email, and phone number.
   - **Use case**: Use this method to add a new customer to a booking business for appointment scheduling.

#### Example Request Body:
```json
{
  "displayName": "John Doe",
  "emailAddress": "johndoe@example.com",
  "phone": "+1 555 555 5555"
}
```

#### Example Request:
```http
POST https://graph.microsoft.com/v1.0/solutions/bookingBusinesses/{{bookingBusinessId}}/customers
Authorization: Bearer {{microsoft_access_token}}
Content-Type: application/json
```

## 3. Configuration

To use the Microsoft Bookings API, you must authenticate using an **OAuth2 Bearer Token**. This token provides access to booking businesses and customers for managing appointments and related services.

### 1. **Bearer Token Setup**
   - The Microsoft Graph API requires OAuth2 authentication to generate an access token.
   - Obtain an access token by following the OAuth2 flow for Microsoft services, using the **Microsoft Identity platform**.
   - The access token must be included in the Authorization header for each API request.

### 2. **Required Scopes**
   The following OAuth2 scopes are typically required:
   - `Bookings.ReadWrite.All`: Allows reading and writing to Microsoft Bookings businesses and customers.

### 3. **JSON Configuration Example**

```json
{
  "microsoft_access_token": "your_microsoft_oauth2_access_token"
}
```

This configuration allows secure access to Microsoft Bookings for managing booking businesses, customers, and related services.

## 4. Links to Documentation

- [Microsoft Bookings API Documentation](https://learn.microsoft.com/en-us/graph/api/resources/booking-api-overview?view=graph-rest-1.0)
- [Microsoft Graph API Access Setup](https://learn.microsoft.com/en-us/azure/active-directory/develop/v2-oauth2-auth-code-flow)

This documentation provides a guide to interacting with the Microsoft Bookings API, enabling secure access to booking businesses and customers with OAuth2 Bearer Token authentication.
