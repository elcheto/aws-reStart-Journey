# Introduction to AWS Identity and Access Management (IAM)

In many business environments, access involves a single login to a computer or a network of computer systems that provides the user access to all resources on the network. This access includes rights to personal and shared folders on a network server, company intranets, printers, and other network resources and devices. Unauthorized users can quickly exploit these same resources if the access control and associated authentication procedures are not set up properly.

In this lab, I will explore users, user groups, and policies in the AWS Identity and Access Management (IAM) service.

## Objectives

- Create and apply an IAM password policy
- Explore pre-created IAM users and user groups
- Inspect IAM policies as applied to the pre-created user groups
- Add users to user groups with specific capabilities active
- Locate and use the IAM sign-in URL
- Experiment with the effects of policies on service access

AWS IAM Hands-on Lab: Password Policies and User Groups

### Task 1: Configure Account Password Policy
Set a custom password policy to strengthen account security.

1. Open the IAM Console.
2. In the left navigation pane, select Account settings.
3. Click Change password policy.
4. Configure the following requirements:
- Minimum password length: 10
- Select all checkboxes except "Password expiration requires administrator reset."
- Password expiration: 90 days.
- Password reuse: Prevent reuse of 5 passwords.

Click Save changes.

### Task 2: Explore Users and Groups
Verify pre-created IAM entities and understand their permissions.

View Users: Go to Users in the left pane. Verify user-1, user-2, and user-3 exist.

View Groups: Go to User groups and review the following:

EC2-Support: Contains AmazonEC2ReadOnlyAccess (Managed Policy).

S3-Support: Contains AmazonS3ReadOnlyAccess (Managed Policy).

EC2-Admin: Contains EC2-Admin-Policy (Customer Inline Policy) for starting/stopping instances.

### Task 3: Assign Users to Groups
Map users to their respective business roles.

S3-Support Group: Add user-1.

EC2-Support Group: Add user-2.

EC2-Admin Group: Add user-3.

Verification: Ensure each group now shows a count of 1 in the Users column.

Task 4: Test Permissions
Validate access control by signing in as different users in an Incognito/Private window.

User 1: S3 Support
Sign-in URL: Found on the IAM Dashboard.

Test S3: Should be able to view buckets and contents.

Test EC2: Should see "Not Authorized" errors.

User 2: EC2 Support
Test EC2: Should be able to view (Describe) instances.

Action Test: Attempt to Stop an instance. This should fail (Unauthorized).

Test S3: Should be unable to list buckets.

User 3: EC2 Admin
Test EC2: Should be able to view instances.

Action Test: Attempt to Stop an instance. This should succeed (Status: Stopping).


