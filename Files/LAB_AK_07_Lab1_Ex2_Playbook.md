# Create a Playbook / Logic App for automation
A security playbook is a collection of procedures that can be run from Azure Sentinel in response to an alert. A security playbook can help automate and orchestrate your response, and can be run manually or set to run automatically when specific alerts are triggered. Security playbooks in Azure Sentinel are based on Azure Logic Apps, which means that you get all the power, customizability, and built-in templates of Logic Apps. Each playbook is created for the specific subscription you choose, but when you look at the Playbooks page, you will see all the playbooks across any selected subscriptions.

### Task 1: Create a Security Operations Center Team in Microsoft Teams.

In this task, you will create a Microsoft Teams team for use in the lab.

6. In Microsoft Teams, select **Teams**, then at the bottom, select **Join or create a team**.

7. Select **Create a Team** in the main window.

8. Select **From scratch**.

9. Select **Private**.

10. Give the team the name: **SOC** and select **Create**.

11. In the Add members to SOC, select **Skip**. 

12. Click the **...** next to the team name SOC, and select **Add channel**.

13. Enter a channel name of *New Alerts* then select **Add**.

### Task 2: Create a Playbook in Azure Sentinel.

In this task, you will create a Logic App that will be used as a Playbook in Azure Sentinel.

1. In the Edge browser, navigate to the Azure portal at https://portal.azure.com.

4. In the Search bar of the Azure portal, type *Sentinel*, then select **Azure Sentinel**.

5. Select your Azure Sentinel Workspace you created earlier.

6. Select the **Community** page in the Configuration area on the left side of the page.

7. Select the **Go to Azure Sentinel community** button.

8. Select the **Playbooks** folder.

9. Select the **Post-Message-Teams** folder.

10. Select **Deploy to Azure** button.

11. Select your Azure Subscription.

12. For Resource Group, select **Create New** and enter *rg-Playbooks*.

13. For region, select the appropriate region for your situation.  The default region will likely be optimal.

14. For User Name, enter the user name **Tenant Email**

15. Select **Review + create**.

16. Now select **create**.

**Note** Wait for the deployment to finish before proceeding to the next task.

### Task 3: Update a Playbook in Azure Sentinel.

In this task, you will update the new playbook with the proper connection information.

1. In the Search bar of the Azure portal, type *Sentinel*, then select **Azure Sentinel**.

2. Select your Azure Sentinel Workspace.

3. Select the **Automation** from the Configuration area, and then select the **Playbooks** tab.

4. Click on the **Post-Message-Teams** playbook, 

5. On the Logic App page for *Post-Message-Teams*, select **Edit**.

6. Click on the first Connections block at the top.  

7. Select **Add new**, and sign in with your Azure subscription admin credentials.

8. Click on the second Connection block in the middle.  

9. Select **Add new**, and sign in with your Azure subscription admin credentials.

10. Click on the third Connection block.  

11. Select **Add new**, and sign in with your Azure subscription admin credentials.

12. In the Post a message block, for the Team, select the **X** at the end of the edit box.  The edit box will be changed to a dropdown with a listing of the Teams.  Select **SOC**.

13. For the Channel, select the **X** at the end of the edit box.  The edit box will be changed to a dropdown with a listing of the Channels.  Select **New Alerts**.

14. Select **Save**.

The Logic App will be used in a future lab.

# Security Playbook in Azure Sentinel

Follow these steps to create a new security playbook in Azure Sentinel:


1.  Open **Azure Sentinel** dashboard.

2. Under **Configuration**, select **Playbooks**.

3. In the **Azure Sentinel - Playbooks** page, click **+ Add Playbook** button.

4. In the **Create Logic app** page, type the requested information to create your new logic app, and click **Review + create** then click **Create**. 

1. Once created click **Go to resource**.

5. In the **Logic App Designer** select the template you want to use. If you select a template that necessitates credentials, you will have to provide them. Alternatively, you can create a new blank playbook from scratch. Select **Blank Logic App**. 
   
6. You are taken to the Logic App Designer where you can either build new or edit the template.

7. If you are creating a blank playbook, in the **Search all connectors and triggers** field, type *Azure Sentinel*, and select **When a response to an Azure Sentinel alert is triggered**. 

   **Note**: You may be required to re-authenticate. If so, click **Sign in** and authenticate with your Azure credentials.
   
8. Click **Save** and return to the Azure Sentinel blade.  After it is created, the new playbook appears in the **Playbooks** list. If it doesn’t appear, click **Refresh**.

9.  Use the **Get entities** functions, which enable you to get the relevant entities from inside the **Entities** list, such as accounts, IP addresses and hosts. This will enable you to run actions on specific entities.

10.  Now you can define what happens when you trigger the playbook. You can add an action, logical condition, switch case conditions, or loops.

### How to run a security playbook

You can run a playbook on demand.

To run a playbook on-demand:

1. In the **Incidents** page, select an incident and click on **View full details**.

2. In the **Alerts** tab, click on the alert you want to run the playbook on, and scroll all the way to the right and click **View playbooks** and select a playbook to **run** from the list of available playbooks on the subscription. 

## Automate threat responses

SIEM/SOC teams can be inundated with security alerts on a regular basis. The volume of alerts generated is so huge, that available security admins are overwhelmed. This results all too often in situations where many alerts can't be investigated, leaving the organization vulnerable to attacks that go unnoticed. 

Many, if not most, of these alerts conform to recurring patterns that can be addressed by specific and defined remediation actions. Azure Sentinel already enables you to define your remediation in playbooks. It is also possible to set real-time automation as part of your playbook definition to enable you to fully automate a defined response to particular security alerts. Using real-time automation, response teams can significantly reduce their workload by fully automating the routine responses to recurring types of alerts, allowing you to concentrate more on unique alerts, analyzing patterns, threat hunting, and more.

### Automate Responses

Select the alert for which you want to automate the response.
In the **Edit alert rule** page, under **Real-time automation**, choose the **Triggered playbook** you want to run when this alert rule is matched.
Select **Save**.

**Results**: In this lab, you learned how to use playbooks in Azure Sentinel.
