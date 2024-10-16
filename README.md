# README-s-files for plugins in NoCode-x


### Google Docs Plugin Documentation

#### 1. Overview
This plugin provides integration with the Google Docs API, allowing you to interact with Google documents. It offers several methods for creating new documents, batch updating document content, and fetching documents by their ID.

Additionally, the plugin is integrated with Pinecone, enabling seamless interaction between Google Docs content and Pinecone's vector database for advanced data management, search, and processing.

#### 2. Available Methods

1. **Create a Document**
   - **What it does**: Creates a new document in Google Docs.
   - **Configuration**:
     - Requires authentication via Google API OAuth 2.0.
     - You need to provide a title for the document.

2. **Batch Update a Document**
   - **What it does**: Allows batch updates to be applied to a document, such as adding text, formatting, or replacing content.
   - **Configuration**:
     - Requires authentication via Google API OAuth 2.0.
     - You need to provide the document ID and a list of update requests.
   - **Example Request**:
   ```json
   {
     "documentId": "your_doc_id",
     "requests": [
       {
         "insertText": {
           "location": {
             "index": 1
           },
           "text": "New text to insert"
         }
       }
     ]
   }
   ```

3. **Get Document by ID**
   - **What it does**: Fetches the content of a Google Docs document by its ID.
   - **Configuration**:
     - Requires authentication via Google API OAuth 2.0.
     - You need to provide the document ID.
   - **Example Request**:
   ```json
   {
     "documentId": "your_doc_id"
   }
   ```

### 3. Configuration

To configure this plugin, you need to provide the following:

- **Google Docs API Access**: The plugin uses the user's delegated credentials and requires an access token (ACCESS_TOKEN) with the appropriate scopes to interact with Google Docs (e.g., `https://www.googleapis.com/auth/documents.readonly`, `https://www.googleapis.com/auth/documents`). The access can be granted either through user delegation or directly via a standard user account.

  - **How to generate an access token**:
    - Log in to your Google Cloud account.
    - Enable the Google Docs API for your project.
    - Create OAuth 2.0 credentials in the Google Cloud Console (either for user delegation or directly for the user).
    - Obtain the access token using the credentials.
  
  - The plugin will automatically handle and apply the user's delegated credentials through the `ACCESS_TOKEN` variable, allowing seamless access to Google Docs. Ensure that the token is refreshed appropriately.

- **Data Format**: The API credentials and other configurations should be provided in JSON format. Here's an example:

```json
{
  "ACCESS_TOKEN": "your_access_token"
}
```

This approach allows flexibility in using either delegated credentials or a direct user access token for the plugin configuration.

#### 4. Pinecone Integration

The plugin is integrated with Pinecone to enable efficient vector-based search and data processing on Google Docs content. Once documents are fetched from Google Docs, their text can be indexed in Pinecone's vector database for further querying and analysis.

Ensure that both Google Docs and Pinecone API credentials are provided for smooth integration.

#### 5. Links to Documentation

- [Google Docs API Documentation](https://developers.google.com/docs/api)
- [Creating OAuth Credentials in Google Cloud](https://cloud.google.com/docs/authentication)
- [Pinecone Documentation](https://docs.pinecone.io)
