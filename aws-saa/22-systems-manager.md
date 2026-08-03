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

## automation and documents
1. tool that simplifies common maintenance and remediation tasks.
2. supports ec2, rd2, s3, more.
3. Create own or use predefined automations.
4. Automation - tasks defined in a runbook performed Automation service.
   1. disable public access for sec grps
   2. restarting ec2 w/wo approval
5. Triggering automation
   1. Schedule using Maintenance Windows
   2. via EventBridge.
   3. works with AWS Config rule remediations.
   4. manually trigger in console or cli.
6. aws sm Documents
   - allows you to define actions that Systems Manager performs on managed instances.
   - there are owned by Amazon, not customizable.
   - can create own.
   - create and shared docs.
7. **Exam scenario:** Enforce compliance of ec2, use Automation to remediate

## Run command
1. allow you to remotely and securely manage managed nodes.
2. automate common admin tasks and perform one-time config changes at scale.
3. execute scripts, one time command.
4. Connect via SSM agent.
5. Concepts
   1. Logging - commands logs can be saved to s3 and cw logs.
   2. Trigger - console, sdk, cli, eventbridge.
   3. Security - API activity is captured via AWS cloudtrail. Restrict access by iam.