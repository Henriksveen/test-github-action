# GitHub Actions Permissions Guide

## Error: "GitHub Actions is not permitted to create or approve pull requests"

If you encounter this error when running the workflow, you need to change some settings in your repository. There are two ways to fix this:

### Option 1: Configure Repository Settings (Recommended)

1. Go to your repository's **Settings**
2. Click on **Actions** in the left sidebar
3. Under **General**, find the **Workflow permissions** section
4. Select **"Read and write permissions"**
5. Check the box that says **"Allow GitHub Actions to create and approve pull requests"**
6. Click **Save**

This allows GitHub Actions to create pull requests using the built-in `GITHUB_TOKEN`.

### Option 2: Use a Personal Access Token (PAT)

If you cannot change the repository settings (e.g., due to organization policies):

1. Create a Personal Access Token with `repo` scope
   - Go to your GitHub profile settings → Developer settings → Personal access tokens → Tokens (classic)
   - Generate a new token with `repo` scope
   - Copy the token

2. Add the token as a repository secret:
   - Go to your repository's Settings → Secrets and variables → Actions
   - Click "New repository secret"
   - Name it `PAT` or similar
   - Paste your token as the value
   - Click "Add secret"

3. Update the workflow file to use this token:
   ```yaml
   - name: Create Pull Request
     id: cpr
     uses: peter-evans/create-pull-request@v7
     with:
       token: ${{ secrets.PAT }}
       # other parameters remain the same...
   ```

After making these changes, the workflow should be able to create pull requests.
