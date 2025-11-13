---

layout: single
title: "Remotely Run Commands on an EC2 Instance with AWS Systems Manager"
permalink: /remotely_run_commands/
author_profile: true
toc: true
toc_sticky: true
toc_label: "AWS System Manager"
header:
  overlay_color: "#db9a39"
  overlay_filter: "0.5"

---

**Remotely Run Commands on an EC2 Instance with AWS Systems Manager**

**Project Overview**

A hands-on implementation of AWS Systems Manager to remotely manage EC2 instances without traditional SSH access. This project demonstrates cloud infrastructure management following enterprise security best practices.

**Technologies Used**

AWS Systems Manager - Remote command execution and fleet management

Amazon EC2 - Virtual server instances

AWS IAM - Identity and access management

Amazon Linux - Operating system

Shell Scripting - Automation commands

**Problem Statement**

As a System Administrator, I needed to update packages on EC2 instances while adhering to strict security policies that prohibited:

  Direct SSH access to production servers

  Use of bastion hosts

  Remote PowerShell connections

**Solution Architecture**

The solution leverages AWS Systems Manager's Run Command feature to securely execute administrative tasks on EC2 instances through AWS's managed infrastructure.

**Implementation Walkthrough**

**Step 1: Create IAM Role for Systems Manager**

First, I created an IAM role that allows EC2 instances to communicate with Systems Manager.
<details>
<summary>📸 Click to view: IAM Console</summary>
![IAM Console](/assets/images/running_commands/step1_create_iam_role.png)
</details>
_Key Actions:_

Created EnablesEC2ToAccessSystemsManagerRole role

Attached AmazonEC2RoleforSSM policy

Enabled EC2-to-Systems Manager communication

**Step 2: Launch EC2 Instance**

Next, I launched an Amazon Linux EC2 instance with the IAM role attached.
<details>
<summary>📸 Click to view: EC2 Console Dashboard</summary>
![EC2 Console]({{ site.baseurl }}/assets/images/running_commands/step2_ec2_launch.png)

<summary>📸 Click to view: Attaching IAM Role</summary>
![Attach IAM Role]({{ site.baseurl }}/assets/images/projects/aws-ssm/12-attach-iam-role.png)
Attaching the IAM role to enable Systems Manager access
</details>
_Key Actions:_

Selected Amazon Linux 2 AMI (pre-installed with SSM Agent)

Chose t2.micro instance type

No SSH key pair required - demonstrating secure access via Systems Manager

Attached the IAM role created in Step 1


Step 3: Update Systems Manager Agent
Following AWS best practices, I updated the SSM Agent on the newly created instance.
<details>
<summary>📸 Click to view: Systems Manager Console</summary>
![Systems Manager Console]({{ site.baseurl }}/assets/images/projects/aws-ssm/13-ssm-console.png)
Navigating to AWS Systems Manager console
</details>
<details>
<summary>📸 Click to view: Fleet Manager</summary>
![Fleet Manager]({{ site.baseurl }}/assets/images/projects/aws-ssm/14-fleet-manager.png)
Opening Fleet Manager to view managed instances
</details>
<details>
<summary>📸 Click to view: Selecting Instance</summary>
![Select Instance]({{ site.baseurl }}/assets/images/projects/aws-ssm/15-select-instance.png)
Selecting the MyEC2Tutorial instance from Fleet Manager
</details>
<details>
<summary>📸 Click to view: Node Actions Menu</summary>
![Node Actions]({{ site.baseurl }}/assets/images/projects/aws-ssm/16-node-actions.png)
Choosing Execute Run Command from Node Actions dropdown
</details>
<details>
<summary>📸 Click to view: Update SSM Agent Document</summary>
![Update SSM Agent]({{ site.baseurl }}/assets/images/projects/aws-ssm/17-update-ssm-agent.png)
Selecting AWS-UpdateSSMAgent document for agent update
</details>
<details>
<summary>📸 Click to view: Selecting Target Instance</summary>
![Select Target]({{ site.baseurl }}/assets/images/projects/aws-ssm/18-select-target.png)
Selecting the target instance for the update command
</details>
<details>
<summary>📸 Click to view: Command Success ✅</summary>
![Command Success]({{ site.baseurl }}/assets/images/projects/aws-ssm/19-command-success.png)
Successful agent update confirmation
</details>
Key Actions:

Used Fleet Manager to view managed instances
Executed AWS-UpdateSSMAgent document
Verified successful command execution


Step 4: Run Remote Shell Script
Finally, I remotely executed a package update command without SSH access.
<details>
<summary>📸 Click to view: Run Shell Script Document</summary>
![Run Shell Script]({{ site.baseurl }}/assets/images/projects/aws-ssm/20-run-shell-script.png)
Selecting AWS-RunShellScript document for remote execution
</details>
<details>
<summary>📸 Click to view: Entering Update Command</summary>
![Enter Command]({{ site.baseurl }}/assets/images/projects/aws-ssm/21-enter-command.png)
Entering the yum update command: sudo yum update -y
</details>
<details>
<summary>📸 Click to view: Target Selection</summary>
![Select Target Again]({{ site.baseurl }}/assets/images/projects/aws-ssm/22-select-target-run.png)
Selecting target instance for command execution
</details>
<details>
<summary>📸 Click to view: Command Execution Status</summary>
![Command Running]({{ site.baseurl }}/assets/images/projects/aws-ssm/23-command-running.png)
Monitoring command execution in progress
</details>
<details>
<summary>📸 Click to view: Command Output & Results</summary>
![View Output]({{ site.baseurl }}/assets/images/projects/aws-ssm/24-view-output.png)
Viewing detailed command output and verification
</details>
Command Executed:
bashsudo yum update -y
Key Actions:

