# README-s-files for plugins in NoCode-x


# GitLab Plugin Documentation

## 1. Overview

This plugin provides integration with the GitLab API, allowing you to interact with GitLab projects, users, and issues. It offers several methods for retrieving user information, fetching project lists, and managing issues.

Additionally, the plugin has been integrated with **Pinecone**, allowing seamless interaction between GitLab data and Pinecone's vector database for advanced data management and processing.

## 2. Available Methods

### 1. **Get Logged-in User**
   - **What it does**: Fetches information about the currently authenticated user in GitLab.
   - **Configuration**: 
     - Requires authentication via a GitLab API token with appropriate scopes (`read_user`).
   - **Example Request**:
     ```json
     {
       "token": "your_gitlab_token"
     }
     ```

### 2. **Get Users List**
   - **What it does**: Retrieves a list of users in the GitLab instance.
   - **Configuration**: 
     - Requires authentication via a GitLab API token.
   - **Example Request**:
     ```json
     {
       "token": "your_gitlab_token"
     }
     ```

### 3. **Get Project's List**
   - **What it does**: Fetches a list of projects associated with the authenticated user or within a group.
   - **Configuration**: 
     - Requires authentication via a GitLab API token with `read_api` or `read_repository` permissions.
   - **Example Request**:
     ```json
     {
       "token": "your_gitlab_token"
     }
     ```

### 4. **Get Issues List**
   - **What it does**: Retrieves a list of issues from a specific project.
   - **Configuration**: 
     - Requires authentication via a GitLab API token and the project ID from which to fetch the issues.
     - Requires `read_api` permissions.
   - **Example Request**:
     ```json
     {
       "token": "your_gitlab_token",
       "project_id": "123456"
     }
     ```

## 3. Configuration

To configure this plugin, you need to provide the following:

- **GitLab API Token**: This plugin requires a personal access token from GitLab with appropriate permissions for the necessary methods.
  
  To generate a token:
  
  1. Log in to your GitLab account.
  2. Go to **Settings** > **Access Tokens**.
  3. Generate a new token with the required scopes (e.g., `read_user`, `read_api`, `read_repository`).
  4. Store the token securely and provide it in the plugin configuration.

- **Data Format**: The API credentials and other configurations should be provided in JSON format. Here's an example:

  ```json
  {
    "Personal_access_token": "your_gitlab_token"
  }
  ```

- **Pinecone Integration**: The plugin can seamlessly interact with Pinecone by passing GitLab project, user, or issue data directly into Pinecone's vector database for further processing. Ensure that both GitLab and Pinecone API credentials are provided for smooth integration.

## 4. Links to Documentation

- [GitLab REST API Documentation](https://docs.gitlab.com/ee/api/)
- [Creating a Personal Access Token in GitLab](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html)
- [Pinecone Documentation](https://docs.pinecone.io)

