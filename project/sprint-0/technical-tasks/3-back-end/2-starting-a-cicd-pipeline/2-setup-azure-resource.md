# Setup azure resource

## 1. Acceptance Criteria

At the end of this task you should have a resource in Azure to deploy your backend application to.

Your GitHub repository should contain the building blocks to start building your own pipelines.

## 2. Implementation Details

### 2.1. Creating the resource

1. From the Azure portal, create a new "Web App" resource
1. Fill in the following information in the tab "Project Details":
    * Subscription -> Azure for Students
    * Resource Group -> The group you created in [1-set-up-azure-for-students](../../1-azure/1-set-up-azure-for-students.md)
    * Name -> `<your-name>-backend`
    * Publish -> Code
    * Runtime stack -> Java 21
    * Java web server stack -> Java SE (Embedded Web Server)
    * Operating System -> Linux
    * Region -> West Europe

    <a href="./images/2-1-Azure-Web-App-Project-Details.png">
        <img src="./images/2-1-Azure-Web-App-Project-Details.png">
    </a>

1. Fill in the following information in the tab "Pricing Plans":
    * Linux Plan -> Create new -> `<your-name>-pricingplan`
    * Pricing plan -> Free F1 (Shared infrastructure)

    <a href="./images/2-2-Azure-Web-App-Pricing-Details.png">
        <img src="./images/2-2-Azure-Web-App-Pricing-Details.png">
    </a>

1. Click on `Review + create`
1. Double check the overview, especially the pricing plan!
1. Click on `Create`

### 2.2. Accepting the dummy assignment

When you accepted the GitHub Classroom assignment for the backend project, you didn't automatically
become a member of the `UCLL-AO-SoftwareEngineering` organization. This is because individual assignments
only add you as an "outside contributor". To make the next step work, however, you will need to become
a member. As a workaround there's a third "Dummy" assignment you'll have to accept.

1. Accept the dummy assignment (link on Toledo)
1. Join the "Iedereen" group

This will add you to a team that contains all students that follow this course. As a side effect, because you're
a part of a team you will automatically become a member of `UCLL-AO-SoftwareEngineering`. You should now be
able to proceed with the next steps. You can safely ignore the dummy assignment.

### 2.3. Connecting your GitHub repository

1. Open your newly created App Service
1. In the menu, select Deployment Center
1. Fill in the following information:
    * Source -> GitHub
    * Signed in as -> Log in
    * Organization -> UCLL-AO-SoftwareEngineering
    * Repository -> your backend repository
    * Branch -> the default branch in your repository
    * Workflow Option -> Add a workflow...
      * If this option is not visible, ignore the instruction above
    * Authentication type -> Basic authentication
    * Leave the other settings as is
    
    <a href="./images/2-3-Azure-Web-App-Deployment-Center.png">
        <img src="./images/2-3-Azure-Web-App-Deployment-Center.png">
    </a>

1. If everything is looking ok, click "Save" at the top
1. Go to your repository on GitHub and check the following things:
    * In Settings > Secrets and variables > Actions a `AZUREAPPSERVICE_PUBLISH_PROFILE..` has been added
        * This will allow your build to authenticate itself to Azure
    * In Code a folder `.github/workflows` has been created
        * The folder contains one workflow file

### 2.4. Running the created pipeline

1. Run the created workflow via the Actions tab, it should succeed
1. Check that your code is on Azure by executing the GET request to `/hello`

### 2.5. Preparing for the next sprint

Carefully examine the generated workflow file, you should completely understand its contents and what it is doing before continuing!

The generated pipeline is fine, but it has one disadvantage. It builds the source code and deploys it in the same workflow. It is useful to separate the two workflows:

* One pipeline builds the deployable artifact and pushes it to a _package registry_, here the artifact is stored and can be viewed and downloaded forever
* A second pipeline retrieves the artifact from the registry and deploys it to Azure

By separating the two steps we can create more complex flows:

* Build the source code, store it in the registry and on a test environment
* Once the application is verified on the test environment, deploy it to the production environment

In a later sprint, we will add a test environment. To be ready for that step, we will create two pipelines and work with a registry in sprint-1.

Move or comment the created workflow file so that GitHub no longer runs the action. We will use parts of it in sprint-1.