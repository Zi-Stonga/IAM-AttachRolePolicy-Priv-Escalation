# AWS IAM Role Privelege Escalation


### IAM attached role policies grant roles higher priveleges with managed policies. These policies can be assumed and exploited to gain higher access, which can result in sensitive data exposure.

#### A role's trust policy dictates wether an IAM user has AssumeRole permission. That permission and iam:AttachRolePolicy permissions allows the user to update permissions. We'll leverage this configuration to accss a bucket with PII.

##### We'll start off with getting our user information 

![alt text](https://github.com/Zi-Stonga/IAM-AttachRolePolicy-Priv-Escalation/blob/main/Images/Enumeration1.PNG)


Our user has no inline policies so we'll get his group information

![alt text](https://github.com/Zi-Stonga/IAM-AttachRolePolicy-Priv-Escalation/blob/main/Images/Policy.PNG)


![alt text](https://github.com/Zi-Stonga/IAM-AttachRolePolicy-Priv-Escalation/blob/main/Images/Policy1.PNG)

![alt text](https://github.com/Zi-Stonga/IAM-AttachRolePolicy-Priv-Escalation/blob/main/Images/Policy2.PNG)

![alt text](https://github.com/Zi-Stonga/IAM-AttachRolePolicy-Priv-Escalation/blob/main/Images/Policy3.PNG)

We see that we have the ability to attach a role policy to the Support Role. Let's take a look at the Support Role.

![alt text](https://github.com/Zi-Stonga/IAM-AttachRolePolicy-Priv-Escalation/blob/main/Images/Support.PNG)

Let's enumerate for policies associated with the Support Role.

![alt text](https://github.com/Zi-Stonga/IAM-AttachRolePolicy-Priv-Escalation/blob/main/Images/Enumerate.PNG)

![alt text](https://github.com/Zi-Stonga/IAM-AttachRolePolicy-Priv-Escalation/blob/main/Images/AccessingNotSensitiveBucket.PNG)



The Support Role has a policy attached granting S3 data access. We'll assume that role.

![alt text](https://github.com/Zi-Stonga/IAM-AttachRolePolicy-Priv-Escalation/blob/main/Images/TempCredentials.PNG)

![alt text](https://github.com/Zi-Stonga/IAM-AttachRolePolicy-Priv-Escalation/blob/main/Images/TempC.PNG)

![alt text](https://github.com/Zi-Stonga/IAM-AttachRolePolicy-Priv-Escalation/blob/main/Images/Bucket_contents.PNG)



