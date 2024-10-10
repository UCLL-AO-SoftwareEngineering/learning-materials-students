# Set up Azure for Students

In this course we will use Azure to deploy the backend. The frontend and database could be deployed
on Azure as well, but we recommend to use Vercel for these instead.

Azure is a paying cloud platform, but as long as you have access to a student email, you can get free
credits for Azure every year.

Azure will be used to deploy your application so that it is publicly available.

We will do our best to not use any of the credits. Upgrading to a more powerful instance (and hence using more credits)
could be useful to speed things up, but everything should be doable with the free allocation that Azure offers.

## 1. Acceptance Criteria

You have access to an Azure environment with student credit available.

## 2. Implementation Details

1. Go to [Azure for Students](https://azure.microsoft.com/en-us/free/students)
1. Click on the `Start free` button and follow the wizard (use your UCLL-account)
1. [Azure portal](https://portal.azure.com/) allows you to view your created resources and used credits
    * Normally the amount of credits should not decrease, since we will only use free resources
1. Create [a Resource Group](https://learn.microsoft.com/en-us/azure/role-based-access-control/quickstart-assign-role-user-portal) for all resources
    * A Resource Group is a logical namespace for resources, we will add everything we create to the same resource group.

### Extremely Important Notice

**Do not fill in any payment information on Azure!!** 

* Without entering payment information, if your credits are spent you will lose access to your resources. 
* With payment information, if your credits are spent you will keep access but start receiving bills.
  Should you vastly misconfigure (overscale) your resources, the costs can be (very) high.

**Do not fill in any payment information on Azure!!** 