# Enhancing Security and Compliance with AWS Control Tower Landing Zone - Upgrade to Version 3.2

In the world of cloud computing, maintaining robust security and compliance standards is paramount. One of the key tools in achieving this is AWS Control Tower, a powerful service that helps organizations set up and govern a secure, multi-account AWS environment. Recently, AWS Control Tower released version 3.2, introducing critical improvements and changes that align with best practices for enhanced security and compliance. In this blog post, we'll explore these changes, their significance, and why the upgrade to [version 3.2](https://docs.aws.amazon.com/controltower/latest/userguide/2023-all.html#lz-3-2) is essential for organizations using AWS Control Tower.

## The Role Transition

In previous versions of AWS Control Tower Landing Zone, such as version 3.0, the **AWSControlTowerExecution** role played a crucial role in performing operations within member accounts. This role, while functional, had a broad set of permissions, which could potentially introduce security risks. 

## Introducing AWSServiceRoleForAWSControlTower 

With the release of AWS Control Tower Landing Zone version 3.2, a new Service-Linked Role (SLR) named **AWSServiceRoleForAWSControlTower** takes center stage. This SLR is designed to adhere to the principle of least privilege, which means it provides only the permissions required for specific tasks. In the case of AWSServiceRoleForAWSControlTower, its scope includes creating and maintaining managed rules in member accounts, publishing security notifications through AWS Simple Notification Service (SNS), and verifying drift.

## Expected Impact on AWS CloudTrail and GuardDuty Alerts:

During the upgrade process, Control Tower will be shifting from the use of the "AWSControlTowerExecution" role to the newly introduced "AWSServiceRoleForAWSControlTower." While this transition is a significant step toward enhancing security and access control, it comes with a brief but expected side effect.

AWS CloudTrail, which meticulously records actions and events within our AWS accounts, may experience a momentary disruption. Specifically, there may be a temporary disabling of CloudTrail functionality across all member accounts. This interruption is anticipated to last for a brief period, estimated to be approximately one to two minutes. Please note that this disruption is a natural part of the transition process and is not indicative of any issues.

Additionally, due to this temporary pause in AWS CloudTrail, it's possible that GuardDuty alerts, which help us detect and respond to potential security threats, may be triggered during this brief interval. 

## Action Plan

To execute this upgrade, plan for a scheduled downtime in your AWS environment. The Control Tower Landing Zone upgrade to version 3.2 is a deliberate and strategic step that should be undertaken with care. It's essential to communicate the change effectively to all relevant stakeholders and coordinate the upgrade across all accounts within your organization.