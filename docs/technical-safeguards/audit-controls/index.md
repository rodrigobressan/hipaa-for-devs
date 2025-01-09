---
title: Audit Controls
parent: Technical Safeguards
nav_order: 2
---

This post will break down the Audit Controls requirement, provide real-world examples, and offer best practices for both product development and infrastructure management to ensure HIPAA compliance. We'll also refer to Amazon Web Services (AWS) as an example of how cloud infrastructure can be used to meet these standards.

## What is the Audit Controls Standard?

The Audit Controls standard requires organizations to:

> "Implement hardware, software, and/or procedural mechanisms that record and examine activity in information systems that contain or use electronic protected health information (EPHI)."
>

In simpler terms, it means your system must have the ability to log and review user actions related to EPHI. These logs help identify any security breaches, unauthorized access, or other suspicious activities.

## How to Implement HIPAA-Compliant Audit Controls in Your Product

### 1. **Use Logging Mechanisms for EPHI Access and Modifications**

Your system must record when users access or modify EPHI. This includes capturing details like:

- **Who** accessed the data
- **What** action was performed (e.g., read, modify, delete)
- **When** the action occurred
- **Where** the action originated from (IP address, device type)
- **Why** (if applicable, such as a request made via a support ticket)

### Example:

If a healthcare worker accesses a patient's medical records, an audit log should capture the username, the patient ID, the timestamp, and the type of access (e.g., view or edit).

AWS Tools for Logging:

- **AWS CloudTrail**: CloudTrail allows you to record API calls made on AWS services and store them in a secure log file. This can capture user actions like accessing a database or changing configuration settings.
- **AWS CloudWatch Logs**: CloudWatch can collect logs from your EC2 instances or Lambda functions, providing detailed information about application-level events.

### 2. **Monitor Logs Regularly**

It’s not enough to just collect logs. You must also review them periodically to identify unusual or unauthorized activities.

### Example:

Let’s say an employee accesses sensitive records outside of regular working hours. Your audit controls should flag this as an anomaly.

AWS Tools for Monitoring:

- **AWS GuardDuty**: This is an intelligent threat detection service that can automatically monitor your AWS environment for unusual activity and potential security threats.
- **AWS Security Hub**: Security Hub aggregates security findings from various AWS services, including GuardDuty and CloudTrail, to give you an overview of any suspicious activities.

### 3. **Define Clear Access Control Policies**

It’s important to set clear policies on who can access EPHI and what they can do with it. Implement role-based access controls (RBAC) so that only authorized personnel have access to specific data.

### Example:

A nurse should only be able to view patient records, not modify them. An administrator, on the other hand, may have permissions to both view and update data.

AWS Tools for Access Control:

- **AWS Identity and Access Management (IAM)**: IAM helps you control who can access what resources in AWS. You can define specific roles (e.g., nurse, administrator) and attach permissions based on those roles.

### 4. **Ensure Data Integrity with Non-Repudiation**

The Audit Controls standard also requires you to ensure data integrity. This means that once data is recorded in the audit logs, it should not be tampered with or deleted. You need to ensure that logs are protected and available for future review.

### Example:

Imagine a situation where an attacker tries to delete their tracks after accessing EPHI. Your audit logs should be tamper-proof to prevent this.

AWS Tools for Data Integrity:

- **AWS CloudTrail Log Integrity**: CloudTrail logs can be encrypted and stored in a way that prevents tampering, ensuring the integrity of the audit trail.
- **Amazon S3 with Object Locking**: Store logs in S3 with versioning and object locking to prevent unauthorized deletions or modifications.

### 5. **Establish Incident Response Procedures**

If your audit logs reveal unauthorized access, you need to have a process in place to investigate and respond. This includes identifying the issue, assessing the damage, and taking corrective actions.

### Example:

If an audit report flags an unauthorized access attempt, your team should have a clear process to follow to investigate, resolve, and document the incident.

AWS Tools for Incident Response:

- **AWS Lambda**: Set up automated workflows that respond to specific events, such as sending an alert to security personnel when suspicious activity is detected.
- **Amazon SNS**: Integrate Amazon Simple Notification Service (SNS) to trigger automatic notifications when certain events are logged.

## Key Questions to Consider for Audit Controls

To ensure your system is compliant, ask the following questions:

- **What audit control mechanisms are reasonable and appropriate for my system?**
  Consider factors like the size of your organization, the volume of EPHI processed, and the sensitivity of the data when determining what should be logged and monitored.
- **What are the audit control capabilities of the information systems I’m using?**
  Review the logging features and integrations offered by your infrastructure (e.g., AWS CloudTrail, CloudWatch) and your application framework.
- **Do my audit controls help ensure compliance with the required Information System Activity Review?**
  Make sure your logs are sufficient to allow for regular reviews, audits, and compliance checks as required by HIPAA.

## Best Practices for Maintaining Audit Controls

1. **Conduct Regular Security Audits**: Perform periodic security audits to ensure that your logging and monitoring mechanisms are working as expected.
2. **Automate Where Possible**: Use automated tools to gather logs and monitor suspicious activity, so you can react quickly to potential breaches.
3. **Educate Your Team**: Ensure that your team understands the importance of logging and reporting on EPHI access and modifications.
4. **Document Everything**: Keep thorough records of your audit logs and any incidents for potential audits or investigations.