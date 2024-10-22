# README-s-files for plugins in NoCode-x


# Bitbucket Pinecone Assistant Plugin Documentation

## 1. Overview

This plugin provides integration with the Bitbucket API, allowing you to interact with repositories, files, and workspaces. It offers several methods for committing files, fetching file contents, and listing user workspaces.

Additionally, the plugin has been integrated with **Pinecone**, allowing seamless interaction between Bitbucket data and Pinecone's vector database for advanced data management and processing.

## 2. Available Methods

### 1. **Get File or Directory Contents**
   - **What it does**: Retrieves the content of a specific file or the listing of a directory from a Bitbucket repository.
   - **Configuration**: 
     - Requires authentication via a Bitbucket API token with `repository:read` permissions.
     - You need to provide the repository, branch, and the file or directory path.
   - **Example Request**:
     ```plaintext
     GET https://api.bitbucket.org/2.0/repositories/{{workspaceSlug}}/{{repoSlug}}/src/{{commit}}/{{path}}?max_depth=3&pagelen=100
     ```

   - **What it returns**: List of files in the repository starting from the specified path (e.g., `/` for the root directory). It supports recursive file fetching through `max_depth`.

### 2. **Fetch File by Path**
   - **What it does**: Fetches a specific file from a Bitbucket repository using its exact path.
   - **Configuration**:
     - Requires authentication via a Bitbucket API token with `repository:read` permissions.
     - You need to provide the repository, branch, and the file path.
   - **Example Request**:
     ```plaintext
     GET https://api.bitbucket.org/2.0/repositories/{{workspaceSlug}}/{{repoSlug}}/src/{{commit}}/{{path}}
     ```

   - **What it returns**: The content of the specified file.

### 3. **Feed Assistant (Upload Files to Pinecone Assistant)**
   - **What it does**: Uploads files fetched from Bitbucket to a Pinecone Assistant for further processing or data vectorization.
   - **How it works**:
     - This method fetches files using the Bitbucket `Get File or Directory Contents` or `Fetch File by Path` methods and uploads them directly to a Pinecone Assistant.
     - Requires authentication with both Bitbucket and Pinecone API tokens.
     - The file path in Bitbucket and the Pinecone Assistant name need to be provided.
   - **Example Request** (Upload file to Pinecone Assistant):
     ```plaintext
     POST https://prod-1-data.ke.pinecone.io/assistant/files/{{ASSISTANT_NAME}}
     ```

     ```json
     {
       "file": "file_contents",
       "metadata": {
         "filename": "example.txt",
         "source": "Bitbucket"
       }
     }
     ```

   - **What it returns**: Confirmation of the file upload to Pinecone Assistant.

## 3. Configuration

To configure this plugin, you need to provide the following:

- **Bitbucket API Token**: This plugin requires a personal access token from Bitbucket with appropriate permissions (`repository:read`, `repository:write`, `account:read`) for the necessary methods.
  
  To generate a token:
  
  - Log in to your Bitbucket account.
  - Go to **Personal Settings** > **App passwords**.
  - Generate a new token with the required scopes.
  - Store the token securely and provide it in the plugin configuration.

- **Pinecone API Token**: The plugin requires a valid Pinecone API token for integration with Pinecone Assistant. You must generate this token from the Pinecone dashboard and include it in the plugin configuration.
  
  To generate a token:
  
  - Log in to your Pinecone account.
  - Go to **API Keys** and create a new key with the required permissions.
  - Store the token securely and provide it in the plugin configuration.

- **Data Format**: The API credentials and other configurations should be provided in JSON format. Here's an example:

  ```json
  {
    "Repository_Access_Token": "your_repository_access_token",
    "Pinecone_Access_Token": "your_pinecone_access_token"
  }
  ```

- **Pinecone Integration**: The plugin can seamlessly interact with Pinecone by passing Bitbucket repository or workspace data directly into Pinecone's vector database for further processing. Ensure that both Bitbucket and Pinecone API credentials are provided for smooth integration.

## 4. Links to Documentation

- [Bitbucket REST API Documentation](https://developer.atlassian.com/bitbucket/api/2/reference/)
- [Creating a Repository Access Token in Bitbucket](https://support.atlassian.com/bitbucket-cloud/docs/app-passwords/)
- [Pinecone Documentation](https://docs.pinecone.io)
