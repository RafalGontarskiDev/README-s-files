# Google Photos API Plugin Documentation

## 1. Overview

The **Google Photos API Plugin** enables seamless interaction with Google Photos, allowing users to manage albums, media items, and create new albums or upload photos. Authentication is managed through **OAuth2 Bearer Access Token**, which includes delegated user access and necessary scopes for secure interaction with the Google Photos API.

## 2. Available Methods

### 1. **Albums List**
   - **Endpoint**: `GET https://photoslibrary.googleapis.com/v1/albums`
   - **What it does**: Retrieves a list of albums from the user's Google Photos library.
   - **Configuration**:
     - Requires Bearer Token authentication with proper OAuth2 scopes.
     - **Scopes required**: `https://www.googleapis.com/auth/photoslibrary.readonly`
   - **Use case**: Use this method to fetch a list of all albums in a user's Google Photos account for display or management.

#### Example Request:
```http
GET https://photoslibrary.googleapis.com/v1/albums
Authorization: Bearer {{access_token}}
```

### 2. **Get Album by ID**
   - **Endpoint**: `GET https://photoslibrary.googleapis.com/v1/albums/{{albumId}}`
   - **What it does**: Retrieves details of a specific album by its unique `albumId`.
   - **Configuration**:
     - Requires `albumId`, the unique identifier of the album.
     - Requires Bearer Token authentication with proper OAuth2 scopes.
     - **Scopes required**: `https://www.googleapis.com/auth/photoslibrary.readonly`
   - **Use case**: Use this method to fetch detailed information about a specific album in Google Photos.

#### Example Request:
```http
GET https://photoslibrary.googleapis.com/v1/albums/{{albumId}}
Authorization: Bearer {{access_token}}
```

### 3. **MediaItems List**
   - **Endpoint**: `GET https://photoslibrary.googleapis.com/v1/mediaItems`
   - **What it does**: Retrieves a list of media items (photos and videos) from the user's Google Photos library.
   - **Configuration**:
     - Requires Bearer Token authentication with proper OAuth2 scopes.
     - **Scopes required**: `https://www.googleapis.com/auth/photoslibrary.readonly`
   - **Use case**: Use this method to list all media items (photos and videos) in the user’s Google Photos library.

#### Example Request:
```http
GET https://photoslibrary.googleapis.com/v1/mediaItems
Authorization: Bearer {{access_token}}
```

### 4. **Media Items Batch Create**
   - **Endpoint**: `POST https://photoslibrary.googleapis.com/v1/mediaItems:batchCreate`
   - **What it does**: Uploads new media items (photos or videos) to the user's Google Photos library in batch.
   - **Configuration**:
     - Requires Bearer Token authentication with proper OAuth2 scopes.
     - **Scopes required**: `https://www.googleapis.com/auth/photoslibrary.appendonly`
     - The request body must include the media items to be uploaded.
   - **Use case**: Use this method to programmatically upload photos or videos to the user’s Google Photos library.

#### Example Request Body:
```json
{
  "newMediaItems": [
    {
      "description": "Vacation photo",
      "simpleMediaItem": {
        "uploadToken": "your_upload_token"
      }
    }
  ]
}
```

#### Example Request:
```http
POST https://photoslibrary.googleapis.com/v1/mediaItems:batchCreate
Authorization: Bearer {{access_token}}
Content-Type: application/json
```

### 5. **Create Album**
   - **Endpoint**: `POST https://photoslibrary.googleapis.com/v1/albums`
   - **What it does**: Creates a new album in the user's Google Photos library.
   - **Configuration**:
     - Requires Bearer Token authentication with proper OAuth2 scopes.
     - **Scopes required**: `https://www.googleapis.com/auth/photoslibrary`
     - The request body must contain details about the new album, such as its title.
   - **Use case**: Use this method to create new albums for organizing photos and videos in Google Photos.

#### Example Request Body:
```json
{
  "album": {
    "title": "New Album"
  }
}
```

#### Example Request:
```http
POST https://photoslibrary.googleapis.com/v1/albums
Authorization: Bearer {{access_token}}
Content-Type: application/json
```

## 3. Configuration

To use this plugin, you must authenticate using **OAuth2 Bearer Access Token** with the appropriate scopes for each method. The access token grants permission for specific actions on behalf of the user.

### 1. **OAuth2 Setup for Google Photos API**
   - **Delegated user type**: The plugin acts on behalf of the authenticated user, allowing it to access their Google Photos library.
   - **Required Scopes**:
     - `https://www.googleapis.com/auth/photoslibrary.readonly`: Read-only access to view media items and albums.
     - `https://www.googleapis.com/auth/photoslibrary.appendonly`: Allows appending new media items.
     - `https://www.googleapis.com/auth/photoslibrary`: Full access to create and modify albums and media.
   - The OAuth2 consent flow must be followed to obtain the **access token**, which is then used in the Authorization header for API requests.

### 2. **Steps to Configure OAuth2**
   - Create a Google Cloud project and enable the **Google Photos API**.
   - Configure OAuth2 credentials in the Google Cloud Console.
   - Generate an **access token** for the authenticated user by completing the OAuth2 consent flow with the required scopes.
   - Use the **Bearer access token** in API requests for authentication.

### 3. **JSON Configuration Example**

```json
{
  "access_token": "your_google_oauth_access_token"
}
```

This configuration allows secure access to the Google Photos API for retrieving and managing albums and media items.

## 4. Links to Documentation

- [Google Photos API Documentation](https://developers.google.com/photos/library/reference/rest)
- [Google OAuth2 Setup](https://developers.google.com/identity/protocols/oauth2)

This documentation provides a detailed guide to interacting with the Google Photos API, ensuring secure and efficient management of photos, albums, and media items with proper OAuth2 authentication.
