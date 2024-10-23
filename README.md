# README-s-files for plugins in NoCode-x


# GitHub API Plugin Documentation

## 1. Overview

The GitHub API plugin enables interaction with GitHub's user and repository data. This plugin allows you to retrieve user details, access repository content, and create new repositories using GitHub's API. Authentication is handled through personal access tokens, ensuring secure access to GitHub resources.

## 2. Available Methods

### 1. **Get User by ID**
   - **Endpoint**: `GET https://api.github.com/user/{{id}}`
   - **What it does**: Retrieves information about a specific GitHub user by their user ID.
   - **Configuration**: 
     - Requires `id`, which is the GitHub user's unique ID.
     - Requires a GitHub API token with `user` scope.
   - **Use case**: Use this method to fetch detailed information about a user, such as their profile, public repositories, and activity.

### 2. **Get Repository Content List**
   - **Endpoint**: `GET https://api.github.com/repos/{{owner}}/{{repo}}/contents`
   - **What it does**: Fetches the content (files and directories) of a specified GitHub repository.
   - **Configuration**:
     - Requires `owner` (the GitHub username or organization name) and `repo` (the repository name).
     - Requires a GitHub API token with `repo` scope to access private repositories.
   - **Use case**: Retrieve the structure of a repository to view and interact with its content.

### 3. **Get Repository Content File by Path**
   - **Endpoint**: `GET https://api.github.com/repos/{{owner}}/{{repo}}/contents/{{path}}`
   - **What it does**: Retrieves the content of a specific file within a repository.
   - **Configuration**:
     - Requires `owner`, `repo`, and `path` (the exact file path in the repository).
     - Requires a GitHub API token with `repo` scope for private repositories.
   - **Use case**: Useful for accessing raw file data in a repository for local use or further analysis.

### 4. **Create Repository**
   - **Endpoint**: `POST https://api.github.com/user/repos`
   - **What it does**: Creates a new repository under the authenticated user's GitHub account.
   - **Configuration**:
     - Requires a GitHub API token with `repo` and `public_repo` scopes.
     - The request body must include parameters such as `name` (repository name), `description`, `private` (whether the repo is private), etc.
   - **Use case**: Use this method to programmatically create a new repository for code management, collaboration, or version control.

#### Example Request Body:
```json
{
  "name": "new-repo",
  "description": "This is your repository",
  "private": false
}
```

## 3. Configuration

To use this plugin, you will need to provide a GitHub **personal access token**. The token must have the appropriate scopes (permissions) based on the methods you intend to use.

### 1. **GitHub Personal Access Token**
   - Personal access tokens are required for authenticating requests to GitHub's API.
   - Steps to generate a token:
     - Log in to GitHub.
     - Go to **Settings** > **Developer Settings** > **Personal Access Tokens**.
     - Create a new token and select the required scopes (e.g., `user`, `repo`, `public_repo`).
     - Securely store the token, as it will be used for all API requests.

### 2. **JSON Configuration Example**

```json
{
  "GitHub_token": "your_github_personal_access_token"
}
```

This configuration allows the plugin to authenticate with GitHub and perform the described actions.

## 4. Links to Documentation

- [GitHub REST API Documentation](https://docs.github.com/en/rest)
- [GitHub Personal Access Token Guide](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)

This documentation provides everything you need to interact with GitHub’s user and repository management system via its API.
