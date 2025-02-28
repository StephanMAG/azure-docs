---
title: 'Tutorial: User provisioning for ThousandEyes - Azure AD'
description: Learn how to configure Azure Active Directory to automatically provision and de-provision user accounts to ThousandEyes.
services: active-directory
author: ArvindHarinder1
manager: CelesteDG
ms.service: active-directory
ms.subservice: saas-app-tutorial
ms.workload: identity
ms.topic: tutorial
ms.date: 11/21/2022
ms.author: arvinh
---

# Tutorial: Configure ThousandEyes for automatic user provisioning

The objective of this tutorial is to show you the steps you need to perform in ThousandEyes and Azure AD to automatically provision and de-provision user accounts from Azure AD to ThousandEyes. 

## Prerequisites

The scenario outlined in this tutorial assumes that you already have the following items:

* An Azure Active directory tenant
* A ThousandEyes tenant with the [Standard plan](https://www.thousandeyes.com/pricing) or better enabled 
* A user account in ThousandEyes with Admin permissions 

> [!NOTE]
> The Azure AD provisioning integration relies on the [ThousandEyes SCIM API](https://success.thousandeyes.com/PublicArticlePage?articleIdParam=kA044000000CnWrCAK), which is available to ThousandEyes teams on the Standard plan or better.

## Assigning users to ThousandEyes

Azure Active Directory uses a concept called "assignments" to determine which users should receive access to selected apps. In the context of automatic user account provisioning, only the users and groups that have been "assigned" to an application in Azure AD is synchronized. 

Before configuring and enabling the provisioning service, you need to decide what users and/or groups in Azure AD represent the users who need access to your ThousandEyes app. Once decided, you can assign these users to your ThousandEyes app by following the instructions here:

[Assign a user or group to an enterprise app](../manage-apps/assign-user-or-group-access-portal.md)

### Important tips for assigning users to ThousandEyes

* It is recommended that a single Azure AD user is assigned to ThousandEyes to test the provisioning configuration. Additional users and/or groups may be assigned later.

* When assigning a user to ThousandEyes, you must select either the **User** role, or another valid application-specific role (if available) in the assignment dialog. The **Default Access** role does not work for provisioning, and these users are skipped.

## Configuring user provisioning to ThousandEyes 

This section guides you through connecting your Azure AD to ThousandEyes's user account provisioning API, and configuring the provisioning service to create, update, and disable assigned user accounts in ThousandEyes based on user and group assignment in Azure AD.

> [!TIP]
> You may also choose to enabled SAML-based Single Sign-On for ThousandEyes, following the instructions provided in [Azure portal](https://portal.azure.com). Single sign-on can be configured independently of automatic provisioning, though these two features compliment each other.

### Configure automatic user account provisioning to ThousandEyes in Azure AD

1. Sign in to the [Azure portal](https://portal.azure.com). Select **Enterprise Applications**, then select **All applications**.

	![Enterprise applications blade](common/enterprise-applications.png)

2. If you have already configured ThousandEyes for single sign-on, search for your instance of ThousandEyes using the search field. Otherwise, select **Add** and search for **ThousandEyes** in the application gallery. Select ThousandEyes from the search results, and add it to your list of applications.

	![The ThousandEyes link in the Applications list](common/all-applications.png)
	
3. Select your instance of ThousandEyes, then select the **Provisioning** tab.

	![Provisioning tab](common/provisioning.png)

4. Set the **Provisioning Mode** to **Automatic**.

![Screenshot shows the Provisioning tab for ThousandEyes with Automatic selected for Provisioning Mode.](./media/thousandeyes-provisioning-tutorial/ThousandEyes1.png)
	

5. Under the **Admin Credentials**  section, input the **OAuth Bearer Token**
generated by your ThousandEyes's account (you can find and or generate a token under your ThousandEyes account **Profile** section).

	![Screenshot shows where to find the Account Settings link for the Current Account Group.](./media/thousandeyes-provisioning-tutorial/ThousandEyes2.png)

6. In the Azure portal, click **Test Connection** to ensure Azure AD can connect to your ThousandEyes app. If the connection fails, ensure your ThousandEyes account has Admin permissions and try step 5 again.

7. In the **Notification Email** field, enter the email address of a person or group who should receive the provisioning error notifications and select the **Send an email notification when a failure occurs** check box.

	![Notification Email](common/provisioning-notification-email.png)

8. Click **Save**.

9. Under the Mappings section, select **Synchronize Azure Active Directory Users to ThousandEyes**.

10. Review the user attributes that are synchronized from Azure AD to ThousandEyes in the **Attribute-Mapping** section. The attributes selected as **Matching** properties are used to match the user accounts in Parsable for update operations. If you choose to change the [matching target attribute](../app-provisioning/customize-application-attributes.md), you will need to ensure that the Parsable API supports filtering users based on that attribute. Select the **Save** button to commit any changes.

 	 |Attribute|Type|Supported for filtering|
  	 |---|---|---|
  	 |externalId|String|&check;|
  	 |userName|String|&check;|
  	 |active|Boolean|
  	 |displayName|String|
  	 |emails[type eq "work"].value|String|
  	 |name.formatted|String|


11. To configure scoping filters, refer to the following instructions provided in the [Scoping filter tutorial](../app-provisioning/define-conditional-rules-for-provisioning-user-accounts.md).

12. To enable the Azure AD provisioning service for ThousandEyes, change the **Provisioning Status** to **On** in the **Settings** section.

	![Provisioning Status Toggled On](common/provisioning-toggle-on.png)

13. Define the users and/or groups that you would like to provision to ThousandEyes by choosing the desired values in **Scope** in the **Settings** section.

	![Provisioning Scope](common/provisioning-scope.png)

14. When you are ready to provision, click **Save**.

	![Saving Provisioning Configuration](common/provisioning-configuration-save.png)

This operation starts the initial synchronization cycle of all users and groups defined in **Scope** in the **Settings** section. The initial cycle takes longer to perform than subsequent cycles, which occur approximately every 40 minutes as long as the Azure AD provisioning service is running. 

## Step 6. Monitor your deployment
Once you've configured provisioning, use the following resources to monitor your deployment:

1. Use the [provisioning logs](../reports-monitoring/concept-provisioning-logs.md) to determine which users have been provisioned successfully or unsuccessfully
2. Check the [progress bar](../app-provisioning/application-provisioning-when-will-provisioning-finish-specific-user.md) to see the status of the provisioning cycle and how close it is to completion
3. If the provisioning configuration seems to be in an unhealthy state, the application will go into quarantine. Learn more about quarantine states [here](../app-provisioning/application-provisioning-quarantine-status.md).  

## Additional resources

* [Managing user account provisioning for Enterprise Apps](../app-provisioning/configure-automatic-user-provisioning-portal.md)
* [What is application access and single sign-on with Azure Active Directory?](../manage-apps/what-is-single-sign-on.md)

## Next steps

* [Learn how to review logs and get reports on provisioning activity](../app-provisioning/check-status-user-account-provisioning.md)