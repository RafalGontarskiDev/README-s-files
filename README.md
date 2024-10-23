# README-s-files for plugins in NoCode-x


# GitLab API Plugin Documentation

## 1. Overview

This plugin provides integration with the GitLab API, enabling various interactions with GitLab's user data, repositories, and files. It allows you to retrieve information about users, access project repositories, and download files from the GitLab repository. Authentication is managed through personal access tokens, ensuring secure access to the necessary GitLab resources.

## 2. Available Methods

### 1. **Get Users List**
   - **Endpoint**: `GET https://gitlab.com/api/v4/users`
   - **What it does**: Retrieves a list of users in the GitLab instance.
   - **Configuration**: 
     - Requires a GitLab API token with the `read_user` scope.
   - **Use case**: Useful for fetching information about users within the GitLab system, such as when creating a user directory or managing user-related tasks.

### 2. **List Repository Tree**
   - **Endpoint**: `GET https://gitlab.com/api/v4/projects/{{projectId}}/repository/tree`
   - **What it does**: Fetches the structure of a specific project repository, including files and folders.
   - **Configuration**: 
     - Requires `projectId`, the unique ID of the GitLab project.
     - Requires a GitLab API token with `read_repository` permission.
   - **Use case**: Use this method to retrieve the entire file structure of a repository, which can help in navigating large projects or preparing for file downloads.

### 3. **Downloading a File from the Project Repository**
   - **Endpoint**: `GET https://gitlab.com/api/v4/projects/{{projectId}}/repository/files/{{filePath}}/raw`
   - **What it does**: Fetches the raw content of a specified file from the GitLab repository.
   - **Configuration**:
     - Requires `projectId` and `filePath`, the exact path to the file in the repository.
     - Requires a GitLab API token with `read_repository` permission.
   - **Use case**: This method is useful for downloading files directly from the GitLab repository, such as for local development, code reviews, or data analysis.

## 3. Configuration

To use this plugin, you'll need to provide a GitLab **personal access token**. The token must have the appropriate scopes (permissions) for the methods described above. Here’s how you can set up the configuration:

### 1. **Personal Access Token**
   - Personal access tokens are required to authenticate requests to GitLab's API.
   - You must create a token with the necessary permissions, such as `read_user` and `read_repository`, depending on which methods you intend to use.

### 2. **Steps to Generate Personal Access Token**
   - Log in to your GitLab account.
   - Navigate to **Settings** > **Access Tokens**.
   - Create a new token and select the required scopes based on the methods you will use (e.g., `read_user`, `read_repository`).
   - Once generated, securely store this token, as it will be needed for all API requests.

### 3. **JSON Configuration Example**

```json
{
  "Personal_access_token": "your_gitlab_personal_access_token"
}
```

This configuration will allow the plugin to authenticate with GitLab and access user lists, project repositories, and files using the provided methods.

## 4. Links to Documentation

- [GitLab REST API Documentation](https://docs.gitlab.com/ee/api/)
- [GitLab Personal Access Token Guide](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html)

This documentation provides an easy guide to accessing and interacting with GitLab's API, ensuring secure access and efficient use of repository and user data.
