# API Management DevOps Resource Kit - Github Actions

This repo contains three sample github actions for the [API Management DevOps Resource Kit](https://github.com/Azure/azure-api-management-devops-resource-kit).

## InstallResourceKit
This needs to be run before the RunCreator or RunExtractor actions.  It downloads a specific release from the resource kit repo, unpacks it and installs the compiles application as a dotnet global tool.

**usage**

```
- name: Install DevOps Toolkit
  uses: fortunkam/apim-devops-resource-kit-actions/install-resource-kit@v1.1
  with:
    creds: ${{ secrets.AZURE_CREDENTIALS }}
    releaseVersion: 0.7

```

The `releaseVersion` parameter corresponds to a release tag in the resource kit repo.  The latest release is `0.7`.
The `creds` parameter is a json object containing the output of an `az ad sp create-for-rbac ...` command, as detailed [here](https://docs.microsoft.com/en-us/azure/developer/github/connect-from-azure?tabs=azure-portal%2Cwindows#use-the-azure-login-action-with-a-service-principal-secret), this is usually referenced as a github secret.


## RunCreator
Runs the creator tool with the supplied yaml file.

**usage**

```
- name: Run the creator Tool
  uses: fortunkam/apim-devops-resource-kit-actions/run-creator@v1.1
  with:
    workingDirectory: ./api/Creator
    configFile: myapi.yml

```

## RunExtractor
Runs the extractor tool with the supplied json file.

**usage**

```
- name: Run the extractor Tool
  uses: fortunkam/apim-devops-resource-kit-actions/run-extractor@v1.1
  with:
    workingDirectory: ./api/Creator
    configFile: extractorConfig.json

```