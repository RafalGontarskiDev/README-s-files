# Jotform API Plugin Documentation

## 1. Overview

The **Jotform API Plugin** provides integration with Jotform, allowing users to retrieve forms, create new forms, and access form submissions. The plugin utilizes API key authentication to securely interact with Jotform data. It simplifies form management and submissions retrieval for a variety of use cases, including automation, reporting, and data analysis.

## 2. Available Methods

### 1. **Get Form by ID**
   - **Endpoint**: `GET https://eu-api.jotform.com/form/{{formID}}`
   - **What it does**: Retrieves a specific form by its unique form ID.
   - **Configuration**:
     - Requires `formID`, the unique identifier of the form in Jotform.
     - Requires an API key with read access to the form.
   - **Use case**: Use this method to retrieve the structure, settings, and details of a specific form for display or analysis.

### 2. **Create Form**
   - **Endpoint**: `POST https://eu-api.jotform.com/form`
   - **What it does**: Creates a new form in Jotform.
   - **Configuration**:
     - Requires an API key with full access to create forms.
     - The request body should contain the necessary form details, such as the form title, questions, and other settings.
   - **Use case**: Automatically generate new forms for various use cases like surveys, feedback collection, or registration forms.

#### Example Request Body:
```json
{
  "title": "New Form",
  "questions": [
    {
      "type": "control_textbox",
      "text": "Your Name",
      "name": "q1"
    }
  ]
}
```

### 3. **Get Form Submissions**
   - **Endpoint**: `GET https://eu-api.jotform.com/form/{{formId}}/submissions`
   - **What it does**: Retrieves the submissions of a specified form by its unique form ID.
   - **Configuration**:
     - Requires `formId`, the unique identifier of the form.
     - Requires an API key with read access to the form and its submissions.
   - **Use case**: Use this method to gather form responses for analysis, reporting, or exporting submission data to other systems.

## 3. Configuration

To use this plugin, you will need to authenticate using a **Jotform API key**. The API key must have the appropriate permissions based on the actions you intend to perform (read access for retrieving forms or submissions, full access for creating forms).

### 1. **Jotform API Key**
   - You can generate an API key by logging into your Jotform account:
     - Navigate to **My Account** > **API**.
     - Generate a new API key with the necessary permissions (e.g., read, create).
     - Store this key securely, as it will be required for all API requests.

### 2. **JSON Configuration Example**

```json
{
  "API_Key": "your_jotform_api_key"
}
```

This configuration allows you to authenticate with Jotform and use the described methods to interact with forms and submissions.

## 4. Links to Documentation

- [Jotform API Documentation](https://api.jotform.com/docs/)
- [Jotform API Key Setup](https://www.jotform.com/help/253-how-to-create-a-jotform-api-key)

This documentation provides a detailed guide to working with the Jotform API, ensuring smooth interaction with forms and submissions while maintaining secure API key access.
