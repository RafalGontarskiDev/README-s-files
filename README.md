# Mandrill API Plugin Documentation

## Introduction

This plugin allows you to interact with the Mandrill API to manage your email templates and retrieve account information. You can perform actions such as retrieving user information, getting template details, and adding new templates.

## Configuration

To use the plugin, you need to create a configuration data object that includes your Mandrill API key. This API key authenticates your requests to the Mandrill API.

### Creating Configuration Data

Your configuration data should be a JSON object that includes the following field:

- **`key`**: Your Mandrill API key.

**Example Configuration:**

```json
{
  "key": "your_api_key"
}
```

## Available Methods

### 1. [Get User Info](https://mailchimp.com/developer/transactional/api/users/get-user-info/)

- **Endpoint:** `POST https://mandrillapp.com/api/1.0/users/info`
- **Description:** Retrieves information about the authenticated user, including account details, reputation, and sending limits.

#### How to Use

1. **Prepare the Request Body:** Include your API key in the request body.

   **Example:**

   ```json
   {
     "key": "your_api_key"
   }
   ```

2. **Make the Request:** Send a POST request to the endpoint with the request body.

   **Example Request:**

   ```
   POST https://mandrillapp.com/api/1.0/users/info
   Content-Type: application/json
   ```

#### Expected Response

- Returns user account details such as username, reputation score, and email statistics.

### 2. [Get Template Info](https://mailchimp.com/developer/transactional/api/templates/get-template-info/)

- **Endpoint:** `POST https://mandrillapp.com/api/1.0/templates/info`
- **Description:** Retrieves detailed information about a specific email template.

#### How to Use

1. **Prepare the Request Body:** Include your API key and the name of the template you want to retrieve.

   **Example:**

   ```json
   {
     "key": "your_api_key",
     "name": "template_name"
   }
   ```

2. **Make the Request:** Send a POST request to the endpoint with the request body.

   **Example Request:**

   ```
   POST https://mandrillapp.com/api/1.0/templates/info
   Content-Type: application/json
   ```

#### Expected Response

- Returns detailed information about the specified template, including its HTML code, metadata, and last update timestamp.

### 3. [Add Template](https://mailchimp.com/developer/transactional/api/templates/add-template/)

- **Endpoint:** `POST https://mandrillapp.com/api/1.0/templates/add`
- **Description:** Creates a new email template in Mandrill for sending transactional emails.

#### How to Use

1. **Prepare the Request Body:** Include your API key and the template details such as name, HTML code, and optional settings.

   **Example:**

   ```json
   {
     "key": "your_api_key",
     "name": "new_template",
     "code": "<html><body><h1>Hello World!</h1></body></html>",
     "publish": true
   }
   ```

   - **Fields:**
     - `key`: Your Mandrill API key.
     - `name`: The name for the new template.
     - `code`: The HTML content of the template.
     - `publish`: (Optional) Set to `true` to publish the template immediately.

2. **Make the Request:** Send a POST request to the endpoint with the request body.

   **Example Request:**

   ```
   POST https://mandrillapp.com/api/1.0/templates/add
   Content-Type: application/json
   ```

#### Expected Response

- Returns details of the newly created template, including its unique ID and creation timestamp.

---

**Note:** Ensure that all requests include the `Content-Type: application/json` header and that your API key is kept secure.

For more information on each endpoint and additional parameters, refer to the [Mandrill API Documentation](https://mandrillapp.com/api/docs/).
This documentation provides a guide to interacting with the Stripe Events API, enabling secure access to event listings and details using Basic Authentication with your Stripe Secret key.
