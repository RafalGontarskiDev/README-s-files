# Airtable API Plugin Documentation

## 1. Overview

The **Airtable API Plugin** allows integration with Airtable, enabling users to manage databases, tables, and records. This plugin provides methods to list records, create and update bases and tables, retrieve and delete specific records, and more. Authentication is handled through Bearer Token using a **USER TOKEN**, ensuring secure access to Airtable's resources.

## 2. Available Methods

### 1. **List Records**
   - **Endpoint**: `GET https://api.airtable.com/v0/{{baseId}}/{{tableName}}`
   - **What it does**: Retrieves a list of records from a specified table in Airtable.
   - **Configuration**:
     - Requires `baseId`, the ID of the Airtable base.
     - Requires `tableName`, the name of the table.
     - Requires Bearer Token authentication with the `USER_TOKEN`.
   - **Use case**: Use this method to fetch and display records from a particular table in Airtable.

### 2. **Get Record**
   - **Endpoint**: `GET https://api.airtable.com/v0/{{baseId}}/{{tableIdOrName}}/{{recordId}}`
   - **What it does**: Retrieves a specific record by its unique `recordId`.
   - **Configuration**:
     - Requires `baseId` and `tableIdOrName`, the name or ID of the table.
     - Requires `recordId`, the unique identifier of the record.
     - Requires Bearer Token authentication with the `USER_TOKEN`.
   - **Use case**: Use this method to retrieve detailed information about a specific record in a table.

### 3. **Create Base**
   - **Endpoint**: `POST https://api.airtable.com/v0/meta/bases`
   - **What it does**: Creates a new base in Airtable.
   - **Configuration**:
     - Requires a Bearer Token with the necessary permissions (`USER_TOKEN`).
     - The request body must include details such as the base name and configurations.
   - **Use case**: Use this method to programmatically create a new Airtable base for organizing data.

#### Example Request Body:
```json
{
  "name": "New Base"
}
```

### 4. **Create Table**
   - **Endpoint**: `POST https://api.airtable.com/v0/meta/bases/{{baseId}}/tables`
   - **What it does**: Creates a new table within an existing base.
   - **Configuration**:
     - Requires `baseId`, the ID of the base.
     - Requires a Bearer Token for authentication (`USER_TOKEN`).
     - The request body should contain table details like the table name and field configurations.
   - **Use case**: Use this method to add a new table to an existing base for managing records.

#### Example Request Body:
```json
{
  "name": "New Table",
  "fields": [
    {
      "name": "Field 1",
      "type": "singleLineText"
    },
    {
      "name": "Field 2",
      "type": "number"
    }
  ]
}
```

### 5. **Create Record**
   - **Endpoint**: `POST https://api.airtable.com/v0/{{baseId}}/{{tableName}}`
   - **What it does**: Adds a new record to a specified table in Airtable.
   - **Configuration**:
     - Requires `baseId`, the ID of the base.
     - Requires `tableName`, the name of the table.
     - Requires a Bearer Token for authentication (`USER_TOKEN`).
     - The request body should contain the fields and data for the new record.
   - **Use case**: Use this method to insert new data into an existing table.

#### Example Request Body:
```json
{
  "fields": {
    "Name": "John Doe",
    "Age": 30
  }
}
```

### 6. **Update Table**
   - **Endpoint**: `PATCH https://api.airtable.com/v0/meta/bases/{{baseId}}/tables/{{tableName}}`
   - **What it does**: Updates the structure of a table, such as adding, renaming, or deleting fields.
   - **Configuration**:
     - Requires `baseId` and `tableName`.
     - Requires Bearer Token authentication with the `USER_TOKEN`.
     - The request body should include details of the changes.
   - **Use case**: Use this method to update a table's configuration, like changing field names or types.

#### Example Request Body:
```json
{
  "fields": [
    {
      "name": "New Field Name",
      "type": "singleLineText"
    }
  ]
}
```

### 7. **Delete Record**
   - **Endpoint**: `DELETE https://api.airtable.com/v0/{{baseId}}/{{tableIdOrName}}/{{recordId}}`
   - **What it does**: Deletes a specific record from a table.
   - **Configuration**:
     - Requires `baseId`, `tableIdOrName`, and `recordId`.
     - Requires Bearer Token authentication with the `USER_TOKEN`.
   - **Use case**: Use this method to delete specific records when they are no longer needed.

## 3. Configuration

To use this plugin, you will need to authenticate using a **Bearer Token**. This token must have the necessary permissions to interact with the Airtable API based on the actions you intend to perform.

### 1. **Bearer Token Setup**
   - In Airtable, you can generate a personal API key (Bearer Token) from your account settings.
   - This token should be passed as a Bearer token in the headers of all API requests.

### 2. **JSON Configuration Example**

```json
{
  "USER_TOKEN": "your_airtable_bearer_token"
}
```

This configuration allows the plugin to authenticate with Airtable and perform the various actions described above.

## 4. Links to Documentation

- [Airtable API Documentation](https://airtable.com/api)

This documentation provides a clear guide to interacting with Airtable’s API, enabling seamless management of bases, tables, and records with secure Bearer Token authentication.
