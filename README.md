# README-s-files for plugins in NoCode-x


# Bitbucket Plugin Documentation

## 1. Overview

This plugin provides integration with the Bitbucket API, allowing you to interact with repositories, files, and workspaces. It offers several methods for committing files, fetching file contents, and listing user workspaces.

Additionally, the plugin has been integrated with **Pinecone**, allowing seamless interaction between Bitbucket data and Pinecone's vector database for advanced data management and processing.

## 2. Available Methods

### 1. **Create a Commit by Uploading a File**
   - **What it does**: Creates a new commit in a Bitbucket repository by uploading a file.
   - **Configuration**: 
     - Requires authentication via a Bitbucket API token with `repository:write` permissions.
     - You need to provide the repository, branch, and file path.
   - **Example Request**:
     ```json
     {
       "files": "file_path",
       "branch": "main",
       "message": "message",
       "author": "Author Name <e-mail>"
     }
     ```

### 2. **Get File or Directory Contents**
   - **What it does**: Retrieves the content of a specific file or the listing of a directory from a Bitbucket repository.
   - **Configuration**: 
     - Requires authentication via a Bitbucket API token with `repository:read` permissions.
     - You need to provide the repository, branch, and the file or directory path.

### 3. **List Workspaces for User**
   - **What it does**: Fetches a list of workspaces associated with the authenticated user in Bitbucket.
   - **Configuration**: 
     - Requires authentication via a Bitbucket API token with `account:read` permissions.

## 3. Configuration

To configure this plugin, you need to provide the following:

- **Bitbucket API Token**: This plugin requires a personal access token from Bitbucket with appropriate permissions (`repository:read`, `repository:write`, `account:read`) for the necessary methods.
  
  To generate a token:
  
  1. Log in to your Bitbucket account.
  2. Go to **Personal Settings** > **App passwords**.
  3. Generate a new token with the required scopes.
  4. Store the token securely and provide it in the plugin configuration.

- **Data Format**: The API credentials and other configurations should be provided in JSON format. Here's an example:

  ```json
  {
    "Repository_Access_Token": "your_repository_access_token"
  }
  ```

- **Pinecone Integration**: The plugin can seamlessly interact with Pinecone by passing Bitbucket repository or workspace data directly into Pinecone's vector database for further processing. Ensure that both Bitbucket and Pinecone API credentials are provided for smooth integration.

## 4. Links to Documentation

- [Bitbucket REST API Documentation](https://developer.atlassian.com/bitbucket/api/2/reference/)
- [Creating a Repository Access Token in Bitbucket](https://support.atlassian.com/bitbucket-cloud/docs/app-passwords/)
- [Pinecone Documentation](https://docs.pinecone.io)
