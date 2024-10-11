# README-s-files for plugins in NoCode-x

# GitHub Plugin Documentation

## 1. Overview
This plugin provides integration with the GitHub API, allowing you to interact with GitHub repositories and users. It offers several methods for repository creation, fetching user information, and retrieving repository content.

## 2. Available Methods

### 1. **Create Repository**
   - **What it does**: Creates a new repository in the authenticated user's GitHub account.
   - **Configuration**: 
     - Requires authentication via a GitHub API token with `repo` permissions.
     - You need to provide the repository name and other optional parameters such as visibility (public/private).
   - **Example Request**:
     ```json
     {
       "name": "my-new-repo",
       "description": "This is my new repository",
       "homepage" : "https://github.com",
       "private": true,
       "is_template": true
     }
     ```

### 2. **Get User**
   - **What it does**: Fetches information about the authenticated user or any specified user on GitHub.
   - **Configuration**: 
     - No special configuration needed beyond GitHub API authentication.

### 3. **Get User by ID**
   - **What it does**: Fetches detailed information about a user based on their unique GitHub user ID.
   - **Configuration**: 
     - Requires the GitHub user ID as an input.
     - Standard API token authentication is required.
   - **Example Request**:
     ```json
     {
       "userId": 583231
     }
     ```

### 4. **Get Repository Content File by Path**
   - **What it does**: Retrieves the content of a specific file from a repository by providing the repository path.
   - **Configuration**: 
     - Requires repository name, file path, and the branch from which to fetch the content.
     - API token with `repo` permissions.
   - **Example Request**:
     ```json
     {
       "owner": "owner_name",
       "repo": "repo_name",
       "path": "README.md"
     }
     ```

### 5. **Get Repository Content List**
   - **What it does**: Lists the contents of a directory or repository root.
   - **Configuration**: 
     - Requires repository name and path (optional, defaults to root).
     - API token with `repo` permissions.
   - **Example Request**:
     ```json
     {
       "owner": "owner_name",
       "repo": "repo_name",
       "path": ""
     }
     ```

## 3. Configuration

To configure this plugin, you need to provide the following:

- **GitHub API Token**: This plugin requires a personal access token from GitHub with appropriate permissions (`repo` scope) for the necessary methods.
  
  To generate a token:
  1. Log in to your GitHub account.
  2. Go to **Settings** > **Developer settings** > **Personal access tokens**.
  3. Generate a new token with the required scopes.
  
  Store the token securely and provide it in the plugin configuration.

- **Data Format**: The API credentials and other configurations should be provided in JSON format. Here's an example:

  ```json
  {
    "Personal_access_token": "your_personal_access_token"
  }
  ```

## 4. Links to Documentation

- [GitHub REST API Documentation](https://docs.github.com/en/rest)
- [Creating a Personal Access Token](https://docs.github.com/en/github/authenticating-to-github/creating-a-personal-access-token)
