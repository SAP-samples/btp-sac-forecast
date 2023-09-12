# Integrate the Risk Management Application with SAP Build Work Zone, standard edition

In this section, you will connect the Risk Management application to SAP Build Work Zone, standard edition. This allows to have one central entry point to show all your SAP BTP applications :

 1. Create Your SAP Build Work Zone, standard edition Site
 2. Launch Your SAP Build Work Zone, Standard Edition Site
 
![solution-diagram-Integrate-stories](./images/solution-diagram-integrate-story-SBWZ.jpg)

## Create Your SAP Build Work Zone, standard edition Site

1. Open the **SAP BTP cockpit**, navigate to your subaccount and choose **Servces** &rarr; **Instances and Subscriptions**. 
2. From the **Subscriptions** list, select **SAP Build Work Zone, standard edition**.

![BTP-Cockpit-BWZ-goto-application](./images/BTP-Cockpit-BWZ-goto-application.jpg)

3. Choose **Channel Manager** on the left-hand side and refresh the HTML5 Apps entry, because the content providers aren’t reloaded automatically when you push an application, so it’s important to manually refresh.

![SBWZ-refresh_html5_apps](./images/SBWZ-refresh_html5_apps.jpg)

4. Choose **Content Manager** &rarr; **Content Explorer** and open the content provider **HTML5 Apps**.

![SBWZ-Cockpit-content-explorer](./images/SBWZ-Cockpit-content-explorer.jpg)

5. Select the **Risks** and **Mitigations** checkboxes, and then choose **Add to My Content**.

![SBWZ-Cockpit-Add-the-Risks-and-mitigations-to-my-content](./images/SBWZ-Cockpit-Add-the-Risks-and-mitigations-to-my-content.jpg)

6. Choose **Content Manager** &rarr; **My Content**.

7. In the **Items** list, choose **Everyone**. **Everyone** is a role that has to be assigned to the Risks and Mitigations applications so all users can access them.

![SBWZ-Cockpit-my-content-everyone](./images/SBWZ-Cockpit-my-content-everyone.jpg)

8. Choose **Edit**, then choose **+ Search for items to assign** field. Choose **"(+)"** to assign the Risks and Mitigations applications to the role, and choose **Save**.

![SBWZ-Cockpit-role-everyone-assign-apps](./images/SBWZ-Cockpit-role-everyone-assign-apps.jpg)

9. Navigate back to **My Content**.
10. Choose **New** &rarr; **Group**.

![SBWZ-Cockpit-new-group](./images/SBWZ-Cockpit-new-group.jpg)

11. In the **PROPERTIES** tab, in the **Title** field, enter **Risk Management**.Then, assign the **Risks** and **Mitigations** alications to it, to display the Risks and Mitigations applications in a group called Risk Management.

![SBWZ-Cockpit-new-group-assign-apps](./images/SBWZ-Cockpit-new-group-assign-apps.jpg)

12. Choose **Site Directory** &rarr; **Create Site**, and in the **Site Name** field, enter **Risk Management**. Choose **Create**.

![SBWZ-Cockpit-create-new-site](./images/SBWZ-Cockpit-create-new-site.jpg)

The new site gets the Everyone role by default, so you don’t have to assign it explicitly.

## 2. Launch Your SAP Build Work Zone, Standard Edition Site

1. Choose **Go to Site**.

![SBWZ-Cockpit-open-site](./images/SBWZ-Cockpit-open-site.jpg)

2. You can see the Risk Management group that includes the Mitigations and Risks applications.

![SBWZ-Cockpit-applications-groups](./images/SBWZ-Cockpit-applications-groups.jpg)

3. Go to the application and choose the **Risks** tile. Then, choose **Go**.

![SBWZ-Cockpit-risks-list-view-site](./images/SBWZ-Cockpit-risks-list-view-site.jpg)

4. Now, you should be able to create new entries entries in the Risks application.

![SBWZ-Cockpit-Insert-new-risks](./images/SBWZ-Cockpit-Insert-new-risks.jpg)

### Result
You have integrated the Risk Management reference application in SAP Build Work Zone, standard edition.

### Next Step
You will add Calculation Views to the Risk Management application to be consumed in SAP Analytics Cloud later on.
