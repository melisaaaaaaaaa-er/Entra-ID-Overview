# Microsoft Entra ID Overview - Users, Groups, Access Management

<h2>Purpose</h2>

- Configure and observe the effects of various Microsoft Entra ID/Azure Active Directory permission types across the different hierarchical layers of Azure.

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/Lab%20overview%20diagram.png"/>

#
<h3>Creating New Users on Microsoft Entra ID/Azure Active Directory</h3>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/1.png"/>

Navigate to the Microsoft Entra ID Default Directory and select the “Users” option on the left-hand side.

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/2.png"/>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/3.png"/>

Select “New user” and input the respective user account credentials on the following page. 

Select “Review + create”.

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/4.png"/>

The first account created for this lab is “globalreaderjohn”. This account will be used to test and observe the effects of the Global Reader role permissions on Entra ID.

#
<h2>Group Permissions and Access Management</h2>

This part of the lab pertains to assigning user accounts roles at various levels of the Active Directory/Entra ID hierarchy and testing out their capabilities on the system.

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/5.png"/>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/6.png"/>

To assign roles to a user, select the respective user from the “All users” list.

Navigate to “Assigned roles” from the left-hand menu, select “Add assignments” and add the Global Reader role from the built-in roles list. 

This role allows users to read/view anything a Global Administrator can, but cannot update or otherwise make changes to anything.

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/7.png"/>

Navigate to the user account overview panel and copy the “User principal name”. 

This is the username needed to sign into the account on the Azure portal.

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/8.png"/>

On an incognito browser page, go to portal.azure.com and sign in using the globalreaderjohn account.

Here we will be testing out what this user is capable of given the role permissions imposed on it.

#
<h4>Global Reader</h4>

According to the documentation (https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-reader) the Global Reader “can read settings and administrative information across Microsoft 365 services but can’t take management actions. Global Reader is the read-only counterpart to Global Administrator”.

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/9.png"/>

Cannot access Azure Subscriptions.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/11.png"/>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/12.png"/>

Can access User accounts and basic information about them.

Cannot perform password changes.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/13.png"/>

Cannot create new users.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/14.png"/>

Cannot access Resource Groups.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/15.png"/>

Cannot access Storage Accounts

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/16.png"/>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/17.png"/>

Can create and delete Management Groups.

#
<h4>Subscription Reader</h4>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/18.png"/>

Create a new user named “subreaderjane” (Subscription Reader Jane).

This account will be used to evaluate the Subscription Reader role level access.

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/19.png"/>

Navigate to your Azure Subscription dashboard and enter the “Access control (IAM)” settings.
Select “Add role assignment”.

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/20.png"/>

Select “Reader” in the Role panel.

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/21.png"/>

Select the subreaderjane account in the Members panel.

You will have assigned subreaderjane with the ability to read within the respective subscription.

This will allow you to view anything already within the subscription, but not make changes or add anything to existing services.

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/22.png"/>

As with the Global Reader account, sign in to subreaderjane on an incognito tab.

Navigate to Azure Subscriptions. Naturally, they can be accessed with the Reader role.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/23.png"/>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/26.png"/>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/28.png"/>

You can access existing Resource Groups, but cannot make new ones or delete existing ones.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/24.png"/>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/27.png"/>

Exisitng VMs can be viewed. New VMs cannot be created.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/25.png"/>

New storage accounts cannot be created, though I image existing storage accounts could be seen. I didn’t have any in my Tenant at the time of this lab so I could not test this out directly.

#
<h4>Resource Group Contributor</h4>

The contributor role is essentially an administrator – having unfettered access and ability to do anything on the system. The only limitation is that it cannot assign contributor/admin privileges to other users.

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/29.png"/>

Create another user account named “rgcontributordave” (Resource Group Contributor Dave).

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/30.png"/>

Create a new Resource Group named “Permission-Tester” so as to not mess up our current set-up.

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/31.png"/>

Navigate to the Access control (IAM) panel on Permission-Tester and select “Add role assignment”.

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/32.png"/>

Under Roles, go to “Privileged administrator roles” and select “Contributor”.

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/33.png"/>

Under “Members” add the rgcontributordave account.

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/34.png"/>

As done previously, sign in to the account and check the Subscriptions panel. You will be able to see the Subscription under which your respective Resource Group belongs to.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/35.png"/>

You can also access the Resource Group and any services within it, but no other RG or their services.

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/36.png"/>

You cannot create new RGs.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/38.png"/>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/40.png"/>

You can create new services in the RG such as Storage Accounts and VMs.

#
<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/42.png"/>

<img src="https://raw.githubusercontent.com/melisaaaaaaaaa-er/Entra-ID-Overview-Images/main/43.png"/>

You can even delete the RG (and the services within it by extension).
You have essentially unlimited capabilities within the RG with a Contributor role, but these do not extend beyond the RG.

