# Stripe Events API Plugin Documentation

## 1. Overview

The **Stripe Events API Plugin** allows integration with Stripe’s event tracking, enabling users to list all events or retrieve details about a specific event. Authentication is managed through **Basic Authentication** using `Secret_key`, ensuring secure access to Stripe's resources.

## 2. Available Methods

### 1. **List All Events**
   - **Endpoint**: `GET https://api.stripe.com/v1/events`
   - **What it does**: Retrieves a list of all events that have occurred in your Stripe account, such as payments, refunds, or subscription updates.
   - **Configuration**:
     - Requires **Basic Authentication** using `Secret_key`.
     - Optional query parameters can be used to filter results by event type or date range.
   - **Use case**: Use this method to monitor and track various events within your Stripe account for auditing or troubleshooting purposes.

#### Example Request:
```http
GET https://api.stripe.com/v1/events
Authorization: Basic {{base64_encoded(Secret_key:)}}
```

### 2. **Retrieve an Event**
   - **Endpoint**: `GET https://api.stripe.com/v1/events/{{eventId}}`
   - **What it does**: Retrieves detailed information about a specific event using its `eventId`.
   - **Configuration**:
     - Requires `eventId`, the unique identifier of the event.
     - Requires **Basic Authentication** using `Secret_key`.
   - **Use case**: Use this method to get detailed information on a particular event for verification, debugging, or analysis.

#### Example Request:
```http
GET https://api.stripe.com/v1/events/{{eventId}}
Authorization: Basic {{base64_encoded(Secret_key:)}}
```

## 3. Configuration

To use the Stripe Events API, you must authenticate using **Basic Authentication** with your `Secret_key`. The API key is passed as the username in the Basic Authentication scheme, with no password required.

### 1. **Basic Authentication Setup**
   - Use your Stripe `Secret_key` as the username for Basic Authentication.
   - The credentials must be base64 encoded.
   - The Authorization header will look like this:
     - `Authorization: Basic base64(Secret_key:)`

### 2. **JSON Configuration Example**

```json
{
  "Secret_key": "your_stripe_secret_key"
}
```

This configuration ensures secure access to Stripe’s event tracking resources.

## 4. Links to Documentation

- [Stripe Events API Documentation](https://stripe.com/docs/api/events)
- [Stripe API Access Setup](https://stripe.com/docs/keys)

This documentation provides a guide to interacting with the Stripe Events API, enabling secure access to event listings and details using Basic Authentication with your Stripe Secret key.
