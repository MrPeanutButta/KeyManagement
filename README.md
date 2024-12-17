# Rotate Google Maps API Key GitHub Action

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

## Conclusion

This GitHub Action provides an automated way to rotate your Google Maps API key and store the new key securely in Azure Key Vault. Ensure your GitHub secrets are correctly configured before running the action.

## Documentation

- [Google Maps Platform Documentation](https://developers.google.com/maps/apis-by-platform)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Azure Key Vault Documentation](https://learn.microsoft.com/en-us/azure/key-vault/)