# azure-taggingresources
Tagging existing resources in azure
# Tagging Pipeline

This is a starter Azure DevOps pipeline to add tags to Azure resources using a CSV file. The pipeline installs PowerShell Core, verifies directory contents, and applies tags to specified resources based on the CSV input.

## Prerequisites

1. **Azure Subscription**: Access to an Azure Subscription with permissions to manage resource tags.
2. **CSV File**: A `resources.csv` file should be placed in the `tagging-scripts/tagging/` directory. The file should contain details of resources in the following columns:
   - `ResourceName`: The Azure resource name.
   - `Environment`: Environment name (e.g., "Dev", "Prod").
   - `Application`: Application name associated with the resource.
   - `Owner`: Resource owner.
   - `Team`: Team responsible for the resource.

### Sample CSV Format

```csv
ResourceName,Environment,Application,Owner,Team
myResource,Prod,AppA,UserX,TeamA
myOtherResource,Dev,AppB,UserY,TeamB


Pipeline Steps
Step 1: Trigger
The pipeline trigger is set to none, meaning it won’t run automatically. You can manually start this pipeline as needed.

Step 2: Setup Pool
The pipeline uses the ubuntu-22.04 virtual machine image.

Step 3: Install PowerShell Core
Installs PowerShell Core on the Ubuntu image by adding the Microsoft repository.

Step 4: Apply Tags to Azure Resources
Using the AzurePowerShell@5 task, the pipeline runs a PowerShell script that:

Checks for resources.csv: Verifies that the CSV file exists in the specified directory.
Reads CSV Data: Imports data from the CSV file.
Finds Resources: Searches for each resource in Azure by ResourceName.
Applies Tags: Updates each found resource with tags specified in the CSV file (Environment, Application, Owner, and Team).
Important Notes
Ensure the Azure subscription in azureSubscription is set to the correct name and ID.
Verify that the subscription has the necessary permissions to read and modify resource tags.
Running the Pipeline
Commit the YAML pipeline and resources.csv to the repository.
Manually trigger the pipeline in Azure DevOps.
Review the logs to confirm the successful tag application.
