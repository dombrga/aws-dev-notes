## aws cloudformation
1. infrastructure as code (IAC)
   - provision and management of infrastucsure using code instead of manual process, like doing it in console.
2. benefits
   1. quickly duplicate env across regions and accounts.
   2. avoid human error because of template.

**Exam pro tip:** Whenever possible, select an answer that does not include manual steps. Think automation and IAC if possible.

## aws cloudformation
1. aws svc to declare aws infra as code for repeatable automated deployment via **stacks**.
2. support tags and stack identifiers.
3. supports json and yaml.
4. aws cf template sections
   1. Resources - only required section, others are optional.
   2. Parameters - used to input custom values.
   3. Outputs - output values from stack for easy reference.
   4. Mappings
   5. Conditions
5. Stacks are regional.
6. aws cf service role - allows cf to make api calls to resources for you.
7. Infrastructure composer - to visualize

## Delete aws cf stacks
1. Termination policy
   - to be enabled for each stack.
   - prevent stacks from being deleted.
   - disabled by default
2. Stack policy
   - prevent resource updates.

## cf stack sets
1. feature that enables you to create, update, delete stacks across multi accounts and regions.
2. centrally manage stacks.
3. permissions
   1. self-managed
   2. service-managed

## aws cf change sets
1. to preview how all proposed changes to existing stack might impact current resources.
2. changes will only be made when you execute the change set.

## cf custom resources
1. write custom and complex logic not supported by built in resource types.
2. example: executing db migration or init script after rds instance is created.

## cfn-init
1. helper script in cf that helps define init tasks.
2. similar to user data in ec2 instance.
3. defined in Metadata section of ec2 resource.
4. allows to update ec2 instances in place.

## aws service catalog
1. to create ang manage catalogs of IT services deemed to be approved for use within aws.
2. deploy pre-approved catalog items (cf templates)

## aws proton
1. automate iac provisioning and deployment.
2. define standardized infra for serverless and container-based apps.