Executed shell script remotely via Systems Manager
Performed system package updates without SSH
Monitored command execution and reviewed output


Step 5: Cleanup Resources
To avoid unnecessary charges, I terminated all resources.
<details>
<summary>📸 Click to view: Terminating Instance</summary>
![Terminate Instance]({{ site.baseurl }}/assets/images/projects/aws-ssm/25-terminate-instance.png)
Terminating the EC2 instance to complete cleanup
</details>

Key Achievements
✅ Implemented secure remote management without SSH access
✅ Automated administrative tasks at scale
✅ Followed AWS security best practices
✅ Successfully managed instance lifecycle
✅ Demonstrated proficiency with AWS management tools
Skills Demonstrated

Cloud Infrastructure Management: EC2 instance configuration and lifecycle management
Security & Compliance: IAM role creation, policy attachment, and access control
Automation: Remote command execution and systems administration
AWS Services: Systems Manager, EC2, IAM, Fleet Manager
Linux Administration: Package management and system updates
Documentation: Clear technical documentation and process recording

Lessons Learned

AWS Systems Manager provides a secure alternative to traditional SSH access
IAM roles are essential for service-to-service communication in AWS
Fleet Manager simplifies management of multiple instances
Proper documentation of infrastructure decisions is crucial
Security controls can be maintained while enabling operational efficiency

Future Enhancements

Implement automated patching schedules using Maintenance Windows
Configure State Manager for compliance monitoring
Set up Session Manager for interactive shell access
Create custom SSM documents for recurring tasks
Integrate with AWS CloudWatch for monitoring and alerts

Technical Specifications

AWS Region: Configurable across all AWS regions
Cost: Free Tier eligible
Duration: 10-minute implementation
Difficulty Level: Beginner
Instance Type: t2.micro
Operating System: Amazon Linux 2

Conclusion
This project demonstrates practical cloud infrastructure management skills using AWS Systems Manager. By implementing secure, scalable remote management capabilities, I've shown the ability to balance operational requirements with security best practices—a critical skill for modern DevOps and Cloud Engineering roles.

Project Status: ✅ Completed
Date: October 2025
AWS Services: Systems Manager, EC2, IAM

📋 Quick Reference
<details>
<summary>📚 View All Screenshots (Expandable Gallery)</summary>
IAM Setup

[IAM Console]({{ site.baseurl }}/assets/images/projects/aws-ssm/01-iam-console.png)
[Create Role]({{ site.baseurl }}/assets/images/projects/aws-ssm/02-create-role.png)
[Select EC2]({{ site.baseurl }}/assets/images/projects/aws-ssm/03-select-ec2.png)
[Add Permissions]({{ site.baseurl }}/assets/images/projects/aws-ssm/04-add-permissions.png)
[Name Role]({{ site.baseurl }}/assets/images/projects/aws-ssm/05-name-role.png)

EC2 Launch

[EC2 Console]({{ site.baseurl }}/assets/images/projects/aws-ssm/06-ec2-console.png)
[Name Instance]({{ site.baseurl }}/assets/images/projects/aws-ssm/07-name-instance.png)
[Select AMI]({{ site.baseurl }}/assets/images/projects/aws-ssm/08-select-ami.png)
[Instance Type]({{ site.baseurl }}/assets/images/projects/aws-ssm/09-instance-type.png)
[No Key Pair]({{ site.baseurl }}/assets/images/projects/aws-ssm/10-no-keypair.png)
[Network Settings]({{ site.baseurl }}/assets/images/projects/aws-ssm/11-network-settings.png)
[Attach IAM Role]({{ site.baseurl }}/assets/images/projects/aws-ssm/12-attach-iam-role.png)

Systems Manager Operations

[SSM Console]({{ site.baseurl }}/assets/images/projects/aws-ssm/13-ssm-console.png)
[Fleet Manager]({{ site.baseurl }}/assets/images/projects/aws-ssm/14-fleet-manager.png)
[Select Instance]({{ site.baseurl }}/assets/images/projects/aws-ssm/15-select-instance.png)
[Node Actions]({{ site.baseurl }}/assets/images/projects/aws-ssm/16-node-actions.png)
[Update Agent]({{ site.baseurl }}/assets/images/projects/aws-ssm/17-update-ssm-agent.png)
[Select Target]({{ site.baseurl }}/assets/images/projects/aws-ssm/18-select-target.png)
[Command Success]({{ site.baseurl }}/assets/images/projects/aws-ssm/19-command-success.png)
[Run Shell Script]({{ site.baseurl }}/assets/images/projects/aws-ssm/20-run-shell-script.png)
[Enter Command]({{ site.baseurl }}/assets/images/projects/aws-ssm/21-enter-command.png)
[Run Command]({{ site.baseurl }}/assets/images/projects/aws-ssm/22-select-target-run.png)
[Command Running]({{ site.baseurl }}/assets/images/projects/aws-ssm/23-command-running.png)
[View Output]({{ site.baseurl }}/assets/images/projects/aws-ssm/24-view-output.png)
[Terminate]({{ site.baseurl }}/assets/images/projects/aws-ssm/25-terminate-instance.png)

</details>
