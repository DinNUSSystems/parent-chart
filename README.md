# Parent-Chart Helm Repository

This repository details how to manually manage a Helm chart repository using GitHub Pages and GitHub Releases, focusing on a chart named `parent-chart`.

## Prerequisites

Ensure you have the following installed before proceeding:
- Git
- Helm
- Access to GitHub (account and properly configured git settings)

## Step 1: Set Up Your GitHub Repository

1. **Create a new GitHub repository** called `parent-chart`.
2. **Clone this repository locally**:
   ```bash
   git clone https://github.com/yourusername/parent-chart.git
   cd parent-chart

## Step 2: Create Your Helm Chart
1. **Generate the Helm chart**:
  ```bash
  helm create parent-chart

Modify the chart as necessaryto fit your needs. for example changing the version in Chart.yaml

## Step 3: Package the Helm Chart
Package the Helm chart and store it in the docs directory:
```bash
    helm package parent-chart -d docs
This creates a .tgz file, which is your packaged Helm chart.

## Step 4: Create GitHub Release
Prepare the chart for release:
```bash
  git add .
  git commit -m "Prepare Helm chart for initial release"
  git push origin main

Create a release on GitHub:
Navigate to "Releases".
Click "Create a new release".
Use the tag version, e.g., v1.0.0, and attach the .tgz file from the docs directory.
## Step 5: Update Index File
Generate and commit the index.yaml:

```bash
helm repo index docs --url https://yourusername.github.io/parent-chart/
git add docs/index.yaml
git commit -m "Update Helm repository index"
git push origin main

## Step 6: Set Up GitHub Pages
Activate GitHub Pages:
Navigate to your repository settings.
Go to the "Pages" section.
Configure it to publish from the main branch and the /docs folder.

## Step 7: Add Repository to Helm
Add your Helm repository:
```bash
helm repo add your-charts https://yourusername.github.io/parent-chart/
helm repo update
## Step 8: Install or Pull the Helm Chart
Install your Helm chart:

```bash
helm install my-parent-chart your-charts/parent-chart --version 1.0.0
Pull the Helm chart to inspect it:

```bash
helm pull your-charts/parent-chart --version 1.0.0
