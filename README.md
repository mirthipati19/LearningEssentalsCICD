# LearnSmartCoding.EssentialProducts.API - CI/CD Pipeline

This repository contains a .NET Core API application with a fully automated **CI/CD pipeline** using **Azure DevOps Classic Editor**. The project includes both Continuous Integration (CI) and Continuous Deployment (CD) to an **IIS web server**.

---

## 🚀 CI Pipeline (Build Pipeline)

The CI pipeline performs the following steps:

1. **Restore NuGet Packages**
   - Command: `dotnet restore`
   - Restores dependencies from the solution file:  
     `**/*/LearnSmartCoding.EssentialProducts.API.sln`

2. **Build the Solution**
   - Command: `dotnet build`
   - Builds all projects using the `Release` configuration.

3. **Run Unit Tests**
   - Command: `dotnet test`
   - Tests are discovered using the pattern: `**/*[Tt]ests/*.csproj`

4. **Publish the Application**
   - Command: `dotnet publish`
   - Publishes output to the staging directory for deployment.

5. **Publish Artifacts**
   - Artifact: `drop`
   - Artifacts are used in the release pipeline.

---

## 🔄 CD Pipeline (Release Pipeline)

The CD pipeline is configured to deploy the published application to an **IIS Web Server** using a deployment group.

### Stage: `prod`

#### Tasks:

1. **IIS Web App Manage**
   - **Configuration Type**: `IIS Website`
   - **Action**: `Create or Update`
   - **Website Name**: `Mynewwebsite2`
   - **Binding**: `http://All Unassigned:5360`

2. **IIS Web App Deploy**
   - Deploys the artifact (`drop`) to the IIS site configured above.

---

## 🔧 Prerequisites

- Azure DevOps project with a pipeline set up.
- IIS server added to an **Azure DevOps Deployment Group**.
- Proper port (e.g., 5360) opened on the server for access.

---

## 📁 Project Structure

