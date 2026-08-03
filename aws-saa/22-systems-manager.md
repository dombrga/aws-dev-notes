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