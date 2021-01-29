# Deleting the organization by removing the management account<a name="orgs_manage_org_delete"></a>

**Note**  
AWS Organizations is introducing a new version of the Organizations management console\. You can switch between the old console and the new console by choosing the link in the notice boxes at the top of the console\. We encourage you to try the new version and let us know what you think\. We want your feedback and read each submission\.

When you no longer need your organization, you can delete it\. This removes the management account from the organization and deletes the organization itself\. The former management account becomes a standalone AWS account\. You then have three options: You can continue to use it as a standalone account, you can use it to create a different organization, or you can accept an invitation from another organization to add the account to that organization as a member account\. 

**Important**  
If you delete an organization, you can't recover it\. If you created any policies inside of the organization, they are also deleted and can't be recovered\.
You can delete an organization only after you remove all member accounts from the organization\. If you created some of your member accounts using AWS Organizations, you might be blocked from removing those accounts\. You can remove a member account only if it has all the information that is required to operate as a standalone AWS account\. For more information about how to provide that information and then remove the account, see [Leaving an organization as a member account](orgs_manage_accounts_remove.md#orgs_manage_accounts_leave-as-member)\.
If any member accounts are in a suspended state because you closed them before removing them from the organization, you can't remove them from the organization until they are finally closed\. This can take up to 90 days, and can prevent you from deleting the organization until then\.

When you remove the management account from an organization by deleting the organization, the account is affected in the following ways:
+ The account is responsible for paying only its own charges and is no longer responsible for the charges incurred by any other account\.
+ Integration with other services might be disabled\. For example, AWS Single Sign\-On requires an organization to operate, so if you remove an account from an organization that supports AWS SSO, the users in that account can no longer use that service\.

The management account of an organization is never affected by service control policies \(SCPs\), so there is no change in permissions after SCPs are no longer available\.

**Minimum permissions**  
To delete an organization, you must sign in as an IAM user or role in the management account, and you must have the following permissions:  
`organizations:DeleteOrganization`
`organizations:DescribeOrganization` – required only when using the Organizations console

------
#### [ Old console ]

**To remove the management account from an organization and delete the organization**

1. Sign in to the [AWS Organizations console](https://console.aws.amazon.com/organizations)\. You must sign in as an IAM user, assume an IAM role, or sign in as the root user \([not recommended](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#lock-away-credentials)\) in the organization’s management account\. 

1. Before you can delete the organization, you must first remove all accounts from the organization\. For more information, see [Removing a member account from your organization](orgs_manage_accounts_remove.md)\.

1. On the **[Settings](https://console.aws.amazon.com/organizations/home#/organization/settings)** tab, choose **Delete organization**\.

1. In the **Delete organization** confirmation dialog box, choose **Delete organization**\.

1. \(Optional\) If you also want to close the management account, you can follow the steps at [Closing an AWS account](orgs_manage_accounts_close.md)\.

------
#### [ New console ]

**To remove the management account from an organization and delete the organization**

1. Sign in to the [AWS Organizations console](https://console.aws.amazon.com/organizations/v2)\. You must sign in as an IAM user, assume an IAM role, or sign in as the root user \([not recommended](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#lock-away-credentials)\) in the organization’s management account\. 

1. Before you can delete the organization, you must first remove all accounts from the organization\. For more information, see [Removing a member account from your organization](orgs_manage_accounts_remove.md)\.

1. Navigate to the **[Settings](https://console.aws.amazon.com/organizations/v2/home/settings)** page, and then choose **Delete organization**\.

1. In the **Delete organization** confirmation dialog box, enter the organization's ID which is displayed in the line above the text box\. Then, choose **Delete organization**\.

1. \(Optional\) If you also want to close the management account, you can follow the steps at [Closing an AWS account](orgs_manage_accounts_close.md)\.

------
#### [ AWS CLI & AWS SDKs ]

**To remove the management account from an organization and delete the organization**  
You can use one of the following commands to delete an organization: 
+ AWS CLI: [aws organizations delete\-organization](https://docs.aws.amazon.com/cli/latest/reference/organizations/delete-organization.html)

  The following example deletes the organization for which the AWS account whose credentials are used is the management account\.

  ```
  $ aws organizations delete-organizations
  ```

  This command produces no output when successful\.
+ AWS SDKs: [DeleteOrganization](https://docs.aws.amazon.com/organizations/latest/APIReference/API_DeleteOrganization.html)

------