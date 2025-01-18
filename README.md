# Azure-web-apps Lab 9a
Create an Azure web app, manage the deployment, and scale the app.
Task 1: Create and configure an Azure web app
In this task, you create an Azure web app. Azure App Services is a Platform As a Service (PAAS) solution for web, mobile, and other web-based applications. Azure web apps is part Azure App Services hosting most runtime environments, such as PHP, Java, and .NET. The app service plan that you select determines the web app compute, storage, and features.
Sign in to the Azure portal - https://portal.azure.com.
Search for and select App services.
Select + Create, from drop-down menu, Web App. Notice the other choices.
On the Basics tab of the Create Web App blade, specify the following settings (leave others with their default values):
Setting
Value
Subscription
your Azure subscription
Resource group
az104-rg9 (If necessary, select Create new)
Web app name
any globally unique name
Publish
Code
Runtime stack
PHP 8.2
Operating system
Linux
Region
East US
Pricing plans
Premium V3 P1V3
Zone redundancy
accept the defaults

Click Review + create, and then Create.
Note: Wait until the Web App is created before you proceed to the next task. This should take about a minute.
Note: If the deployment fails, change to another region and try again. For example, switch to East US 2.
After the deployment, select Go to resource.
Task 2: Create and configure a deployment slot
In this task, you will create a staging deployment slot. Deployment slots enable you to perform testing prior to making your app available to the public (or your end users). After you have performed testing, you can swap the slot from development or staging to production. Many organizations use slots to perform pre-production testing. Additionally, many organizations run multiple slots for every application (for example, development, QA, test, and production).
On the blade of the newly deployed Web App, click the Default domain link to display the default web page in a new browser tab.
Close the new browser tab and, back in the Azure portal, in the Deployment section of the Web App blade, click Deployment slots.
Note: The Web App, at this point, has a single deployment slot labeled PRODUCTION.
Click Add slot, and add a new slot with the following settings:
Setting
Value
Name
staging
Clone settings from
Do not clone settings

Select Add.
Back on the Deployment slots blade of the Web App, click the entry representing the newly created staging slot.
Note: This will open the blade displaying the properties of the staging slot.
Review the staging slot blade and note that its URL differs from the one assigned to the production slot.
Task 3: Configure Web App deployment settings
In this task, you will configure Web App deployment settings. Deployment settings allow for continuous deployment. This ensures that the app service has the latest version of the application.
In the staging slot, select Deployment Center and then select Settings.
Note: Make sure you are on the staging slot blade (instead than the production slot).
In the Source drop-down list, select External Git. Notice the other choices.
In the repository field, enter https://github.com/Azure-Samples/php-docs-hello-world
In the branch field, enter master.
Select Save.
From the staging slot, select Overview.
Select the Default domain link, and open the URL in a new tab.
Verify that the staging slot displays Hello World.
Note: The deployment may take a minute. Be sure to Refresh the application page.
Task 4: Swap deployment slots
In this task, you will swap the staging slot with the production slot. Swapping a slot allows you to use the code that you have tested in your staging slot, and move it to production. The Azure portal will also prompt you if you need to move other application settings that you have customized for the slot. Swapping slots is a common task for application teams and application support teams, especially those deploying routine app updates and bug fixes.
Navigate back to the Deployment slots blade, and then select Swap.
Review the default settings and click Start Swap.
On the Overview blade of the Web App select the Default domain link to display the website home page.
Verify the production web page displays the Hello World! page.
Note: Copy the Default domain URL you will need it for load testing in the next task.
Task 5: Configure and test autoscaling of the Azure Web App
In this task, you will configure autoscaling of Azure Web App. Autoscaling enables you to maintain optimal performance for your web app when traffic to the web app increases. To determine when the app should scale you can monitor metrics like CPU usage, memory, or bandwidth.
In the Settings section, select Scale out (App Service plan).
Note: Ensure you are working on the production slot not the staging slot.
From the Scaling section, select Automatic. Notice the Rules Based option. Rules based scaling can be configured for different app metrics.
In the Maximum burst field, select 2.

Select Save.
Select Diagnose and solve problems (left pane).
In the Load Test your App box, select Create Load Test.
Select + Create and give your load test a name. The name must be unique.
Select Review + create and then Create.
Wait for the load test to create, and then select Go to resource.


From the Overview
Add HTTP requests, select Create.


On the Test plan tab, click Add request. In the URL field, paste in your Default domain URL. Ensure this is properly formatted and begins with https://.
Select Review + create and Create.
Note: It may take a couple of minutes to create the test.
Review the test results including Virtual users, Response time, and Requests/sec.
Select Stop to complete the test run.
Cleanup your resources
If you are working with your own subscription take a minute to delete the lab resources. This will ensure resources are freed up and cost is minimized. The easiest way to delete the lab resources is to delete the lab resource group.
In the Azure portal, select the resource group, select Delete the resource group, Enter resource group name, and then click Delete.
Using Azure PowerShell, Remove-AzResourceGroup -Name resourceGroupName.
Using the CLI, az group delete --name resourceGroupName.
Extend your learning with Copilot
Copilot can assist you in learning how to use the Azure scripting tools. Copilot can also assist in areas not covered in the lab or where you need more information. Open an Edge browser and choose Copilot (top right) or navigate to copilot.microsoft.com. Take a few minutes to try these prompts.
Summarize the steps to create and configure an Azure web app.
What are ways I can scale an Azure Web App?
Learn more with self-paced training
Stage a web app deployment for testing and rollback by using App Service deployment slots. Use deployment slots to streamline deployment and roll back a web app in Azure App Service.
Scale an App Service web app to efficiently meet demand with App Service scale up and scale out. Respond to periods of increased activity by incrementally increasing the resources available and then, to reduce costs, decreasing these resources when activity drops.
Key takeaways
Congratulations on completing the lab. Here are the main takeaways for this lab.
Azure App Services lets you quickly build, deploy, and scale web apps.
App Service includes support for many developer environments including ASP.NET, Java, PHP, and Python.
Deployment slots allow you to create separate environments for deploying and testing your web app.
You can manually or automatically scale a web app to handle additional demand.
A wide variety of diagnostics and testing tools are available.
