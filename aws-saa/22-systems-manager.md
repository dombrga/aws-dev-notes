## aws systems manager
1. suite of tools to view, control, automate nodes in aws, other cloud providers, onprem.
2. must be managed, means SSM agent installed and connected.
3. iam permissions required.
4. SSM Agent
   - required amazon software that runs on the nodes.
   - allows aws system manager to update, manage, configure resources.
   - need IAM permissions
   - possible to install SSM on youw own compute or another cloud.
5. Capabilities
   1. automation
   2. run command
   3. patch manager
   4. parameter store
   5. maintenance windows
   6. session manager.

## Patch manager and maintenance windows
1. Patch manager
   - automate patching of managed instances.
   - OS and app patches.
   - supports Windows.
   - supports Linux.
   - ec2 instances, edge devicesm onprem, VMs
   - **patch policies**, and **patch baselines** to config patching rules.
   - **Scan** and **Scan and install** patching ops.
   - offers predefined and custom patch baselines.
   - **Exam scenario:** If need to automate OS updates and scan for patch compliance of fleet of thousands of windows and linux ec2 instances, think of Patch Manager.
2. Maintenenace Windows
   - define schedule for performing possibly disruptive actions on managed instances.
   - supports s3, sqs, opensearch service, but mostly for ec2.