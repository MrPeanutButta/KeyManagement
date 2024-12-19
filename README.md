# Rotate Google Maps API Key GitHub Action

> This documentation was genearate using Github Copilot.

This GitHub Action automates the process of rotating the Google Maps API key. It performs the following steps:

1. Checks out the repository.
2. Authenticates to Google Cloud.
3. Sets up the Google Cloud SDK.
4. Logs into Azure using service principal credentials.
5. Retrieves the current Google Maps API key from Azure Key Vault.
6. Creates a new Google Maps API key using the Google Cloud SDK.
7. Stores the new Google Maps API key in Azure Key Vault.

## Prerequisites

Before using this action, ensure you have the following:

- A Google Cloud project with the necessary permissions to create API keys.
- An Azure Key Vault to store the API keys.
- GitHub secrets configured with the following keys:
  - `GCP_SA_KEY`: Google Cloud service account key in JSON format.
  - `GCP_PROJECT_ID`: Google Cloud project ID.
  - `AZURE_CREDENTIALS`: Azure service principal credentials in JSON format.
  - `KEYVAULT_NAME`: Name of the Azure Key Vault.
  - `GMAPS_API_SECRET_NAME`: Name of the secret in Azure Key Vault where the Google Maps API key is stored.

## Running the Action Manually

To run the action manually, navigate to the "Actions" tab in your GitHub repository, select the workflow, and click "Run workflow".

## Documentation

- [Google Maps Platform Documentation](https://developers.google.com/maps/apis-by-platform)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Azure Key Vault Documentation](https://learn.microsoft.com/en-us/azure/key-vault/)

## Operational Documentation for Rotate API Key Workflow

### Overview
This document provides instructions on how to operate, maintain, and enhance the GitHub Actions workflow for rotating the Google Maps API key. The workflow automates the process of creating a new API key and storing it securely in Azure Key Vault.

### Workflow Steps

1. **Install Components**
   - Ensure the necessary components are installed. This is specified at the beginning of the workflow.

2. **Login to Azure**
   - The workflow logs into the Azure tenant using service principal credentials stored in GitHub secrets.
   - **Action Used**: `Azure/login@v1`
   - **Secrets Required**: `AZURE_CREDENTIALS`

3. **Retrieve API Secret from Azure Key Vault**
   - The workflow retrieves the current Google Maps API key from Azure Key Vault.
   - **Action Used**: `Azure/get-keyvault-secrets@v1` (deprecated, consider using `azure/cli@v2` for future enhancements)
   - **Secrets Required**: `KEYVAULT_NAME`, `GMAPS_API_SECRET_NAME`

4. **Create a New Google Maps API Key**
   - The workflow uses the Google Cloud SDK to create a new API key.
   - **Command Used**: `gcloud alpha services api-keys create`
   - **Secrets Required**: `GCP_PROJECT_ID`

5. **Store New API Key in Azure Key Vault**
   - The new API key is stored securely in Azure Key Vault.
   - **Action Used**: `azure/cli@v2`
   - **Secrets Required**: `KEYVAULT_NAME`, `GMAPS_API_SECRET_NAME`

### Enhancements

- **Deprecation Notice**: The `Azure/get-keyvault-secrets@v1` action is deprecated. It is recommended to use the `azure/cli@v2` action with a custom script to access Azure Key Vault.
- **Security**: Ensure that all sensitive information is handled securely and that secrets are stored in GitHub secrets.

### Disclosure of AI Tools
This documentation was generated with the assistance of GitHub Copilot, an AI tool. The benefits of using this tool include increased efficiency and the ability to quickly generate boilerplate code and documentation. However, drawbacks include the need for careful review to ensure accuracy and relevance to the specific use case.

## Conclusion

This GitHub Action provides an automated way to rotate your Google Maps API key and store the new key securely in Azure Key Vault. Ensure your GitHub secrets are correctly configured before running the action.