# Setup Vercel project

## 1. Acceptance Criteria

At the end of this task you should have a project in Vercel to deploy your frontend application to.

## 2. Implementation Details

The following instructions were based on this how-to guide:

- [How can I use GitHub Actions with Vercel?](https://vercel.com/guides/how-can-i-use-github-actions-with-vercel)
- [How do I use a Vercel API Access Token?](https://vercel.com/guides/how-do-i-use-a-vercel-api-access-token)

### 2.1. Creating a Vercel Access Token

1. Go to the [Account Tokens page](https://vercel.com/account/tokens)
1. Create a token:
    - Give it a descriptive name like "GitHub deploy token"
    - Set the scope to your Hobby tier "team"
    - It's always a good practice to set an expiration date. You could
      set this to e.g. 1 year.
1. Add the token to the secrets of your GitHub repository:
    1. Go to your fronted GitHub repository
    1. Go to Settings
    1. Under "Security" open "Secrets an variables"
    1. Choose "Actions"
    1. Add a new repository secret with name `VERCEL_TOKEN` and value the token you just generated

### 2.2. Creating and linking your frontend project

1. Install the Vercel CLI:
   ```
   npm install --global vercel@latest
   ```
1. Login with Vercel CLI:
   ```
   vercel login
   ```
1. Inside the project folder, run:
   ```
   vercel link
   ```
1. Inside the generated `.vercel` folder, save the `projectId` and `orgId` from `project.json`
1. Add the project ID to GitHub as a repository secret called `VERCEL_PROJECT_ID`, and the
   org ID as a secret called `VERCEL_ORG_ID`.

### 2.3. Creating the GitHub Actions workflow

Add the following file in your project as `.github/workflows/deploy_prod.yml`:

```yaml
name: Vercel Production Deployment
env:
  VERCEL_ORG_ID: ${{ secrets.VERCEL_ORG_ID }}
  VERCEL_PROJECT_ID: ${{ secrets.VERCEL_PROJECT_ID }}
on:
  push:
    branches:
      - main
jobs:
  Deploy-Production:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Install Vercel CLI
        run: npm install --global vercel@latest
      - name: Pull Vercel Environment Information
        run: vercel pull --yes --environment=production --token=${{ secrets.VERCEL_TOKEN }}
      - name: Build Project Artifacts
        run: vercel build --prod --token=${{ secrets.VERCEL_TOKEN }}
      - name: Deploy Project Artifacts to Vercel
        run: vercel deploy --prebuilt --prod --token=${{ secrets.VERCEL_TOKEN }}
```

Study this file and look up what you don't understand. You should be able to explain everything that this file does.

### 2.4. End of the line

A disadvantage is that this method is that it builds the source code and deploys it in the same workflow. It is useful to separate the two workflows:

* One pipeline builds the deployable artifact and pushes it to a _package registry_, here the artifact is stored and can be viewed and downloaded forever
* A second pipeline retrieves the artifact from the registry and deploys it to Vercel

By separating the two steps we can create more complex flows:

* Build the source code, store it in the registry and on a test environment
* Once the application is verified on the test environment, deploy it to the production environment

However, in order to keep the scope of the project limited, this is where the CI/CD part of the frontend ends.
Further elaboration of the CI/CD parts will focus solely on the backend, but ideally you'd do the same things
you're doing to the backend CI/CD bits to the frontend as well. You could always try this as an exercise.